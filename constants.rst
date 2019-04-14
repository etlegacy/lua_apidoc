=========
Constants
=========

**Constants** are strings set on the server.


CS constants
============


=============================  ======================================================
Name                           Value
=============================  ======================================================
et.CS_SERVERINFO               0
et.CS_SYSTEMINFO               1
et.CS_MUSIC                    2
et.CS_MESSAGE                  3
et.CS_MOTD                     4
et.CS_WARMUP                   5
et.CS_VOTE_TIME                6
et.CS_VOTE_STRING              7
et.CS_VOTE_YES                 8
et.CS_VOTE_NO                  9
et.CS_GAME_VERSION             10
et.CS_LEVEL_START_TIME         11
et.CS_INTERMISSION             12
et.CS_MULTI_INFO               13
et.CS_MULTI_MAPWINNER          14
et.CS_MULTI_OBJECTIVE          15
et.CS_SCREENFADE               17
et.CS_FOGVARS                  18
et.CS_SKYBOXORG                19
et.CS_TARGETEFFECT             20
et.CS_WOLFINFO                 21
et.CS_FIRSTBLOOD               22
et.CS_ROUNDSCORES1             23
et.CS_ROUNDSCORES2             24
et.CS_MAIN_AXIS_OBJECTIVE      25
et.CS_MAIN_ALLIES_OBJECTIVE    26
et.CS_MUSIC_QUEUE              27
et.CS_SCRIPT_MOVER_NAMES       28
et.CS_CONSTRUCTION_NAMES       29
et.CS_VERSIONINFO              30
et.CS_REINFSEEDS               31
et.CS_SERVERTOGGLES            32
et.CS_GLOBALFOGVARS            33
et.CS_AXIS_MAPS_XP             34
et.CS_ALLIED_MAPS_XP           35
et.CS_INTERMISSION_START_TIME  36
et.CS_ENDGAME_STATS            37
et.CS_CHARGETIMES              38
et.CS_FILTERCAMS               39
et.CS_LEGACYINFO               40
et.CS_SVCVAR                   41
et.CS_CONFIGNAME               42
et.CS_TEAMRESTRICTIONS         43
et.CS_UPGRADERANGE             44
et.CS_MODELS                   64
et.CS_SOUNDS                   320 *(CS_MODELS + MAX_MODELS)*
et.CS_SHADER                   576 *(CS_SOUNDS + MAX_SOUNDS)*
et.CS_SHADERSTATE              608 *(CS_SHADERS + MAX_CS_SHADERS)*
et.CS_SKINS                    609 *(CS_SHADERSTATE + 1)*
et.CS_CHARACTERS               673 *(CS_SKINS + MAX_CS_SKINS)*
et.CS_PLAYERS                  689 *(CS_CHARACTERS + MAX_CHARACTERS)*
et.CS_MULTI_SPAWNTARGETS       753 *(CS_PLAYERS + MAX_CLIENTS)*
et.CS_OID_TRIGGERS             769 *(CS_MULTI_SPAWNTARGETS + MAX_MULTI_SPAWNTARGETS)*
et.CS_OID_DATA                 787 *(CS_OID_TRIGGERS + MAX_OID_TRIGGERS)*
et.CS_DLIGHTS                  805 *(CS_OID_DATA + MAX_OID_TRIGGERS)*
et.CS_SPLINES                  821 *(CS_DLIGHTS + MAX_DLIGHT_CONFIGSTRINGS)*
et.CS_TAGCONNECTS              829 *(CS_SPLINES + MAX_SPLINE_CONFIGSTRINGS)*
et.CS_FIRETEAMS                893 *(CS_TAGCONNECTS + MAX_TAGCONNECTS)*
et.CS_CUSTMOTD                 905 *(CS_FIRETEAMS + MAX_FIRETEAMS)*
et.CS_STRINGS                  911 *(CS_CUSTMOTD + MAX_MOTDLINES)*
et.CS_MAX                      943 *(CS_STRINGS + MAX_CSSTRINGS)*
=============================  ======================================================


MAX constants
=============


