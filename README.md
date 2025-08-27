# BETTERME Mobile

## Description
The mobile frontend for BETTERME, built with Flutter, provides a native mobile experience for tracking nutrition and workouts on iOS and Android. It communicates with the BETTERME backend API to manage user data.

## Prerequisites
- **Flutter**: Install via Homebrew (`brew install flutter`) and verify with `flutter doctor`.
- **Xcode**: Install via the Mac App Store, then configure:
  ```zsh
  sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
  sudo xcodebuild -runFirstLaunch
  sudo xcodebuild -license
  ```
- **CocoaPods**: Install via `brew install cocoapods` (version 1.16.2 or higher).
- **Android Studio**: Install via `brew install --cask android-studio` for Android development.
- **MacOS**: Compatible with MacBook M3 (16GB RAM).

## Installation
1. **Clone the repository**:
   ```zsh
   git clone https://github.com/username/better_me_mobile.git
   cd better_me_mobile
   ```
2. **Initialize Flutter project**:
   ```zsh
   flutter create .
   ```
3. **Install dependencies**:
   ```zsh
   flutter pub get
   pod install --project-directory=ios
   ```
   - Ensure `pubspec.yaml` includes dependencies and assets:
     ```yaml
     dependencies:
       flutter:
         sdk: flutter
       http: ^1.2.2
       flutter_dotenv: ^5.1.0
       permission_handler: ^11.3.1
     flutter:
       uses-material-design: true
       assets:
         - .env
     ```
   - Run `flutter pub get` to resolve dependencies.
   - If `pod install` fails, manually create `Podfile`:
     ```zsh
     cd ios
     pod init
     pod install
     ```

4. **Configure Android SDK**:
   - Open Android Studio and use the SDK Manager (**Preferences > Appearance & Behavior > System Settings > Android SDK**):
     - **SDK Platforms**: Ensure Android 16.0 (Baklava, API Level 36) is installed.
     - **SDK Tools**: Install Android SDK Command-line Tools (latest), Build-Tools (e.g., 36.0.0), and Platform-Tools.
     - Click **Apply** to install.
   - Accept licenses:
     ```zsh
     flutter doctor --android-licenses
     ```

## Usage
1. **Run the development server**:
   ```zsh
   flutter run -d <device_id>
   ```
   - List devices with `flutter devices`.
   - Set up an iOS simulator:
     ```zsh
     xcrun simctl create "iPhone 16 Pro" com.apple.CoreSimulator.SimDeviceType.iPhone-16-Pro com.apple.CoreSimulator.SimRuntime.iOS-18-6
     xcrun simctl boot "iPhone 16 Pro"
     open -a Simulator
     ```
   - Set up an Android emulator in Android Studio (Device Manager):
     ```zsh
     ~/Library/Android/sdk/emulator/emulator -avd <emulator_name>
     ```
   - For physical devices, connect via USB and enable Developer Mode.
2. **Configure API**:
   - Ensure the BETTERME backend is running (see [better_me_backend](https://github.com/username/better_me_backend)) at `http://localhost:8000`.
   - Expose with `ngrok`:
     ```zsh
     brew install ngrok
     ngrok http 8000
     ```
   - Create `.env` in project root:
     ```zsh
     echo "API_URL=https://your-ngrok-url.ngrok.io" > .env
     ```
   - Update `pubspec.yaml` with `flutter_dotenv` and assets.
3. Example usage:
   - Log meals and workouts via the mobile app.
   - View summaries of your nutrition and fitness progress.

## Shutting Down
1. **Stop the Flutter app**:
   - Press `q` in the terminal running `flutter run`.
   - Or kill the process:
     ```zsh
     ps aux | grep flutter
     kill -9 <flutter_pid>
     ```
2. **Shut down the iOS simulator**:
   ```zsh
   xcrun simctl shutdown "iPhone 16 Pro"
   osascript -e 'quit app "Simulator"'
   ```
3. **Stop the backend**:
   - Press `Ctrl+C` in the terminal running `fastapi dev main.py`.
   - Deactivate the virtual environment:
     ```zsh
     deactivate
     ```
   - Or kill the process:
     ```zsh
     ps aux | grep uvicorn
     kill -9 <uvicorn_pid>
     ```
4. **Stop ngrok**:
   - Press `Ctrl+C` in the terminal running `ngrok http 8000`.
   - Or kill the process:
     ```zsh
     ps aux | grep ngrok
     kill -9 <ngrok_pid>
     ```
5. **Clean Flutter build**:
   ```zsh
   cd better_me/better_me_mobile
   flutter clean
   flutter doctor --clear-device-cache
   ```

## Project Structure
- `lib/`: Contains Dart source code (e.g., `main.dart`).
- `pubspec.yaml`: Defines dependencies (e.g., `http`, `flutter_dotenv`, `permission_handler`) and assets.
- `ios/`, `android/`: Platform-specific configurations.
- `.gitignore`: Ignores build artifacts (e.g., `build/`, `.dart_tool/`, `.env`, `*.apk`, `*.aab`).

## Troubleshooting
- **Invalid `pubspec.yaml`**:
  - Ensure `assets` is under the `flutter` section:
    ```yaml
    flutter:
      assets:
        - .env
    ```
  - Run `flutter pub get`.
- **Missing `.env`**:
  - If `FileNotFoundError` occurs with `flutter_dotenv`:
    ```zsh
    echo "API_URL=https://your-ngrok-url.ngrok.io" > .env
    chmod +r .env
    ```
  - Alternatively, move to `assets/`:
    ```zsh
    mkdir assets
    mv .env assets/
    ```
    Update `pubspec.yaml` and `main.dart` accordingly.
- **No iOS Simulators**:
  - Create iPhone 16 Pro simulator:
    ```zsh
    xcrun simctl create "iPhone 16 Pro" com.apple.CoreSimulator.SimDeviceType.iPhone-16-Pro com.apple.CoreSimulator.SimRuntime.iOS-18-6
    ```
  - Boot simulator:
    ```zsh
    xcrun simctl boot "iPhone 16 Pro"
    open -a Simulator
    ```
  - Clear Flutter device cache:
    ```zsh
    flutter doctor --clear-device-cache
    flutter devices --device-timeout 30
    ```
- **macOS Launch Failure**:
  - Avoid macOS target; disable in `pubspec.yaml`:
    ```yaml
    flutter:
      macos: false
    ```
  - Use Android/iOS:
    ```zsh
    flutter run -d <android_or_ios_device_id>
    ```

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