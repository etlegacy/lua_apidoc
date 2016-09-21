=========
Functions
=========

**Functions** allow to manipulate and control the server, or alter internal structures and entities.


Modules
=======


et.RegisterModname( modname )
-----------------------------

Registers a descriptive name for this mod.

* **modname** is the name to register the Lua module.


vmnumber = et.FindSelf()
------------------------

Returns the assigned Lua VM slot number.

* **vmnumber** is the returned slot number assigned to this Lua VM.


modname, signature = et.FindMod( vmnumber )
-------------------------------------------

Returns the name and SHA1 signature for the mod loaded in a VM slot.

* **vmnumber** is the VM slot number of the Lua module.
* **modname, signature** are the returned registered module's name and SHA-1 signature. Returns **nil, nil** if the VM slot is invalid.


success = et.IPCSend( vmnumber, message )
-----------------------------------------

Sends a message string to the mod in the another VM slot.

* **vmnumber** is the VM slot number of the Lua module to send a message to.
* **message** is the message to sent to the Lua module.

Returns 1 if the message is sent successfully, and 0 if it fails.

.. important:: The mod receiving message must have an `et_IPCReceive() <functions.html#et-ipcreceive-vmnumber-message>`__ callback.

.. note:: Data cannot be received and sent back in the same server frame.


et_IPCReceive( vmnumber, message )
----------------------------------

Called when another module sends an `et.IPCSend() <functions.html#success-et-ipcsend-vmnumber-message>`__ message to this module.

* **vmnumber** is the VM slot number of the sender.
* **message** is the message sent.

.. important:: The sender module must be loaded earlier in the `lua_modules <cvars.html#lua-modules>`__ cvar, otherwise the receiver module cannot find it.

.. tip:: See the `Inter Process Communication (IPC) <sample.html#inter-process-communication-ipc>`__ sample code for an example of communication between different loaded Lua modules.


Printing
========


et.G_Print( text )
------------------

Prints text to the server console.

* **text** is the printed string.


et.G_LogPrint( text )
---------------------

Prints text to the server console and writes it to the server log.

* **text** is the printed and logged string.


Argument handling
=================

These functions are to be used within the `command callback <callbacks.html#commands>`__ functions.


args = et.ConcatArgs( index )
-----------------------------

Returns all arguments beginning concatenated into a single string.

* **index** is the index of the first argument in the concatenated string.
* **args** is the returned concatenated string.


argcount = et.trap_Argc()
-------------------------

Returns the number of command line arguments in the server command.

* **argcount** is the returned count of arguments.


arg = et.trap_Argv( index )
---------------------------

Returns the contents of the command line argument.

* **index** is the index of the argument to return.
* **arg** is the returned argument.


Cvars
=====


cvarvalue = et.trap_Cvar_Get( name )
------------------------------------

Returns the value of the given cvar.

* **name** is the name of the cvar.
* **cvarvalue** is the returned string containing the value. If there is no cvar with the given name, the returning string has zero length.


et.trap_Cvar_Set( name, cvarvalue )
-----------------------------------

Sets value to a cvar.

* **name** is the name of the cvar to set.
* **cvarvalue** is the new value for the cvar.


Configstrings
=============


configstring = et.trap_GetConfigstring( index )
-----------------------------------------------

Returns content of the configstring index.

* **index** is the index of the configstring. See `et.CS_* constants <constants.html#cs-constants>`__ for possible values.
* **configstring** is the returned string containing the full configstring.


et.trap_SetConfigstring( index, value )
---------------------------------------

Sets the full configstring.

* **index** is the configstring index. See `et.CS_* constants <constants.html#cs-constants>`__ for possible values.
* **value** is the full configstring to set.


Server
======


et.trap_SendConsoleCommand( when, command )
-------------------------------------------

Sends command to the server console.

* **when** tells when the command is executed. See `et.EXEC_* constants <constants.html#exec-constants>`__ for possible values.
* **command** is the full command to execute.


Clients
=======


et.trap_SendServerCommand( clientnum, command )
-----------------------------------------------