=============================  ==================
Name                           Value
=============================  ==================
et.MAX_CLIENTS                 64
et.MAX_MODELS                  256
et.MAX_SOUNDS                  256
et.MAX_CS_SKINS                64
et.MAX_CSSTRINGS               32
et.MAX_CS_SHADERS              32
et.MAX_SERVER_TAGS             256
et.MAX_TAG_FILES               64
et.MAX_MULTI_SPAWNTARGETS      16
et.MAX_DLIGHT_CONFIGSTRINGS    16
et.MAX_SPLINE_CONFIGSTRINGS    8
et.MAX_OID_TRIGGERS            18
et.MAX_CHARACTERS              16
et.MAX_TAGCONNECTS             64
et.MAX_FIRETEAMS               12
et.MAX_MOTDLINES               6
=============================  ==================


GS constants
============


==========================  ==================  =========================================================
Name                        Value               Description
==========================  ==================  =========================================================
et.GS_INITIALIZE            -1                  Map changing/loading
et.GS_PLAYING               0                   Game is running
et.GS_WARMUP_COUNTDOWN      1                   Warmup countdown is active
et.GS_WARMUP                2                   Warmup active (waiting for players to ready themselves)
et.GS_INTERMISSION          3                   Intermission screen is shown to players
et.GS_WAITING_FOR_PLAYERS   4                   Unused?
et.GS_RESET                 5                   Used to reset match instead of restarting map
==========================  ==================  =========================================================


TEAM constants
==============


==================  ==================  =========================================================
Name                Value               Description
==================  ==================  =========================================================
et.TEAM_FREE        0                   Unassigned
et.TEAM_AXIS        1                   Axis
et.TEAM_ALLIES      2                   Allies
et.TEAM_SPECTATOR   3                   Spectators
et.TEAM_NUM_TEAMS   4                   Number of teams
==================  ==================  =========================================================


SK constants
============


==============================================  ==================  =========================================================
Name                                            Value               Description
==============================================  ==================  =========================================================
et.SK_BATTLE_SENSE                              0                   Unassigned
et.SK_EXPLOSIVES_AND_CONSTRUCTION               1                   Engineering
et.SK_FIRST_AID                                 2                   First Aid
et.SK_SIGNALS                                   3                   Signals
et.SK_LIGHT_WEAPONS                             4                   Light Weapons
et.SK_HEAVY_WEAPONS                             1                   Heavy Weapons
et.SK_MILITARY_INTELLIGENCE_AND_SCOPED_WEAPONS  2                   Covert Ops
et.SK_NUM_SKILLS                                3                   Number of skills
==============================================  ==================  =========================================================


WP constants
============


=============================  ==================  ==================================
Name                           Value               Description
=============================  ==================  ==================================
et.WP_NONE                     0                   No weapon
et.WP_KNIFE                    1                   Axis Knife Dagger
et.WP_LUGER                    2                   Luger
et.WP_MP40                     3                   MP40
et.WP_GRENADE_LAUNCHER         4                   Axis Grenade
et.WP_PANZERFAUST              5                   Panzerfaust
et.WP_FLAMETHROWER             6                   Flamethrower
et.WP_COLT                     7                   Colt 1911
et.WP_THOMPSON                 8                   Thompson
et.WP_GRENADE_PINEAPPLE        9                   Allies Grenade
et.WP_STEN                     10                  Sten
et.WP_MEDIC_SYRINGE            11                  Syringe
et.WP_AMMO                     12                  Ammo pack
et.WP_ARTY                     13                  Artillery
et.WP_SILENCER                 14                  Silenced Luger
et.WP_DYNAMITE                 15                  Dynamite
et.WP_SMOKETRAIL               16                  Artillery Initial smoke
et.WP_MAPMORTAR                17                  Fixed Mortars
et.VERYBIGEXPLOSION            18                  Airstrike Explosion effect
et.WP_MEDKIT                   19                  Medic pack
et.WP_BINOCULARS               20                  Binoculars
et.WP_PLIERS                   21                  Pliers
et.WP_SMOKE_MARKER             22                  Airstrike Marker
et.WP_KAR98                    23                  Kar98 (Axis Rifle)
et.WP_CARBINE                  24                  M1 Garand
et.WP_GARAND                   25                  Scoped M1 Garand
et.WP_LANDMINE                 26                  Landmine
et.WP_SATCHEL                  27                  Satchel
et.WP_SATCHEL_DET              28                  Satchel Detonator
et.WP_SMOKE_BOMB               29                  Smoke Grenade
et.WP_MOBILE_MG42              30                  Mobile MG42
et.WP_K43                      31                  K43 (Axis Sniper Rifle)
et.WP_FG42                     32                  FG42
et.WP_DUMMY_MG42               33                  Fixed MG42
et.WP_MORTAR                   34                  Allies Mortar
et.WP_AKIMBO_COLT              35                  Akimbo Colts 1911
et.WP_AKIMBO_LUGER             36                  Akimbo Lugers
et.WP_GPG40                    37                  Kar98 (Grenade Loaded)
et.WP_M7                       38                  M1 Garand (Grenade Loaded)
et.WP_SILENCED_COLT            39                  Silenced Colt 1911
et.WP_GARAND_SCOPE             40                  Scoped M1 Garand (Scoped Mode)
et.WP_K43_SCOPE                41                  K43 (Scoped Mode)
et.WP_FG42SCOPE                42                  FG42 (Scoped Mode)
et.WP_MORTAR_SET               43                  Allies Deployed Mortar
et.WP_MEDIC_ADRENALINE         44                  Adrenaline
et.WP_AKIMBO_SILENCEDCOLT      45                  Akimbo Silenced Colts 1911
et.WP_AKIMBO_SILENCEDLUGER     46                  Akimbo Silenced Lugers
et.WP_MOBILE_MG42_SET          47                  Deployed Mobile MG42
et.WP_KNIFE_KABAR              48                  Allies KA-BAR Knife
et.WP_MOBILE_BROWNING          49                  Mobile Browning
et.WP_MOBILE_BROWNING_SET      50                  Deployed Mobile Browning
et.WP_MORTAR2                  51                  Axis Mortar
et.WP_MORTAR2_SET              52                  Axis Deployed Mortar
et.WP_BAZOOKA                  53                  Bazooka
et.WP_MP34                     54                  MP34
et.WP_AIRSTRIKE                55                  Airstrike
et.WP_NUM_WEAPONS              56                  Number of weapons
=============================  ==================  ==================================


