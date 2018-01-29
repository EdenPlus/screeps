# screeps
Jeff and Justen's collaboration to make Jeff's Screeps code suck less (that should be easy).

/* From status report:
 This code is supposed to record in memory the tick at which each controller level was reached.
 It was used as a benchmark for whether certain building and creep strategies were faster than others.
        Why does this exist?
        // Controller level up tick recorder start
        if (!curRoom.memory.levelTime) {
            curRoom.memory.levelTime = [];
        } else if (!curRoom.memory.levelTime[curRoom.controller.level]) {
            curRoom.memory.levelTime[curRoom.controller.level] =
                { level: curRoom.controller.level, time: Game.time}
        }
        // Controller level up tick recorder end
*/
