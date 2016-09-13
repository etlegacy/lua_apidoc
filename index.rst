.. Legacy Lua API documentation master file, created by
   sphinx-quickstart on Tue Sep 13 00:05:27 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Legacy Lua API
==============

Welcome to the Legacy Lua API's documentation!

The **Legacy mod** is the default mod shipped with `ET: Legacy <http://www.etlegacy.com>`_. It supports server-side modifications via the `Lua <http://www.lua.org/>`_ scripting language.

If present, the embedded **Lua 5.3** interpreter will load user-defined scripts from the Legacy directory. It also provides an "et" library of function calls for Lua that allow access to the server engine, and provides callbacks so a server side mod may trigger on specific server events.

For more information about Lua, check out the `Reference Manual <http://www.lua.org/manual/5.3/>`_, the online edition of the book `Programming in Lua <http://www.lua.org/pil/>`_ or the `Lua-users wiki <http://lua-users.org/wiki/>`_.

If you want to see some ET-specific Lua examples, you can check the `ET Legacy Lua scripts <https://github.com/etlegacy/etlegacy-lua_scripts>`_ repository.


Contents
--------

.. toctree::
   :maxdepth: 2

   intro
   cvars
   commands
   functions
   callbacks
   fields
   constants
   database
   sample


Indices and tables
------------------

* :ref:`genindex`
* :ref:`search`