MOD constants
=============


=========================================  ==================
Name                                       Value
=========================================  ==================
et.MOD_UNKNOWN                             0
et.MOD_MACHINEGUN                          1
et.MOD_BROWNING                            2
et.MOD_MG42                                3
et.MOD_GRENADE                             4
et.MOD_KNIFE                               5
et.MOD_LUGER                               6
et.MOD_COLT                                7
et.MOD_MP40                                8
et.MOD_THOMPSON                            9
et.MOD_STEN                                10
et.MOD_GARAND                              11
et.MOD_SILENCER                            12
et.MOD_FG42                                13
et.MOD_FG42SCOPE                           14
et.MOD_PANZERFAUST                         15
et.MOD_GRENADE_LAUNCHER                    16
et.MOD_FLAMETHROWER                        17
et.MOD_GRENADE_PINEAPPLE                   18
et.MOD_MAPMORTAR                           19
et.MOD_MAPMORTAR_SPLASH                    20
et.MOD_KICKED                              21
et.MOD_DYNAMITE                            22
et.MOD_AIRSTRIKE                           23
et.MOD_SYRINGE                             24
et.MOD_AMMO                                25
et.MOD_ARTY                                26
et.MOD_WATER                               27
et.MOD_SLIME                               28
et.MOD_LAVA                                29
et.MOD_CRUSH                               30
et.MOD_TELEFRAG                            31
et.MOD_FALLING                             32
et.MOD_SUICIDE                             33
et.MOD_TARGET_LASER                        34
et.MOD_TRIGGER_HURT                        35
et.MOD_EXPLOSIVE                           36
et.MOD_CARBINE                             37
et.MOD_KAR98                               38
et.MOD_GPG40                               39
et.MOD_M7                                  40
et.MOD_LANDMINE                            41
et.MOD_SATCHEL                             42
et.MOD_SMOKEBOMB                           43
et.MOD_MOBILE_MG42                         44
et.MOD_SILENCED_COLT                       45
et.MOD_GARAND_SCOPE                        46
et.MOD_CRUSH_CONSTRUCTION                  47
et.MOD_CRUSH_CONSTRUCTIONDEATH             48
et.MOD_CRUSH_CONSTRUCTIONDEATH_NOATTACKER  49
et.MOD_K43                                 50
et.MOD_K43_SCOPE                           51
et.MOD_MORTAR                              52
et.MOD_AKIMBO_COLT                         53
et.MOD_AKIMBO_LUGER                        54
et.MOD_AKIMBO_SILENCEDCOLT                 55
et.MOD_AKIMBO_SILENCEDLUGER                56
et.MOD_SMOKEGRENADE                        57
et.MOD_SWAP_PLACES                         58
et.MOD_SWITCHTEAM                          59
et.MOD_SHOVE                               60
et.MOD_KNIFE_KABAR                         61
et.MOD_MOBILE_BROWNING                     62
et.MOD_MORTAR2                             63
et.MOD_BAZOOKA                             64
et.MOD_BACKSTAB                            65
et.MOD_MP34                                66
et.MOD_NUM_MODS                            67
=========================================  ==================


