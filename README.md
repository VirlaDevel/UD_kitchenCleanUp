# UD_kitchenCleanUp

## Description

This is a udacity project on the topic "Unreal and VR". In this game the player (as VR pawn) has to catch plates which were thrown by a "malfunctioning" plate warmer. The player's goal is to catch those plates before they hit any solid object and "wash" them in the sink. Every plate that was successfully placed in the sink is counted as score, which is visible as pile in proximity to the player. 
The game can be startet and stopped with a big red button. Anyway, the game's duration is limited to 45 seconds per play. The player is informed with sound cues for:
- the start
- every new plate thrown 
- every plate crashed
- every plate washed
- the last 10 seconds
- the end of game

## Software and Hardware

The project was conducted with the Unreal Engine 4.15.3, the Oculus Audio Plugin and some additional ".wav files" downloaded from www.freesound.org, and http://www.grsites.com/archive/sounds, respectively. The environment was provided by udacity's project team "Learn Unreal VR Foundations" as template. Additional assets (plate warmer, crashed plate and hands) were designed by the project team with ZBrush 4R8 and Maya 2018.
The project has been tested with the HTC Vive, but should work with the Oculus Rift as well.

## Blueprints

The player may posess the myVR_pawn with two hands, which have a custom animation (ABP_hand and ABP_hand2) to grab. For the game a myVR_playerController, a myVR_cameraManager and a myVR_gameMode has been implemented and set up. The player can grab plates with the motioncontroller trigger. We used the My_PickUpInterface to communicate with the BP_plate. These plates are spawnd automaticly when the player starts the game with the BP_starter_button, via am event dispatcher. When plates hit solid object the actor is destroyed and a custom BP_platBroken is spawned with sound cue. Whithin the starter button a timer by function name is set with decrement of one second. The button may be used to start, actively stopp (destroy all spawned BP_plates) and to keep track of the timer. The BP_plateshooter is the dish warmer which spawns the plates with a random impuls in the direction of the player (note: gravitiy has been reduced to -110 whithin BP_plate to slow down motions). BP_pileSpawn is a reference point to spawn BP_plate_stapable, which is the optical score for the player. Every caught plate cane be placed in the sink, whithin a trigger box (BP_wash) to score points. BP_wash keeps track of the score and sets the score to zero whene player has restarted the game, further it is linked to BP_waterjet which will be visible when a plate has been put into the sink. Whithin multiple blueprints links via casting have been implemented.

## Annotations

This project has been conducted by Dejan Popic and Sebastian Strahm. Both working at the Swiss Distance Learning Universtiy.
Last Changes: 02.05.2018
