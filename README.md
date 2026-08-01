🎵 Skfy

A modern, Spotify-inspired music streaming app for Android — built with Kotlin & Jetpack Compose.

Show Image Show Image Show Image Show Image

</div>
📖 Overview

Skfy is an original Android music player built as a learning/portfolio project. It supports playing your own local audio files and streaming tracks from a self-hosted, GitHub-based library — all wrapped in a clean, animated, Material 3 UI inspired by modern streaming apps.

⚠️ Not affiliated with Spotify. Skfy is an independent, original app. All UI, branding, and code are original work; no Spotify assets, trademarks, or copyrighted content are used or distributed.

✨ Features
🎧 Local playback — scans device storage via MediaStore for MP3, WAV, AAC, FLAC, M4A, and OGG files
☁️ Remote streaming — streams tracks from a JSON-described library hosted on GitHub (jsDelivr / raw.githubusercontent.com)
🏠 Home feed — Continue Listening, Recently Played, Top Songs, Recommended, Albums, Artists, Playlists
🔍 Live search — across local and remote songs, artists, albums, and playlists
📚 Library — Favorites, Downloads, Folders, History, Most Played
▶️ Full-screen player — rotating artwork, blurred background, queue, sleep timer, playback speed, basic equalizer, lyrics panel
🎚️ Mini-player — persistent, swipe-to-dismiss, expands with a smooth shared-element transition
📥 Downloads — resumable downloads for remote tracks
🎵 Playlists — create, edit, and mix local + remote tracks
🌓 Dark / Light / Dynamic color (Material You) theming
📱 Media session integration — lock screen, notification, Bluetooth, and headset controls
📡 Offline-first — full functionality without network access for local content
🛠️ Tech Stack
Layer	Technology
Language	Kotlin
UI	Jetpack Compose + Material 3
Architecture	MVVM + Clean Architecture + Repository pattern
DI	Hilt
Async	Coroutines + Flow
Networking	Retrofit + OkHttp
JSON	Moshi
Local DB	Room
Preferences	DataStore
Background work	WorkManager
Playback	AndroidX Media3 (ExoPlayer + MediaSession)
Image loading	Coil
Testing	JUnit5, MockK, Turbine, Compose UI Test
🏗️ Architecture
app/
├── data/
│   ├── local/          # Room entities, DAOs, MediaStore scanner
│   ├── remote/         # Retrofit services, DTOs, GitHub JSON parsing
│   └── repository/     # Repository implementations
├── domain/
│   ├── model/           # Domain models
│   ├── repository/      # Repository interfaces
│   └── usecase/         # Business logic
├── presentation/
│   ├── home/
│   ├── search/
│   ├── library/
│   ├── player/
│   ├── settings/
│   └── components/      # Shared composables
├── player/               # Media3 playback service, MediaSession
├── di/                   # Hilt modules
├── navigation/           # Navigation Compose graph
└── ui/theme/             # Colors, typography, dynamic theming

Follows a unidirectional data flow: UI → ViewModel (StateFlow) → UseCase → Repository → Room / Retrofit.

📦 Remote Library Format

Skfy can stream from any public GitHub repository structured like this:

music-library/
├── json/
│   ├── songs.json
│   ├── albums.json
│   ├── artists.json
│   ├── playlists.json
│   └── config.json
├── covers/
└── songs/

Example songs.json entry:

json
{
  "id": "1",
  "title": "Song Name",
  "artist": "Artist",
  "album": "Album",
  "duration": "03:22",
  "cover": "covers/song.jpg",
  "url": "songs/song.mp3"
}

The base URL is derived automatically from your GitHub username, repo, and branch (configured in-app under Settings) — never hardcoded.

⚠️ Content note: Only host audio files you have the rights to distribute (original recordings, royalty-free tracks, or explicitly licensed content). GitHub/jsDelivr are not designed as a media CDN — expect file-size limits (~20 MB/file on jsDelivr's free tier) and no guarantee of bandwidth at scale. This is intended for personal libraries and demos, not commercial distribution.

🚀 Getting Started
Prerequisites
Android Studio (latest stable)
JDK 17+
An Android device or emulator running API 28+
Setup
bash
git clone https://github.com/<your-username>/skfy.git
cd skfy
Open the project in Android Studio and let Gradle sync.
Run the app on an emulator or physical device.
Grant storage/media permissions when prompted to enable local library scanning.
(Optional) Go to Settings → Remote Library and enter your GitHub username, repository name, and branch to enable remote streaming.
Build from command line
bash
./gradlew assembleDebug

The APK will be output to app/build/outputs/apk/debug/.

🗺️ Roadmap
 Android Auto certification
 Lyrics sync (LRC support)
 Chromecast support
 Cloud backup for playlists/favorites
 Widget support
🤝 Contributing

Contributions are welcome!

Fork the repository
Create a feature branch (git checkout -b feature/your-feature)
Commit your changes (git commit -m "Add your feature")
Push to the branch (git push origin feature/your-feature)
Open a Pull Request

Please open an issue first for major changes so we can discuss the approach.

📄 License

This project is licensed under the MIT License.

⚠️ Disclaimer

Skfy is an independent, open-source project built for educational purposes. It is not affiliated with, endorsed by, or connected to Spotify AB or any other music streaming service. Users are solely responsible for ensuring they have the legal right to any audio content they add to their local library or remote GitHub repository.
