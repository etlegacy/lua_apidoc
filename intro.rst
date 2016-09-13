============
Introduction
============

Legacy's Lua API is the interface for communication between Lua and Legacy mod.

The basic idea for this Lua API is event-management. After a certain event, the lua-interaction-code in Legacy executes a predefined function, with additional predefined arguments.

For example, if a player dies the `et_Obituary( victim, killer, meansOfDeath ) <callbacks.html#et-obituary-victim-killer-meansofdeath>`__ function is executed. The Lua API allows you to manipulate and control this information.

In some cases you can also return a value to Legacy, whenever you intercepted something (i.e. a command), and prevent Legacy to handle it further.

This way, you can easily define new commands, or alter existing ones. Through special functions, it is also possible to alter Legacy's internal structures or Entities (remap shaders, manipulate client XP, set and read cvars, etc.).


Implementation
==============

Legacy's Lua API follows mostly the `ETPub <http://www.etpub.org/>`_ implementation with partial code of the `NoQuarter <http://shitstorm.org/noquarter/>`_ implemention. The ETPub implementation being built to be compatible with `ETPro's Lua <http://wolfwiki.anime.net/index.php/Lua_Mod_API>`_, all scripts written in ETPro's documentation should be valid and more or less compatible with Legacy mod's Lua API.

.. important:: As Legacy uses the newer Lua 5.3, you might want to check the *Incompatibilities with the Previous Version* sections of the `Lua 5.1 <https://www.lua.org/manual/5.1/manual.html#7>`_, `Lua 5.2 <https://www.lua.org/manual/5.2/manual.html#8>`_, and `Lua 5.3 <https://www.lua.org/manual/5.3/manual.html#8>`_ manuals while porting scripts written for other mods.

Standard libraries
==================

The following standard Lua libraries are initialized by default and available to Legacy Lua scripts:

* `basic <http://www.lua.org/manual/5.3/manual.html#6.1>`_
* `string <http://www.lua.org/manual/5.3/manual.html#6.4>`_
* `table <http://www.lua.org/manual/5.3/manual.html#6.6>`_
* `math <http://www.lua.org/manual/5.3/manual.html#6.7>`_
* `i/o <http://www.lua.org/manual/5.3/manual.html#6.8>`_
* `os <http://www.lua.org/manual/5.3/manual.html#6.9>`_ (available features vary depending on your OS)
