# screeps
Jeff and Justen's collaboration to make Jeff's Screeps code suck less (that should be easy).

## Notes
```javascript
room.find(...)
```
is faster than 
```javascript
_.filter(Game...)
```
It searches only that room, and if it's done once for all members of a category (Like FIND_MY_CREEPS) then filtered for something more specific (Like creep.memory.role == 'fighter')
#### An example of this:
```javascript
var allCreepsInRoom = Game.rooms['sim'].find(FIND_MY_CREEPS);

var harvesters = _.filter(allCreepsInRoom, (creep) => creep.memory.role == 'harvester');
var builders = _.filter(allCreepsInRoom, (creep) => creep.memory.role == 'builder');
var upgraders = _.filter(allCreepsInRoom, (creep) => creep.memory.role == 'upgrader');
```
