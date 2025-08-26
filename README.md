# BETTERME Mobile

## Description
The mobile frontend for BETTERME, planned to be built with Flutter (or another framework like Swift, Tauri, or Flet), will provide a native mobile experience for tracking nutrition and workouts. It will communicate with the BETTERME backend API to manage user data.

## Prerequisites
- **Flutter**: Install Flutter SDK (if using Flutter) following [official instructions](https://flutter.dev/docs/get-started/install/macos).
- **MacOS**: Compatible with your MacBook M3 (16GB RAM).
- **Xcode** (for iOS development) or **Android Studio** (for Android development, if using Flutter or similar).

## Installation
1. **Clone the repository** (once created):
   ```zsh
   git clone https://github.com/username/better_me_mobile.git
   cd better_me_mobile
   ```
2. **Install dependencies** (example for Flutter):
   ```zsh
   flutter pub get
   ```
   Note: Adjust this step based on the chosen framework (e.g., Swift, Tauri, or Flet).

## Usage
1. **Run the development server** (example for Flutter):
   ```zsh
   flutter run
   ```
2. Ensure the BETTERME backend is running (see [better_me_backend](https://github.com/username/better_me_backend)) to handle API requests.
3. Example usage:
   - Log meals and workouts via the mobile app.
   - View summaries of your nutrition and fitness progress.
4. Note: Specific instructions will be updated once the mobile framework is chosen.

## Project Structure
- To be defined based on the chosen framework (e.g., `lib/` for Flutter source code).
- `.gitignore`: Will ignore framework-specific build artifacts (e.g., `build/`, `.dart_tool/` for Flutter).

## Contributing
1. Fork the repository.
2. Create a new branch:
   ```zsh
   git checkout -b feature-branch
   ```
3. Make your changes and commit:
   ```zsh
   git commit -m 'Add some feature'
   ```
4. Push to the branch:
   ```zsh
   git push origin feature-branch
   ```
5. Open a pull request.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Related Repositories
- **Frontend**: [better_me_frontend](https://github.com/username/better_me_frontend)
- **Backend**: [better_me_backend](https://github.com/username/better_me_backend)