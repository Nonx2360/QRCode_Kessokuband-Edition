#  QR Generator Pro

> A modern, professional QR Code Generator with glassmorphism design, dynamic backgrounds, and logo integration capabilities.

[![Made with HTML5](https://img.shields.io/badge/Made%20with-HTML5-E34F26?style=flat-square&logo=html5)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![Styled with Tailwind CSS](https://img.shields.io/badge/Styled%20with-Tailwind%20CSS-38B2AC?style=flat-square&logo=tailwind-css)](https://tailwindcss.com/)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=flat-square&logo=javascript)](https://www.javascript.com/)

---

##  Features

###  Visual Design
- **Glassmorphism UI**: Stunning semi-transparent card with backdrop blur (`backdrop-blur-xl`) and color saturation effects (`backdrop-saturate-150`)
- **Dynamic Random Wallpapers**: Automatically loads a random background image from your `Wallpaper/` folder on each page load
- **Custom Scrollbar**: Themed scrollbar matching the dark aesthetic
- **Smooth Transitions**: 700ms ease-in-out transitions for background changes
- **Responsive Design**: Fully responsive layout with mobile-first approach (`max-w-md` container)
- **Professional Typography**: Uses Google's 'Inter' font family (weights: 400, 500, 600, 700)

###  QR Code Generation
- **URL Encoding**: Convert any URL into a scannable QR code
- **Color Customization**: 
  - Custom QR code module color (default: `#000000` black)
  - Custom background color (default: `#ffffff` white)
- **High Error Correction**: Uses `QRCode.CorrectLevel.H` (High) - allows up to 30% damage/obscuration
- **Optimal Size**: Generates 250×250px QR codes for perfect balance of quality and file size
- **Canvas-Based**: Leverages HTML5 Canvas API for precise rendering

###  Logo Integration
- **Automatic Upload**: Accept any image format through file input (`accept="image/*"`)
- **Smart Centering**: Automatically centers the logo on the QR code
- **Intelligent Sizing**: 
  - Automatically resizes logos to max 20% of QR code dimensions
  - Maintains original aspect ratio
  - Prevents scanning errors while maximizing logo visibility
- **Canvas Composition**: Uses `drawImage()` API for seamless logo overlay
- **Real-time Preview**: Logo appears on the QR code instantly

###  Export Features
- **PNG Download**: One-click download of generated QR codes
- **Composite Export**: Downloaded image includes both QR code and logo
- **Custom Filename**: Downloads as `qr_code_with_logo.png`

---

##  Technical Stack

| Technology | Purpose | Version/Details |
|------------|---------|----------------|
| **HTML5** | Structure & Canvas API | Standard |
| **Tailwind CSS** | Styling & Utilities | CDN (Latest) |
| **JavaScript** | Business Logic | ES6+ |
| **QRCode.js** | QR Generation | v1.0.0 (CDN) |
| **Google Fonts** | Typography | Inter Font Family |

### Key Libraries & CDNs
```html
<!-- Tailwind CSS -->
<script src="https://cdn.tailwindcss.com"></script>

<!-- QRCode.js -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>

<!-- Google Fonts - Inter -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```

---

##  Getting Started

### Prerequisites
- Modern web browser with JavaScript enabled
- No server required - works offline after initial load
- Optional: Images for the `Wallpaper/` directory

### Installation

1. **Clone or Download**
   ```bash
   git clone https://github.com/yourusername/qr-generator-pro.git
   cd qr-generator-pro
   ```

2. **Set Up Wallpapers**
   - Create a `Wallpaper/` directory in the same folder as `index.html`
   - Add your background images (PNG, JPG, etc.)
   - Update the wallpapers array in `index.html` (lines 162-184):
   ```javascript
   const wallpapers = [
       "your-image-1.png",
       "your-image-2.jpg",
       // Add more filenames here
   ];
   ```

3. **Open & Use**
   - Simply open `index.html` in any modern browser
   - No build process or npm installation needed!

---

##  Usage Guide

### Basic QR Code Generation
1. **Enter URL**: Type or paste your target URL in the "Target URL" field
2. **Click Generate**: Press the "Generate QR Code" button
3. **Download**: Click "Download PNG" to save your QR code

### Adding a Logo
1. Click the **"Choose File"** button under "Logo (Optional)"
2. Select your logo image (PNG/JPG/SVG/etc.)
3. Enter your URL and generate
4. The logo will automatically appear centered on the QR code

### Color Customization
1. **QR Color**: Click the color picker under "QR Color" to change module color
2. **Background**: Click the color picker under "Background" to change the QR background
3. Generate to see your custom colors

### Tips for Best Results
- ✅ Use high-contrast colors (e.g., black QR on white background)
- ✅ Keep logos simple and recognizable
- ✅ Test QR codes with your phone camera before printing
- ✅ For print: Use default black/white for maximum scannability
- ⚠️ Avoid very light or similar colors for QR and background

---

##  Project Structure

```
QRCode/
│
├── index.html              # Main application (single-file architecture)
│   ├── <head>              # Meta, fonts, Tailwind config
│   ├── <style>             # Custom scrollbar styles
│   ├── <body>              # Glassmorphism UI
│   └── <script>            # QR generation & logo logic
│
├── Wallpaper/              # Background images directory
│   ├── 103933948_p0.png
│   ├── wallpaper22.png
│   └── ... (21 images total by default)
│
└── README.md               # This file
```

---

##  Customization Guide

### 1. Tailwind Color Scheme
The app uses a custom `brand` color palette. To change accent colors, modify the Tailwind config (lines 13-30):

```javascript
tailwind.config = {
    theme: {
        extend: {
            colors: {
                brand: {
                    50: '#eff6ff',   // Lightest
                    100: '#dbeafe',
                    500: '#3b82f6',  // Primary
                    600: '#2563eb',  // Buttons
                    700: '#1d4ed8',  // Darkest
                }
            }
        }
    }
}
```

### 2. Glassmorphism Effect
To adjust the glass effect intensity, modify these classes on line 58:

```html
<!-- Current settings -->
bg-slate-900/70          <!-- Background opacity (70%) -->
backdrop-blur-xl          <!-- Blur strength (xl = 24px) -->
backdrop-saturate-150     <!-- Color saturation (150%) -->

<!-- Try these alternatives -->
bg-slate-900/50          <!-- More transparent -->
backdrop-blur-2xl         <!-- Stronger blur -->
backdrop-saturate-200     <!-- More vibrant -->
```

### 3. Logo Size Adjustment
To change the logo size limit, edit line 252:

```javascript
const logoMaxSize = qrSize * 0.20;  // Current: 20%

// Options:
// 0.15 = 15% (safer, smaller logo)
// 0.25 = 25% (larger, still scannable with high error correction)
// 0.30 = 30% (maximum recommended)
```

### 4. QR Code Size
To change the output QR code dimensions, edit line 223:

```javascript
const qrSize = 250;  // Current size in pixels

// Recommended sizes:
// 200 = Smaller file size
// 300 = Higher quality for printing
// 500 = Maximum detail (larger file)
```

### 5. Adding/Removing Wallpapers
Update the wallpapers array (lines 162-184):

```javascript
const wallpapers = [
    "new-wallpaper-1.jpg",
    "new-wallpaper-2.png",
    // Auto-selected randomly on page load
];
```

### 6. Background Behavior
Current settings (line 54):
- `bg-fixed` - Wallpaper stays fixed while scrolling
- `bg-cover` - Wallpaper covers entire viewport
- `bg-center` - Wallpaper centered

---

##  Technical Details

### QR Code Error Correction
The app uses **High (H) Level** error correction:
- Recovers up to **30%** of damaged data
- Enables logo placement without breaking scannability
- Trade-off: Slightly larger/denser QR codes

### Canvas Drawing Process
1. `QRCode.js` generates QR code on a `<canvas>` element
2. JavaScript accesses the canvas context
3. Logo image is loaded and resized
4. Logo is drawn at calculated center coordinates
5. Canvas is converted to Data URL
6. Image element's `src` is updated

### Logo Sizing Algorithm
```javascript
// Aspect ratio preservation logic
if (logoWidth > logoHeight) {
    if (logoWidth > logoMaxSize) {
        logoHeight *= logoMaxSize / logoWidth;
        logoWidth = logoMaxSize;
    }
} else {
    if (logoHeight > logoMaxSize) {
        logoWidth *= logoMaxSize / logoHeight;
        logoHeight = logoMaxSize;
    }
}
```

---

##  Troubleshooting

### Issue: QR Code Not Scanning
**Solution:**
- Use higher contrast colors (black/white recommended)
- Reduce logo size (edit `logoMaxSize` to 0.15)
- Ensure adequate lighting when scanning
- Try scanning from different distances

### Issue: Logo Appears Blurry
**Solution:**
- Upload higher resolution logo files
- Increase `qrSize` to 300 or 400 pixels
- Use PNG format for logos (better quality)

### Issue: Wallpaper Not Loading
**Solution:**
- Check that images exist in `Wallpaper/` folder
- Verify filenames match the `wallpapers` array exactly
- Check browser console (F12) for errors
- Ensure image formats are supported (PNG, JPG, WebP)

### Issue: Download Button Not Working
**Solution:**
- Wait for QR code to fully generate (50ms delay)
- Check if browser blocks automatic downloads
- Try right-click → "Save image as..." on the QR code

### Issue: Colors Look Different After Download
**Solution:**
- This is normal - browsers render colors slightly differently
- For print: stick to black/white
- For digital: test on target devices

---

## 🌐 Browser Compatibility

| Browser | Version | Support |
|---------|---------|---------|
| Chrome | 90+ | ✅ Full |
| Firefox | 88+ | ✅ Full |
| Safari | 14+ | ✅ Full |
| Edge | 90+ | ✅ Full |
| Opera | 76+ | ✅ Full |

**Required Features:**
- HTML5 Canvas API
- FileReader API
- ES6+ JavaScript
- CSS Backdrop Filters

---

##  Code Architecture

### Single-File Design
The entire application is contained in `index.html` for:
- ✅ Easy deployment (just upload one file)
- ✅ No build process required
- ✅ Works offline after initial CDN load
- ✅ Simple to understand and modify

### State Management
```javascript
// Global state variables
let logoDataUrl = null;  // Stores uploaded logo as Data URL

// DOM references (cached for performance)
const urlInput = document.getElementById('urlInput');
const logoInput = document.getElementById('logoInput');
// ... etc
```

### Event Flow
```
Page Load → Set Random Wallpaper
User Uploads Logo → FileReader converts to Data URL
User Clicks Generate → QRCode.js creates canvas
If Logo Exists → Draw logo on canvas after 50ms delay
User Clicks Download → Trigger download from canvas Data URL
```

---

##  Future Enhancement Ideas

- [ ] Add QR code size selector (S/M/L)
- [ ] Support vCard, WiFi, Email QR codes
- [ ] Add QR code scanner/reader functionality
- [ ] Theme switcher (light/dark mode)
- [ ] SVG export option
- [ ] Batch QR code generation
- [ ] QR code history/saved codes
- [ ] Share directly to social media
- [ ] Print optimization mode
- [ ] Logo position adjustment (corners vs center)

---

## 🤝 Contributing

Contributions are welcome! Here's how:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Code Style Guidelines
- Use meaningful variable names
- Comment complex logic
- Follow existing indentation (4 spaces)
- Test in multiple browsers

---

##  License

This project is open-source and available under the **MIT License**.

```
MIT License

Copyright (c) 2025 Nonx2

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction...
```

See the full license in the [LICENSE](LICENSE) file.

---

##  Author

**Nonx2**
- Portfolio: [https://nonx2360.github.io/About-Me/](https://nonx2360.github.io/About-Me/)
- GitHub: [@Nonx2360](https://github.com/Nonx2360)

---

##  Acknowledgments

- **QRCode.js** - Lightweight QR code generation library
- **Tailwind CSS** - Utility-first CSS framework
- **Google Fonts** - Inter typography
- **Glassmorphism** design trend inspiration

---

##  Statistics

- **Lines of Code**: ~311
- **File Size**: ~14KB (uncompressed)
- **Dependencies**: 2 (Tailwind, QRCode.js)
- **Supported Image Formats**: PNG, JPG, JPEG, GIF, WebP, SVG
- **Default QR Size**: 250×250px
- **Max Logo Coverage**: 20% (50×50px at default size)
- **Error Correction**: 30% (Level H)

---

<div align="center">

### ⭐ Star this repo if you find it helpful!

Made with ❤️ by Nonx2

</div>
