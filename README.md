Bowling House API
====

This is a backend API for a Bowling house based on the Ten-pin bowling [https://en.wikipedia.org/wiki/Ten-pin_bowling]


**Available endpoints (localhost:8085)**

* Start New Game /startNewGame
* Show total Score (all players) /score/total
* Show Score by player /score/{playerName}
* Play a frame /play/
 

**Here are some examples to show usage**
To call this endpoints it can be done in two ways:
* swagger-ui which is available on the root path: localhost:8085
* using curl:

start new game (maximum of players is 8):

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: text/plain' -d '{ \ 
   "nameOfThePlayers": [ \ 
     "samuel", "marques" \ 
   ], \ 
   "numberOfPlayers": 2 \ 
 }' 'http://localhost:8085/bowlinggame/startNewGame/'
 
```

show the total score

```
curl -X GET --header 'Accept: application/json' 'http://localhost:8085/bowlinggame/score/total'
```
show the score by player name

```
curl -X GET --header 'Accept: application/json' 'http://localhost:8085/bowlinggame/score/samuel'
```
play a new frame

```
curl -X POST --header 'Content-Type: application/json' --header 'Accept: text/plain' 'http://localhost:8085/bowlinggame/play/?rollsRequest.firstRoll=X&playerName=samuel'

```
*Notes about playing/scoring system:* 
* by default every player has 10 frames
* each frame as a maximum of 10 points
* if the player scores a strike in the last frame, he gets two extra rolls or if he scores one Spare he gets one extra roll
* Within the 10 normal frames: 
** Strikes are requested by setting the first roll as X and the second roll should not be given
** Spares are requested by setting the second roll as / 
* After scoring a strike or spare in the tenth frame:
** The score counts the number of pins in the extra(s) roll(s)
** Therefore, it should be sent only the number of points in the extra frame and not X or / 
     
     
*useful links*
* https://spring.io/projects/spring-boot 
* https://swagger.io/
* https://en.wikipedia.org/wiki/Test-driven_development
* http://site.mockito.org/ 

created by: Samuel Marques 
Any question just send me a message, thanks!