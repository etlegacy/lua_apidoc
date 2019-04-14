======
Fields
======

**Fields** are entity parameters supported by `et.gentity_get() <functions.html#variable-et-gentity-get-entnum-fieldname-arrayindex>`__ and `et.gentity_set() <functions.html#et-gentity-set-entnum-fieldname-arrayindex-value>`__ functions.


Player fields
=============


=================================  ===========  ========  ==================================
Name                               Type         Flag      Description
=================================  ===========  ========  ==================================
noclip                             int          ro
lastKillTime                       int          ro
saved_persistant                   int_array    ro
lastConstructibleBlockingWarnTime  int          ro
landmineSpottedTime                int          ro
lasthurt_client                    int          ro
lasthurt_mod                       int          ro
lasthurt_time                      int          ro
respawnTime                        int          ro
inactivityTime                     int          rw
inactivityWarning                  int          rw
combatState                        int          ro
deathAnimTime                      int          ro
deathTime                          int          ro
disguiseClientNum                  int          ro
medals                             int          ro
acc                                float        ro
hspct                              float        ro
freezed                            int          rw
constructSoundTime                 int          ro

pers.connected                     int          ro
pers.netname                       string       noptr
pers.localClient                   int          rw
pers.initialSpawn                  int          rw
pers.enterTime                     int          rw
pers.connectTime                   int          ro
pers.teamState.state               int          rw
pers.voteCount                     int          rw
pers.complaints                    int          rw
pers.complaintClient               int          rw
pers.complaintEndTime              int          rw
pers.lastReinforceTime             int          rw
pers.applicationClient             int          rw
pers.applicationEndTime            int          rw
pers.invitationClient              int          rw
pers.invitationEndTime             int          rw
pers.propositionClient             int          rw
pers.propositionClient2            int          rw
pers.propositionEndTime            int          rw
pers.autofireteamEndTime           int          rw
pers.autofireteamCreateEndTime     int          rw
pers.autofireteamJoinEndTime       int          rw
pers.lastSpawnTime                 int          ro
pers.ready                         int          rw
pers.lastkilled_client             int          ro
pers.lastrevive_client             int          ro
pers.lastkiller_client             int          ro
pers.lastammo_client               int          ro
pers.lasthealth_client             int          rw
pers.lastteambleed_client          int          ro
pers.lastteambleed_dmg             int          ro
pers.playerStats.hitRegions        int_array    ro
pers.lastBattleSenseBonusTime      int          ro
pers.lastHQMineReportTime          int          ro
pers.maxHealth                     int          ro
pers.playerStats.selfkills         int          ro

ps.pm_flags                        int          ro
ps.pm_time                         int          ro
ps.pm_type                         int          ro
ps.eFlags                          int          ro
ps.weapon                          int          ro
ps.weaponstate                     int          ro
ps.stats                           int_array    rw
ps.persistant                      int_array    rw
ps.ping                            int          ro
ps.powerups                        int_array    rw
ps.origin                          vec3         rw
ps.viewangles                      vec3         rw
ps.velocity                        vec3         rw
ps.ammo                            int_array    rw
ps.ammoclip                        int_array    rw
ps.classWeaponTime                 int          rw
ps.viewheight                      int          ro
ps.leanf                           float        ro

sess.sessionTeam                   int          rw
sess.spectatorTime                 int          rw
sess.spectatorState                int          rw
sess.spectatorClient               int          rw
sess.playerType                    int          rw
sess.playerWeapon                  int          rw
sess.playerWeapon2                 int          rw
sess.spawnObjectiveIndex           int          rw
sess.latchPlayerType               int          rw
sess.latchPlayerWeapon             int          rw
sess.latchPlayerWeapon2            int          rw
sess.ignoreClients                 int_array    rw
sess.muted                         int          rw
sess.skillpoints                   float_array  ro
sess.startskillpoints              float_array  ro
sess.startxptotal                  float        ro
sess.skill                         int_array    rw
sess.rank                          int          rw
sess.medals                        int_array    rw
sess.referee                       int          rw
sess.rounds                        int          rw
sess.spec_invite                   int          rw
sess.spec_team                     int          rw
sess.kills                         int          rw
sess.deaths                        int          rw
sess.gibs                          int          rw
sess.self_kills                    int          rw
sess.team_kills                    int          rw
sess.team_gibs                     int          rw
sess.damage_given                  int          rw
sess.damage_received               int          rw
sess.team_damage_given             int          rw
sess.team_damage_received          int          rw
sess.time_axis                     int          ro
sess.time_allies                   int          ro
sess.time_played                   int          ro
sess.mu                            float        ro
sess.sigma                         float        ro
sess.oldmu                         float        ro
sess.oldsigma                      float        ro
sess.uci                           int          rw
sess.aWeaponStats                  weaponstat   ro
=================================  ===========  ========  ==================================

.. note:: All the session `sess.*` fields will return `nil` unless the entity is associated with a client slot.

.. note:: All array variables need to be get or set with an additional parameter.


Entity fields
=============


