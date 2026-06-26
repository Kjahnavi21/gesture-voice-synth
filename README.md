# Gesture Voice Explorer

Gesture Voice Explorer is a small browser-based prototype that maps simple user input to voice-like sound using vanilla HTML, CSS, JavaScript, and the Web Audio API.

The project explores how gesture-like interaction can be translated into sound parameters such as pitch, volume, and tone shape. It is designed as a lightweight creative technology experiment focused on interaction, audio synthesis, and accessible interface design.

## Overview

This prototype lets users control synthesized sound through mouse or trackpad movement inside a gesture area. It also includes direct fine-tune controls for users who prefer sliders over continuous movement.

The main interaction is:

- Move left and right to change pitch.
- Move up and down to change volume.
- Use the tone selector to change the waveform.
- Use sliders to directly fine-tune pitch and volume.

This is not a medical or therapeutic tool. It is a small experiment in browser-based gesture-to-sound mapping.

## Demo

Open `index.html` in a browser to run the prototype locally.

## How to Use

1. Open `index.html` in a browser.
2. Click **Start Audio**.
3. Move your mouse or trackpad inside the gesture area.
4. Move left or right to change the pitch.
5. Move up or down to change the volume.
6. Use the **Tone shape** dropdown to switch between sine, triangle, and square waves.
7. Use the **Fine-Tune Controls** sliders for direct pitch and volume control.
8. Click **Stop Audio** to end the sound.

For comfort, start with your device volume low.

## Features

- Built with vanilla HTML, CSS, and JavaScript.
- Uses the Web Audio API for browser-based sound synthesis.
- Maps mouse movement to pitch and volume.
- Includes slider-based fine-tune controls.
- Provides a tone shape selector for different oscillator waveforms.
- Shows live pitch, volume, and input mode values.
- Uses a responsive layout for different screen sizes.
- Starts audio only after user interaction.

## Technical Overview

The sound is created using the Web Audio API.

The audio chain is:

`OscillatorNode -> GainNode -> Audio Destination`

- `OscillatorNode` generates the tone.
- `GainNode` controls the volume.
- Mouse position and slider values update the oscillator frequency and gain value.
- `setTargetAtTime()` smooths pitch and volume changes so the sound does not jump abruptly.

## Input Mapping

The gesture area maps mouse position to audio values.

### Pitch

Horizontal position controls pitch.

- Left side = lower pitch
- Right side = higher pitch

Current pitch range: `100 Hz` to `800 Hz`

### Volume

Vertical position controls volume.

- Top = louder
- Bottom = softer

Current volume range: `0.02` to `0.30`

## Design Choices

### Gesture-Like Interaction

Mouse and trackpad movement are used as simple stand-ins for gesture input. This keeps the prototype lightweight while still exploring the idea of mapping physical movement to sound.

### Fine-Tune Controls

The pitch and volume sliders provide a direct way to control the same sound parameters used in the gesture area. This makes the interface easier to test, easier to understand, and more flexible for users who may prefer labeled controls.

### User-Controlled Audio

The page does not play sound automatically. Users must click **Start Audio** before sound begins. This follows browser audio requirements and gives users control over when sound starts and stops.

### Low Default Volume

The default volume is intentionally low to reduce the chance of loud or surprising sound.

### Clear Feedback

The interface displays the current pitch, volume, and input mode so users can understand how their actions affect the sound.

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
- Multiple ways to control the same sound parameters
- Responsive layout for different screen sizes

## Future Improvements

Possible future improvements include:

- Adding keyboard controls
- Adding webcam-based gesture input
- Exploring MediaPipe Face Mesh for facial landmark tracking
- Mapping facial gestures to sound parameters
- Adding calibration for comfortable pitch and volume ranges
- Exploring more voice-like synthesis techniques
- Improving visual feedback for remote usability testing

## Files

- `index.html` - Main prototype with HTML, CSS, and JavaScript in one file

## Tools Used

- HTML
- CSS
- Vanilla JavaScript
- Web Audio API