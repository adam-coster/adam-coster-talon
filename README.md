# bscotch_talon

Talon Voice scripts extending `knausj_talon`.

## Requirements

- [Talon (beta)](https://talonvoice.com/)
- [`knausj_talon`](https://github.com/knausj85/knausj_talon)

## Platform Compatibility

While the scripts here shouldn't create problems on non-Windows platforms, it's likely that they will not work on anything but Windows.

## Installation

If you've installed everything correctly, you should be able to navigate to the `%APPDATA%\talon\user` folder and see at least the following two folders:

- `adam-coster-talon`
- `knausj_talon`

> 💡 If you already have Talon running and `knausj_talon` installed, you can say the command `"talon home"` to open the `%APPDATA%\talon` folder.

### Prereqs

- Install/update to the latest beta version of Talon. This can be found in the [Talon Beta channel](https://talonvoice.slack.com/archives/G9YTMSZ2T) for Talon's Patreon subscribers.
- Install the latest [`knausj_talon`](https://github.com/knausj85/knausj_talon) scripts. (The installation instructions for the scripts in this repo also apply to `knausj_talon`.)

### Install/update manually (no Git required)

*If you use Git you can skip to the next section.*

1. [Download a zip](https://github.com/bscotch/bscotch_talon/archive/refs/heads/develop.zip) of this repo (and the [`knausj_talon` zip](https://github.com/knausj85/knausj_talon/archive/refs/heads/main.zip), if not already installed).
2. Unzip it
3. In File Explorer, go to `%APPDATA%\talon\user`
4. Drag the `bscotch_talon` folder into the `%APPDATA%\talon\user` folder

### Install/Update with GitHub Desktop

If you use [GitHub Desktop](https://desktop.github.com/) to install these and the `knausj_talon` scripts, it will be easier to keep things up to date.

Open up GitHub Desktop and then:

1. Go to <kbd><kbd>File</kbd>-><kbd>Clone repository</kbd></kbd>
2. Go to the **URL** tab
3. Enter `bscotch/bscotch_talon`
   - For `knausj_talon`, enter `knausj85/knausj_talon`
4. Click <kbd>Choose...</kbd> to open up the file prompt
5. Paste `%APPDATA%\talon\user` into the address bar and click <kbd>Select Folder</kbd>
6. Click <kbd>Clone</kbd>

## Features

This section provides information and tips about some of the features provided by this collection of Talon scripts. Assume that it isn't fully up to date and is non-comprehensive.

### Focus a window by app and title

> 💬 `focus <user.running_applications> [<user.text>]`

This command replaces the `knausj_talon` script `focus <user.running_applications>`, so that you can specify *which* window, by title, in cases where you have multiple windows open for a given application.

If the optional title text is not provided, the command falls back on the `knausj_talon` script's default behavior.

This command performs fuzzy matching for titles. It scores all windows and returns the one with the highest score, so you can pull up a window even if you were quite inaccurate in specifying its title (but you may also get a window you didn't expect).

- 💡 You can rename your Chrome windows to whatever you please, so that the title for a given window stops changing based on which tab is currently active. **⚠️ Warning ⚠ renaming Chrome windows will break your website-specific Talon scripts, since they use the window title to determine context.**
- 💡 You can change how Visual Studio Code names its windows, at the user and workspace levels, using the `window.title` setting.
- 💡 Try to name things so that they're easy to group. For example, I have a Chrome window named `talon` and a VSCode window that includes the word "talon" in its title, so that I can say `focus chrome talon` or `focus vscode talon` to go to the right app for things related to working on Talon.

## Extending/changing functionality

Talon automatically loads any `.talon` or `.py` files it finds inside of the `%APPDATA%\talon\user` folder (nesting is allowed), so you can add or change functionality by editing, changing, or deleting files in that folder.

### Use [Settings](https://talon.wiki/unofficial_talon_docs/#settings) when possible

Instead of making edits to shared `.talon` and `.py` files for things specific to your setup, expose settings in your scripts and set their values locally.

- Create a file at `%APPDATA%\talon\user\settings.talon` to store your local-only settings. This file will be found by Talon, but it won't be tracked by any of the git repos inside of `%APPDATA%\talon\user\`, so you can use it to make local overrides.
- When writing scripts, [expose Settings](https://talon.wiki/unofficial_talon_docs/#settings) that you and others can use for local overrides.
