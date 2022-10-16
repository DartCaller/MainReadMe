# DartCaller 
This readme will explain the purpose and structure of the whole [Dart Caller Github Organisation](https://github.com/DartCaller).
It should serve as a basis to understand the problem, the domain, and the solution. The individual ReadMe's of the other repositories then help give more insights into the finer details of each repository.

## :thinking: The Problem
Imagine playing a dart game :dart: with your friend on a classical, non-electronic dartboard. You have a sheet of paper or a whiteboard to write down and keep track of your scores. But no matter if your friend waits with his throw while you write down your score, or if he does not, I find that keeping track of the score yourself is tedious, distracting, and sometimes straight annoying.

## :bulb: The Solution
The rather obvious solution is to detect the darts and update the score automatically, just like electronic dartboards do. The dart detection technique used within this organization is based on two small cameras sitting on the edge of the dartboard and then calculating the intersection of the line of sights of each camera.

<p align="center">
<img height="400px" src="https://user-images.githubusercontent.com/32591853/120698755-c4805e00-c4af-11eb-8c3d-a791a9832b15.png" />
</p>

## :card_file_box: Repositories
This organisation is split into 3 repositories:

### Web
https://github.com/DartCaller/web
This repository contains the Nuxt.js Frontend that visualizes the current state of the Dart Game. It connects to the server to let the user create a Dart Game, and see the newest scores being added as soon as the darts hit the dartboard.

### Api
https://github.com/DartCaller/api
Here lives the server managing the dart games and keeping them up to date whenever darts hit the dartboard. This server exposes an HTTP route that the python dart recognition software can use when it detected a new dart. As soon as a score is published to that route, the server notifies the frontend about the latest score.

### Darts Recognition
https://github.com/DartCaller/darts-recognition
In this repository lives all the magic. It contains the scripts to control the cameras on the dartboard and the logic to extract the dart scores from the images.
The calculated scores for each dart then get sent to the server.


## :book: Dart Glossary
### Game
A game means the total play between two players and consists of one or more [legs](#legs).
### Leg
A leg is one full round where all players often start with 501 Points and play it down to zero. 
### Game Mode
There are many different Game Modes, the most popular being `501`, where everyone starts with 501 points and has to score it down to zero first. In these repositories, you can also play `301` simply meaning everybody starts with 301 points instead of 501.

### Score
![dartboard-scoring-guide_large](https://user-images.githubusercontent.com/32591853/120363119-11c3ca80-c30c-11eb-91bc-ffe09da22058.jpeg)

image credit to https://shotdarts.com/

The word score in these repositories means either the points achieved with a single dart or three darts of one turn.
The used notation to represent which field was hit is simply a combination of the ring that was hit (S = Single, D = Double, T = Tripple) and the number that was hit. So using the above image as an example:
- The two arrows labeled `Single Scoring` point at `S20` and `S5`
- The arrow labeled `Double Ring` points at `D4`
- The arrow labeled `Triple Ring` points at `T4`
- The arrow labeled `Single Bull` points at `S25`
- The arrow labeled `Double Bull` points at `D25`
