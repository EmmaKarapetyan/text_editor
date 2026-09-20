# Lyrics Studio

Lyrics Studio is a free, browser-only editor for creating timed lyrics and subtitles.

## Workflow

1. Choose a local video or audio file.
2. Paste the lyrics, one subtitle line per line.
3. Generate initial timing with Whisper running in the browser.
4. Check and correct blocks in the editor:
   - edit text
   - change start/end times
   - drag timeline edges
   - set a time from the current video position
   - split, delete, or add blocks
   - drag each lyric to its own position on the video
5. Save a project JSON file or export a rendered H.264/AAC MP4 with the subtitles burned into the video.

The media file is processed locally in the browser. It is not uploaded to a server, and no account or API key is required.

## Free hosting

The page can be hosted as a static site on GitHub Pages, Netlify, or Cloudflare Pages. For GitHub Pages:

1. Create a repository.
2. Upload `index.html`.
3. Open **Settings → Pages**.
4. Select **Deploy from branch**, then the main branch and root folder.

The first timing run downloads the Whisper model into the browser cache, so it may take longer than later runs. Video export also loads an FFmpeg WebAssembly encoder and can take several minutes for high-resolution videos.

## Use on a phone or tablet

The editor is responsive and can be opened from a phone or tablet browser. For testing on the same Wi-Fi network, start the server so it accepts connections from other devices:

```text
python -m http.server 8765 --bind 0.0.0.0
```

Find the computer's local IPv4 address (for example, `192.168.1.25`) and open this address on the phone:

```text
http://192.168.1.25:8765/index.html
```

Allow Python through the Windows Firewall if the phone cannot connect. For access outside the local network, publish the folder through a static HTTPS host such as GitHub Pages, Netlify, or Cloudflare Pages. Video files and project data remain in the browser on the device being used.
