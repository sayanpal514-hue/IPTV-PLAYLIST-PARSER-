# 📺 Sportlink - IPTV Playlist Parser & Video Player

A powerful, modern browser-based IPTV player with support for M3U playlists, JSON APIs, and DRM-protected streams. Built with Shaka Player for seamless streaming of 1000+ channels across multiple formats and categories.

[![Version](https://img.shields.io/badge/version-2.0.0-red?style=flat-square)](https://github.com/sayanpal514-hue/IPTV-PLAYLIST-PARSER-)
[![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Web-brightgreen?style=flat-square)](https://sayanpal514-hue.github.io/IPTV-PLAYLIST-PARSER-/)
[![Build Status](https://img.shields.io/badge/status-Active-success?style=flat-square)]()
[![Browser Support](https://img.shields.io/badge/browsers-Chrome%20%7C%20Firefox%20%7C%20Edge%20%7C%20Safari-informational?style=flat-square)]()

---

## 🎯 Live Demo

**[👉 Try the Live Player Now](https://sayanpal514-hue.github.io/IPTV-PLAYLIST-PARSER-/)**

Experience 1,173+ streaming channels with full DRM support, adaptive bitrate streaming, and advanced playback controls.

---

## ✨ Features

### 🎬 Playback & Streaming
- **Multi-Format Support** - DASH (`.mpd`)
- **Adaptive Bitrate Streaming** - Automatic quality switching based on network conditions
- **DRM Protection** - Clear Key DRM decryption support
- **Picture-in-Picture** - Float video while browsing (PiP)
- **Fullscreen Mode** - Immersive viewing experience
- **Video Fit Controls** - Cycle between Fit, Fill, and Zoom modes

### 📋 Playlist Management
- **M3U Playlist Support** - Extended M3U format with attributes
- **JSON API Support** - Load channels from JSON endpoints
- **Auto-Save** - Remembers last loaded playlist in localStorage
- **Quick Load** - Load URL, paste content, or use sample playlists
- **1000+ Channels** - Organized by category (Sports, Movies, News, etc.)

### 🔐 Security & Authentication
- **Cookie Injection** - Support for authentication cookies
- **Custom Headers** - User-Agent, Origin, Referer spoofing
- **Secure Key Management** - Handle DRM keys safely
- **HTTPS Ready** - Works with encrypted streams

### 📱 User Experience
- **Responsive Design** - Mobile, tablet, and desktop optimized
- **Touch Support** - Full touch controls for mobile devices
- **Dark Theme** - Easy on the eyes, modern aesthetic
- **Category Filtering** - Organize channels by type
- **Search Functionality** - Find channels quickly
- **Channel Cards** - Logo, name, language, and category at a glance

### 🛠️ Developer Features
- **Shaka Player Integration** - Industry-standard DASH/HLS player
- **Network Optimization** - Automatic retry with exponential backoff
- **Device Detection** - Auto-adjusted quality for device capabilities
- **Comprehensive Logging** - Debug mode for troubleshooting
- **Modular Code** - Easy to extend and customize

---

## 🚀 Quick Start

### Option 1: Open Directly
Simply open the deployed player in your browser:
```
https://sayanpal514-hue.github.io/IPTV-PLAYLIST-PARSER-/
```

### Option 2: Clone & Host Locally

```bash
# Clone the repository
git clone https://github.com/sayanpal514-hue/IPTV-PLAYLIST-PARSER-.git
cd IPTV-PLAYLIST-PARSER-

# Open in browser (requires Python 3 for local server)
python3 -m http.server 8000
# Visit: http://localhost:8000
```

### Loading Your First Playlist

#### Method A: Load from URL
1. Click **"Load URL"** button
2. Paste your M3U or JSON URL:
   ```
   https://example.com/playlist.m3u
   ```
3. Click **"Load"**
4. Click any channel card to play

#### Method B: Paste Playlist Content
1. Click **"📋 Paste"** button
2. Paste your M3U or JSON content
3. Click **"▶ Parse"**
4. Select a channel to stream

#### Method C: Use Sample Playlist
1. Click **"📄 Sample"** button
2. Click **"▶ Parse"**
3. Start watching immediately

---

## 📋 Supported Formats

### M3U Playlist Format

Standard extended M3U format with IPTV attributes:

```m3u
#EXTM3U
#EXTINF:-1 tvg-id="460" tvg-name="Star Sports Select 1 HD" tvg-logo="https://example.com/logo.jpg" group-title="Sports",Star Sports Select 1 HD
#KODIPROP:inputstream.adaptive.manifest_type=mpd
#KODIPROP:inputstream.adaptive.license_type=clearkey
#KODIPROP:inputstream.adaptive.license_key=32characterhexkeyid:32characterhexkey
#EXTVLCOPT:http-user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64)
#EXTHTTP:{"cookie":"__hdnea__=value123", "Origin":"https://example.com", "Referer":"https://example.com"}
https://example.com/stream.mpd

#EXTINF:-1 tvg-id="100" tvg-name="Colors HD" tvg-logo="https://example.com/colors.png" group-title="Entertainment",Colors HD
https://example.com/colors.m3u8
```

### JSON API Format - Option 1 (Recommended)

```json
{
  "channels": [
    {
      "id": "ch_001",
      "name": "Star Sports 1 HD",
      "stream_url": "https://example.com/stream.mpd",
      "logo": "https://example.com/logo.jpg",
      "group": "Sports",
      "language": "English",
      "key_id": "32characterhexkeyid",
      "key": "32characterhexkey",
      "cookie": "__hdnea__=value123",
      "user_agent": "Mozilla/5.0...",
      "origin": "https://example.com",
      "referer": "https://example.com"
    },
    {
      "id": "ch_002",
      "name": "Colors HD",
      "stream_url": "https://example.com/colors.m3u8",
      "logo": "https://example.com/colors.png",
      "group": "Entertainment",
      "language": "Hindi"
    }
  ]
}
```

### JSON API Format - Option 2 (Direct Array)

```json
[
  {
    "id": "ch_001",
    "name": "Star Sports 1 HD",
    "mpd_url": "https://example.com/stream.mpd",
    "keyId": "32characterhexkeyid",
    "key": "32characterhexkey",
    "cookie": "__hdnea__=value123",
    "group": "Sports",
    "logo": "https://example.com/logo.jpg"
  }
]
```

---

## 🔧 M3U Tag Reference

| Tag | Attribute | Description | Example |
|-----|-----------|-------------|---------|
| `#EXTINF` | `tvg-id` | Channel ID | `tvg-id="460"` |
| `#EXTINF` | `tvg-name` | Channel name | `tvg-name="Star Sports"` |
| `#EXTINF` | `tvg-logo` | Logo URL | `tvg-logo="https://example.com/logo.jpg"` |
| `#EXTINF` | `group-title` | Category | `group-title="Sports"` |
| `#KODIPROP` | `inputstream.adaptive.manifest_type` | Stream type | `=mpd` or `=hls` |
| `#KODIPROP` | `inputstream.adaptive.license_type` | DRM type | `=clearkey` |
| `#KODIPROP` | `inputstream.adaptive.license_key` | DRM key | `=keyid:key` (64 hex chars) |
| `#EXTVLCOPT` | `http-user-agent` | Custom user agent | `=Mozilla/5.0...` |
| `#EXTHTTP` | JSON object | Custom headers | `{"cookie":"...", "Origin":"..."}` |

---

## 🎯 Use Cases

### Personal IPTV Setup
Set up your own IPTV player for family streaming with custom playlists and DRM-protected content.

### Testing & Debugging
Test M3U playlists, JSON APIs, and stream configurations before deploying to other devices.

### Content Aggregation
Combine multiple IPTV sources into one interface with organized categories and search.

### Live Event Streaming
Stream live sports, news, and events with adaptive bitrate for varying network conditions.

### Educational Broadcasting
Create playlists for educational content and institutional streaming.

---

## 🛠️ Technical Architecture

### Core Technology Stack
- **Shaka Player** v4.16.2 - Industry-standard DASH/HLS player by Google
- **Vanilla JavaScript** - No dependencies, lightweight and fast
- **HTML5 Video API** - Native browser video capabilities
- **Local Storage** - Client-side persistence

### Streaming Protocols
- **DASH (Dynamic Adaptive Streaming over HTTP)** - `.mpd` manifests
- **HLS (HTTP Live Streaming)** - `.m3u8` playlists
- **Progressive HTTP** - Direct media file streaming

### DRM Support
- **Clear Key DRM** - Unencrypted key decryption
- **License Key Format** - `keyid:key` (32 hex chars each)
- **Secure Delivery** - HTTPS for key transmission

### Adaptive Quality
Automatic device detection and optimization:

| Device | Resolution | Bitrate |
|--------|-----------|---------|
| Low-end (Mobile) | 480p | 1.2 Mbps |
| Mid-range (Tablet) | 720p | 3.5 Mbps |
| High-end (Desktop) | 1080p | Unlimited |

### Network Resilience
- Automatic retry on failure (up to 5 attempts)
- Exponential backoff strategy
- Connection error detection
- Timeout handling (30s default)

---

## 📊 Supported Browsers

| Browser | Desktop | Mobile | Status |
|---------|---------|--------|--------|
| Chrome | ✅ Full | ✅ Full | Fully Supported |
| Firefox | ✅ Full | ✅ Full | Fully Supported |
| Edge | ✅ Full | ✅ Full | Fully Supported |
| Safari | ⚠️ HLS only | ✅ Full | Limited (HLS) |
| Opera | ✅ Full | ✅ Full | Fully Supported |
| IE 11 | ❌ Not Supported | - | Unsupported |

**Note:** Safari has limited DASH/DRM support; HLS works perfectly.

---

## 🎮 Player Controls

### Keyboard Shortcuts
| Key | Action |
|-----|--------|
| `Space` | Play/Pause |
| `F` | Toggle Fullscreen |
| `M` | Toggle Mute |
| `↑/↓` | Volume Control |
| `←/→` | Seek (±5 seconds) |
| `P` | Picture-in-Picture |
| `T` | Video Fit Mode |

### Mouse Controls
- **Click video** - Play/Pause
- **Double-click** - Fullscreen toggle
- **Scroll wheel** - Volume control
- **Drag** - Seek through timeline

### Touch Controls
- **Tap** - Play/Pause
- **Double-tap** - Fullscreen
- **Swipe left/right** - Seek
- **Pinch** - Zoom (in Zoom mode)

---

## 🔒 Security & Privacy

### What This Player Does
- ✅ Processes streams locally in your browser
- ✅ Stores preferences in browser's localStorage
- ✅ Handles cookies for authentication
- ✅ Supports HTTPS streams

### What This Player Doesn't Do
- ❌ Send your data to external servers
- ❌ Track your viewing habits
- ❌ Store personal information
- ❌ Display advertisements

### Best Practices
1. **DRM Keys** - Keep `key_id:key` pairs confidential
2. **Cookies** - Clear sensitive cookies after use
3. **URLs** - Use HTTPS sources when possible
4. **Content** - Only stream content you own or have rights to
5. **Local Storage** - Clear browser cache periodically

---

## 🐛 Troubleshooting

### "No streams found"
**Issue:** Playlist loads but shows no channels
- ✅ Verify playlist format starts with `#EXTM3U`
- ✅ Check JSON structure matches expected format
- ✅ Ensure URLs are properly formatted
- ✅ Validate that stream URLs are accessible

**Solution:**
```bash
# Test URL accessibility
curl -I https://example.com/stream.mpd
```

---

### "Stream unavailable / 404 Error"
**Issue:** Selected channel won't play
- ✅ Stream URL may be expired or offline
- ✅ Server may be down temporarily
- ✅ Regional restrictions might apply
- ✅ Geoblocking could be active

**Solution:**
- Try refreshing the playlist
- Test with a VPN if geoblocked
- Wait and retry after some time
- Check if alternate streams are available

---

### "DRM Error / Playback Failed"
**Issue:** Protected content won't play
- ✅ Verify `key_id:key` format (32 hex chars each, separated by colon)
- ✅ Ensure key matches the content
- ✅ Check license type is set to `clearkey`
- ✅ Confirm manifest requires DRM protection

**Example Valid Key:**
```
key_id: 1234567890abcdef1234567890abcdef
key:    fedcba0987654321fedcba0987654321
Format: 1234567890abcdef1234567890abcdef:fedcba0987654321fedcba0987654321
```

---

### "Buffering / Quality Too Low"
**Issue:** Stream stutters or quality is poor
- ✅ Check internet speed (min. 2 Mbps for 720p)
- ✅ Player auto-adjusts quality to network speed
- ✅ Try closing other apps consuming bandwidth
- ✅ Restart player and select stream again

**Network Requirements:**
- 480p: 1+ Mbps
- 720p: 2.5+ Mbps
- 1080p: 5+ Mbps

---

### "CORS / Access-Control Error"
**Issue:** Cross-Origin error when loading playlist
- ✅ Playlist source may not allow cross-origin access
- ✅ Server CORS headers might be misconfigured
- ✅ Try using a CORS proxy (not recommended for security)

**Workaround:**
Contact the playlist provider to enable CORS headers.

---

### "Cookie/Header Not Working"
**Issue:** Authentication isn't working
- ✅ Verify cookie format: `name=value`
- ✅ Ensure JSON syntax is correct for `#EXTHTTP`
- ✅ Check if cookie has expired
- ✅ Try URL-encoding cookie values if special chars present

**Example:**
```json
{
  "cookie": "__hdnea__=abcd1234; secure=true",
  "Origin": "https://example.com",
  "Referer": "https://example.com/watch"
}
```

---

### "Player Won't Load in Browser X"
**Solution:**
- ✅ Update your browser to latest version
- ✅ Clear browser cache and cookies
- ✅ Disable browser extensions (ad blockers, etc.)
- ✅ Try an incognito/private window
- ✅ Check browser console for errors (F12)

---

## 📚 API Reference

### JavaScript API (For Developers)

```javascript
// Get player instance
const player = document.querySelector('video');

// Play stream
player.play();

// Pause stream
player.pause();

// Set volume (0-1)
player.volume = 0.5;

// Seek to time (seconds)
player.currentTime = 120;

// Get current quality
console.log(player.getStats());

// Listen for errors
player.addEventListener('error', (e) => {
  console.error('Playback error:', e);
});
```

### Local Storage Keys

```javascript
// Last loaded playlist URL
localStorage.getItem('lastPlaylistUrl');

// Last selected channel
localStorage.getItem('lastSelectedChannel');

// Saved preferences
localStorage.getItem('playerSettings');
```

---

## 🚀 Deployment

### Deploy to GitHub Pages
1. Fork the repository
2. Enable GitHub Pages in settings
3. Select `main` branch as source
4. Your player is live at: `https://yourusername.github.io/IPTV-PLAYLIST-PARSER-/`

### Deploy to Netlify
1. Connect your GitHub repo
2. Build settings: Leave empty (static site)
3. Publish directory: `/` (root)
4. Deploy and access via Netlify domain

### Deploy to Docker
```dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
EXPOSE 80
```

```bash
docker build -t iptv-player .
docker run -p 80:80 iptv-player
```

### Deploy to Your Own Server
```bash
# Upload files via FTP/SFTP
scp -r ./* user@server:/var/www/html/iptv-player/
```

---

## 🤝 Contributing

We welcome contributions! Here's how to help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/awesome-feature`)
3. **Commit** your changes (`git commit -m 'Add awesome feature'`)
4. **Push** to the branch (`git push origin feature/awesome-feature`)
5. **Open** a Pull Request

### Contribution Ideas
- 🌍 Translations to other languages
- 🎨 UI/UX improvements
- 🐛 Bug fixes and error handling
- ⚡ Performance optimizations
- 📚 Documentation improvements
- 🧪 Test coverage
- 🔧 Feature requests

---

## 📝 License

MIT License - Free to use, modify, and distribute for any purpose.

```
Copyright (c) 2024 Sportlink Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 🙏 Credits & Acknowledgments

- **[Shaka Player](https://shaka-player-demo.appspot.com/)** - Google's powerful DASH/HLS player
- **[Feather Icons](https://feathericons.com/)** - Beautiful, minimalist icons
- **[HTML5 Video API](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)** - Browser video standard
- Inspired by open-source IPTV projects and streaming community

---

## 🐛 Known Limitations

- Safari only supports HLS (`.m3u8`), not DASH (`.mpd`)
- DRM protection limited to Clear Key (no Widevine/PlayReady)
- Some older devices may not support 1080p playback
- Picture-in-Picture not available on all browsers

---

## 📞 Support & Contact

### Getting Help
- 🔍 **Search** existing [GitHub Issues](https://github.com/sayanpal514-hue/IPTV-PLAYLIST-PARSER-/issues)
- 💬 **Create** a new issue with detailed description
- 📧 **Email** maintainer for security concerns
- 💡 **Discussions** for feature requests and ideas

### Report a Bug
When reporting bugs, please include:
- Browser and version
- Operating system
- Playlist source (M3U/JSON URL)
- Error message or description
- Steps to reproduce

---

## 🗺️ Roadmap

### Coming Soon
- [ ] Search and filter channels by name/category
- [ ] Favorites/watchlist functionality
- [ ] Viewing history and resume playback
- [ ] EPG (Electronic Program Guide) support
- [ ] Channel organization and custom sorting
- [ ] Light/Dark theme toggle
- [ ] Subtitle/caption support
- [ ] Playlist scheduling
- [ ] Analytics dashboard (optional)

### Future Plans
- [ ] Mobile app (React Native)
- [ ] Desktop app (Electron)
- [ ] Multi-user support with cloud sync
- [ ] Advanced DVR capabilities
- [ ] Widevine DRM support
- [ ] Dolby Digital 5.1 support

---

## 📊 Stats

- **1,173+** streaming channels
- **50+** categories
- **30+** languages supported
- **100%** client-side processing
- **0** external dependencies
- **< 500KB** total size

---

## ⭐ Show Your Support

If you find this project useful, please:
- ⭐ **Star** the repository
- 🍴 **Fork** for your needs
- 📢 **Share** with others
- 🤝 **Contribute** improvements

**Made with ❤️ by the Sportlink Community**

```
  ╔═══════════════════════════════════════════════════════════════╗
  ║                                                               ║
  ║    📺 Sportlink - Stream Anything, Anywhere, Anytime        ║
  ║                                                               ║
  ║    https://sayanpal514-hue.github.io/IPTV-PLAYLIST-PARSER-/  ║
  ║                                                               ║
  ╚═══════════════════════════════════════════════════════════════╝
```

---

**Last Updated:** August 2024  
**Status:** ✅ Active & Maintained  
**Questions?** Open an issue on GitHub!
