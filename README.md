# Barrier Build and Setup Guide (Full Step-by-Step)

This document explains how to build Barrier from source on Linux and create a desktop shortcut with an icon.

---

## 1. Prepare the Source

Download or clone the Barrier source:

```bash
cd ~/Downloads/
git clone https://github.com/KenyanAudo03/barrier.git
cd ~/Downloads/barrier
```

## 2. Create Build Directory

```bash
mkdir build
cd build
```

## 3. Configure Build with CMake

```bash
cmake ..
```

- This step checks for dependencies and generates the Makefiles.
- You might see warnings like:

```pgsql
CMake Deprecation Warning: Compatibility with CMake < 3.10 will be removed in a future version.
```

## 4. Build Barrier

```bash
make -j$(nproc)
```

- -j$(nproc) uses all CPU cores for faster compilation. You may also encounter errors

## 5. Install Barrier

```bash
sudo make install
```

## 6. Locate Executable

```bash
ls ~/Downloads/barrier/build/src/
# You should see directories like lib/, gui/, cmd/, etc.
```

## 7. Add Icon

```bash
mkdir -p ~/.local/share/icons
mv ~/Downloads/path-to-downloaded-barrier-icon ~/.local/share/icons/barrier.png
```

## 8. Create Desktop Shortcut

```bash
nano ~/.local/share/applications/barrier.desktop
```

Paste

```ini
[Desktop Entry]
Name=Barrier
Comment=Barrier Client/Server
Exec=barrier
Icon=/home/your-username/.local/share/icons/barrier.png
Terminal=false
Type=Application
Categories=Utility;
```

**Replace your-username with your Linu username**
_Save(Ctrl+), exit (Ctrl+X), and make it executable:_

```bash
chmod +x ~/.local/share/applications/barrier.desktop
```

## 9. Lauch Barrier

```bash
barrier
```
