# Color Sample Portrait

A web application that captures color samples from your webcam and creates portraits with custom tiled backgrounds using AI-powered background segmentation.

## Features

- **Interactive Color Sampling**: Click on different areas of your image to collect 5 unique color samples
- **AI-Powered Background Removal**: Uses Google's MediaPipe Selfie Segmentation for precise person/background separation
- **Custom Background Generation**: Creates artistic tiled patterns from your collected colors
- **Real-time Processing**: Live webcam preview and instant color capture
- **Mobile-Friendly**: Works on mobile browsers with camera access

## How It Works

1. **Welcome**: Introduction and camera permissions
2. **Color Sampling**: Click 5 different areas in your webcam feed to collect colors
3. **Photo Preparation**: Position yourself and prepare for capture
4. **Countdown**: 3-second countdown before photo capture
5. **Final Result**: View your portrait with AI-generated background

## Technology Stack

- **Frontend**: Vanilla HTML5, CSS3, JavaScript
- **AI Segmentation**: Google MediaPipe Selfie Segmentation
- **Image Processing**: HTML5 Canvas API
- **Camera Access**: WebRTC getUserMedia API

## AI Attribution

This project uses **Google MediaPipe Selfie Segmentation** for background removal:

- **MediaPipe**: Copyright 2020 Google LLC
- **License**: Apache License 2.0
- **Documentation**: https://google.github.io/mediapipe/solutions/selfie_segmentation.html

## Browser Compatibility

- **Desktop**: Chrome, Firefox, Safari, Edge (latest versions)
- **Mobile**: Requires HTTPS for camera access
- **Requirements**: WebRTC and Canvas 2D support

## Deployment

This project is automatically deployed to GitHub Pages via GitHub Actions on every push to `main`.

## License

MIT License

## Acknowledgments

- **Google MediaPipe Team** for the selfie segmentation technology
- **Danna Feintuch** for collaboration on the project
