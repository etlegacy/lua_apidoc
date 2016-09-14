======
Fields
======

Here are all available Lua fields supported by `et.gentity_get() <functions.html#variable-et-gentity-get-entnum-fieldname-arrayindex>`__ and `et.gentity_set() <functions.html#et-gentity-set-entnum-fieldname-arrayindex-value>`__ functions.


Player fields
=============


=================================  ===========  ========  ==================================
Name                               Type         Flag      Description
=================================  ===========  ========  ==================================
noclip                             INT          RO
lastKillTime                       INT          RO
saved_persistant                   INT_ARRAY    RO
lastConstructibleBlockingWarnTime  INT          RO
landmineSpottedTime                INT          RO
lasthurt_client                    INT          RO
lasthurt_mod                       INT          RO
lasthurt_time                      INT          RO
respawnTime                        INT          RO
inactivityTime                     INT          RW
inactivityWarning                  INT          RW
PCSpecialPickedUpCount             INT          RO
combatState                        INT          RO
deathAnimTime                      INT          RO
deathTime                          INT          RO
disguiseClientNum                  INT          RO
medals                             INT          RO
acc                                FLOAT        RO
hspct                              FLOAT        RO
freezed                            INT          RW
constructSoundTime                 INT          RO

pers.connected                     INT          RO
pers.netname                       STRING       NOPTR
pers.localClient                   INT          RW
pers.initialSpawn                  INT          RW
pers.enterTime                     INT          RW
pers.connectTime                   INT          RO
pers.teamState.state               INT          RW
pers.voteCount                     INT          RW
pers.complaints                    INT          RW
pers.complaintClient               INT          RW
pers.complaintEndTime              INT          RW
pers.lastReinforceTime             INT          RW
pers.applicationClient             INT          RW
pers.applicationEndTime            INT          RW
pers.invitationClient              INT          RW
pers.invitationEndTime             INT          RW
pers.propositionClient             INT          RW
pers.propositionClient2            INT          RW
pers.propositionEndTime            INT          RW
pers.autofireteamEndTime           INT          RW
pers.autofireteamCreateEndTime     INT          RW
pers.autofireteamJoinEndTime       INT          RW
pers.lastSpawnTime                 INT          RO
pers.ready                         INT          RW
pers.lastkilled_client             INT          RO
pers.lastrevive_client             INT          RO
pers.lastkiller_client             INT          RO
pers.lastammo_client               INT          RO
pers.lasthealth_client             INT          RO
pers.lastteambleed_client          INT          RO
pers.lastteambleed_dmg             INT          RO
pers.playerStats.hitRegions        INT_ARRAY    RO
pers.lastBattleSenseBonusTime      INT          RO
pers.lastHQMineReportTime          INT          RO
pers.maxHealth                     INT          RO
pers.playerStats.selfkills         INT          RO

ps.pm_flags                        INT          RO
ps.pm_time                         INT          RO
ps.eFlags                          INT          RO
ps.weapon                          INT          RO
ps.weaponstate                     INT          RO
ps.stats                           INT_ARRAY    RW
ps.persistant                      INT_ARRAY    RW
ps.ping                            INT          RO
ps.powerups                        INT_ARRAY    RW
ps.origin                          VEC3         RW
ps.ammo                            INT_ARRAY    RW
ps.ammoclip                        INT_ARRAY    RW
ps.classWeaponTime                 INT          RW

sess.sessionTeam                   INT          RW
sess.spectatorTime                 INT          RW
sess.spectatorState                INT          RW
sess.spectatorClient               INT          RW
sess.playerType                    INT          RW
sess.playerWeapon                  INT          RW
sess.playerWeapon2                 INT          RW
sess.spawnObjectiveIndex           INT          RW
sess.latchPlayerType               INT          RW
sess.latchPlayerWeapon             INT          RW
sess.latchPlayerWeapon2            INT          RW
sess.ignoreClients                 INT_ARRAY    RW
sess.muted                         INT          RW
sess.skillpoints                   FLOAT_ARRAY  RO
sess.startskillpoints              FLOAT_ARRAY  RO
sess.startxptotal                  FLOAT        RO
sess.skill                         INT_ARRAY    RW
sess.rank                          INT          RW
sess.medals                        INT_ARRAY    RW
sess.referee                       INT          RW
sess.rounds                        INT          RW
sess.spec_invite                   INT          RW
sess.spec_team                     INT          RW
sess.kills                         INT          RW
sess.deaths                        INT          RW
sess.gibs                          INT          RW
sess.self_kills                    INT          RW
sess.team_kills                    INT          RW
sess.team_gibs                     INT          RW
sess.damage_given                  INT          RW
sess.damage_received               INT          RW
sess.team_damage_given             INT          RW
sess.team_damage_received          INT          RW
sess.time_axis                     INT          RW
sess.time_allies                   INT          RW
sess.time_played                   INT          RW
sess.mu                            FLOAT        RW
sess.sigma                         FLOAT        RW
sess.oldmu                         FLOAT        RW
sess.oldsigma                      FLOAT        RW
sess.uci                           INT          RW
sess.aWeaponStats                  WEAPONSTAT   RW
=================================  ===========  ========  ==================================

