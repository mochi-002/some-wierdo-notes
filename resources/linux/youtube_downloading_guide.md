# 📥 YouTube Downloading & Merging Guide (Linux)

A clean reference for **downloading YouTube videos** and ensuring **video + audio are merged into a single MP4 file** using **yt-dlp** and **ffmpeg**.

---

## 🛠 Tools Overview

### 🔹 yt-dlp

- Modern YouTube downloader
    
- Handles playlists, formats, quality selection
    
- Uses **ffmpeg** automatically for merging
    

### 🔹 FFmpeg

- Media processing tool
    
- Used for **lossless merging**, cutting, converting
    

---

## 📦 Installation (Arch Linux)

```bash
sudo pacman -S yt-dlp ffmpeg
```

Verify:

```bash
yt-dlp --version
ffmpeg -version
```

---

## 🎥 Download ONE Video (720p, MP4, video + audio together)

```bash
yt-dlp \
-f "bv*[height<=720][ext=mp4]+ba[ext=m4a]" \
--merge-output-format mp4 \
-o "~/Videos/%(title)s.%(ext)s" \
"https://www.youtube.com/watch?v=VIDEO_ID"
```

✔ Output: **single MP4 file**

---

## 📂 Download Playlist (720p, MP4, merged)

```bash
yt-dlp \
-f "bv*[height<=720][ext=mp4]+ba[ext=m4a]/b[ext=mp4]" \
--merge-output-format mp4 \
-o "~/Videos/%(playlist_title)s/%(playlist_index)02d - %(title)s.%(ext)s" \
"PLAYLIST_URL"
```

---

## ▶️ Download ONLY ONE Video from a Playlist

### 🔹 By index (example: video #7)

```bash
yt-dlp \
--playlist-items 7 \
-f "bv*[height<=720][ext=mp4]+ba[ext=m4a]" \
--merge-output-format mp4 \
-o "~/Videos/%(title)s.%(ext)s" \
"PLAYLIST_URL"
```

### 🔹 Find playlist indexes

```bash
yt-dlp --flat-playlist "PLAYLIST_URL"
```

---

## ⏭ Start from a Specific Video in Playlist

```bash
yt-dlp \
--playlist-start 5 \
-f "bv*[height<=720][ext=mp4]+ba[ext=m4a]" \
--merge-output-format mp4 \
"PLAYLIST_URL"
```

---

## 🔊 Audio Only (MP3)

```bash
yt-dlp -x --audio-format mp3 "VIDEO_URL"
```

High quality:

```bash
yt-dlp -x -f bestaudio --audio-format mp3 "VIDEO_URL"
```

---

## 🧩 Manual Merging (FFmpeg)

### 🔹 Merge video + audio (lossless)

```bash
ffmpeg -i video.mp4 -i audio.m4a -c copy output.mp4
```

### 🔹 Explicit stream mapping

```bash
ffmpeg -i video.mp4 -i audio.m4a \
-map 0:v:0 -map 1:a:0 -c copy output.mp4
```

---

## ✂️ Cut Video After Download

```bash
ffmpeg -ss 00:10:00 -i input.mp4 -c copy output.mp4
```

---

## 🔍 Inspect File Streams

```bash
ffprobe output.mp4
```

---

## ⚠️ Common Mistakes

❌ `yt-dlp -f bestvideo URL` → video only (no audio)

❌ `-o "~/Videos/"` → invalid output template

✅ Always include filename:

```bash
-o "~/Videos/%(title)s.%(ext)s"
```

---

## ⭐ Recommended Alias (Optional)

Add to `~/.bashrc` or `~/.zshrc`:

```bash
alias ytmp4='yt-dlp -f "bv*[height<=720][ext=mp4]+ba[ext=m4a]" --merge-output-format mp4'
```

Usage:

```bash
ytmp4 "VIDEO_URL"
```

---

## ⚖️ Legal Note

- Download only content you **own** or have **permission** to use
    
- Respect YouTube Terms of Service and local laws
    

---

> ✅ This setup covers **single videos**, **playlists**, **quality control**, and **proper merging**.