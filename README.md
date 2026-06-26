# Sky Relic

## Overview

Sky Relic is a first person exploration game developed in Unreal Engine 5 using Blueprints.

The goal is simple. The player explores the environment, collects all relics, and reaches the end of the game. The first two levels unlock a portal after all relics have been collected, while collecting the relics in the final level completes the game.

## Controls

* **W, A, S, D** Move
* **Mouse** Look around
* **Space** Jump
* **Space (while in the air)** Double Jump

## Project Structure

The project contains three levels connected through portals.

Each level contains five collectible relics. The first two levels use portals for progression, while the third level ends with the victory screen after collecting the final relics.

A countdown timer is enabled only in Levels 2 and 3. If the timer reaches zero, the player loses and the Game Over screen is displayed.

## Blueprints

### BP_SkyRelicGameMode

This Blueprint controls the main game flow.

It is responsible for:

* Detecting the current level
* Setting the correct objective text for the HUD
* Starting and updating the countdown timer
* Checking the win and lose conditions
* Displaying the Win and Game Over screens
* Tracking the number of collected relics
* Unlocking portals after all relics have been collected

### BP_Relic

A parent Blueprint used for every collectible relic.

When the player overlaps with a relic, it:

* Increases the relic counter
* Updates the HUD
* Calls the GameMode to check if the collection goal has been reached
* Destroys itself after being collected

Child Blueprints were created from this parent for the different relics used in each level.

### BP_Portal

The portal Blueprint is used to move the player between levels.

Each portal has an editable destination level, allowing the same Blueprint to be reused throughout the project.

The portal remains locked until all relics in the current level have been collected.

### Player Character

The player uses a first person character with movement, jumping and double jumping.

Mixamo animations were imported, retargeted and applied to the character to improve movement.

## User Interface

The project contains three widgets.

**HUD**

* Current objective
* Relic counter
* Countdown timer

**Game Over Screen**

* Displayed when the timer reaches zero.

**Win Screen**

* Displayed after collecting all relics in the final level.

## Blueprint Logic

The gameplay logic is organised into reusable functions.

Main functions include:

* Starting the level timer
* Updating the timer
* Showing the Game Over screen
* Showing the Win screen
* Adding collected relics
* Checking whether the collection objective has been completed

This keeps the Event Graph cleaner and separates the main gameplay systems into smaller, reusable parts.
