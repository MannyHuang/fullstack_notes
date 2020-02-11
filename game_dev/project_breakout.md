## shortlist of features to add
- improve score calculation based on block hit and block desctruction
- slow down time on special block hit
- manny balls at start with very long paddle
- add keyboard support
spawn manny blocks in different direction on special block - hit
change the hit vfx and increase size of the ball on block - hit
make the surrounding environment dark and light source to - the ball instead
reverse camera to enable bottom top gameplay to break user - tempo
- reference
  - https://community.gamedev.tv/tags/34_BR_CUD?utm_source=udemy.com&utm_medium=Automation&utm_campaign=tag_links

## History
- Breakout (Atari, 1976)
	- paddle & ball vs. blocks
- Arkanoid
	- paddle & ball vs. blocks & other stuff

## core elements
- multi-hit breakable blocks
- block and ball size variation
- block color variation
- unbreakable blocks
- powerups
  - ball adheres to paddle
  - ball is slowed
  - ball damage increases
  - ball becomes larger
  - extra ball in play
  - paddle becomes wider
  - powerups fall from the formations force player to choose which one to pickup
- powerdowns
  - slow paddle
  - narrower paddle
  - fast ball
  - tiny ball
- ball trajectory controller
  - grabs the ball and ejects it upon a trigger event
  - a hole sucks in the ball and auto-releases it at pre-determined trajectory
  - wedge shape, force ball to return at less-predictable angle
  - channel shape, constrains ball's movement along a new angle
- Ball speed amplifiers
  - bumpers or regions that speed up the ball
- moving powerups and powerdowns
  - makes them harder/easier to obtain
  - osicallating, path-based, logic-based
- switches
  - open up reward area
- ball traps
  - small gaps that holds more balls
  - player action tirgger the payload to be released
- bombs
  - explode when hit
- sheilds
  - powerup that blocks ball from fallinng
  - destroyed depending on duration or number of hits
- invisible blocks
  - only visible for a short time after one of them is hit
- progressive blocks
  - blocks move one level lower each time
  - force player to focus on lower levels of blocks
- multiple paddles
  - give user two paddles, one above another