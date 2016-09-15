=============
Miscellaneous
=============


Damage flags
============

`Damage flags` are bitflags that controls how damage is inflicted.
The following bits are available.


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
