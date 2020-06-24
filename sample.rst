===========
Sample code
===========

.. tip:: If you want to see some specific Lua examples, you can check the `Lua scripts <https://github.com/etlegacy/etlegacy-lua-scripts>`_ repository.


General
=======


General example::

    --[[
    Lua Example ETLegacy
    --]]

    function et_InitGame(levelTime,randomSeed,restart)
        et.RegisterModname("Lua Example") -- Registering the modname.
        et.G_Print("Lua Loaded!\n") -- Printing out that the lua module has been loaded!
    end

    function et_ClientCommand(clientNum, command)
        local mapname = et.trap_Cvar_Get( "mapname" ) -- local varible storing the map name
        if string.lower(command) == "mapname" then -- checking if the command is /mapname
            et.trap_SendServerCommand(clientNum, "chat \"Current Map:"..mapname.." \n\"") -- printing out the map name to the client
        end
        return 1
    end


This code does nothing useful besides demonstrate and exercise the Lua API::

    -- printf wrapper
    function et.G_Printf(...)
           et.G_Print(string.format(unpack(arg)))
    end


    -- test some of the supported etpro lua functions
    function test_lua_functions()
           et.trap_Cvar_Set( "bla1", "bla2" )
           et.G_Printf( "sv_hostname [%s]\n", et.trap_Cvar_Get( "sv_hostname" ) )
           et.G_Printf( "configstring 1 [%s] \n", et.trap_GetConfigstring( 1 ) )
           et.trap_SetConfigstring( 4, "yadda test" )
           et.G_Printf( "configstring 4 [%s]\n", et.trap_GetConfigstring( 4 ) )
           et.trap_SendConsoleCommand( et.EXEC_APPEND, "cvarlist *charge*\n" )
           et.trap_SendServerCommand( -1, "print \"Yadda yadda\"" )
           et.G_Printf( "gentity[1022].classname = [%s]", et.gentity_get( 1022, "classname" ) )
    end


    -- called when game inits
    function et_InitGame( levelTime, randomSeed, restart )
           et.G_Printf( "et_InitGame [%d] [%d] [%d]\n", levelTime, randomSeed, restart )
           et.RegisterModname( "bani qagame " .. et.FindSelf() )
    --     test_lua_functions()
    end


    -- called every server frame
    function et_RunFrame( levelTime )
           if math.mod( levelTime, 1000 ) == 0 then
    --             et.G_Printf( et_RunFrame [%d]\n", levelTime )
           end
    end


    -- called for every clientcommand
    -- return 1 if intercepted, 0 if passthrough
    function et_ClientCommand( clientNum, cmd )
           et.G_Printf( "et_ClientCommand: [%d] [%s]\n", et.trap_Argc(), cmd )
           return 0
    end


    -- called for every consolecommand
    -- return 1 if intercepted, 0 if passthrough
    function et_ConsoleCommand()
           et.G_Printf( "et_ConsoleCommand: [%s] [%s]\n", et.trap_Argc(), et.trap_Argv(0) )
           if et.trap_Argv(0) == "listmods" then
                   i = 1
                   repeat
                           modname, signature = et.FindMod( i )
                           if modname and signature then
                                   et.G_Printf( "vm slot [%d] name [%s] signature [%s]\n", i, modname, signature )
                                   et.IPCSend( i, "hello" )
                           end
                           i = i + 1
                   until modname == nil or signature == nil
                   return 1
           end
           return 0
     end


    -- called when we receive an IPC from another VM
    function et_IPCReceive( vmnumber, message )
           et.G_Printf( "IPCReceive [%d] from [%d] message [%s]\n", et.FindSelf(), vmnumber, message )
    end


    -- called for every ClientConnect
    function et_ClientConnect( clientNum, firstTime, isBot )
           et.G_Printf( "et_ClientConnect: [%d] [%d] [%d]\n", clientNum, firstTime, isBot )
    --     return "go away"
           return nil
    end


    -- called for every ClientDisconnect
    function et_ClientDisconnect( clientNum )
           et.G_Printf( "et_ClientDisconnect: [%d]\n", clientNum )
    end


    -- called for every ClientBegin
    function et_ClientBegin( clientNum )
           et.G_Printf( "et_ClientBegin: [%d]\n", clientNum )
    end


    -- called for every ClientUserinfoChanged
    function et_ClientUserinfoChanged( clientNum )
           et.G_Printf( "et_ClientUserinfoChanged: [%d] = [%s]\n", clientNum, et.trap_GetUserinfo( clientNum ) )
    end


    -- called for every trap_Printf
    function et_Print( text )
    --     et.G_Printf( "et_Print [%s]", text )
    end


Configstring
============

Example::

    -- get the name of client #3 using configstrings
    local cs = et.trap_GetConfigstring(et.CS_PLAYERS + 3)
    local name = et.Info_ValueForKey(cs, "n")


Inter Process Communication (IPC)
=================================

Example scripts illustrating communication between these scripts using the `et.IPCSend() <functions.html#success-et-ipcsend-vmnumber-message>`__ and `et_IPCReceive() <functions.html#et-ipcreceive-vmnumber-message>`__ functions.


Sender
------

Example of sender module::

    --[[
    ipcdemo-admin.lua
    --]]

    local IPCQueue = {}
    local AdminGUIDs = {
            -- name,       guid,                              level
            { "Vetinari", "ABCDEF1234567890ABCDEF1234567890", 5 },
            { "Havelock", "1234567890ABCDEF1234567890ABCDEF", 3 }
        }

    function et_InitGame(levelTime, randomSeed, restart)
         et.RegisterModname("ipcdemo-admin.lua")
    end

    function et_IPCReceive(vm, msg)
        local level
        local junk1, junk2, id = string.find(msg, "IsAdmin:%s+(%d+)")
        if id ~= nil then
            id    = tonumber(id)
            guid  = et.Info_ValueForKey(et.trap_GetUserinfo(id), "cl_guid")
            level = table.foreach(AdminGUIDs,
                function(i, admin)
                    if admin[2] == guid then
                        return(admin[3])
                    end
                end
            )
            if level == nil then
                level = 0
            end
            table.insert(IPCQueue, { vm, level, id })
        end
    end

    function et_RunFrame(lvltime)
        table.foreach(IPCQueue,
            function(i, queue)
                local ok = et.IPCSend(queue[1],
                                string.format("IsAdmin: %d %d", queue[2], queue[3]))
                if ok ~= 1 then
                    local mod, cksum = et.FindMod(queue[1])
                    et.G_Print(string.format("ipcdemo-admin: IPCSend to %s (vm: %d) failed", mod, queue[1]))
                end
            end
        )
        IPCQueue = {}
    end


Receiver
--------

Example of receiver module::

    --[[
    ipcdemo-cmd.lua
    --]]

    local admin_vm    = -1
    local CommandQueue = {}

    function et_InitGame(levelTime, randomSeed, restart)
        local mod = ""
        local sig = ""
        local i = 1
        while mod ~= nil do
            mod, sig = et.FindMod(i)
            if string.find(mod, "^ipcdemo-admin.lua") == 1 then
                admin_vm = i
                mod      = nil
            end
            i = i + 1
        end
        if admin_vm == -1 then
            et.G_Print("ipcdemo-cmd.lua: Could not find vm number for ipcdemo-admin.lua")
        end
        et.RegisterModname("ipcdemo-cmd.lua")
    end

    function et_IPCReceive(vm, msg)
        if vm == admin_vm then
            local junk1,junk2,level,id = string.find(msg, "IsAdmin:%s+(%d+)%s+(%d)")
            if level ~= nil and id ~= nil then
                runAction(tonumber(id), tonumber(level))
            end
        end
    end

    function runAction(id, level)
        local done = table.foreach(CommandQueue,
            function(i, queue)
                if id == queue[1] then
                    if queue[2] <= level then
                        if queue[4] == nil then
                            et.trap_SendConsoleCommand(et.EXEC_INSERT, queue[3])
                        else
                            et.trap_SendConsoleCommand(et.EXEC_INSERT,
                                    string.format("%s %s", queue[3], queue[4]))
                        end
                    end
                    return(i)
                end
            end
        )
        if done ~= nil then
            table.remove(CommandQueue, done)
        end
    end

    function et_ClientCommand(id, command)
        local arg0 = et.trap_Argv(0)
        local arg1 = et.trap_Argv(1)
        if arg0 == "say" then
            if arg1 == "!axis" then
                --          id, lvl, cmd,         argument
                queueCommand(id, 4, "forceteam r", id)
            elseif arg1 == "!allies" then
                queueCommand(id, 4, "forceteam b", id)
            elseif arg1 == "!shuffle" then
                queueCommand(id, 3, "shuffleteamsxp_norestart", nil)
            end
        end
        return(0)
    end

    function queueCommand(id, level, cmd, argument)
        if admin_vm ~= -1 then
            local ok = et.IPCSend(admin_vm, string.format("IsAdmin: %d", id))
            if ok ~= 1 then
                et.G_Print("ipcdemo-cmd: IPCSend to ipcdemo-admin failed")
            else
                table.insert(CommandQueue, { id, level, cmd, argument })
            end
        end
    end


Database
========


Exemple using LuaSQL.


Basic use
---------

Here is an example of the basic use of the library::

    --[[
    LuaSQL demo
    --]]

    -- load driver
    local driver = require "luasql.sqlite3"
    -- create environment object
    env = assert (driver.sqlite3())
    -- connect to data source
    con = assert (env:connect("luasql-test"))
    -- reset our table
    res = con:execute"DROP TABLE people"
    res = assert (con:execute[[
      CREATE TABLE people(
        name  varchar(50),
        email varchar(50)
      )
    ]])
    -- add a few elements
    list = {
      { name="Jose das Couves", email="jose@couves.com", },
      { name="Manoel Joaquim", email="manoel.joaquim@cafundo.com", },
      { name="Maria das Dores", email="maria@dores.com", },
    }
    for i, p in pairs (list) do
      res = assert (con:execute(string.format([[
        INSERT INTO people
        VALUES ('%s', '%s')]], p.name, p.email)
      ))
    end
    -- retrieve a cursor
    cur = assert (con:execute"SELECT name, email from people")
    -- print all rows, the rows will be indexed by field names
    row = cur:fetch ({}, "a")
    while row do
      et.G_Print("Name:" .. row.name .. ", E-mail: " .. row.email .."\n")
      -- reusing the table of results
      row = cur:fetch (row, "a")
    end
    -- close everything
    cur:close() -- already closed because all the result set was consumed
    con:close()
    env:close()


And the output of this script should be::

    Name: Jose das Couves, E-mail: jose@couves.com
    Name: Manoel Joaquim, E-mail: manoel.joaquim@cafundo.com
    Name: Maria das Dores, E-mail: maria@dores.com


Iterator
--------

Here is how to create an iterator over the result of a SELECT query::

    function rows (connection, sql_statement)
      local cursor = assert (connection:execute (sql_statement))
      return function ()
        return cursor:fetch()
      end
    end

Here is how the iterator is used::

    env = assert (require"luasql.mysql".mysql())
    con = assert (env:connect"my_db")
    for id, name, address in rows (con, "select * from contacts") do
      print (string.format ("%s: %s", name, address))
    end

Obviously, the code above only works if there is a table called contacts with the columns id, name and address in this order. At the end of the loop the cursor will be automatically closed by the driver.
