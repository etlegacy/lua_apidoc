=====
Cvars
=====

Here is a list of all the Lua cvars of Legacy mod.


.. note:: Changing either cvar will cause all currently loaded modules to quit and be unloaded until the next `map_restart`.


lua_modules
-----------

**Default:** "" (disabled)

Space separated list of lua modules for Legacy mod to load. Modules will be run in the order listed.


lua_allowedmodules
------------------

**Default:** "" (disabled)

If set, only lua modules with the matching SHA1 signatures listed in this cvar will be allowed to load.