PW constants
============


===================  ==================  ======================
Name                 Value               Description
===================  ==================  ======================
et.PW_NONE           0                   No powerup (unused)
et.PW_INVULNERABLE   1                   Has spawn shield
et.PW_NOFATIGUE      4                   Can sprint
et.PW_REDFLAG        5                   Holds Axis objective
et.PW_BLUEFLAG       6                   Holds Allied objective
et.PW_OPS_DISGUISED  7                   Is disguised
et.PW_OPS_CLASS_1    8                   Disguised class helper
et.PW_OPS_CLASS_2    9                   Disguised class helper
et.PW_OPS_CLASS_3    10                  Disguised class helper
et.PW_ADRENALINE     11                  Has adrenaline
et.PW_BLACKOUT       14                  Spec blackout
et.PW_MVCLIENTLIST   15                  Static MV client info
et.PW_NUM_POWERUPS   16                  Number of powerups
===================  ==================  ======================


SAY constants
=============


=================  ==================  ==================
Name               Value               Description
=================  ==================  ==================
et.SAY_ALL         0                   Message will be sent to everyone.
et.SAY_TEAM        1                   Message will be sent to the client's team.
et.SAY_BUDDY       2                   Message will be sent to the client's fireteam.
et.SAY_TEAMNL      3                   Message will be sent to the client's team, without location.
=================  ==================  ==================


PM constants
============


==================  ==========  ==================
Name                Value       Description
==================  ==========  ==================
et.PM_NORMAL        0           Can accelerate and turn
et.PM_NOCLIP        1           Noclip movement
et.PM_SPECTATOR     2           Still run into walls
et.PM_DEAD          3           No acceleration or turning, but free falling
et.PM_FREEZE        4           Stuck in place with no control
et.PM_INTERMISSION  5           No movement or status bar
==================  ==========  ==================


STATS constants
===============


