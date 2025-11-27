# yt-dlp-nuitka

This repository automatically builds **standalone Nuitka binaries of yt-dlp** for Windows (x64 and ARM64).

Every 6 hours the workflow:

1. Checks the latest yt-dlp release
2. Clones the matching source tag
3. Builds it with **Nuitka (standalone, LTO, UPX)**
4. Publishes the zipped `dist/` folder as a GitHub release

No source code is stored here, the repo exists only to automate these builds.

---

## Why does this exist?

My project **[jely2002/youtube-dl-gui](https://github.com/jely2002/youtube-dl-gui)** (Open Video Downloader) uses these Nuitka builds for the Microsoft Store version.

PyInstaller cannot run inside MSIX/AppContainer environments because it expects unrestricted filesystem access and unpacking, which is blocked in the sandbox.

Nuitka produces a real native executable with a fully self-contained dist folder, which does work inside the Windows Store sandbox.  
So OVD uses these Nuitka-built yt-dlp binaries instead of PyInstaller builds.

---

## License

This project is licensed under **The Unlicense**.