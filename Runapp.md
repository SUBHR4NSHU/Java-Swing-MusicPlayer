# How to Run the MP3 Music Player App

## Table of Contents
- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Running the Application](#running-the-application)
- [Alternative Methods](#alternative-methods)
- [Troubleshooting](#troubleshooting)
- [Using the Application](#using-the-application)

---

## Prerequisites

Before running the application, ensure you have the following installed:

### 1. Java Development Kit (JDK)
- **Required Version:** JDK 18 or higher
- **Check if installed:** Open terminal/command prompt and type:
  ```bash
  java -version
  javac -version
  ```
- **Download:** [Oracle JDK](https://www.oracle.com/java/technologies/downloads/) or [OpenJDK](https://openjdk.org/)

### 2. Required Libraries
The project uses the following JAR libraries (already included in the `lib/` folder):
- `jaudiotagger-3.0.1.jar` - For editing MP3 file metadata
- `jlayer-1.0.1.jar` - MP3 decoder/player library
- `mp3agic-0.9.0.jar` - For reading MP3 files and manipulating ID3 tags

---

## Project Structure

```
Java-Swing-MusicPlayer/
├── lib/                          # Dependencies (JAR files)
│   ├── jaudiotagger-3.0.1.jar
│   ├── jlayer-1.0.1.jar
│   └── mp3agic-0.9.0.jar
├── src/                          # Source code
│   ├── App.java                 # Application entry point
│   ├── MusicPlayer.java         # Core player logic
│   ├── MusicPlayerGUI.java      # GUI components
│   ├── MusicPlaylistDialog.java # Playlist dialog
│   ├── Song.java                # Song data model
│   └── assets/                  # Sample MP3 files
│       ├── Wind Riders - Asher Fulero.mp3
│       ├── Tropic Fuse - French Fuse.mp3
│       └── Auld Lang Syne (Instrumental) - Jingle Punks.mp3
├── out/production/MP3MusicPlayer/  # Compiled classes
└── README.md
```

---

## Running the Application

### Method 1: Quick Run (Compiled Classes Already Exist)

If the classes are already compiled in the `out/production/MP3MusicPlayer/` directory:

#### On Windows:
```bash
cd D:\Java-Swing-MusicPlayer
java -cp "out/production/MP3MusicPlayer;lib/*" App
```

#### On Linux/Mac:
```bash
cd /path/to/Java-Swing-MusicPlayer
java -cp "out/production/MP3MusicPlayer:lib/*" App
```

---

### Method 2: Compile and Run (Recommended)

If you need to compile the source code first:

#### Step 1: Navigate to Project Directory

**Windows:**
```bash
cd D:\Java-Swing-MusicPlayer
```

**Linux/Mac:**
```bash
cd /path/to/Java-Swing-MusicPlayer
```

#### Step 2: Compile the Java Files

**Windows:**
```bash
javac -encoding UTF-8 -cp "lib/*;src" src/App.java src/*.java -d out/production/MP3MusicPlayer
```

**Linux/Mac:**
```bash
javac -encoding UTF-8 -cp "lib/*:src" src/App.java src/*.java -d out/production/MP3MusicPlayer
```

**Explanation:**
- `-encoding UTF-8` - Specifies character encoding for the source files
- `-cp "lib/*;src"` - Sets the classpath to include all JAR files in lib/ and source files
- `src/App.java src/*.java` - Source files to compile
- `-d out/production/MP3MusicPlayer` - Output directory for compiled classes

#### Step 3: Run the Application

**Windows:**
```bash
java -cp "out/production/MP3MusicPlayer;lib/*" App
```

**Linux/Mac:**
```bash
java -cp "out/production/MP3MusicPlayer:lib/*" App
```

**Explanation:**
- `java` - Java runtime
- `-cp` - Classpath flag
- `"out/production/MP3MusicPlayer;lib/*"` - Include compiled classes and all JAR libraries
- `App` - Main class to run

---

### Method 3: Compile with Explicit File List

If you prefer to compile each file individually:

```bash
javac -encoding UTF-8 -cp "lib/*" -d out/production/MP3MusicPlayer src/App.java src/MusicPlayer.java src/MusicPlayerGUI.java src/MusicPlaylistDialog.java src/Song.java
```

Then run:
```bash
java -cp "out/production/MP3MusicPlayer;lib/*" App
```

---

## Alternative Methods

### Using an IDE (IntelliJ IDEA, Eclipse, VS Code)

1. **Open the Project**
   - Open your IDE
   - Import/open the Java-Swing-MusicPlayer folder

2. **Configure Libraries**
   - Add all JAR files in `lib/` folder to your project's classpath/build path
   - In IntelliJ: Right-click `lib/` → Add as Library
   - In Eclipse: Right-click project → Properties → Java Build Path → Add External JARs

3. **Run the Application**
   - Open `App.java`
   - Click the "Run" button or press `Ctrl+F11` (IntelliJ) / `F11` (Eclipse)

---

## Troubleshooting

### Issue 1: "javac is not recognized as an internal or external command"
**Solution:** 
- JDK is not installed or not in PATH
- Install JDK and add `bin` directory to system PATH
- Restart your terminal/IDE after installation

### Issue 2: "java.lang.NoClassDefFoundError" or "ClassNotFoundException"
**Solution:** 
- Classpath is not set correctly
- Make sure the classpath includes both compiled classes and JAR files
- Check the separator character (Windows: `;`, Linux/Mac: `:`)

### Issue 3: "java.lang.ClassNotFoundException: App"
**Solution:** 
- You're not running from the correct directory
- Navigate to the project root directory before running

### Issue 4: "encoding" errors during compilation
**Solution:** 
- Some file names contain special characters
- Use the `-encoding UTF-8` flag as shown in the compile commands

### Issue 5: GUI window doesn't appear
**Solution:** 
- Check if the application is running in background
- Look in your taskbar/activity monitor for Java processes
- Try running with debugging: `java -cp ... App` (without background execution)

### Issue 6: MP3 files won't play
**Solution:** 
- Ensure MP3 files are in the `src/assets/` directory
- Check that the JAR libraries are properly included in classpath
- Verify file paths in the code match your directory structure

---

## Using the Application

### Main Features

Once the application is running, you'll see a GUI window with:

1. **Playback Controls**
   - ▶ Play/Resume button
   - ⏸ Pause button
   - ⏭ Next song
   - ⏮ Previous song
   - 🎙 Record button (for creating playlists)

2. **Display Information**
   - Song title
   - Artist name
   - Song duration

3. **Playback Slider**
   - Drag to seek to different positions in the song

### Creating and Loading Playlists

1. **Create Playlist:**
   - Click the record button
   - Select multiple MP3 files
   - The playlist will be saved as a `.txt` file

2. **Load Playlist:**
   - Existing playlists (playlist.txt, playlist2.txt, playlist3.txt) can be loaded
   - Each line in the playlist file is a path to an MP3 file

### Sample Songs

The application comes with 3 sample MP3 files in `src/assets/`:
- Wind Riders - Asher Fulero.mp3
- Tropic Fuse - French Fuse.mp3
- Auld Lang Syne (Instrumental) - Jingle Punks.mp3

---

## Quick Reference Commands

### Windows:
```bash
# Compile
javac -encoding UTF-8 -cp "lib/*;src" src/App.java src/*.java -d out/production/MP3MusicPlayer

# Run
java -cp "out/production/MP3MusicPlayer;lib/*" App

# Clean compiled files
del /s /q out\production\MP3MusicPlayer\*.class
```

### Linux/Mac:
```bash
# Compile
javac -encoding UTF-8 -cp "lib/*:src" src/App.java src/*.java -d out/production/MP3MusicPlayer

# Run
java -cp "out/production/MP3MusicPlayer:lib/*" App

# Clean compiled files
rm -rf out/production/MP3MusicPlayer/*.class
```

---

## Notes

- The application uses Java Swing for the graphical user interface
- The GUI is set to a fixed size of 400x600 pixels
- All UI components are positioned using null layout with coordinates
- The application follows a black and white color scheme
- Background tasks run in EDT (Event Dispatch Thread) for thread safety

---

## Additional Resources

- [JDK Documentation](https://docs.oracle.com/en/java/javase/)
- [Swing Tutorial](https://docs.oracle.com/javase/tutorial/uiswing/)
- [MP3agic Documentation](https://github.com/mpatric/mp3agic)
- [JLayer Documentation](http://www.javazoom.net/javalayer/javalayer.html)

---

**Enjoy your music! 🎵**

