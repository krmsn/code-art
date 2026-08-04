# AUTOSCOPY

AUTOSCOPY is an experimental algorithmic art project that transforms live webcam input into a dynamic field of ASCII symbols. By mapping luminance and motion data to a structured character grid, the system simulates depth and spatial perception in an abstract, text-based medium.

## Overview

Running on a lightweight local Python server, AUTOSCOPY interfaces directly with the user’s webcam hardware to continuously capture and reinterpret the environment in real time. The result is a living ASCII projection—part mirror, part illusion—where density, contrast, and symbol selection create a shifting sense of form, distance, and movement.

This project sits at the intersection of generative art, computer vision, and retro terminal aesthetics, exploring how minimal visual primitives can evoke surprisingly rich dimensional experiences.

## Features

- Real-time webcam capture and processing  
- ASCII-based rendering engine  
- Depth illusion via luminance and motion mapping  
- Lightweight local Python server  
- Abstract, generative visual output  

## Tech Stack

- Python  
- OpenCV (for webcam capture and image processing)  
- NumPy (for fast array manipulation)  
- Optional: Flask or FastAPI (for local server interface)  

## Getting Started

### Prerequisites

- Python 3.9+  
- A working webcam  

### Installation

```bash
git clone https://github.com/your-username/autoscopy.git
cd autoscopy
pip install -r requirements.txt