# screeps
Jeff and Justen's collaboration to make Jeff's Screeps code suck less (that should be easy).

### Notes
room.find(...) is faster than \_.filter(Game...) It searches only that room, and if it's done once for all members of a category (Like FIND_MY_CREEPS) then filtered for something more specific (Like creep.memory.role == 'fighter')
