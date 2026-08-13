A powerful, browser-based video player that supports M3U playlists and JSON APIs with DRM-protected MPD streams. Built with Shaka Player, it handles Clear Key DRM, cookies, custom headers, and user-agent spoofing.

![Version](https://img.shields.io/badge/version-1.0.0-red)
![License](https://img.shields.io/badge/license-MIT-blue)
![Platform](https://img.shields.io/badge/platform-Web-brightgreen)

---

## ✨ Features

- **M3U Playlist Support** - Parse standard M3U playlists with extended attributes
- **JSON API Support** - Load channel data from JSON APIs
- **DRM Playback** - Clear Key DRM support via Shaka Player
- **Cookie & Header Injection** - Pass cookies, User-Agent, Origin, Referer
- **Multi-Format** - Supports both `.mpd` (DASH) and `.m3u8` (HLS) streams
- **Auto-Save** - Remembers last loaded playlist in localStorage
- **Mobile Friendly** - Responsive design with touch support
- **Picture-in-Picture** - PiP support on compatible browsers
- **Adaptive Bitrate** - Quality adjustment based on network conditions
- **Video Fit Controls** - Cycle between Fit, Fill, and Zoom modes

---

## 🚀 Quick Start

### 1. Open the Player
Simply open the `index.html` file in any modern browser (Chrome, Firefox, Edge, Safari).

### 2. Load a Playlist

#### Option A: Load from URL
1. Enter a URL pointing to an M3U playlist or JSON API
2. Click **"Load URL"**

#### Option B: Paste Playlist
1. Click **"📋 Paste"**
2. Paste your M3U or JSON content
3. Click **"▶ Parse"**

#### Option C: Use Sample
1. Click **"📄 Sample"** to load a demo playlist
2. Click **"▶ Parse"** to load it

### 3. Watch Streams
- Click any channel card to start playing
- Use the video controls to play/pause, adjust volume, or go fullscreen

---

## 📋 Supported Formats

### M3U Playlist Format
```m3u
#EXTM3U
#EXTINF:-1 tvg-id="460" tvg-name="Star Sports Select 1 HD" tvg-logo="https://example.com/logo.jpg" group-title="Sports",Star Sports Select 1 HD
#KODIPROP:inputstream.adaptive.manifest_type=mpd
#KODIPROP:inputstream.adaptive.license_type=clearkey
#KODIPROP:inputstream.adaptive.license_key=keyid:key
#EXTVLCOPT:http-user-agent=CustomUserAgent
#EXTHTTP:{"cookie":"__hdnea__=...", "Origin":"https://example.com", "Referer":"https://example.com"}
https://example.com/stream.mpd
```

### JSON API Format
```json
{
  "channels": [
    {
      "id": "channel_id",
      "name": "Channel Name",
      "stream_url": "https://example.com/stream.mpd",
      "logo": "https://example.com/logo.jpg",
      "group": "Sports",
      "key_id": "32characterhexkeyid",
      "key": "32characterhexkey",
      "cookie": "__hdnea__=...",
      "user_agent": "Custom User Agent"
    }
  ]
}
```

Or direct array format:
```json
[
  {
    "id": "channel_id",
    "name": "Channel Name",
    "mpd_url": "https://example.com/stream.mpd",
    "keyId": "32characterhexkeyid",
    "key": "32characterhexkey",
    "cookie": "__hdnea__=...",
    "group": "Sports"
  }
]
```

---

## 🔧 Supported Tags

| Tag | Description |
|-----|-------------|
| `#EXTINF` | Channel info: `tvg-id`, `tvg-name`, `tvg-logo`, `group-title` |
| `#KODIPROP:inputstream.adaptive.license_key` | Clear Key DRM: `key_id:key` |
| `#KODIPROP:inputstream.adaptive.manifest_type=mpd` | MPD manifest type |
| `#KODIPROP:inputstream.adaptive.license_type=clearkey` | Clear Key license type |
| `#EXTVLCOPT:http-user-agent` | Custom User-Agent header |
| `#EXTHTTP` | JSON with `cookie`, `Origin`, `Referer` headers |

---

## 🛠️ Technical Details

### Player Engine
- **Shaka Player** v4.16.2 - Google's open-source DASH/HLS player
- **DRM Support** - Clear Key decryption
- **Adaptive Bitrate** - Automatic quality switching based on network

### Device Optimization
- Automatically adjusts quality based on device capabilities:
  - **Low-end**: 480p, 1.2 Mbps
  - **Mid-range**: 720p, 3.5 Mbps
  - **High-end**: 1080p, unlimited

### Network Handling
- Automatic retry on connection failures (up to 5 attempts)
- Cookie injection for authenticated streams
- Custom headers (User-Agent, Referer, Origin)

---

## 📱 Browser Support

| Browser | Support |
|---------|---------|
| Chrome | ✅ Full |
| Firefox | ✅ Full |
| Edge | ✅ Full |
| Safari | ✅ Full (HLS only) |
| Mobile Chrome | ✅ Full |
| Mobile Safari | ✅ Full |

---

## 🔒 Security Notes

- **DRM Keys**: Keep your `key_id:key` pairs secure
- **Cookies**: The player stores cookies in localStorage - clear them after use if sensitive
- **Content**: Only use with content you have rights to stream

---

## 🐛 Troubleshooting

### "No streams found"
- Check if your playlist contains valid URLs
- Ensure the M3U format is correct (starts with `#EXTM3U`)
- For JSON, check the structure matches the expected format

### "Stream unavailable"
- The stream might be offline or the URL expired
- Try refreshing the playlist
- Check if the cookie/key are still valid

### "DRM error"
- Verify the `key_id:key` is correct
- Ensure the manifest requires Clear Key DRM
- Check if the key matches the content

### "Buffering"
- The player automatically adjusts quality based on network speed
- Try switching to a lower quality stream if available
- Check your network connection

---

## 📝 License

MIT License - Free to use, modify, and distribute.

---

## 🙏 Credits

- Built with [Shaka Player](https://shaka-player-demo.appspot.com/)
- Icons by [Feather Icons](https://feathericons.com/)
- Inspired by open-source streaming projects

---

## 📞 Support

For issues or questions, please open an issue on the repository or contact the maintainer.

---

**Made with ❤️ for streaming enthusiasts**
```
