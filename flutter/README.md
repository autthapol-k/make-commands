# Flutter Project Makefile

This Flutter project includes a Makefile with various commands to streamline development workflows. Below are all available commands and their descriptions.

## Quick Start

To set up the project and run all necessary build steps:

```bash
make all
```

## Available Commands

### 🔧 Setup & Dependencies

#### `make pub-get`
Downloads and installs all Flutter dependencies specified in `pubspec.yaml`.

```bash
make pub-get
```

#### `make clean`
Cleans the Flutter project by removing build artifacts and cached files.

```bash
make clean
```

### 🏗️ Code Generation

#### `make build-gen`
Runs the build runner to generate code (typically for packages like json_annotation, freezed, etc.).

```bash
make build-gen
```

**Note:** Uses `--delete-conflicting-outputs` flag to automatically resolve conflicts.

#### `make build-watch`
Runs the build runner in watch mode, automatically regenerating code when source files change.

```bash
make build-watch
```

**Note:** Uses `--delete-conflicting-outputs` flag to automatically resolve conflicts.

#### `make build-slang`
Generates internationalization (i18n) files using the slang package.

```bash
make build-slang
```

### 🎨 App Flavors

#### `make flavor-gen`
Generates app flavors and configurations for different environments using flutter_flavorizr.

```bash
make flavor-gen
```

**Includes:**
- Asset management (download, extract, clean)
- Android configuration (manifest, build.gradle, icons)
- iOS configuration (podfile, xcconfig, build targets, schema, icons, plist)
- Firebase and Huawei AGConnect setup
- IDE configuration

### 🧪 Testing & Coverage

#### `make test-coverage`
Runs Flutter tests with coverage analysis and generates an HTML coverage report.

```bash
make test-coverage
```

**Process:**
1. Runs `flutter test --coverage`
2. Extracts coverage data for bloc, use_cases, and repositories
3. Generates HTML coverage report
4. Opens the coverage report in your default browser

**Output:** Coverage report will be available in `coverage/html/index.html`

### 🚀 Complete Build

#### `make all`
Runs the complete build pipeline in the following order:

```bash
make all
```

**Execution order:**
1. `clean` - Clean previous builds
2. `pub-get` - Install dependencies
3. `build-gen` - Generate code
4. `build-slang` - Generate i18n files

## Development Workflow

### Initial Setup
```bash
make all
```

### During Development
```bash
# For continuous code generation
make build-watch

# For testing with coverage
make test-coverage
```

### Before Deployment
```bash
# Generate flavors if needed
make flavor-gen

# Run complete build
make all
```

## Prerequisites

Make sure you have the following tools installed:
- Flutter SDK
- Dart SDK
- Make (usually pre-installed on macOS/Linux)
- lcov (for coverage reports): `brew install lcov` on macOS

## Notes

- All commands are designed to be run from the project root directory
- The Makefile uses `--delete-conflicting-outputs` for build_runner commands to automatically handle conflicts
- Coverage reports focus on business logic layers (bloc, use_cases, repositories)
