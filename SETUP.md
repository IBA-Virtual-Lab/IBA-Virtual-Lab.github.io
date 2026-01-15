# IBA Virtual Lab - Setup Instructions

This repository contains the HTML wrapper for the IBA Virtual Lab Unity WebGL application.

## Quick Start

### 1. Build Your Unity Project for WebGL

1. Open your Unity project
2. Go to **File > Build Settings**
3. Select **WebGL** as the platform
4. Click **Switch Platform** if not already selected
5. Click **Build** and choose a build folder (e.g., `WebGL-Build`)

### 2. Deploy Your Build

After building, Unity will create a folder with the following structure:
```
WebGL-Build/
├── Build/
│   ├── Build.data
│   ├── Build.framework.js
│   ├── Build.loader.js
│   └── Build.wasm
├── TemplateData/
│   └── (style files)
└── index.html
```

### 3. Use This Repository's HTML Wrapper

1. Copy the `Build` folder from your Unity WebGL build to this repository's root
2. Copy the `StreamingAssets` folder if your project uses it
3. Open `index.html` in a web browser

**Note:** Due to CORS restrictions, you'll need to serve the files through a web server. You cannot simply open `index.html` directly in a browser.

### 4. Serve Locally for Testing

You can use any web server. Here are some options:

#### Python 3
```bash
python -m http.server 8000
```

#### Python 2
```bash
python -m SimpleHTTPServer 8000
```

#### Node.js (using http-server)
```bash
npx http-server -p 8000
```

#### PHP
```bash
php -S localhost:8000
```

Then open your browser to `http://localhost:8000`

## Deployment to GitHub Pages

This repository is set up for GitHub Pages deployment:

1. Ensure your `Build` folder is in the repository root
2. Commit and push your changes
3. Go to your repository **Settings > Pages**
4. Set the source to the main branch
5. Your site will be available at `https://IBA-Virtual-Lab.github.io/`

## Customization

### Updating Branding

Edit `index.html` to customize:
- Page title (line 8)
- Header title and description (lines 197-198)
- Footer information (lines 213-215)
- Color scheme (CSS variables in the `<style>` section)

### Build Folder Configuration

If your build folder has a different name, update the `buildUrl` variable in the JavaScript section:

```javascript
var buildUrl = "Build"; // Change this to match your build folder name
```

### Responsive Design

The wrapper is responsive and works on:
- Desktop browsers
- Tablets
- Mobile devices

The aspect ratio automatically adjusts for smaller screens.

## Troubleshooting

### "Unity build files not found" Warning

This means the `Build` folder is not in the correct location or hasn't been added yet. Ensure:
1. You've built your Unity project for WebGL
2. The `Build` folder is in the repository root
3. The folder contains `Build.loader.js`, `Build.data`, `Build.framework.js`, and `Build.wasm`

### Black Screen or Loading Forever

1. Check the browser console for errors (F12)
2. Ensure you're serving the files through a web server (not `file://`)
3. Check that all build files are present and not corrupted
4. Verify your Unity build settings are correct

### Memory Issues

If your application is large, you may need to adjust Unity's memory settings:
1. In Unity, go to **Edit > Project Settings > Player**
2. Under **Publishing Settings**, increase the **Memory Size** if needed

## Technical Details

### Features

- ✅ Responsive design (desktop, tablet, mobile)
- ✅ Custom loading bar with progress indicator
- ✅ Fullscreen support
- ✅ Error handling and user feedback
- ✅ Modern, professional styling
- ✅ Mobile-optimized viewport settings
- ✅ CORS-safe implementation
- ✅ Accessible controls

### Browser Compatibility

Tested and working on:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

### File Structure

```
repository/
├── index.html          # Main HTML wrapper (this file)
├── Build/              # Unity WebGL build files (add after building)
│   ├── Build.data
│   ├── Build.framework.js
│   ├── Build.loader.js
│   └── Build.wasm
├── StreamingAssets/    # Optional: Unity streaming assets
├── README.md           # Project description
├── SETUP.md           # This setup guide
└── .gitignore         # Git ignore rules
```

## Support

For issues or questions:
- Open an issue on [GitHub](https://github.com/IBA-Virtual-Lab/IBA-Virtual-Lab.github.io/issues)
- Contact: NTNU Ålesund - Department of Biological Sciences (IBA)

## License

See [LICENSE](LICENSE) file for details.
