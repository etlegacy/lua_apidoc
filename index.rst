.. Legacy Lua API documentation master file, created by
   sphinx-quickstart on Tue Sep 13 00:05:27 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Legacy Lua API
==============

Welcome to the Legacy Lua API's documentation!

The **Legacy mod** is the default mod shipped with `ET: Legacy <http://www.etlegacy.com>`_. It supports server-side modifications via the `Lua <http://www.lua.org/>`_ scripting language, with the Legacy Lua API being the interface for communication between them.

The embedded **Lua 5.3** interpreter will load user-defined scripts if present in the `Legacy` directory. The Lua API provides an "et" library of `function calls <functions.html>`__ that allow access to the server engine, and also provides `callbacks <callbacks.html>`__ so a server side mod may trigger on specific server events.

In some cases values can be returned to Legacy mod, whenever something is intercepted (i.e. a command) and prevented to be further handled. This way, new commands can easily be defined or existing ones can be altered.

Through special functions, it is also possible to alter internal structures or entities (manipulate client XP, set and read cvars, remap shaders, etc.).
For example, if a player dies the `et_Obituary( victim, killer, meansOfDeath ) <callbacks.html#et-obituary-target-attacker-meansofdeath>`__ function is executed, and the Lua API allows you to manipulate and control this information.

.. note:: Like qagame, Lua modules are unloaded and reloaded on `map_restart` and map changes, which means that all global variables and other information is lost. Persistent data can be stored in `cvars <functions.html#cvars>`__, external `files <functions.html#filesystem>`__ or `database <database.html>`__.


Implementation
==============

Legacy's Lua API follows mostly the `ETPub <http://www.etpub.org/>`_ implementation with partial code of the `NoQuarter <http://shitstorm.org/noquarter/>`_ implemention. The ETPub implementation being built to be compatible with `ETPro's Lua <http://wolfwiki.anime.net/index.php/Lua_Mod_API>`_, all scripts written in ETPro's documentation should be valid and more or less compatible with Legacy mod's Lua API.

.. important:: As Legacy uses the newer Lua 5.3, you might want to check the **Incompatibilities with the Previous Version** sections of the `Lua 5.1 <https://www.lua.org/manual/5.1/manual.html#7>`_, `Lua 5.2 <https://www.lua.org/manual/5.2/manual.html#8>`_, and `Lua 5.3 <https://www.lua.org/manual/5.3/manual.html#8>`_ manuals while porting scripts written for other mods.


Contents
========

.. toctree::
   :maxdepth: 1

   standard
   cvars
   commands
   functions
   callbacks
   fields
   constants
   misc
   database
   sample