Sends the command command to the client clientnum. If clientnum is `-1`, the command is broadcast to all clients.

.. tip:: See `SendServerCommand() <misc.html#sendservercommand>`__ for a detailed example usage of possible commands.


et.trap_DropClient( clientnum, reason, bantime )
-------------------------------------------------

Disconnects client from the server.

* **clientnum** is the slot number of the client.
* **reason** is the descriptive reason for the kick which is reported to the client.
* **bantime** is the length of the ban in seconds.


clientnum = et.ClientNumberFromString( string )
-----------------------------------------------

Searches for one partial match with player name.

* **string** is a pattern to match against client names.
* **clientnum** is the returned client slot number if one match is found, otherwise **nil** is returned (none or more than one match).


et.G_Say( clientNum, mode, text )
---------------------------------

Sends a chat command on behalf of client.

* **clientnum** is the slot number of the client.
* **mode** is the broadcast mode. See `et.SAY_* constants <constants.html#say-constants>`__.
* **text** is the chat text.


et.MutePlayer( clientnum, duration, reason )
--------------------------------------------

Mutes the specified player.

* **clientnum** is the slot number of the client to mute.
* **duration** is the optional duration of the mute in seconds.
* **reason** is the optional reason of the mute.


et.UnmutePlayer( clientnum )
----------------------------

Unmutes the specified player.

* **clientnum** is the slot number of the client to unmute.


Userinfo
========


userinfo = et.trap_GetUserinfo( clientNum )
-------------------------------------------

Returns the userinfo string of a client.

* **clientnum** is the slot number of the client.
* **userinfo** is the returned string of the specified client.


et.trap_SetUserinfo( clientnum, userinfo )
------------------------------------------

Sets the userinfo string of the client to the specified userinfo.

* **clientnum** is the slot number of the client.
* **userinfo** is the userinfo string that replaces the current userinfo.

.. note:: The `et.ClientUserinfoChanged() <#et-clientuserinfochanged-clientnum>`__ function must be called after this function for the changes to take effect.


et.ClientUserinfoChanged( clientnum )
-------------------------------------

Loads the new userinfo string of the client and sets the client settings to match it.

* **clientnum** is the slot number of the client.


String utility
==============


newinfostring = et.Info_RemoveKey( infostring, key )
----------------------------------------------------

Removes a key and its associated value from an infostring.

* **infostring** is the infostring from which to remove the key.
* **key** is the key to remove.
* **newinfostring** is the returned modified infostring without the key.


newinfostring = et.Info_SetValueForKey( infostring, key, value )
----------------------------------------------------------------

Sets a value in an infostring.

* **infostring** is the original infostring.
* **key** is the key to set.
* **value** is the value to set to the key. If empty, the key is removed from the infostring.
* **newinfostring** is the returned modified infostring.


keyvalue = et.Info_ValueForKey( infostring, key )
-------------------------------------------------

Returns a value from an infostring.

* **infostring** is the infostring from where to search the key.
* **key** is the key which value is returned.
* **keyvalue** is the returned value from the searched key. If key is not present in the infostring, an empty string is returned.


cleanstring = et.Q_CleanStr( string )
-------------------------------------

Returns string stripped of all color codes and special characters.

* **string** is the string to clean.
* **cleanstring** is the returned cleaned string.


Filesystem
==========


fd, len = et.trap_FS_FOpenFile( filename, mode )
------------------------------------------------

Opens a file in the local file system.

* **filename** is the name of the file to open. The file is opened under the current working directory and absolute paths will not work.
* **mode** is the access mode the file is opened. See `et.FS_* constants <constants.html#fs-constants>`__ for possible values.
* **fd, len** are returned descriptor of the file and the length of the file. On error, len returns **-1**.


filedata = et.trap_FS_Read( fd, count )
---------------------------------------

Reads from an open file.

* **fd** is the descriptor of the file to read.
* **count** is the amount of bytes to read.
* **filedata** is the returned value that have the read bytes.


count = et.trap_FS_Write( filedata, count, fd )
-----------------------------------------------

Writes at the end of an open file.

