# Minimal CImg Demo

CImg is a C++ image manipulation library aiming at utilizing templates to create an easy to use API.
This is the minimal CImg demo shown on the Tutorial section of the website.
This repository aims to make the example build across macOS and Windows.

## Dependencies

This demo utilizes a minimal set of dependencies that CImg requires but does not include.

### Display

#### macOS

In macOS, CImg relies on the X11 API to display windows.
The X11 API is provided by XQuartz.

To install XQuartz,
go to [https://www.xquartz.org](https://www.xquartz.org),
download the `.dmg` image file under "Quick Download",
double click the file to mount it,
double click the `.pkg` file found in the image,
and follow the instructions.

#### Windows

In Windows, CImg relies on the [Windows GDI](https://docs.microsoft.com/en-us/windows/desktop/gdi/windows-gdi) API.
As it is a native API, nothing needs to be separately installed.

### Image Formats

By itself CImg only supports bitmap image manipulation.
However, most images in daily usage are of more compact formats, such as JPEG and PNG.
CImg relies on [ImageMagick](https://www.imagemagick.org/script/index.php) to read and write in those formats.

#### macOS

In macOS, I recommend [Homebrew](https://brew.sh) for installing commandline apps like ImageMagick.

To install Homebrew, go to [https://brew.sh](https://brew.sh) and follow the instructions there.

Afterwards, run the following command in Terminal to install ImageMagick.

    brew install imagemagick

#### Windows

In Windows, go to [https://www.imagemagick.org/script/download.php#windows](https://www.imagemagick.org/script/download.php#windows) and download the latest installer.

## Building

### macOS

To compile the demo, clone the repo and in the folder run:

    clang++ main.cpp -o main -I/opt/X11/include -L/opt/X11/lib -lX11 -lpthread

Let me explain the parameteres used:

- `-I/opt/X11/include -L/opt/X11/lib`: XQuartz is installed at `/opt/X11`, therefore the corresponding include and library directories need to be specified
- `-lX11`: instructs linker to dynamically link to X11
- `-lpthread`: CImg makes use of multi-thread programming, and in macOS it uses pthread
