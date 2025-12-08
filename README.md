# Color Sample Portrait

A web application that captures color samples from your webcam and creates beautiful portraits with custom tiled backgrounds using AI-powered background segmentation.

## Features

- **Interactive Color Sampling**: Click on different areas of your image to collect 5 unique color samples
- **AI-Powered Background Removal**: Uses Google's MediaPipe Selfie Segmentation for precise person/background separation
- **Custom Background Generation**: Creates artistic tiled patterns from your collected colors
- **Real-time Processing**: Live webcam preview and instant color capture
- **Mobile-Friendly**: HTTPS support for mobile device camera access
- **Debug Mode**: Comprehensive visualization of segmentation process

## Quick Start

1. **Install Dependencies**
   ```bash
   npm install
   ```

2. **Generate SSL Certificates** (for mobile camera access)
   ```bash
   openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
   ```

3. **Start the Server**
   ```bash
   npm start    # Production server
   npm run dev  # Development with auto-reload
   ```

4. **Access the Application**
   - HTTPS: `https://localhost:3443` (recommended for mobile)
   - HTTP: `http://localhost:3000` (desktop fallback)

## How It Works

1. **Welcome**: Introduction and camera permissions
2. **Color Sampling**: Click 5 different areas in your webcam feed to collect colors
3. **Photo Preparation**: Position yourself and prepare for photo capture
4. **Countdown**: 3-second countdown before photo capture
5. **Final Result**: View your portrait with AI-generated background

## Technology Stack

- **Backend**: Node.js with Express.js
- **Frontend**: Vanilla HTML5, CSS3, JavaScript
- **AI Segmentation**: Google MediaPipe Selfie Segmentation
- **Image Processing**: HTML5 Canvas API
- **Camera Access**: WebRTC getUserMedia API

## AI Attribution

This project uses **Google MediaPipe Selfie Segmentation** for advanced background removal:

- **MediaPipe**: Copyright 2020 Google LLC
- **License**: Apache License 2.0
- **Documentation**: https://google.github.io/mediapipe/solutions/selfie_segmentation.html
- **CDN Libraries**:
  - `@mediapipe/camera_utils`
  - `@mediapipe/control_utils`
  - `@mediapipe/drawing_utils`
  - `@mediapipe/selfie_segmentation`

MediaPipe provides state-of-the-art machine learning solutions for live and streaming media. The selfie segmentation model enables precise person/background separation in real-time web applications.

## Browser Compatibility

- **Desktop**: Chrome, Firefox, Safari, Edge (latest versions)
- **Mobile**: Requires HTTPS for camera access
- **WebRTC Support**: Required for camera functionality
- **Canvas 2D**: Required for image processing

## Development

The application requires no build process - it's pure HTML, CSS, and JavaScript with CDN-loaded dependencies.

### Project Structure
```
swatchme/
├── server.js          # Express server with HTTP/HTTPS setup
├── public/
│   ├── index.html     # Main application
│   └── styles.css     # Styling and animations
├── cert.pem          # SSL certificate (generated)
├── key.pem           # SSL private key (generated)
└── package.json      # Dependencies and scripts
```

### Debug Mode

Enable debug mode in the final result screen to view:
- Original webcam image
- MediaPipe segmentation mask
- Generated tiled background

## Deployment

### GitHub Pages (Automatic)

The project includes a GitHub Actions workflow that automatically deploys on push to main:
- Copies public files to root directory
- Excludes server files and dependencies
- Deploys to `gh-pages` branch

### AWS CloudFront (Manual)

Deploy to AWS S3 + CloudFront for production hosting:

```bash
# Deploy to AWS
./deploy.sh
```

The deployment script will:
1. Check AWS CLI authentication
2. Auto-detect the correct CloudFront distribution
3. Sync files to S3 bucket: `s3://swatchme/site/`
4. Invalidate CloudFront cache
5. Display the live URL

**Prerequisites:**
- AWS CLI installed and configured
- Valid AWS credentials with S3 and CloudFront permissions
- Access to the `swatchme` S3 bucket

### Validate CloudFront Configuration

If CloudFront configuration changes or you need to verify the setup:

```bash
./validate-cloudfront.sh
```

This script will:
- List all CloudFront distributions
- Identify the correct distribution for SwatchMe
- Show detailed configuration (origin, aliases, status)
- Verify S3 bucket exists and contains content
- Display distribution ID and URLs

**Auto-Detection Logic:**
The deployment script automatically finds the CloudFront distribution by matching:
- **Origin**: `swatchme.s3.us-east-1.amazonaws.com`
- **Alias**: `swatchme.coryallen.ninja`

If your CloudFront configuration changes:
1. Run `./validate-cloudfront.sh` to identify the new distribution
2. Update `EXPECTED_ORIGIN` and `EXPECTED_ALIAS` in both scripts
3. The deploy script will automatically use the updated values

## License

MIT License

## Acknowledgments

- **Google MediaPipe Team** for the exceptional selfie segmentation technology
- **MediaPipe Contributors** for open-source machine learning solutions
- **WebRTC Community** for browser camera access standards