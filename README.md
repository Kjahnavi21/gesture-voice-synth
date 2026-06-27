# Gesture Voice Explorer

Gesture Voice Explorer is a small browser-based creative coding prototype that maps user input to voice-like sound using vanilla HTML, CSS, JavaScript, and the Web Audio API.

The project explores gesture-to-sound interaction through two experiments:

1. A main mouse/trackpad-based gesture interface
2. An optional webcam-based motion experiment

Both experiments are lightweight, browser-based, and built without frameworks or build tools.

## Overview

The main prototype lets users control synthesized sound by moving inside a gesture area. Horizontal movement changes pitch, vertical movement changes volume, and a tone selector changes the waveform.

The webcam experimental explores how camera input can also be used as a simple gesture signal. It compares the current webcam frame to the previous frame, estimates where movement is happening, and maps that movement position to sound.

This project is not a medical or therapeutic tool. It is a small experiment in browser-based gesture-to-sound mapping, interaction design, and accessible audio interfaces.

## Files

- `index.html`  
  Main prototype using mouse or trackpad movement to control sound.

- `webcam-experimental.html`  
  Optional webcam experiment using browser camera access and canvas-based motion tracking.

- `README.md`  
  Project documentation.

## How to Run

### Main Prototype

Open `index.html` directly in a browser.

### Webcam Experiment

The webcam experiment may need to be run through `localhost` or HTTPS because browsers often restrict camera access from local files.

From the project folder, run:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000/webcam-experimental.html
```

Allow camera permission when the browser asks.

For comfort, start with your device volume low.

## Main Prototype: Gesture Voice Explorer

The main prototype maps mouse or trackpad movement to sound.

### How to Use

1. Open `index.html` in a browser.
2. Click **Start Audio**.
3. Move your mouse or trackpad inside the gesture area.
4. Move left or right to change pitch.
5. Move up or down to change volume.
6. Use the **Tone shape** dropdown to switch between sine, triangle, and square waves.
7. Use the **Fine-Tune Controls** sliders for direct pitch and volume control.
8. Click **Stop Audio** to end the sound.

### Features

- Mouse or trackpad movement controls pitch and volume.
- Sliders provide direct fine-tune controls.
- Tone shape selector changes the oscillator waveform.
- Live values show pitch, volume, and input mode.
- Audio starts only after user interaction.
- Responsive layout adapts to different screen sizes.

## Webcam Experiment

The webcam experiment uses camera input as a simple gesture source.

### How It Works

The webcam experiment:

1. Gets webcam access with `navigator.mediaDevices.getUserMedia()`.
2. Draws each video frame to a hidden `<canvas>`.
3. Reads pixel data from the canvas.
4. Compares the current frame to the previous frame.
5. Finds where movement is happening in the frame.
6. Maps the movement position to sound.

### Input Mapping

- Movement left or right changes pitch.
- Movement up or down changes volume.
- The displayed pitch and volume values are smoothed to reduce jitter.

This version does not use facial landmark tracking. It is a simple motion-based experiment using only built-in browser APIs.

## Technical Overview

The audio is created with the Web Audio API.

The audio chain is:

```text
OscillatorNode -> GainNode -> Audio Destination
```

- `OscillatorNode` generates the tone.
- `GainNode` controls the volume.
- User input updates oscillator frequency and gain.
- `setTargetAtTime()` smooths pitch and volume changes.

## Input Mapping

### Main Prototype

In `index.html`:

- Mouse X position controls pitch.
- Mouse Y position controls volume.
- Sliders provide direct control over the same parameters.

Current pitch range:

```text
100 Hz to 800 Hz
```

Current volume range:

```text
0.02 to 0.30
```

### Webcam Experiment

In `webcam-experimental.html`:

- Movement X position controls pitch.
- Movement Y position controls volume.
- Motion values are smoothed before updating sound.

Current pitch range:

```text
120 Hz to 800 Hz
```

Current volume range:

```text
0.01 to 0.30
```

## Design Choices

### Simple Gesture-Based Interaction

Mouse, trackpad, and webcam motion are used as lightweight stand-ins for gesture input. This keeps the project simple while still exploring how physical movement can shape sound.

### Fine-Tune Controls

The main prototype includes pitch and volume sliders. These provide a direct way to control the same sound parameters used in the gesture area. This makes the interface easier to test, easier to understand, and more flexible for users who prefer labeled controls.

### User-Controlled Audio

The project does not autoplay sound. Users must click **Start Audio** before sound begins. This follows browser audio requirements and gives users control over when sound starts and stops.

### Low Default Volume

The default volume is intentionally low to reduce the chance of loud or surprising sound.

### Clear Feedback

The interface displays live sound values so users can understand how their movement affects the audio.

### Responsive Layout

The layout uses CSS Grid on larger screens and switches to a single-column layout on smaller screens.

## Accessibility Considerations

This prototype includes:

- Clearly labeled controls
- Large buttons
- Readable text
- A visible stop button
- No autoplaying audio
- Low default volume
- Multiple ways to control sound parameters
- Responsive layout for different screen sizes

## Future Improvements

Possible future improvements include:

- Adding keyboard controls
- Adding calibration for comfortable pitch and volume ranges
- Adding more voice-like synthesis techniques
- Adding visual feedback for movement tracking
- Exploring MediaPipe Face Mesh for facial landmark tracking
- Mapping facial gestures such as mouth opening, eyebrow movement, or head position to sound parameters
- Improving webcam stability across different lighting conditions and backgrounds

## Tools Used

- HTML
- CSS
- Vanilla JavaScript
- Web Audio API
- `getUserMedia()` for webcam access
- Canvas API for webcam frame analysis
