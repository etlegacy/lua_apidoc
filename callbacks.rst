=========
Callbacks
=========

**Callbacks** trigger on specific server events.


qagame execution
================


et_InitGame( levelTime, randomSeed, restart )
---------------------------------------------

Called when qagame initializes.

* **levelTime** is the current level time in milliseconds.
* **randomSeed** is a number that can be used to seed random number generators.
* **restart** indicates if et_InitGame() is being called due to a `map_restart` (1) or not (0).


et_ShutdownGame( restart )
--------------------------

Called when qagame shuts down.

* **restart** indicates if the shutdown is being called due to a `map_restart` (1) or not (0).


et_RunFrame( levelTime )
------------------------

Called when qagame runs a server frame.

* **levelTime** is the current level time in milliseconds.


et_Quit()
---------

Called when Legacy unloads the mod.

The mod should close all open filedescriptors and perform all cleanup.


Client management
=================


rejectreason = et_ClientConnect( clientNum, firstTime, isBot )
--------------------------------------------------------------

Called when a client attempts to connect to the server.

* **clientNum** is the client slot id.
* **firstTime** indicates if this is a new connection (1) or a reconnection (0).
* **isBot** indicates if the client is a bot (1) or not (0).

If the mod accepts the connection, it returns **nil**. Otherwise, the mod should return a string describing the reason the client connection was rejected.


et_ClientDisconnect( clientNum )
--------------------------------

Called when a client disconnects.

* **clientNum** is the client slot id.


et_ClientBegin( clientNum )
---------------------------

Called when a client begins (becomes active, and enters the gameworld).

* **clientNum** is the client slot id.


et_ClientUserinfoChanged( clientNum )
-------------------------------------

Called when a client's Userinfo string has changed.

* **clientNum** is the client slot id.

.. note:: This only gets called when the players `CS_PLAYERS` config string changes, rather than every time the userinfo changes. This only happens for a subset of userinfo fields.


et_ClientSpawn( clientNum, revived, teamChange, restoreHealth )
---------------------------------------------------------------

Called when a client is spawned.

* **clientNum** is the client slot id.
* **revived** indicates if the client was spawned by being revived (1) or not (0).
* **teamChange** indicates if the client changed team (1) or not (0).
* **restoreHealth** indicates if the player health bar is fully restored (1) or not (0).


Commands
========


intercepted = et_ClientCommand( clientNum, command )
----------------------------------------------------

Called when a command is received from a client.

* **clientNum** is the client slot id.
* **command** is the command.

Returns 1 if the command was intercepted by the mod, and 0 if the command was ignored and passed through to the server (and other mods in the chain).

.. tip:: The actual command can be accessed through the argument handling functions, as seen in the `Sample Code <sample.html>`__.


intercepted = et_ConsoleCommand()
---------------------------------

Called when a command is entered on the server console.

Returns 1 if the command was intercepted, and 0 if the command was ignored and passed through to the server (and other mods in the chain).

.. tip:: The actual command can be accessed through the argument handling functions, as seen in the `Sample Code <sample.html>`__.


XP
==


et_UpgradeSkill( clientNum, skill )
-----------------------------------

Called when a client gets a skill upgrade.

* **clientNum** is the client slot.
* **skill** is the skill number.

Returns -1 to override (abort) the qagame function, anything else to "passthrough". Callback may modify skills (or do anything else it wants) during passthrough.


et_SetPlayerSkill( clientNum, skill )
-------------------------------------

Called when a client skill is set.

* **clientNum** is the client slot.
* **skill** is the skill number.

Returns -1 to override (abort) the qagame function, anything else to "passthrough". Callback may modify skills (or do anything else it wants) during passthrough.


Miscellaneous
=============


et_Print( text )
----------------

Called whenever the server or qagame prints a string to the console.


.. warning:: **DO NOT TRUST STRINGS OBTAINED IN THIS WAY!**

             Text may contain a player name and their chat message, which makes it very easy to spoof.


et_Obituary( target, attacker, meansOfDeath )
---------------------------------------------

Called whenever a player is killed.

* **target** is the victim.
* **attacker** is the killer.
* **meansOfDeath** is the means of death.


et_Damage( target, attacker, damage, damageFlags, meansOfDeath)
---------------------------------------------------------------

Called whenever a player gets damage.

* **target** is the victim.
* **attacker** is the killer.
* **damage** is the amount of damage.
* **damageFlags** controls how damage is inflicted. See `Damage bitflags <misc.html#damage-bitflags>`__ for possible values.
* **meansOfDeath** is the means of death. See `et.MOD_* constants <constants.html#mod-constants>`__ for possible values.


et_WeaponFire( clientNum, weapon )
----------------------------------

Called whenever a weapon is shot.

* **clientNum** is the client slot.
* **weapon** is the weapon shot.


et_SpawnEntitiesFromString()
----------------------------

Called when an entity definition is parsed to spawn gentities.