=================================  ===========  ========  ==================================
Name                               Type         Flag      Description
=================================  ===========  ========  ==================================
activator                          entity       ro
chain                              entity       rw
classname                          string       rw
clipmask                           int          rw
closespeed                         float        rw
count                              int          rw
count2                             int          rw
damage                             int          rw
deathType                          int          rw
delay                              float        rw
dl_atten                           int          rw
dl_color                           vec3         rw
dl_shader                          string       ro
dl_stylestring                     string       ro
duration                           float        rw
end_size                           int          rw
enemy                              entity       rw
entstate                           int          ro
flags                              int          ro
harc                               float        rw
health                             int          rw
inuse                              int          rw
isProp                             int          ro
item                               string       ro
key                                int          rw
message                            string       rw
methodOfDeath                      int          rw
mg42BaseEnt                        int          rw
missionLevel                       int          rw
model                              string       ro
model2                             string       ro
nextTrain                          entity       rw
noise_index                        int          rw
prevTrain                          entity       rw
props_frame_state                  int          ro
r.absmax                           vec3         ro
r.absmin                           vec3         ro
r.bmodel                           int          ro
r.contents                         int          rw
r.currentAngles                    vec3         rw
r.currentOrigin                    vec3         rw
r.eventTime                        int          rw
r.linked                           int          ro
r.maxs                             vec3         rw
r.mins                             vec3         rw
r.ownerNum                         int          rw
r.singleClient                     int          rw
r.svFlags                          int          rw
r.worldflags                       int          ro
radius                             int          rw
random                             float        rw
rotate                             vec3         rw
s.angles                           vec3         rw
s.angles2                          vec3         rw
s.apos                             trajectory   rw
s.clientNum                        int          rw
s.constantLight                    int          rw
s.density                          int          rw
s.dl_intensity                     int          rw
s.dmgFlags                         int          rw
s.eFlags                           int          rw
s.eType                            int          rw
s.effect1Time                      int          rw
s.effect2Time                      int          rw
s.effect3Time                      int          rw
s.frame                            int          rw
s.groundEntityNum                  int          ro
s.loopSound                        int          rw
s.modelindex                       int          rw
s.modelindex2                      int          rw
s.number                           int          ro
s.onFireEnd                        int          rw
s.onFireStart                      int          rw
s.origin                           vec3         rw
s.origin2                          vec3         rw
s.pos                              trajectory   rw
s.powerups                         int          ro
s.solid                            int          rw
s.teamNum                          int          rw
s.time                             int          rw
s.time2                            int          rw
s.weapon                           int          ro
s.eventParm                        int          rw
scriptName                         string       ro
spawnflags                         int          ro
spawnitem                          string       ro
speed                              int          rw
splashDamage                       int          rw
splashMethodOfDeath                int          rw
splashRadius                       int          rw
start_size                         int          rw
tagName                            string       noptr+ro
tagParent                          entity       rw
takedamage                         int          rw
tankLink                           entity       rw
target                             string       rw
TargetAngles                       vec3         rw
TargetFlag                         int          ro
targetname                         string       ro
teamchain                          entity       rw
teammaster                         entity       rw
track                              string       ro
varc                               float        rw
wait                               float        rw
waterlevel                         int          ro
watertype                          int          ro
=================================  ===========  ========  ==================================


Field types
===========


int
---

An integer value.


float
-----

A float value.


string
------

A string.


array
-----

An array is a list of integer or float values. Individual elements of the array are accessed by passing the desired index in the `arrayindex` argument.
Valid array indexes are integers from 0 up to some field specific maximum.

.. note:: The `arrayindex` argument is required when accessing array type fields, so only one element of an array can be accessed in a given call to the `et.gentity_get() <functions.html#variable-et-gentity-get-entnum-fieldname-arrayindex>`__ and `et.gentity_set() <functions.html#et-gentity-set-entnum-fieldname-arrayindex-value>`__ functions.


vec3
----

A vec3_t is a 3-element array of numbers, usually used to store and process coordinates in 3D space.
Similarly, in Legacy a vector is an array (table indexed by integers) containing 3 numbers. It can be accessed by::

    origin = et.gentity_get(entNum, "r.currentOrigin") --a vec3 value
    x, y, z = origin[1], origin[2], origin[3]



trajectory
----------

A trajectory is returned as a lua table as described below::

    {
      trDuration = <number>, --- int
      trTime = <number>, -- int
      trType = <number>, -- see below for allowed values
      trBase = <vec3_t>, -- vec3, as described above
      trDelta = <vec3_t> -- also a vec3
    }


The allowed values for `trType` are as follows:

=================================  =========================================================
Name                               Description
=================================  =========================================================
TR_STATIONARY
TR_INTERPOLATE                     non-parametric, but interpolate between snapshots
TR_LINEAR
TR_LINEAR_STOP
TR_LINEAR_STOP_BACK                so reverse movement can be different than forward
TR_SINE                            value = base + sin( time / duration ) * delta
TR_GRAVITY
TR_GRAVITY_LOW
TR_GRAVITY_FLOAT                   super low grav with no gravity acceleration (floating feathers/fabric/leaves/...)
TR_GRAVITY_PAUSED                  has stopped, but will still do a short trace to see if it should be switched back to TR_GRAVITY
TR_ACCELERATE
TR_DECCELERATE
TR_SPLINE
TR_LINEAR_PATH
=================================  =========================================================

.. note:: Not all values make sense for all entity types.


entity
------

Entity numbers are integers from 0 through 1023.
Some of the entity numbers have special meanings:

===========================  ===============================================================
Value                        Description
===========================  ===============================================================
0 - (sv_privateclients - 1)  Reserved for clients who connect with the private slot password
0 - 63                       Reserved for clients and also the client number
1022                         Worldspawn entity
1023                         ENTITYNUM_NONE which is used to indicate no entity when an entity number will be passed over the network
===========================  ===============================================================

.. note:: Some other fields not listed as type `entity` may take an entity number value. Examples are `mg42BaseEnt` and `s.number`.