======================  ==========  ==================
Name                    Value       Description
======================  ==========  ==================
et.STAT_HEALTH          0           Health
et.STAT_KEYS            1           16 bit fields (only used for binoculars)
et.STAT_DEAD_YAW        2           Look this direction when dead
et.STAT_MAX_HEALTH      3           Health/armor limit
et.STAT_PLAYER_CLASS    4           Player class in multiplayer
et.STAT_XP              5           XP (realtime version, doesn't need to go through scoreboard)
et.STAT_PS_FLAGS        6           Player state flags (used for leaning status)
et.STAT_AIRLEFT         7           Airtime
et.STAT_SPRINTTIME      8           Sprinttime
et.STAT_ANTIWARP_DELAY  9           Extra lag on the lagometer to reflect warp status
======================  ==========  ==================


CONTENTS constants
==================


============================  ==========  ==================
Name                          Value       Description
============================  ==========  ==================
et.CONTENTS_NONE              0x00000000
et.CONTENTS_SOLID             0x00000001
et.CONTENTS_LIGHTGRID         0x00000004
et.CONTENTS_LAVA              0x00000008
et.CONTENTS_SLIME             0x00000010
et.CONTENTS_WATER             0x00000020
et.CONTENTS_FOG               0x00000040
et.CONTENTS_MISSILECLIP       0x00000080
et.CONTENTS_ITEM              0x00000100
et.CONTENTS_MOVER             0x00004000
et.CONTENTS_AREAPORTAL        0x00008000
et.CONTENTS_PLAYERCLIP        0x00010000
et.CONTENTS_MONSTERCLIP       0x00020000
et.CONTENTS_TELEPORTER        0x00040000
et.CONTENTS_JUMPPAD           0x00080000
et.CONTENTS_CLUSTERPORTAL     0x00100000
et.CONTENTS_DONOTENTER        0x00200000  Unused
et.CONTENTS_DONOTENTER_LARGE  0x00400000  Unused
et.CONTENTS_ORIGIN            0x01000000
et.CONTENTS_BODY              0x02000000
et.CONTENTS_CORPSE            0x04000000
et.CONTENTS_DETAIL            0x08000000
et.CONTENTS_STRUCTURAL        0x10000000
et.CONTENTS_TRANSLUCENT       0x20000000
et.CONTENTS_TRIGGER           0x40000000
et.CONTENTS_NODROP            0x80000000
============================  ==========  ==================


SURF constants
==============


====================  ==========  ==================
Name                  Value       Description
====================  ==========  ==================
et.SURF_NODAMAGE      0x00000001
et.SURF_SLICK         0x00000002
et.SURF_SKY           0x00000004
et.SURF_LADDER        0x00000008
et.SURF_NOIMPACT      0x00000010
et.SURF_NOMARKS       0x00000020
et.SURF_SPLASH        0x00000040
et.SURF_NODRAW        0x00000080
et.SURF_HINT          0x00000100
et.SURF_SKIP          0x00000200
et.SURF_NOLIGHTMAP    0x00000400
et.SURF_POINTLIGHT    0x00000800
et.SURF_METAL         0x00001000
et.SURF_NOSTEPS       0x00002000
et.SURF_NONSOLID      0x00004000
et.SURF_LIGHTFILTER   0x00008000
et.SURF_ALPHASHADOW   0x00010000
et.SURF_NODLIGHT      0x00020000
et.SURF_WOOD          0x00040000
et.SURF_GRASS         0x00080000
et.SURF_CERAMIC                   Unused
et.SURF_GRAVEL        0x00100000
et.SURF_GLASS         0x00200000
et.SURF_SNOW          0x00400000
et.SURF_ROOF          0x00800000
et.SURF_RUBBLE        0x01000000
et.SURF_CARPET        0x02000000
et.SURF_MONSTERSLICK  0x04000000
et.SURF_MONSLICK_W    0x08000000
et.SURF_MONSLICK_N    0x10000000
et.SURF_MONSLICK_E    0x20000000
et.SURF_MONSLICK_S    0x40000000
et.SURF_LANDMINE      0x80000000
====================  ==========  ==================


MASK constants
==============


===================  ======================================================  ======================
Name                 Value                                                   Description
===================  ======================================================  ======================
et.MASK_ALL          (-1)
et.MASK_SOLID        (CONTENTS_SOLID)
et.MASK_PLAYERSOLID  (CONTENTS_SOLID | CONTENTS_PLAYERCLIP | CONTENTS_BODY)
et.MASK_WATER        (CONTENTS_WATER | CONTENTS_LAVA | CONTENTS_SLIME)
et.MASK_OPAQUE       (CONTENTS_SOLID | CONTENTS_LAVA)
et.MASK_SHOT         (CONTENTS_SOLID | CONTENTS_BODY | CONTENTS_CORPSE)
et.MASK_MISSILESHOT  (MASK_SHOT | CONTENTS_MISSILECLIP)
===================  ======================================================  ======================


EXEC constants
==============


=================  ==================
Name               Description
=================  ==================
et.EXEC_NOW        Executes instantly, don't return until completed.
et.EXEC_INSERT     Insert at current position, but don't run yet.
et.EXEC_APPEND     Append at the end of the command buffer.
=================  ==================


FS constants
============


=================  ==================
Name               Description
=================  ==================
et.FS_READ         Opens file in read only mode.
et.FS_WRITE        Opens file in write mode, truncates old file if a file already exists.
et.FS_APPEND       Opens file in write mode at the end of file, old file is not erased if it already exists.
et.FS_APPEND_SYNC  Like et.FS_APPEND, but file buffer is flushed to file on hard drive directly after every write operation.
=================  ==================


Misc constants
==============


=================  ====================================  ==================
Name               Value                                 Description
=================  ====================================  ==================
et.HOSTARCH        "WIN32", "MACOS" or "UNIX"            Host architecture
=================  ====================================  ==================


Lua constants
=============


=================  ====================================  ==================
Name               Value                                 Description
=================  ====================================  ==================
LUA_PATH           ./legacy/?.lua;                       Ease use of the require function
                   ./legacy/lualibs/?.lua;               to load scripts
                   fs_homepath/fs_game/?.lua;
                   fs_homepath/fs_game/lualibs/?.lua
LUA_CPATH          ./legacy/lualibs/?.so;                Ease use of the require function
                   fs_homepath/legacy/lualibs/?.so       to load libraries
LUA_DIRSEP         /                                     Directory separator
_VERSION           Lua 5.3                               Lua version
=================  ====================================  ==================
