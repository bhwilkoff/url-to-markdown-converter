# 🔄 URL to Markdown Converter

> Convert any webpage to clean, formatted Markdown instantly - including authenticated pages and Google Sites!

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-brightgreen)](https://bhwilkoff.github.io/url-to-markdown-converter/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![No Build Process](https://img.shields.io/badge/No%20Build-Vanilla%20JS-yellow.svg)](#)

A powerful, client-side tool that converts web pages into clean Markdown format. Works with public pages, authenticated content, and has special optimizations for Google Sites with dynamic class names

## ✨ Features

### 🔐 **Multiple Access Methods**
- **Direct URL Input**: Convert public web pages instantly
- **Bookmarklet**: Extract content from authenticated/login-protected pages
- **Manual HTML**: Paste HTML source for complex scenarios

### 🧠 **Smart Content Extraction**
- **Intelligent Algorithm**: Uses heuristic analysis instead of hardcoded selectors
- **Google Sites Optimized**: Handles dynamic class names and complex layouts
- **Mozilla Readability**: Leverages battle-tested content extraction
- **Navigation Filtering**: Automatically removes menus, ads, and clutter

### 📱 **Cross-Platform Support**
- **Desktop Browsers**: Chrome, Firefox, Safari, Edge
- **Mobile Support**: iPhone Safari bookmarklet integration
- **Responsive Design**: Works on all screen sizes

### 📝 **Clean Markdown Output**
- **GitHub Flavored Markdown**: Tables, strikethrough, task lists
- **Smart Link Handling**: Filters navigation links, preserves content links
- **Image Alt-Text**: Converts images to descriptive text
- **Structured Content**: Maintains headings, lists, and formatting

### 💾 **Export & Share**
- **Download .md Files**: One-click file download
- **Copy to Clipboard**: Quick copy functionality
- **Native Sharing**: iOS/Android share sheet integration
- **Real-time Preview**: See results immediately

## 🚀 Quick Start

### Method 1: Direct URL (Public Pages)
1. Visit [the converter](https://bhwilkoff.github.io/url-to-markdown-converter/)
2. Paste any public URL
3. Click "Convert to Markdown"
4. Download or copy the result

### Method 2: Bookmarklet (Authenticated Pages)
1. **Desktop**: Drag the bookmarklet to your bookmarks bar
2. **iPhone Safari**: Copy bookmarklet code → Create bookmark → Replace URL with code
3. Navigate to any webpage (including login-protected content)
4. Click the bookmarklet
5. Confirm to open the converter with extracted content

### Method 3: Manual HTML (Complex Cases)
1. Right-click on any webpage → "View Page Source"
2. Copy the HTML source code
3. Paste into the "Manual HTML" tab
4. Convert to Markdown

## 🛠️ Installation & Deployment

### GitHub Pages Deployment
```bash
git clone https://github.com/yourusername/url-to-markdown-converter.git
cd url-to-markdown-converter
# No build process needed - just push to GitHub Pages
```

### Local Development
```bash
# Serve locally (Python 3)
python -m http.server 8000

# Or with Node.js
npx http-server

# Open http://localhost:8000
```

### CDN Dependencies
The tool uses these CDN resources:
- [Readability.js](https://unpkg.com/@mozilla/readability@0.4.4/Readability.js)
- [Turndown.js](https://unpkg.com/turndown@7.1.2/turndown.min.js)

## 🏗️ Architecture & How It Works

### Content Extraction Pipeline
1. **Input Processing**: URL fetch, bookmarklet extraction, or manual HTML
2. **Content Analysis**: Heuristic scoring system analyzes all containers
3. **Smart Filtering**: Removes navigation, ads, and UI elements
4. **Markdown Conversion**: Turndown.js converts clean HTML to Markdown
5. **Post-Processing**: Final cleanup and formatting

### Google Sites Intelligence
```javascript
// Heuristic scoring system (simplified)
const score = (container) => {
  let score = 0;
  
  // Positive indicators
  if (textLength > 100) score += textLength / 100;
  if (textToHtmlRatio > 0.3) score += 5;
  if (contentElements > 3) score += 3;
  
  // Negative indicators  
  if (linkDensity > 50) score -= 5;
  if (isNavigation) score -= 10;
  
  return score;
};
```

### Smart Cleaning Algorithm
- **Content Preservation**: Keeps lists, paragraphs, meaningful links
- **Navigation Removal**: Detects and removes repetitive menu structures
- **Ad Filtering**: Removes advertising and promotional content
- **UI Cleanup**: Strips buttons, search boxes, social widgets

## 🔧 Customization Guide

### Adding New Content Selectors
```javascript
// In processHTML() function, modify primary selectors
const primarySelectors = [
  '.your-content-class',
  '[data-content-area]',
  '.main-content',
  // Add your site's content selectors
];
```

### Custom Content Filtering
```javascript
// In cleanAndExtractContent() function
const customUnwantedSelectors = [
  '.your-ads-class',
  '#sidebar',
  '.social-widgets',
  // Add elements to remove
];
```

### Modifying Markdown Output
```javascript
// In turndownService configuration
turndownService.addRule('customRule', {
  filter: 'div.special-content',
  replacement: function(content, node) {
    return `**Special:** ${content}\n\n`;
  }
});
```

### Bookmarklet Customization
```javascript
// Modify the scoring algorithm in the bookmarklet
var scored = allDivs.map(function(div) {
  // Your custom scoring logic
  var score = yourCustomScoringFunction(div);
  return {el: div, score: score, len: textLen};
});
```

### Styling Customization
```css
/* Modify the CSS variables */
:root {
  --primary-gradient: linear-gradient(135deg, #your-color 0%, #your-color2 100%);
  --border-radius: 15px;
  --shadow: 0 10px 30px rgba(0,0,0,0.1);
}
```

## 🎯 Advanced Usage

### Custom Site Integration
```javascript
// Add support for your specific CMS/platform
if (isYourSite) {
  const result = findContentInYourSite(doc);
  // Custom extraction logic
}
```

### API Integration
```javascript
// Add custom CORS proxy
const proxyUrl = `https://your-cors-proxy.com/api?url=${encodeURIComponent(url)}`;
```

### Batch Processing
```javascript
// Process multiple URLs (extend the tool)
const urls = ['url1', 'url2', 'url3'];
const results = await Promise.all(urls.map(convertURL));
```

## 📊 Browser Compatibility

| Feature | Chrome | Firefox | Safari | Edge | iOS Safari | Android |
|---------|--------|---------|--------|------|------------|---------|
| Direct URL | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Bookmarklet | ✅ | ✅ | ✅ | ✅ | ✅ | ❌ |
| Manual HTML | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Clipboard API | ✅ | ✅ | ✅ | ✅ | ⚠️ | ⚠️ |
| File Download | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

**Legend**: ✅ Full Support, ⚠️ Limited Support, ❌ Not Supported

## 🐛 Troubleshooting

### Common Issues

**Bookmarklet not working?**
- Ensure you dragged the link to bookmarks bar (not copied URL)
- Try refreshing the page and dragging again
- For mobile: Copy bookmarklet code, don't drag

**Content not extracting properly?**
- Check browser console for debugging info
- Try Manual HTML method as fallback
- Some sites block CORS requests

**Getting navigation instead of content?**
- The heuristic algorithm should handle this automatically
- Check console logs to see scoring results
- Report persistent issues with specific URLs

### Debug Mode
```javascript
// Enable verbose logging
localStorage.setItem('urlToMarkdown_debug', 'true');
// Check browser console for detailed extraction info
```

## 🤝 Contributing

### Development Setup
1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make changes to the single HTML file
4. Test across browsers
5. Submit a pull request

### Code Structure
```
/
├── index.html          # Main application (all code in one file)
├── README.md          # This file
└── LICENSE           # MIT License
```

### Adding Features
- **New extraction methods**: Modify the `processHTML()` function
- **UI improvements**: Update the embedded CSS
- **New export formats**: Extend the download functionality
- **Mobile enhancements**: Test on iOS/Android devices

### Testing Checklist
- [ ] Desktop browsers (Chrome, Firefox, Safari, Edge)
- [ ] Mobile Safari (iPhone)
- [ ] Bookmarklet functionality
- [ ] Google Sites with various layouts
- [ ] CORS-protected sites
- [ ] Large content extraction
- [ ] Navigation filtering accuracy

## 📋 Roadmap

### Planned Features
- [ ] **Batch Processing**: Convert multiple URLs at once
- [ ] **Custom Templates**: User-defined Markdown formatting
- [ ] **Plugin System**: Extensible extraction modules
- [ ] **Cloud Sync**: Save/sync conversion history
- [ ] **API Endpoint**: REST API for integration
- [ ] **Browser Extension**: Native browser integration

### Content Support Improvements
- [ ] **WordPress Sites**: Enhanced WP theme detection
- [ ] **Medium Articles**: Better Medium.com support
- [ ] **Documentation Sites**: GitBook, GitLab Pages, etc.
- [ ] **E-commerce**: Product page extraction
- [ ] **Social Media**: Twitter thread compilation

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Mozilla Readability**: Core content extraction algorithm
- **Turndown.js**: HTML to Markdown conversion
- **GitHub Pages**: Free hosting platform
- **Community**: Contributors and issue reporters

---

**Made with ❤️ for the open-source community**

*Convert the web, one page at a time* 🌐➡️📝