=============
Miscellaneous
=============

Configstring
============

Configstrings are strings (often in the form of a set of `key\\value` pairs) set on the server and automatically sent to each client.
They can be accessed with the `Configstring <functions.html#configstrings>`__ and `String utility <functions.html#string-utility>`__ functions.

.. tip:: A group of related configstrings usually only have a symbolic name for the first value, with a number added to get a particular value. For example, to access a user `CS_PLAYERS` configstring you must use `et.trap_GetConfigstring(et.CS_PLAYERS + slotNumber)`.

See `et.CS_* constants <constants.html#cs-constants>`__ for available configstrings.

Here is the detailed content of the user **CS_PLAYERS** configstring:

===  ===========================  ===================================================
Key  Value                        Description
===  ===========================  ===================================================
n    pers.netname                 Nickname
t    sess.sessionTeam             Team
c    sess.playerType              Class
lc   sess.latchPlayerType         Latched class
r    sess.rank                    Rank
m    medalStr                     Medals
s    skillStr                     Skills
dn   disguiseClientNum            Disguised covert ops
w    sess.playerWeapon            Weapon
lw   sess.latchPlayerWeapon       Latched primary weapon
sw   sess.latchPlayerWeapon2      Latched secondary weapon
mu   sess.muted                   Muted
ref  sess.referee                 Referee
u    sess.uci                     GeoIP `ISO 3166-1 <https://en.wikipedia.org/wiki/ISO_3166-1>`_ country code
===  ===========================  ===================================================


Userinfo
========


Userinfo strings are strings set on clients for server processing.
They can be accessed with the `Userinfo <functions.html#userinfo>`__ functions.


=====================  ================================  ==================================================
Key                    Example Value                     Description
=====================  ================================  ==================================================
cg_etVersion           Enemy Territory, ET 2.60b         Mod name, ET version
cg_uinfo               12 0 100                          Client settings [cg_autoreload/cg_autoactivate/cg_predictitems] [cl_timenudge] [cl_maxpackets]
g_password             none                              Server password
cl_guid                0123456789ABCDEF0123456789ABCDEF  GUID
cl_wwwDownload         1                                 Missing files downloading toggle
name                   ETLPlayer                         Nickname
rate                   2500                              Rate setting
snaps                  20                                Snaps setting
protocol               84                                Game protocol
qport                  4834                              Randomly chosen as startup
challenge              -686256943                        Random 31 bit integer
ip                     192.168.123.45:27960              IP and port
=====================  ================================  ==================================================

.. note:: The userinfo string of bots only includes the `cl_guid`, `name`, `rate`, `snap` and `ip` keys/values.


SendServerCommand
=================

`et.trap_SendServerCommand() <functions.html#et-trap-sendservercommand-clientnum-command>`__ is used to send a command from the server to one or more clients.

The first argument is the slot number of the client the command is sent to. If it's equal to **-1**, the command is broadcast to all clients.

The following commands can be issued:


Printing
--------


Print a message to the client's console::

    "print \"Message\n\""

Print a message to the client's annoucement area and console::

    "cpm \"Message\n\""

Print a message to the center of the client's screen::

    "cp \"Message\n\""

Print a message to the client's console and writes it to the statsdump file::

    "sc \"Message\n\""


Chatting
--------

Print a message as a global chat message on behalf of the specified client::

    "chat ClientNum \"Message\""

Print a message as a team chat message on behalf of the specified client::

    "tchat ClientNum \"Message\" X-Location Y-Location Z-Location"

* The **X,Y,Z-Location**'s are optional parameters that represent the client's location.

.. Print a message as a fireteam chat message on behalf of the specified client:
..
..    "bchat ClientNum \"Message\" X-Location Y-Location Z-Location"
..
.. * The X,Y,Z-Location's are optional parameters that represent the client's location.

Print a message as a global chat message via rcon (qsay command)::

    "chat \"Message\""


Voice Chat
----------


Send a global voice chat on behalf of the specified client::

    "vchat VoiceOnly ClientNum 50 Vsay-String Vsay-Number \"Custom-Message\"".