* **filedata** is a block of bytes to write.
* **count** is the size of the block to write.
* **fd** is the descriptor of the file.
* **count** is the returned amount of bytes written to the file.


et.trap_FS_FCloseFile( fd )
---------------------------

Closes an opened file.

* **fd** is the descriptor of the opened file.


et.trap_FS_Rename( oldname, newname )
-------------------------------------

Renames a file in the local file system.

* **oldname** is the name of the file to rename.
* **newname** is the name the old file name is changed to.


filelist = et.trap_FS_GetFileList( dirname, fileextension )
----------------------------------------------------------------

Retrieves list of files from a directory.

* **dirname** is the name of the directory.
* **filextension** is the file extension of file names to retrieve.
* **filelist** is the returned array of file names strings.


Indexes
=======


soundindex = et.G_SoundIndex( filename )
----------------------------------------

Returns the index to the searched soundfile.

* **filename** is the sound file name that is searched.
* **soundindex** is the returned string index that includes the filename or 0 if not found.


modelindex = et.G_ModelIndex( filename )
----------------------------------------

Returns the index to the searched model.

* **filename** is the name that is searched.
* **modelindex** is the returned string index that included the filename or 0 if not found.


Sound
=====


et.G_globalSound( sound )
-------------------------

Plays a sound to all connected clients.

* **sound** is the name of the sound to play.


et.G_Sound( entnum, soundindex )
--------------------------------

Plays a sound originating from position of an entity.

* **entnum** is the number of the entity which position is used as the sound origin.
* **soundindex** is the index of the sound that is played.


et.G_ClientSound( clientnum, soundindex )
-----------------------------------------

Plays a sound originating from a client entity to the team members of that client.

* **clientnum** is the slot number of the connected player.
* **soundindex** is the index to the sound to play.


Miscellaneous
=============


milliseconds = et.trap_Milliseconds()
-------------------------------------

Returns level time.

* **milliseconds** is the returned time in milliseconds.


success = et.isBitSet( bit, value )
-----------------------------------

Checks bit status of a bitmask value.

* **bit** is the checked bit.
* **value** is the bitmask value.

Returns 1 if the bit is set in the bitmask value, and 0 if it is not.


et.G_Damage( target, inflictor, attacker, damage, dflags, mod )
---------------------------------------------------------------

Damages target entity on behalf of the attacker entity.

* **target** is the entity number to damage.
* **inflictor** is the entity number that does the damage.
* **attacker** is the entity number that causes the **inflictor** entity to cause damage to **target**.
* **damage** is the amount of damage to inflict.
* **dflags** is the type of damage to inflict. See `Damage bitflags <misc.html#damage-bitflags>`__ for possible values.
* **mod** is the means of death. See `et.MOD_* constants <constants.html#mod-constants>`__ for possible values.


et.G_AddSkillPoints( clientNum, skill, points )
-----------------------------------------------

Adds points to the client's skill.

* **clientNum** is the slot number of the client.
* **skill** identifies the skill that the points are added to. See `Skill types <misc.html#skill-types>`__ for possible values.
* **points** is the amount of points to add.


et.G_LoseSkillPoints( clientNum, skill, points )
------------------------------------------------

Removes points to the client's skill.

* **clientNum** is the slot number of the client.
* **skill** identifies the skill that the points are removed from. See `Skill types <misc.html#skill-types>`__ for possible values.
* **points** is the amount of points to remove.


et.G_XP_Set ( clientNum , xp, skill, add )
------------------------------------------

Sets XP of the client.

* **clientNum** is the slot number of the client.
* **xp** is the number of XP points.
* **skill** identifies the skill that the points are added to. See `Skill types <misc.html#skill-types>`__ for possible values.
* **add** sets the XP points if 0, or adds to the existing XP points if 1.


et.G_ResetXP ( clientNum )
--------------------------

Resets XP of the client.

* **clientNum** is the slot number of the client.


et.AddWeaponToPlayer( clientNum, weapon, ammo, ammoclip, setcurrent )
---------------------------------------------------------------------

