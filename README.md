# The Goose Game Kata
Goose game is a game where two or more players move pieces around a track by rolling a die. The aim of the game is to reach square number sixty-three before any of the other players and avoid obstacles. ([wikipedia](https://en.wikipedia.org/wiki/Game_of_the_Goose))

This kata has been invented by [Matteo Vaccari](https://github.com/xpmatteo), you can find the original slides [here](https://www.slideshare.net/pierodibello/il-dilettevole-giuoco-delloca-coding-dojo).

## General requirements
- You may use whatever programming language you prefer. Use something that you know well.
- You should commit your code on GitHub or any other SCM repository you prefer (e.g. bitbucket, gitlab, etc) and send us the link.
- You should release your work under an OSI-approved open-source license of your choice.
- You should deliver the sources of your application, with a README that explains how to compile and run it.

**IMPORTANT:** Implement the requirements focusing on writing the best code you can produce.

## Features

### 1. Add players
As a player, I want to add me to the game so that I can play.

**Scenarios:**
1. Add Player
   ```js
   If there is no participant
   the user writes: "add player Pippo"
   the system responds: "players: Pippo"
   the user writes: "add player Pluto"
   the system responds: "players: Pippo, Pluto"
   ```

2. Duplicated Player
   ```js
   If there is already a participant "Pippo"
   the user writes: "add player Pippo"
   the system responds: "Pippo: already existing player"
   ```

### 2. Move a player
As a player, I want to move the marker on the board to make the game progress

**Scenarios:**
1. Start
   ```js
   If there are two participants "Pippo" and "Pluto" on space "Start"
   the user writes: "move Pippo 4, 2"
   the system responds: "Pippo rolls 4, 2. Pippo moves from Start to 6"
   the user writes: "move Pluto 2, 2"
   the system responds: "Pluto rolls 2, 2. Pluto moves from Start to 4"
   the user writes: "move Pippo 2, 3"
   the system responds: "Pippo rolls 2, 3. Pippo moves from 6 to 11"
   ```

### 3. Win
As a player, I win the game if I land on space "63"

**Scenarios:**
1. Victory
   ```js
   If there is one participant "Pippo" on space "60"
   the user writes: "move Pippo 1, 2"
   the system responds: "Pippo rolls 1, 2. Pippo moves from 60 to 63. Pippo Wins!!"
   ```

2. Winning with the exact dice shooting
   ```js
   If there is one participant "Pippo" on space "60"
   the user writes: "move Pippo 3, 2"
   the system responds: "Pippo rolls 3, 2. Pippo moves from 60 to 63. Pippo bounces! Pippo returns to 61"
   ```
### 4. The game throws the dice
As a player, I want the game throws the dice for me to save effort

**Scenarios:**
1. Dice roll
   ```js
   If there is one participant "Pippo" on space "4"
   assuming that the dice get 1 and 2
   when the user writes: "move Pippo"
   the system responds: "Pippo rolls 1, 2. Pippo moves from 4 to 7"
   ```

### 5. Space "6" is "The Bridge"
As a player, when I get to the space "The Bridge", I jump to the space "12"

**Scenarios:**
1. Get to "The Bridge"
   ```js
   If there is one participant "Pippo" on space "4"
   assuming that the dice get 1 and 1
   when the user writes: "move Pippo"
   the system responds: "Pippo rolls 1, 1. Pippo moves from 4 to The Bridge. Pippo jumps to 12"
   ```

### 6. If you land on "The Goose", move again
As a player, when I get to a space with a picture of "The Goose", I move forward again by the sum of the two dice rolled before

The spaces 5, 9, 14, 18, 23, 27 have a picture of "The Goose"

**Scenarios:**
1. Single Jump
   ```js
   If there is one participant "Pippo" on space "3"
   assuming that the dice get 1 and 1
   when the user writes: "move Pippo"
   the system responds: "Pippo rolls 1, 1. Pippo moves from 3 to 5, The Goose. Pippo moves again and goes to 7"
   ```

2. Multiple Jump
   ```js
   If there is one participant "Pippo" on space "10"
   assuming that the dice get 2 and 2
   when the user writes: "move Pippo"
   the system responds: "Pippo rolls 2, 2. Pippo moves from 10 to 14, The Goose. Pippo moves again and goes to 18, The Goose. Pippo moves again and goes to 22"
   ```

### 7. Prank (Optional Step)
As a player, when I land on a space occupied by another player, I send him to my previous position so that the game can be more entertaining.

**Scenarios:**
1. Prank
   ```js
   If there are two participants "Pippo" and "Pluto" respectively on spaces "15" and "17"
   assuming that the dice get 1 and 1
   when the user writes: "move Pippo"
   the system responds: "Pippo rolls 1, 1. Pippo moves from 15 to 17. On 17 there is Pluto, who returns to 15"
   ```
