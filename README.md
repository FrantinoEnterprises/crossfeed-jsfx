# Crossfeed JSFX

A REAPER JSFX plugin that makes headphone listening sound more like speakers.

With headphones, each ear hears only one channel. With speakers, each ear also hears the opposite speaker a little later, quieter, and with less treble because the head blocks it. This plugin recreates that with Bauer's stereophonic-to-binaural (bs2b) crossfeed filter.

## Install with ReaPack (recommended)

1. Install [ReaPack](https://reapack.com) if you don't have it.
2. In REAPER: **Extensions → ReaPack → Import repositories…** and paste:
   ```
   https://raw.githubusercontent.com/FrantinoEnterprises/crossfeed-jsfx/main/index.xml
   ```
3. **Extensions → ReaPack → Browse packages…**, find **Crossfeed.jsfx**, right-click → Install, then Apply.

ReaPack installs future versions when you run **Extensions → ReaPack → Synchronize packages**.

### Releasing a new version

1. Edit `Crossfeed.jsfx` and bump `version:` in its header.
2. In `index.xml`, add a new `<version>` block (keep the old ones) with the same version number, a changelog, and a source URL pointing at the new tag, e.g. `.../crossfeed-jsfx/v1.1/Crossfeed.jsfx`.
3. Commit, tag, and push:
   ```sh
   git commit -am "Crossfeed 1.1"
   git tag v1.1
   git push origin main --tags
   ```

## Install manually

Copy or symlink `Crossfeed.jsfx` into your REAPER Effects folder, then rescan or restart REAPER:

| OS      | Folder                                            |
|---------|---------------------------------------------------|
| Linux   | `~/.config/REAPER/Effects/`                       |
| Windows | `%APPDATA%\REAPER\Effects\`                       |
| macOS   | `~/Library/Application Support/REAPER/Effects/`   |

```sh
ln -s "$PWD/Crossfeed.jsfx" ~/.config/REAPER/Effects/Crossfeed.jsfx
```

In the FX browser it shows up as **JS: Crossfeed - speaker sound on headphones**. Put it on the monitoring FX chain (or last on the master bus) so it only affects what you hear on headphones, not your renders.

## Strength

The plugin window shows a head between two speakers. The blue lines are the sound each ear hears from its own speaker, and the orange lines are the crossfeed from the opposite one, which get stronger as you raise the strength. Click a button to choose the strength (default **Medium**):

| Strength | Based on     | Feel |
|----------|--------------|------|
| Light    | Jan Meier    | Subtle; keeps most of the stereo width. |
| Medium   | Chu Moy      | Balanced, classic crossfeed. |
| Full     | bs2b default | Closest to real speakers. |

Use REAPER's own FX bypass checkbox to compare with and without it. Mono tracks pass through untouched.
