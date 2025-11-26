
# PAC-NAM: Legacy C++ Pac-Man with AI Pathfinding

![C++](https://img.shields.io/badge/c++-98%2F11-blue?logo=c%2B%2B&logoColor=white)
![Graphics.h](https://img.shields.io/badge/Library-graphics.h-red)
![Algorithm](https://img.shields.io/badge/Algorithm-BFS-green)


## Description
PAC-NAM is a retro-style arcade game clone developed in C++ using the legacy Borland Graphics Interface (`graphics.h`). The project replicates the core mechanics of Pac-Man, including player movement, coin collection, and ghost behaviors.

What sets this implementation apart is its inclusion of selectable difficulty levels that determine the Artificial Intelligence (AI) of the ghosts. While the easy mode uses random movement, the hard mode implements a Breadth-First Search (BFS) algorithm to calculate the shortest path to the player in real-time.

## Features
* **Dynamic Map Loading:** Reads the game board layout from an external text file (`play_ground.txt`), allowing for custom level designs.
* **Three Difficulty Levels:**
    * **Easy:** Ghosts move randomly.
    * **Medium:** Ghosts move based on Euclidean distance estimation.
    * **Hard:** Ghosts utilize a BFS Pathfinding algorithm to aggressively hunt the player.
* **Classic Gameplay:** Includes collision detection, score tracking, and the four classic ghosts (Blinky, Pinky, Inky, Clyde).
* **Audio/Visual Effects:** Uses `Beep` for sound effects and simple geometric primitives for rendering characters.

## File Descriptions & Implementation Details

### 1. `main.C`
The core application source code.
* **Graphics Initialization:** Sets up the `graphics.h` window (specifically configured for Turbo C++ directories).
* **Game Loop:** Handles input capture (`getch()`), movement logic, and rendering.
* **AI Logic:** Contains the `Pathfinding` function which implements a queue-based BFS to navigate the grid maze.
* **Ghost Logic:** The `enemy_cio` and `moveing` functions determine the next coordinate for the ghosts based on the selected difficulty `level`.

### 2. `play_ground.txt`
The configuration file for the level layout.
* **Format:** A 20x20 matrix of integers.
* **Encoding:**
    * `0`: Wall
    * `1`: Empty Path
    * `2`: Coin
    * `3`: Ghost Spawn
    * `4`: Player Spawn

## Installation & Requirements

**Prerequisites:**
This project relies on the legacy `graphics.h` library, which is native to **Turbo C++**. To run this on modern systems, you have two options:

**Option A: Turbo C++ / DOSBox**
1.  Install Turbo C++.
2.  Place the source files in the `BIN` directory.
3.  Ensure the BGI path in the code (`c:\\turboc3\\bgi`) matches your installation.

**Option B: Modern GCC (MinGW) with WinBGIm**
1.  Install MinGW.
2.  Download and install the **WinBGIm** library (a port of BGI for Windows).
3.  Update the include headers to `<graphics.h>` and compile using `g++`.

**Important File Path Note:**
The code currently looks for the map file at `E://play_ground.txt`. You must either place the file on your E: drive or modify line 550 in `main.C` to match your local file path:
```c
fp = fopen("YOUR_PATH_HERE//play_ground.txt", "r");
````

## Usage

1.  Compile and run `main.C`.
2.  Upon launch, you will be prompted to select a difficulty level (1-3).
3.  **Controls:**
      * **Arrow Up:** Move Up
      * **Arrow Down:** Move Down
      * **Arrow Left:** Move Left
      * **Arrow Right:** Move Right

**Developer Note:**

> "The game processes commands move-by-move, so please wait for the full execution of movements and visual/audio effects after pressing a key before pressing the next one.
> The game retrieves the playground from a text file, the default location of which is specified in line 550.
> This playground is included as a test in the form of a comment at the end of the code. Good luck\!"

**Default Map Layout:**
You can copy this into your `play_ground.txt`:

```text
0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
0 1 1 1 1 1 1 1 1 2 2 1 1 1 1 1 1 1 1 0
0 1 1 1 4 1 1 2 2 2 2 1 1 1 1 1 1 1 1 0
0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 0
0 1 1 2 2 2 2 1 1 1 0 1 1 1 1 2 0 1 1 0
0 1 1 1 1 1 1 1 1 1 0 0 0 1 1 2 0 1 2 0
0 1 2 2 2 1 1 0 0 1 1 1 1 1 1 2 0 1 2 0
0 1 2 2 2 1 1 0 1 1 1 1 1 1 0 0 0 0 0 0
0 0 0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0
0 1 1 1 1 1 1 1 1 1 1 2 2 2 1 1 1 1 1 0
0 1 1 1 2 2 2 2 1 1 1 2 1 1 1 1 1 2 2 0
0 1 1 1 1 1 1 1 1 0 1 2 1 1 1 1 1 2 2 0
0 1 1 1 1 1 1 1 1 0 1 1 1 1 1 0 0 0 0 0
0 1 1 2 1 0 0 0 0 0 1 1 1 1 1 1 1 1 1 0
0 1 1 2 1 1 1 1 1 1 1 1 1 0 0 0 0 1 1 0
0 1 1 2 2 2 2 1 1 1 1 0 0 0 1 2 1 1 1 0
0 1 1 2 1 1 1 1 0 0 0 0 1 1 1 2 1 1 1 0
0 1 1 2 1 3 1 1 0 1 1 1 1 2 2 2 2 2 1 0
0 1 1 1 1 1 1 1 0 1 1 1 1 1 1 2 1 1 1 0
0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
```

## Contributing

Issues and Pull Requests are welcome. If you are porting this to a modern framework (like SFML or SDL), please create a new branch.

## License

This project is open-source.

## Contact

For any inquiries regarding the code logic, please open an issue in the repository.

