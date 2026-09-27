# Tidy Downloads

A simple Python utility that automatically organizes files in your Downloads folder into categories.

## Features

- Organizes files by type
- Creates separate folders for:
  - Images
  - Videos
  - Documents
  - Audio
  - Archives
  - Others
  - Folders
- Can monitor a folder continuously
- Skips temporary and partially downloaded files
- Can wait for files to stop changing before moving them
- Supports organizing a custom folder

## Installation

### Add the Tidy Downloads repository

Import the repository signing key:

```bash
curl -fsSL https://rrnrishabhrakesh-byte.github.io/tidy-downloads-apt/public.key \
| sudo gpg --dearmor --yes -o /etc/apt/keyrings/tidy-downloads-archive-keyring.gpg
```

Add the repository:

```bash
echo "deb [signed-by=/etc/apt/keyrings/tidy-downloads-archive-keyring.gpg] https://rrnrishabhrakesh-byte.github.io/tidy-downloads-apt stable main" \
| sudo tee /etc/apt/sources.list.d/tidy-downloads.list > /dev/null
```

Update APT:

```bash
sudo apt update
```

Install Tidy Downloads:

```bash
sudo apt install tidy-downloads
```

Verify the installation:

```bash
tidy-downloads --help
```

## Usage

By default, Tidy Downloads organizes your `~/Downloads` folder.

### Preview changes

Run:

```bash
tidy-downloads
```

This shows what would be organized without actually moving files.

### Apply changes

To actually organize the files:

```bash
tidy-downloads --apply
```

### Organize another folder

Specify a folder:

```bash
tidy-downloads ~/Desktop
```

To apply the changes:

```bash
tidy-downloads ~/Desktop --apply
```

### Watch a folder

Tidy Downloads can continuously monitor a folder:

```bash
tidy-downloads --watch
```

By default, it checks the folder every 60 seconds.

You can change the interval:

```bash
tidy-downloads --watch --interval 10
```

This checks every 10 seconds.

### Minimum file age

Tidy Downloads can wait before moving recently created files. The default is 30 seconds.

For example:

```bash
tidy-downloads --min-age 60 --apply
```

This waits until files are at least 60 seconds old before organizing them.

### Combine options

Options can be combined. For example:

```bash
tidy-downloads ~/Downloads --watch --interval 30 --min-age 60 --apply
```

This continuously monitors `~/Downloads`, checks every 30 seconds, waits for files to be at least 60 seconds old, and automatically organizes them.

## Categories

Files are sorted based on their file extension.

Typical categories include:

| Category | Examples |
|---|---|
| Images | JPG, PNG, GIF, WEBP |
| Videos | MP4, MKV, AVI, MOV |
| Documents | PDF, DOCX, TXT, ODT |
| Audio | MP3, WAV, FLAC, OGG |
| Archives | ZIP, TAR, GZ, 7Z |
| Others | File types that don't match another category |
| Folders | Directories found in the folder |

## Uninstallation

Remove the package:

```bash
sudo apt remove tidy-downloads
```

To also remove its system configuration files, if any:

```bash
sudo apt purge tidy-downloads
```

Remove the Tidy Downloads APT repository:

```bash
sudo rm /etc/apt/sources.list.d/tidy-downloads.list
```

Remove the repository signing key:

```bash
sudo rm /etc/apt/keyrings/tidy-downloads-archive-keyring.gpg
```

Then update APT:

```bash
sudo apt update
```

## Manual `.deb` Installation

If you already have the `.deb` package, you can install it directly:

```bash
sudo apt install ./tidy-downloads_1.0.0-1_all.deb
```

## Requirements

- Linux
- Python 3
- Debian-based distribution using APT

## Source Code

The source code is available on GitHub:

https://github.com/rrnrishabhrakesh-byte/tidy-downloads

## APT Repository

The APT repository is hosted using GitHub Pages:

https://rrnrishabhrakesh-byte.github.io/tidy-downloads-apt/

## License

See the `LICENSE` file for the project's license.
