# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

- `npm start` - Start production server on port 3000 (HTTP) and 3443 (HTTPS)
- `npm run dev` - Start development server with nodemon for auto-reloading
- `node server.js` - Direct server execution

## SSL Certificate Setup

For HTTPS functionality (required for mobile webcam access):
```bash
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
```

The server will automatically detect and use `cert.pem` and `key.pem` files in the root directory.

## Architecture Overview

This is a **Color Sample Portrait** web application that uses webcam capture, MediaPipe AI segmentation, and canvas manipulation.

### Core Components

**Backend (server.js)**
- Express.js server serving static files from `public/`
- Dual HTTP/HTTPS server setup with automatic IP detection
- SSL certificate handling with graceful fallback to HTTP
- No API endpoints - purely static file serving

**Frontend (public/index.html)**
- Multi-step interactive UI with 5 distinct phases:
  1. Welcome/initialization
  2. Color sampling from webcam (5 samples)
  3. Photo preparation
  4. Countdown and capture
  5. Final result with background replacement

**Key Technical Features:**
- **MediaPipe Selfie Segmentation** - Advanced AI background removal using CDN-loaded MediaPipe libraries
- **Canvas-based Image Processing** - Real-time webcam capture, color sampling, and image composition
- **Debug Mode** - Comprehensive debugging interface showing original image, segmentation mask, and generated background
- **Responsive Design** - Mobile-friendly with HTTPS requirement for mobile webcam access

### File Structure
- `server.js` - Node.js/Express server with HTTP/HTTPS setup
- `public/index.html` - Main application with embedded JavaScript
- `public/styles.css` - Complete styling with animations and responsive design
- `cert.pem` & `key.pem` - SSL certificates (user-generated)

### MediaPipe Integration
- Uses `@mediapipe/selfie_segmentation` for precise person/background separation
- Fallback to basic color-based segmentation if MediaPipe fails
- Handles different mask formats (ImageBitmap, ImageData, Float32Array)
- Includes horizontal flipping to match webcam mirror effect

### Development Notes
- No build process required - pure HTML/CSS/JS
- MediaPipe libraries loaded from CDN
- WebRTC getUserMedia API for camera access
- Canvas 2D API for all image processing
- GitHub Pages deployment workflow included (copies public files to root)

The application requires HTTPS for mobile device camera access but falls back to HTTP for local development.