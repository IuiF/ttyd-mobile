# ttyd with Mobile Browser Support

This is a fork of [ttyd](https://github.com/tsl0922/ttyd) with full mobile browser support, specifically designed to solve the issue where terminal display is hidden by browser address bars and navigation bars when accessing ttyd from smartphones.

## 🚀 Mobile Features

- **Dynamic Viewport Height**: Uses `dvh` units with `vh` fallbacks for perfect mobile display
- **Visual Viewport API**: Responds to iOS address bar show/hide behavior  
- **Safe Area Support**: Full support for notch and Dynamic Island devices
- **Keyboard Adaptation**: Auto-layout adjustment when mobile keyboards appear
- **Portrait/Landscape**: Full orientation support
- **Debounce Handling**: Prevents WebSocket overload during frequent resize events

## 📱 Supported Browsers

- **iOS Safari**: 15.4+ (dvh support)
- **Android Chrome**: 108+ (dvh support)
- **Firefox Mobile**: 101+
- **Samsung Internet**: 21+

## 🔧 Installation & Usage

### Build from Source

```bash
# Clone the repository
git clone https://github.com/IuiF/ttyd-mobile.git
cd ttyd-mobile

# Build frontend
cd html
npm install
npm run build
cd ..

# Build ttyd binary (HTML embedded)
mkdir -p build
cd build
cmake ..
make
cd ..

# Run ttyd with mobile support
./build/ttyd -p 8080 -W bash
```

### Usage (Same as Original)

```bash
# Basic usage
ttyd bash

# Custom port
ttyd -p 8080 bash

# Writable mode
ttyd -p 8080 -W bash
```

**No additional HTML file specification required - mobile support is built-in!**

## 🔍 Technical Implementation

### HTML Changes
- Added viewport meta tag with `viewport-fit=cover`
- Enables full-screen mobile experience

### CSS Enhancements
- Dynamic viewport height (`dvh`) with `vh` fallbacks
- Safe area support using `env(safe-area-inset-*)`
- Responsive design for all screen sizes

### JavaScript Features
- Visual Viewport API integration for iOS address bar handling
- Debounced resize handlers to prevent performance issues
- Automatic container height adjustment

## 📊 Comparison with Original ttyd

| Feature | Original ttyd | Mobile-Enhanced ttyd |
|---------|---------------|----------------------|
| Desktop Display | ✅ Perfect | ✅ Perfect (unchanged) |
| Mobile Display | ❌ Partial/Hidden | ✅ Full Screen |
| iOS Address Bar | ❌ Overlaps | ✅ Dynamic Adjustment |
| Android Keyboard | ❌ Overlaps | ✅ Auto Resize |
| Notch Support | ❌ None | ✅ Safe Area Support |
| Build Process | ✅ Same | ✅ Same |
| Usage Commands | ✅ Same | ✅ Same |

## 🛠️ Development

All mobile enhancements are backward compatible and do not affect desktop functionality.

### Modified Files
- `html/src/template.html` - Viewport configuration
- `html/src/style/index.scss` - Mobile-responsive CSS
- `html/src/components/terminal/xterm/index.ts` - Visual Viewport API
- `html/src/components/terminal/index.tsx` - TypeScript fixes

## 📜 License

Same as original ttyd - MIT License

## 🤝 Contributing

This fork focuses specifically on mobile browser support. For general ttyd features, please contribute to the [original repository](https://github.com/tsl0922/ttyd).

## 🙏 Acknowledgments

- Original [ttyd](https://github.com/tsl0922/ttyd) by [tsl0922](https://github.com/tsl0922)
- Mobile enhancements developed with [Claude Code](https://claude.ai/code)

---

**Now you can access ttyd from any mobile device with perfect full-screen terminal experience!** 📱✨