Adds a weapon to a client.

* **clientNum** is the slot number of the client.
* **weapon** is the weapon to add. See `et.WP_* constants <constants.html#wp-constants>`__ for possible values.
* **ammon** is the number of ammo to add.
* **ammoclip** is the number of ammo clip to add.
* **setcurrent** sets the weapon as current weapon if 1, or does not select it if 0.


et.RemoveWeaponFromPlayer( clientNum, weapon )
----------------------------------------------

Removes a weapon from a client.

* **clientNum** is the slot number of the client.
* **weapon** is the weapon to add. See `et.WP_* constants <constants.html#wp-constants>`__ for possible values.


Entities
========


entnum = et.G_CreateEntity( params )
------------------------------------

Creates a new entity.

* **params** are mapscript parameters.
* **entnum** is the returned number of the new entity.


et.G_DeleteEntity( params )
---------------------------

Deletes an entity.

* **params** are mapscript parameters.


entnum = et.G_TempEntity( origin, event )
-----------------------------------------

Spawns a new temp entity to a location.

* **origin** is the location the temp entity is placed.
* **event** is the event type of the entity. See `Event types <misc.html#event-types>`__ for possible values.
* **entnum** is the returned the number of the new entity.


et.G_FreeEntity( entnum )
-------------------------

Deletes an entity.

* **entnum** is the entity number.


count = et.G_EntitiesFree()
---------------------------

Calculates all free entities.

* **count** is the returned number of free entities.

.. note:: Free client entities (slots) are not counted.


et.G_SetEntState( entnum, newstate )
------------------------------------

Sets an entity state.

* **entnum** is the entity number.
* **newstate** is the new entity state.


et.trap_LinkEntity( entnum )
----------------------------

Links an entity.

* **entnum** is the entity number to link.


et.trap_UnlinkEntity( entnum )
------------------------------

Unlinks an entity.

* **entnum** is the entity number to unlink.


spawnval = et.G_GetSpawnVar( entnum, key )
------------------------------------------

Returns a value of a spawnvar.

* **entnum** is the entity number of the target.
* **key** is the key for the value to return. See `Entity fields <fields.html#entity-fields>`__ for possible values.
* **spawnval** is the returned spawn value.


et.G_SetSpawnVar( entnum, key, value )
--------------------------------------

Sets spawn value to an entity.

* **entitynum** is the target entity.
* **key** is the key for the value. See `Entity fields <fields.html#entity-fields>`__ for possible values.
* **value** is the new value for the key.


variable = et.gentity_get ( entnum, fieldname, arrayindex )
-----------------------------------------------------------

Returns a field value associated with an entity.

* **entnum** is the number of the entity.
* **fieldname** is the name of the field to get. See `Fields <fields.html>`__ for possible values.
* **arrayindex**, if present, specifies which element of an array entity field to get.
* **variable** is the returned field value. For NULL entities or clients, **nil** is returned.

.. note:: `arrayindex` is required when accessing array type fields. Array indexes start at 0.


et.gentity_set( entnum, fieldname, arrayindex, value )
------------------------------------------------------

Sets a value in an entity.

* **entnum** is the entity number that is manipulated.
* **fieldname** is the name of the field to manipulate. See `Fields <fields.html>`__ for possible values.
* **value** is the new value.
* **arrayindex**, if present, specifies which element of an array entity field to set.


et.G_AddEvent( ent, event, eventparm )
--------------------------------------

Adds an event to the entity event sequence.

* **ent** is the entity which event sequnce is handled.
* **event** is the event to add.
* **eventparm** is optional parameter for the event.


Shaders
=======


et.G_ShaderRemap( oldShader, newShader )
----------------------------------------

Remaps shader.

* **oldShader** is the old shader.
* **newShader** is the new shader.


et.G_ResetRemappedShaders()
---------------------------

Resets remapped shaders.


et.G_ShaderRemapFlush()
-----------------------

Flushes remapped shaders.


et.G_SetGlobalFog( params )
---------------------------

Sets global fog to a specific color and density.

* **params** are mapscript fog parameters.
