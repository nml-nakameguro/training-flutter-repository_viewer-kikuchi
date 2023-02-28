# Repository Viewer

## About

This app was created for training Flutter and its code
※Can not build it now

## Requirement

- Dart 2.18.7
- Flutter 3.7.4

## How to setup development environment

<details>
<summary>Steps</summary>

1. Install [Dart](https://dart.dev/)
    - Follow the instruction described at [Get the Dart SDK](https://dart.dev/get-dart)
    - If you're on macOS, you can install Dart with [Homebrew](https://brew.sh/)
      ```
      brew tap dart-lang/dart
      brew install dart
      ```
2. Install [fvm](https://github.com/leoafarias/fvm)
   ```
   dart pub global activate fvm
   ```
3. Install Flutter
   ```
   fvm install
   ```
4. Run `graphql_codegen` plugin to generate code
   ```
   make build-runner
   ```
5. Install Dart packages
   ```
   fvm flutter pub get
   ```
6. Install [rbenv](https://github.com/rbenv/rbenv)
    - Follow the instruction described at https://github.com/rbenv/rbenv#installation
    - If you're on macOS, you can install rbenv with [Homebrew](https://brew.sh/)
      ```
      brew install rbenv
      ```
7. Install [Ruby](https://www.ruby-lang.org/)
   ```
   rbenv install
   ```
8. Install [CocoaPods](https://cocoapods.org/)
   ```
   rbenv exec gem install cocoapods
   ```
9. Install CocoaPods dependencies
   ```
   make ios-pod
   ```
10. Obtain certificates and provisioning profiles to sign iOS app for development
    ```
    make ios-cert
    ```

</details>

## Github token Setting

Please create Personal Access Token below scopes

- [x] : repo
    - [x] : repo:status
    - [x] : repo_deployment
    - [x] : public_repo
    - [x] : repo:invite
    - [x] : security_events
- [ ] : admin:org
    - [ ] : write:org
    - [x] : read:org
    - [ ] : manage_runners:org

## Code structure

### Directories

```
├── android                  Android app files
├── assets                   Asset files for Flutter
├── ios                      iOS app files
│   ├── Runner.xcworkspace       Xcode workspace file
│   └── fastlane                 Fastlane files(will be added at first time ios build)
├── lib                      Flutter app files
│   ├── entity                   Independent data class
│   ├── gen                      Generated files (graphql, rest api, riverpod)
│   ├── graphql                  Graphql query files and shema file
│   ├── provider                 Defintions of Riverpod providers
│   └── ui                       UI layer
└── test                     Test files
```
### Layering

```
┌────────┐
│ UI     │
└───┬────┘
    │  
┌───▼────┐
│ Hooks  │
│Provider│
└───┬────┘
    │ Use
┌───▼────┐
│ entity │
└───▲────┘
    │ 
┌───┴────┐
│graphql │
└────────┘
```
