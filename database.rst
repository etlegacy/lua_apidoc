========
Database
========

Both the Legacy mod and the ET:Legacy engine are built-in with `SQLite3 <https://www.sqlite.org/>`_ database support. The engine allows to execute SQL statement directly in console, while the Legacy mod has access through `LuaSQL <https://keplerproject.github.io/luasql/>`_.

.. tip:: See the `Database <sample.html#database>`__ sample code for an example of basic database usage.


Error handling
==============


LuaSQL is just an abstraction layer that communicates between Lua and a database system. Therefore errors can occur on both levels, that is, inside the database client or inside LuaSQL driver.

Errors such as malformed SQL statements, unknown table names etc. are called database errors and will be reported by the function/method returning `nil` followed by the error message provided by the database system. Errors such as wrong parameters, absent connection, invalid objects etc., called API errors, are usually program errors and so will raise a Lua error.

This behavior will be followed by all functions/methods described in this document unless otherwise stated.


Drivers
=======


A LuaSQL driver allows the use of the LuaSQL API with a database management system that corresponds to the driver. To use a driver you have to load it. The example below::

    local driver = require "luasql.sqlite3"

loads the SQLite3 driver and returns a table with an entry with the name of the driver (sqlite3 in this case).

.. Note that you can have more than one driver loaded at the same time doing something like:
..
..    local odbc_driver = require "luasql.odbc"
..    local oci8_driver = require "luasql.oci8"

.. This example also shows that the driver name not always correspond to the Database name, but to the driver name in the file system. Since it refers to the OCI8 API, the Oracle driver has the name oci8.


Environment objects
===================


An environment object is created by calling the driver's initialization function that is stored in the table returned when it was loaded, indexed with the same name as the driver (odbc, postgres etc). The following example, will try to create an environment object using the SQLite3 driver::

    local driver = require "luasql.sqlite3"
    local env = driver.sqlite3()


env:close()
-----------

Closes the environment `env`. Only successful if all connections pertaining to it were closed first.

Returns **true** in case of success; **false** when the object is already closed.


env:connect(sourcename[,username[,password]])
---------------------------------------------

Connects to a data source specified in sourcename using username and password if they are supplied.
The sourcename may vary according to each driver. SQLite3 uses a simple database name.

.. Some use a simple database name, like PostgreSQL, MySQL and SQLite; the ODBC driver expects the name of the DSN; the Oracle driver expects the service name; See also: PostgreSQL, and MySQL extensions.

    -- database path
    local dbpath = string.gsub(et.trap_Cvar_Get("fs_homepath"), "\\", "/").."/"..et.trap_Cvar_Get("fs_game").."/"
    -- connection
    conn = assert(env:connect(dbpath .. "etl.db"))

Returns a `connection object <database.html#connection-objects>`__.

If desired, Lua scripts can also connect to the engine memory database by the following Lua command::

    conn = assert(env:connect("file::memory:?cache=shared"))

.. Note:: The database is only active when the `db_mode <https://dev.etlegacy.com/projects/etlegacy/wiki/List_of_Cvars#db_-Additional>`_ cvar is set.

To save this in memory database to disk use the **saveDB** console command. See also the `db_url <https://dev.etlegacy.com/projects/etlegacy/wiki/List_of_Cvars#db_-Additional>`_ cvar to specify the database path.


Connection objects
==================


A connection object contains specific attributes and parameters of a single data source connection. A connection object is created by calling the `environment:connect <database.html#env-connect-sourcename-username-password>`__ method.


conn:close()
------------

Closes the connection conn. Only successful if all cursors pertaining to it have been closed and the connection is still open.

Returns **true** in case of success and **false** in case of failure.


conn:commit()
-------------

Commits the current transaction.

.. This feature might not work on database systems that do not implement transactions.

Returns **true** in case of success and **false** when the operation could not be performed or when it is not implemented.


conn:execute(statement)
-----------------------

Executes the given `SQL statement`.

Returns a `cursor object <database.html#cursor-objects>`__ if there are results, or the **number of rows** affected by the command otherwise.


conn:rollback()
---------------

Rolls back the current transaction.

.. This feature might not work on database systems that do not implement transactions.

Returns **true** in case of success and **false** when the operation could not be performed or when it is not implemented.


conn:setautocommit(boolean)
---------------------------

Turns on or off the "auto commit" mode.

.. This feature might not work on database systems that do not implement transactions. On database systems that do not have the concept of "auto commit mode", but do implement transactions, this mechanism is implemented by the driver.

Returns **true** in case of success and **false** when the operation could not be performed or when it is not implemented.


Cursor objects
==============


A cursor object contains methods to retrieve data resulting from an executed statement. A cursor object is created by using the `connection:execute <database.html#conn-execute-statement>`__ function.

.. See also PostgreSQL and Oracle extensions.


cur:close()
-----------

Closes this cursor.

Returns **true** in case of success and **false** when the object is already closed.


cur:fetch([table[,modestring]])
-------------------------------

Retrieves the next row of results.

If fetch is called without parameters, the results will be returned directly to the caller. If fetch is called with a table, the results will be copied into the table and the changed table will be returned. In this case, an optional modestring parameter can be used. It is just a string indicating how the resulting table should be constructed.

The mode string can contain:

* **n**: the resulting table will have numerical indices (default)
* **a**: the resulting table will have alphanumerical indices

The numerical indices are the positions of the fields in the SELECT statement; the alphanumerical indices are the names of the fields.
The optional table parameter is a table that should be used to store the next row. This allows the use of a unique table for many fetches, which can improve the overall performance.

A call to fetch after the last row has already being returned will close the corresponding cursor. There is no guarantee about the types of the results: they may or may not be converted to adequate Lua types by the driver.

..  In the current implementation, the PostgreSQL and MySQL drivers return all values as strings while the ODBC and Oracle drivers convert them to Lua types.

Returns **data**, as above, or **nil** if there are no more rows.

.. note: Note that this method could return nil as a valid result.


cur:getcolnames()
-----------------

Returns a **list (table) of column names**.


cur:getcoltypes()
-----------------

Returns a **list (table) of column types**.


SQLite3 extensions
==================


Besides the basic functionality provided by all drivers, the SQLite3 driver also offers this extra feature:


env:connect(sourcename[,locktimeout])
-------------------------------------

In the SQLite3 driver, this method adds an optional parameter that indicate the amount of milisseconds to wait for a write lock if one cannot be obtained immediately. See also `environment objects <database.html#environment-objects>`__.

Returns a `connection object <database.html#connection-objects>`__.


conn:escape(str)
----------------

Escape especial characters in the given string according to the connection's character set. See also the official documentation of function `sqlite3_mprintf <http://www.sqlite.org/c3ref/mprintf.html>`_.

Returns the **escaped string**.
