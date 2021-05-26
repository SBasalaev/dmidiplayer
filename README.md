Drumstick Multiplatform MIDI File Player
========================================

This application is a multiplatform MIDI file player for Linux, Windows and macOS. It reads .MID (Standard MIDI Files), .KAR (Karaoke), and .WRK (Cakewalk) file formats, and outputs MIDI events to hardware MIDI ports and also software synths.

[Drumstick](https://drumstick.sourceforge.io/docs/index.html) is a set of GPLv3 licensed C++/Qt libraries for MIDI applications. The project includes several tools as examples, and among them is the drumstick-guiplayer utility that leverages the Drumstick::ALSA library, so it is available only for Linux (because the ALSA sequencer is a linux only technology). Some people have requested a program with the same functionalities on Windows and macOS, and here it is. But this program is much more than that, and also works on Linux ...

![Screenshot](https://dmidiplayer.sourceforge.io/screenshot.png "main window")

[![Screencast at YouTube](https://img.youtube.com/vi/rQiWuQkMqsw/0.jpg)](https://www.youtube.com/watch?v=rQiWuQkMqsw)

Some key features:

* MIDI Output to hardware MIDI ports, or any other Drumstick backend like soft synths
* Transpose song tonality between -12 and +12 semitones
* Change MIDI volume level (using MIDI CC7)
* Scale song speed between half and double tempo
* Lyrics, Piano Player and MIDI Channels views
* Supports MID/KAR (Standard MIDI Files) and WRK (Cakewalk) file formats

New in v1.3.0:

* Playlist editor dialog
    * Previous/next song navigation
    * Autogenerated initial playlist
* Samples: several free MIDI/Karaoke classic pieces
* Preferences dialog
    * Auto play/Auto advance
    * Optional dark mode
    * Optional internal icons theme (defaults to desktop environment icon theme)
    * Choice of Qt widgets style
    * Lyrics and Piano Player specific options
* Full screen option on Lyrics and Piano Player windows
* Updated CMake buildsystem
    * Minimum required cmake version 3.14
    * MacOS target: Sierra (10.12)
    * Uninstall target
* Better support for WRK files with lyrics and other metadata
* MIDI texts/lyrics encoding defaults to Latin1
* KeySignature MIDI meta-event processed

New in v1.2.0:

* Lyrics view (karaoke window)
* Character encoding detection
* File Info (metadata) dialog

New in v1.1.0:

* Piano Player, Channels and Rhythm views
* Sticky Window Snapping (Windows OS only)
* Russian translation (Thanks to Sergey Basalaev)
* Spanish translation updated
* Recent files menu options
* Language choice menu options
* Command line options: --portable and --file (for portable configuration)

This multiplatform version offers equivalent functionality replacing Drumstick::ALSA by Drumstick::RT. The MIDI events scheduling/timing is performed inside the program with the only  help of the C++ standard library (threads and chrono). The MIDI output still has access to each operating system's MIDI infrastructure, but also to additional backends like ipMidi and soft synths.

Alright, these are the build requirements:

* C++11 compiler
* Qt5
* [Drumstick 2.2](https://sourceforge.net/projects/drumstick/files/2.2.0/)
* [Uchardet 0.0.7](https://www.freedesktop.org/wiki/Software/uchardet/)
* CMake 3.14

Build and deployment commands (for Linux)

```
$ tar -xvzf dmidiplayer-x.y.z.tar.gz
$ cd dmidiplayer-x.y.z
$ mkdir build
$ cd build
$ cmake .. -DCMAKE_PREFIX_PATH="$HOME/Qt5;$HOME/drumstick2;$HOME/uchardet"
$ make
$ make install
```
You need to replace the contents of the parameter CMAKE_PREFIX_PATH with the actual paths in your system. There are x86_64 precompiled packages for Linux, Windows and macOS at the releases area.

In addition to the released AppImage for Linux, you may find a [Flatpak at FlatHub](https://flathub.org/apps/details/net.sourceforge.dmidiplayer) and binary packages for several Linux distributions:

[![Packaging status](https://repology.org/badge/vertical-allrepos/dmidiplayer.svg)](https://repology.org/project/dmidiplayer/versions)

Enjoy!
