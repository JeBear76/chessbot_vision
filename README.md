# chessbot_vision

Computer vision pipeline for detecting and mapping a physical chessboard using a camera.

## Overview

This project uses OpenCV to:
1. Capture or load an image of a chessboard
2. Detect the inner corners of the board using `findChessboardCornersSB`
3. Compute a homography to map board coordinates to image coordinates
4. Label each square with its chess notation (e.g. `e4`, `d8`)
5. Assign each square a `world_position` (center coordinate in mm) relative to `d8` as the origin

## Setup

Install dependencies:

```bash
pip install -r requirements.txt
```

## Usage

Open and run `camera_scratch.ipynb` in Jupyter or VS Code.

A chessboard image will be read from `test_images/chessboard.png`. If the file does not exist, the script will capture one from the default camera (index 0) and save it.

## Coordinate System

The `world_position` of each square is the center of that square in a 2D coordinate system where:

- Origin `(0, 0)` is the bottom-left corner of square `d8`
- X increases toward files `c`, `b`, `a` (leftward on the board)
- Y increases toward lower ranks (`7`, `6`, ... `1`)
- Each square is `SQUARE_SIZE × SQUARE_SIZE` (default: 55 units)

## Project Structure

```
camera_scratch.ipynb   # Main development notebook
vision_dev.py          # Vision utilities
requirements.txt       # Python dependencies
```