.. note:: All the session `sess.*` fields will return `nil` unless the entity is associated with a client slot.

.. note:: All array variables need to be get or set with an additional parameter.


Entity fields
=============


=================================  ===========  ========  ==================================
Name                               Type         Flag      Description
=================================  ===========  ========  ==================================
activator                          ENTITY       RO
chain                              ENTITY       RW
classname                          STRING       RW
clipmask                           INT          RW
closespeed                         FLOAT        RW
count                              INT          RW
count2                             INT          RW
damage                             INT          RW
deathType                          INT          RW
delay                              FLOAT        RW
dl_atten                           INT          RW
dl_color                           VEC3         RW
dl_shader                          STRING       RO
dl_stylestring                     STRING       RO
duration                           FLOAT        RW
end_size                           INT          RW
enemy                              ENTITY       RW
entstate                           INT          RO
flags                              INT          RO
harc                               FLOAT        RW
health                             INT          RW
inuse                              INT          RW
isProp                             INT          RO
item                               STRING       RO
key                                INT          RW
message                            STRING       RW
methodOfDeath                      INT          RW
mg42BaseEnt                        INT          RW
missionLevel                       INT          RW
model                              STRING       RO
model2                             STRING       RO
nextTrain                          ENTITY       RW
noise_index                        INT          RW
prevTrain                          ENTITY       RW
props_frame_state                  INT          RO
r.absmax                           VEC3         RO
r.absmin                           VEC3         RO
r.bmodel                           INT          RO
r.contents                         INT          RW
r.currentAngles                    VEC3         RW
r.currentOrigin                    VEC3         RW
r.eventTime                        INT          RW
r.linked                           INT          RO
r.maxs                             VEC3         RW
r.mins                             VEC3         RW
r.ownerNum                         INT          RW
r.singleClient                     INT          RW
r.svFlags                          INT          RW
r.worldflags                       INT          RO
radius                             INT          RW
random                             FLOAT        RW
rotate                             VEC3         RW
s.angles                           VEC3         RW
s.angles2                          VEC3         RW
s.apos                             TRAJECTORY   RW
s.clientNum                        INT          RW
s.constantLight                    INT          RW
s.density                          INT          RW
s.dl_intensity                     INT          RW
s.dmgFlags                         INT          RW
s.eFlags                           INT          RW
s.eType                            INT          RW
s.effect1Time                      INT          RW
s.effect2Time                      INT          RW
s.effect3Time                      INT          RW
s.frame                            INT          RW
s.groundEntityNum                  INT          RO
s.loopSound                        INT          RW
s.modelindex                       INT          RW
s.modelindex2                      INT          RW
s.number                           INT          RO
s.onFireEnd                        INT          RW
s.onFireStart                      INT          RW
s.origin                           VEC3         RW
s.origin2                          VEC3         RW
s.pos                              TRAJECTORY   RW
s.powerups                         INT          RO
s.solid                            INT          RW
s.teamNum                          INT          RW
s.time                             INT          RW
s.time2                            INT          RW
s.weapon                           INT          RO
s.eventParm                        INT          RW
scriptName                         STRING       RO
spawnflags                         INT          RO
spawnitem                          STRING       RO
speed                              INT          RW
splashDamage                       INT          RW
splashMethodOfDeath                INT          RW
splashRadius                       INT          RW
start_size                         INT          RW
tagName                            STRING       NOPTR+RO
tagParent                          ENTITY       RW
takedamage                         INT          RW
tankLink                           ENTITY       RW
target                             STRING       RW
TargetAngles                       VEC3         RW
TargetFlag                         INT          RO
targetname                         STRING       RO
teamchain                          ENTITY       RW
teammaster                         ENTITY       RW
track                              STRING       RO
varc                               FLOAT        RW
wait                               FLOAT        RW
waterlevel                         INT          RO
watertype                          INT          RO
=================================  ===========  ========  ==================================
