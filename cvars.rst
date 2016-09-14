=====
Cvars
=====

Here are all available Lua cvars.


.. note:: Changing either cvar will cause all currently loaded modules to quit and be unloaded until the next `map_restart`.


lua_modules
-----------

**Default:** "" (disabled)

Space separated list of lua modules for Legacy mod to load. Modules will be run in the order listed.


lua_allowedmodules
------------------

**Default:** "" (disabled)

If set, only lua modules with the matching SHA1 signatures listed in this cvar will be allowed to load. If empty, all loaded modules are allowed.
