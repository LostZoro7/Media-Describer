# Media Describer

A lightweight desktop tool to inspect media files and automatically generate upload-ready descriptions and BBCode/HTML layouts for trackers and media communities.

---

## Features

- **Automated Metadata Extraction:** Inspects container tracks, video, audio, and subtitle streams via MediaInfo, FFmpeg, and FFprobe.
- **Customizable Templates:** Edit format layouts with live tag syntax highlighting.
- **Integrated Image Hosting:** Automatic screenshot capture and sequential upload failover (supports ImgBB, Freeimage.host, and Imgur Client IDs).
- **Clipboard Sync:** Automatic one-click generation and instant clipboard synchronization on file selection.

---

## Requirements & External Tools

Media Describer relies on standard media binaries. Place the executables in a `lib` folder alongside the application, or configure their path directly within the application settings:

| Binary | Description |
|---|---|
| `ffmpeg.exe` | Video processing & screenshot generation |
| `ffprobe.exe` | Stream stream analysis & duration probing |
| `MediaInfo.exe` | CLI metadata parser |

> **Folder Layout:**
> ```text
> MediaDescriber/
> ├── MediaDescriber.exe
> ├── settings.json (hidden)
> ├── settings.json.bak (hidden)
> └── lib/
>     ├── ffmpeg.exe
>     ├── ffprobe.exe
>     └── MediaInfo.exe
> ```

---

## Configuration

1. Download the latest release from the **Releases** section.
2. Ensure `lib/` contains the necessary binaries or set the custom binary path inside **Settings**.
3. (Optional) Provide API keys for preferred image upload services (ImgBB, Freeimage.host, or Imgur) under **Settings**.
4. Select a site preset, browse for a media file (`.mkv`, `.mp4`, etc.), and click **Generate**.

## Image Host API Keys & Setup

Media Describer uses an automatic fallback chain (`ImgBB` -> `Freeimage.host` -> `Imgur`) to host screenshots. If a service runs into a rate limit or error, it instantly attempts the next configured host.

### 1. ImgBB (Recommended Primary)
1. Go to [api.imgbb.com](https://api.imgbb.com/) and sign up or log in.
2. Click **Get API Key**.
3. Copy your 32-character API key.
4. Paste it into **Settings** ImgBB **API key**.

---

### 2. Freeimage.host (Secondary Fallback)
- **Pre-configured:** Comes with a built-in public key ready out of the box.
- **Custom Key (Optional):** If you prefer using your own account
1. go to [freeimage.host/page/api](https://freeimage.host/page/api)
2. create an account
3. copy your API key and paste it into **Settings** Freeimage.host **API key**.

---

### 3. Imgur (Tertiary Fallback)
1. Log in to [imgur.com](https://imgur.com/).
2. Open the [Imgur Application Registration Page](https://api.imgur.com/oauth2/addclient).
3. Fill in the form:
   - **Application name:** `Media Describer` (or any name you prefer)
   - **Authorization type:** Select **OAuth 2 authorization without a callback URL**
   - **Authorization callback URL:** Leave blank or enter `https://localhost`
   - **Email:** Your email address
4. Submit the form.
5. Copy the generated **Client ID** (you do not need the *Client Secret*).
6. Paste it into **Settings** Imgur **Client ID**.

## License & Third-Party Credits

This project is licensed under the [MIT License](LICENSE).

### Third-Party Binaries
Media Describer relies on external tools located in the `lib/` directory or on your system PATH:
- **[FFmpeg / FFprobe](https://ffmpeg.org/):** Licensed under the GNU Lesser General Public License (LGPL) version 2.1 or later.
- **[MediaInfo](https://mediaarea.net/en/MediaInfo):** Licensed under the BSD 2-Clause License.
