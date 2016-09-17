=====
Cvars
=====

**Cvars** control loaded modules.


.. note:: Changing either cvar will cause all currently loaded modules to quit and be unloaded until the next `map_restart`.


lua_modules
-----------

Space separated list of lua modules for Legacy mod to load. Modules will be run in the order listed.


lua_allowedmodules
------------------

If set, only lua modules with the matching SHA1 signatures listed in this cvar will be allowed to load. If empty, all loaded modules are allowed.