* **VoiceOnly** prints a global chat message on behalf of ClientNum if set to **0**, or only play the sound if set to **1**.
* **Vsay-String** is the global voice chat message.
* **Vsay-Number** is the vsay number of Vsay as listed in the .voice files. It is by default random, but can be set by the player by passing parameters to the vsay command (`/vsay <Vsay-Number> <Vsay-String>`).
* **Custom-Message** is by default empty (\"\"). If set, it prints the message in the chat area.

Send a team voice chat on behalf of the specified client::

    "vtchat VoiceOnly ClientNum 50 Vsay-String X-Location Y-Location Z-Location Vsay-Number \"Custom-Message\""

* **VoiceOnly** prints a team chat message on behalf of ClientNum if set to **0**, or only play the sound if set to **1**.
* **Vsay-String** is the team voice chat message.
* **Vsay-Number** is the vsay number of Vsay as listed in the .voice files. It is by default random, but can be set by the player by passing parameters to the vsay command (`/vsay <Vsay-Number> <Vsay-String>`).
* The **X,Y,Z-Location**'s are optional parameters that represent the client's location.
* **Custom-Message** is by default empty (\"\"). If set, it prints the message in the chat area.

Send a fireteam voice chat on behalf of the specified client::

    "vtchat VoiceOnly ClientNum 50 Fireteam-String X-Location Y-Location Z-Location Vsay-Number \"Custom-Message\""

* **VoiceOnly** prints a fireteam chat message on behalf of ClientNum if set to **0**, or only play the sound if set to **1**.
* **Fireteam-String** is the fireteam voice chat message.
* **Vsay-Number** is the vsay number of Vsay as listed in the .voice files. It is by default random, but can be set by the player by passing parameters to the vsay command (`/vsay <Vsay-Number> <Vsay-String>`).
* The **X,Y,Z-Location**'s are optional parameters that represent the client's location.
* **Custom-Message** is by default empty (\"\"). If set, it prints the message in the chat area.


Fireteam
--------


Show a fireteam invitation message to the client::

    "application Number"

* if **Number** is **> -1**, the "Accept ...'s application to join your fireteam?" message is displayed. In this case, **Number** is the ClientNum of the applying client.
* if **Number** is **-1**, the "Your application has been submitted" message is displayed.
* if **Number** is **-2**, the "Your application failed" message is displayed.
* if **Number** is **-3**, the "Your application has been approved" message is displayed.
* if **Number** is **-4**, the "Your application reply has been sent" message is displayed.

Show a fireteam proposition message to the client::

    "proposition Number Number2"

* if **Number** is **> -1**, the "Accept ...'s proposition to invite ... to your fireteam?" message is displayed. In this case, **Number** is the ClientNum of the proposed client, and **Number2** is the ClientNum of the proposing player.
* if **Number** is **-1**, the "Your proposition has been submitted" message is displayed.
* if **Number** is **-2**, the "Your proposition was rejected" message is displayed.
* if **Number** is **-3**, the "Your proposition was accepted" message is displayed.
* if **Number** is **-4**, the "Your proposition reply has been sent" message is displayed.
* **Number2** is an optional parameter only used when **Number** > **-1**.

Show a fireteam invitation message to the client::

    "invitation Number"

* if **Number** is **> -1**, the "Accept ..'s invitation to join your fireteam?" message is displayed. In this case, **Number** is the ClientNum of the applying client.
* if **Number** is **-1**, the "Your invitation has been submitted" message is displayed.
* if **Number** is **-2**, the "Your invitation rejected" message is displayed.
* if **Number** is **-3**, the "Your invitation was accepted" message is displayed.
* if **Number** is **-4**, the "Your invitation reply has been sent" message is displayed.


Others
------


Show the complaint vote message to the client::

    "complaint Number"

* if **Number** is **> 1**, the "File complaint against ... for team-killing?" message is displayed. In this case, **Number** is the ClientNum of the teamkilling player.
* if **Number** is **-1**, the "Complaint filed" message is displayed.
* if **Number** is **-2**, the "Complaint dismissed" message is displayed.


Set the client game selected spawnpoint::

   "setspawnpt Number"

* **Number** is the selected spawnpoint.

Disconnect the client with a "Server disconnected" message::

    "disconnect \"reason\""

* **reason** is an optional parameter to show a reason after "Server disconnected".

.. note:: Use `et.trap_DropClient() <functions.html#et-trap-dropclient-clientnum-reason-bantime>`__ instead.

Set a client's configstring to a string::

    "cs Number \"String\""

* **String** is the new configstring string.

.. note:: Use `et.trap_SetUserinfo() <functions.html#et-trap-setuserinfo-clientnum-userinfo>`__ instead.

Replace any texture::

    "remapShader \"OldShader\" \"NewShader\" #"

* **OldShader** is the old shader.
* **NewShader** is the new shader.
* **#** is the Timeoffset, which currently should be left as 0.


Damage bitflags
===============


=============================  ==================  ==================================
Name                           Value               Description
=============================  ==================  ==================================
DAMAGE_RADIUS                  1                   Indirect splash damage
DAMAGE_HALF_KNOCKBACK          2                   Do less knockback
DAMAGE_NO_KNOCKBACK            4                   Do not affect velocity, just view angles
DAMAGE_NO_PROTECTION           8                   Armor, shields, invulnerability, godmode have no effect
DAMAGE_NO_TEAM_PROTECTION      16                  (unused)
DAMAGE_DISTANCEFALLOFF         32                  Distance falloff
=============================  ==================  ==================================


Skill types
===========


===========================================  ==================  ====================
Name                                         Value               Description
===========================================  ==================  ====================
SK_BATTLE_SENSE                              0					 Battle Sense
SK_EXPLOSIVES_AND_CONSTRUCTION               1					 Engineering
SK_FIRST_AID                                 2					 First Aid
SK_SIGNALS                                   3					 Signals
SK_LIGHT_WEAPONS                             4					 Light Weapons
SK_HEAVY_WEAPONS                             5					 Heavy Weapons
SK_MILITARY_INTELLIGENCE_AND_SCOPED_WEAPONS  6					 Covert Ops
===========================================  ==================  ====================


Event types
===========


=============================  ==================  ==================================
Name                           Value               Description
=============================  ==================  ==================================
EV_NONE                        0
EV_FOOTSTEP                    1
EV_FOOTSTEP_METAL              2                   (unused)
EV_FOOTSTEP_WOOD               3                   (unused)
EV_FOOTSTEP_GRASS              4                   (unused)
EV_FOOTSTEP_GRAVEL             5                   (unused)
EV_FOOTSTEP_ROOF               6                   (unused)
EV_FOOTSTEP_SNOW               7                   (unused)
EV_FOOTSTEP_CARPET             8                   (unused)
EV_FOOTSPLASH                  9
EV_FOOTWADE                    10                  (unused)
EV_SWIM                        11
EV_STEP_4                      12
EV_STEP_8                      13
EV_STEP_12                     14
EV_STEP_16                     15
EV_FALL_SHORT                  16
EV_FALL_MEDIUM                 17
EV_FALL_FAR                    18
EV_FALL_NDIE                   19
EV_FALL_DMG_10                 20
EV_FALL_DMG_15                 21
EV_FALL_DMG_25                 22
EV_FALL_DMG_50                 23
EV_WATER_TOUCH                 24
EV_WATER_LEAVE                 25
EV_WATER_UNDER                 26
EV_WATER_CLEAR                 27
EV_ITEM_PICKUP                 28
EV_ITEM_PICKUP_QUIET           29
EV_GLOBAL_ITEM_PICKUP          30
EV_NOAMMO                      31
EV_WEAPONSWITCHED              32
EV_EMPTYCLIP                   33                  (unused)
EV_FILL_CLIP                   34
EV_MG42_FIXED                  35
EV_WEAP_OVERHEAT               36
EV_CHANGE_WEAPON               37
EV_CHANGE_WEAPON_2             38
EV_FIRE_WEAPON                 39
EV_FIRE_WEAPONB                40
EV_FIRE_WEAPON_LASTSHOT        41
EV_NOFIRE_UNDERWATER           42
EV_FIRE_WEAPON_MG42            43
EV_FIRE_WEAPON_MOUNTEDMG42     44
EV_ITEM_RESPAWN                45                  (unused)
EV_ITEM_POP                    46                  (unused)
EV_PLAYER_TELEPORT_IN          47                  (unused)
EV_PLAYER_TELEPORT_OUT         48                  (unused)
EV_GRENADE_BOUNCE              49
EV_GENERAL_SOUND               50
EV_GENERAL_SOUND_VOLUME        51
EV_GLOBAL_SOUND                52
EV_GLOBAL_CLIENT_SOUND         53
EV_GLOBAL_TEAM_SOUND           54
EV_FX_SOUND                    55
EV_BULLET_HIT_FLESH            56
EV_BULLET_HIT_WALL             57
EV_MISSILE_HIT                 58
EV_MISSILE_MISS                59
EV_RAILTRAIL                   60
EV_BULLET                      61
EV_LOSE_HAT                    62
EV_PAIN                        63
EV_CROUCH_PAIN                 64                  (unused)
EV_DEATH1                      65                  (unused)
EV_DEATH2                      66                  (unused)
EV_DEATH3                      67                  (unused)
EV_OBITUARY                    68
EV_STOPSTREAMINGSOUND          69
EV_POWERUP_QUAD                70
EV_POWERUP_BATTLESUIT          71
EV_POWERUP_REGEN               72
EV_GIB_PLAYER                  73
EV_DEBUG_LINE,                 74                  (unused)
EV_STOPLOOPINGSOUND            75
EV_TAUNT                       76                  (unused)
EV_SMOKE                       77
EV_SPARKS                      78
EV_SPARKS_ELECTRIC             79
EV_EXPLODE                     80
EV_RUBBLE                      81
EV_EFFECT                      82
EV_MORTAREFX                   83
EV_SPINUP                      84
EV_SNOW_ON                     85                  (unused)
EV_SNOW_OFF                    86                  (unused)
EV_MISSILE_MISS_SMALL          87
EV_MISSILE_MISS_LARGE          88
EV_MORTAR_IMPACT               89
EV_MORTAR_MISS                 90
EV_SPIT_HIT                    91                  (unused)
EV_SPIT_MISS                   92                  (unused)
EV_SHARD                       93
EV_JUNK                        94
EV_EMITTER                     95
EV_OILPARTICLES                96
EV_OILSLICK                    97
EV_OILSLICKREMOVE              98
EV_MG42EFX                     99                  (unused)
EV_FLAKGUN1                    100                 (unused)
EV_FLAKGUN2                    101                 (unused)
EV_FLAKGUN3                    102                 (unused)
EV_FLAKGUN4                    103                 (unused)
EV_EXERT1                      104                 (unused)
EV_EXERT2                      105                 (unused)
EV_EXERT3                      106                 (unused)
EV_SNOWFLURRY                  107
EV_CONCUSSIVE                  108                 (unused)
EV_DUST                        109
EV_RUMBLE_EFX                  110
EV_GUNSPARKS                   111
EV_FLAMETHROWER_EFFECT         112
EV_POPUP                       113                 (unused)
EV_POPUPBOOK                   114                 (unused)
EV_GIVEPAGE                    115                 (unused)
EV_MG42BULLET_HIT_FLESH        116
EV_MG42BULLET_HIT_WALL         117
EV_SHAKE                       118
EV_DISGUISE_SOUND              119
EV_BUILDDECAYED_SOUND          120
EV_FIRE_WEAPON_AAGUN           121
EV_DEBRIS                      122
EV_ALERT_SPEAKER               123
EV_POPUPMESSAGE                124
EV_ARTYMESSAGE                 125
EV_AIRSTRIKEMESSAGE            126
EV_MEDIC_CALL                  127
EV_SHOVE_SOUND                 128
EV_BODY_DP                     129
=============================  ==================  ==================================
