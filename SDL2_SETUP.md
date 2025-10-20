# SDL2 Setup Instructions

This project is configured to use SDL2 for game development. Follow these steps to set up SDL2:

## 1. Download SDL2 (NOT SDL3!)

1. Go to the official SDL2 website: https://www.libsdl.org/download-2.0.php
2. Download the "SDL2-devel-2.x.x-VC.zip" file (Visual C++ development libraries)
   - **IMPORTANT**: Make sure you download SDL2, NOT SDL3!
   - The filename should be something like "SDL2-devel-2.28.5-VC.zip"
3. Extract the downloaded zip file

## 2. Copy SDL2 Files

From the extracted SDL2 folder, copy the following files to your project:

### Headers
- Copy all files from `SDL2-2.x.x\include\SDL2\` to `SDL2\include\SDL2\`
  - This should include files like `SDL.h`, `SDL_events.h`, `SDL_render.h`, etc.

### Libraries (x86 - 32-bit)
- Copy `SDL2-2.x.x\lib\x86\SDL2.lib` to `SDL2\lib\x86\`
- Copy `SDL2-2.x.x\lib\x86\SDL2main.lib` to `SDL2\lib\x86\`

### Libraries (x64 - 64-bit)
- Copy `SDL2-2.x.x\lib\x64\SDL2.lib` to `SDL2\lib\x64\`
- Copy `SDL2-2.x.x\lib\x64\SDL2main.lib` to `SDL2\lib\x64\`

### Runtime DLLs
- Copy `SDL2-2.x.x\lib\x86\SDL2.dll` to your project root (for 32-bit builds)
- Copy `SDL2-2.x.x\lib\x64\SDL2.dll` to your project root (for 64-bit builds)

**Note**: If you accidentally downloaded SDL3 files, you'll need to delete them and download the correct SDL2 files instead.

## 3. Project Structure

After setup, your project should have this structure:
```
alien-game/
├── SDL2/
│   ├── include/
│   │   └── SDL2/
│   │       ├── SDL.h
│   │       ├── SDL_audio.h
│   │       ├── SDL_events.h
│   │       └── ... (all other SDL2 headers)
│   └── lib/
│       ├── x86/
│       │   ├── SDL2.lib
│       │   └── SDL2main.lib
│       └── x64/
│           ├── SDL2.lib
│           └── SDL2main.lib
├── SDL2.dll (for the architecture you're building)
└── ... (your other project files)
```

## 4. Build Configuration

The Visual Studio project file has been configured with:
- Include directories: `$(ProjectDir)SDL2\include`
- Library directories: `$(ProjectDir)SDL2\lib\x86` (for Win32) and `$(ProjectDir)SDL2\lib\x64` (for x64)
- Linked libraries: `SDL2.lib` and `SDL2main.lib`

## 5. Building and Running

1. Open the project in Visual Studio
2. Select your desired platform (x86 or x64)
3. Build the project (Ctrl+Shift+B)
4. Make sure the appropriate `SDL2.dll` is in your project directory
5. Run the executable

## Troubleshooting

- **"Cannot open include file 'SDL2/SDL.h'"**: Make sure you copied the SDL2 headers to `SDL2\include\SDL2\`
- **"Cannot open file 'SDL2.lib'"**: Make sure you copied the library files to the correct `SDL2\lib\x86\` or `SDL2\lib\x64\` directory
- **"The program can't start because SDL2.dll is missing"**: Make sure `SDL2.dll` is in the same directory as your executable

## Alternative: Using vcpkg

If you prefer using a package manager, you can also install SDL2 using vcpkg:

1. Install vcpkg: https://github.com/Microsoft/vcpkg
2. Run: `vcpkg install sdl2:x86-windows` (for 32-bit) or `vcpkg install sdl2:x64-windows` (for 64-bit)
3. Update your project settings to use the vcpkg paths

This approach is more automated but requires additional setup.
