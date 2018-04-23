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
as per [this post](https://screeps.com/forum/topic/1409/game-creeps-filter-vs-room-find-find_my_creeps/2). It searches only that room, and if it's done once for all members of a category (Like FIND_MY_CREEPS) then filtered for something more specific (Like creep.memory.role == 'fighter')
#### An example of this:
```javascript
var allCreepsInRoom = Game.rooms['sim'].find(FIND_MY_CREEPS);

var harvesters = _.filter(allCreepsInRoom, (creep) => creep.memory.role == 'harvester');
var builders = _.filter(allCreepsInRoom, (creep) => creep.memory.role == 'builder');
var upgraders = _.filter(allCreepsInRoom, (creep) => creep.memory.role == 'upgrader');
```
## Auto Upload Code:
```javascript
/* Start Requirements */
const Promise = require("es6-promise").Promise;
const fs = require('fs');
const express = require('express');
const app = express();
const { ScreepsAPI } = require('screeps-api');
const Octokit = require("octokit");
/* End Requirements */

/* Start ScreepsAPI stuff */
// All options are optional
const api = new ScreepsAPI({
  token: '<Screep-Token>',
  protocol: 'https',
  hostname: 'screeps.com',
  port: 443,
  path: '/' // Do no include '/api', it will be added automatically
});
 
// You can overwrite parameters if needed
api.auth('screeps@email.com','notMyPass',{
  protocol: 'https',
  hostname: 'screeps.com',
  port: 443,
  path: '/' // Do no include '/api', it will be added automatically
});
/* End ScreepsAPI stuff */

/* Start GitHub Stuff */
var gh = Octokit.new({
  token: "<GitHub-Token>"
});

var repoowner = "EdenPlus";
var reponame = "screeps";
var repo = gh.getRepo(repoowner, reponame);
var branch = repo.getBranch("prototype");
/*branch.createBranch("trial")
.then(function() {});
branch = repo.getBranch("trial");*/

api.code.get('default').then(function (data) {
    var contents = {};
    for (var a in data.modules) {
        contents[a] = data.modules[a];
    }
    var message = "Automated Update";
    branch.writeMany(contents, message)
    .then(function() {
        console.log("Code posted");
    });
});
/* End GitHub Stuff */
```
