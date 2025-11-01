# PrajnaPlayer v17

PrajnaPlayer v17 is a lightweight, single-file Python media player designed for personal knowledge archives, YouTube transcript collections, Buddhist/academic audio–video libraries, and PharmApp-style R&D folders. It focuses on persistence, offline usage, and consistent theming across Windows/macOS/Linux.

---

## Key Features

- Single-file app: run `PrajnaPlayer_v17.py` directly — easy to ship, back up, and version.
- Auto–assets bootstrap: on first run it can check for the `assets/` folder and download the shared asset pack for v17 so you don’t have to bundle large media/icons each time:
  - https://github.com/nghiencuuthuoc/PrajnaPlayer-Assets/tree/main/Assets_v17
- PharmApp-style UI: cream background, branded footer, ready to plug into other PharmApp utilities.
- Session persistence: remembers last folder, last track, volume, and position (via state JSON) so you can continue later — useful for long Dharma talks or R&D videos.
- Local-first: plays media from your local folders; good for big offline collections.
- Pluggable helpers: planned hooks for getting current Chrome tab URL, refreshing assets, and integrating with other PharmApp tools.
- Fits PharmApp ecosystem: naming, folders, and footer texts match your other tools.

---

## Repository Structure

```text
PrajnaPlayer_v17/
├── PrajnaPlayer_v17.py   # main application entry point
```

---

## Requirements

- Python 3.9+ (3.10/3.11/3.12 should work)
- tkinter (usually included on Windows/macOS; on some Linux distros install `python3-tk`)
- A media backend (e.g. `python-vlc` or the one used in your local version of PrajnaPlayer — adapt in the code if needed)
- Internet access only for the very first run if assets need to be auto-downloaded

---

## Installation

1. Clone or download ZIP of this repo.
2. Make sure you have Python available:
   ```bash
   python --version
   ```
3. (Optional) create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate      # macOS/Linux
   venv\Scripts\activate       # Windows
   ```
4. Install extra packages you use in your local PrajnaPlayer builds (example):
   ```bash
   pip install python-vlc pillow requests
   ```

---

## Run

```bash
python PrajnaPlayer_v17.py
```

On the first run the app can:
- check whether `./assets/` (or your configured assets folder) exists,
- download the shared asset pack for v17 from GitHub,
- save it locally for all later runs.

---

## Assets & Branding

- Default assets URL:
  - https://github.com/nghiencuuthuoc/PrajnaPlayer-Assets/tree/main/Assets_v17
- Keep logos/icons inside `assets/` (icons, banners, screenshots, sample audio).
- If you customize the logo, keep the PharmApp / Nghiên Cứu Thuốc footer so other modules recognize this as part of the same suite.

---

## Suggested Folder Layout

```text
PrajnaPlayer_v17/
├── PrajnaPlayer_v17.py
├── assets/                     # auto-downloaded if missing
│   ├── icons/
│   ├── logos/
│   └── samples/
├── database/                   # optional: metadata, playlists
└── state/                      # optional: last played, GUI state
```

(You can also keep state JSONs next to the script, like other PharmApp tools.)

---

## Persistence (Recommended)

PrajnaPlayer v17 is meant to remember:

- last opened media folder
- last played file
- playback position
- volume
- UI preferences (if implemented in your build)

Store them in something like:

```text
./state_recent.json
./state_<folder-hash>.json
./static.json
```

This keeps behavior consistent with your other players and crawlers.

---

## Development Notes

- Current repo has 1 main file → good candidate to split into:
  - `prajna_player/gui.py`
  - `prajna_player/player.py`
  - `prajna_player/assets.py` (download/check)
  - `prajna_player/state.py`
- Add a CLI flag later:
  ```bash
  python PrajnaPlayer_v17.py --headless --scan "D:\PharmApp\audio"
  ```
- Add a watcher to refresh assets or reconnect to PharmApp dashboards.

---

## License

Add your preferred license here (MIT/BSD/Apache-2.0).
If you want to align with the rest of PharmApp’s public modules, use MIT and add the project footer.

---

## Credits

- PharmApp / Nghiên Cứu Thuốc / RnD Pharma Plus (core ecosystem)
- Author: Bùi Huỳnh Quốc Đạt (project owner / maintainer)
- Community users who test on Windows + shared assets repo

---

## Footer (PharmApp style)

PharmApp // Nghiên Cứu Thuốc // RnD Pharma Plus  
www.pharmapp.vn • www.nghiencuuthuoc.com  
© 2025
