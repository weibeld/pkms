---
title: Android Studio Shortcuts and Tips
date: 2024-03-18
---

## Shortcuts

Custom shortcuts (deviating from defaults):

| Shortcut      | Action                            |
|:--------------|:----------------------------------|
| `Cmd-R`       | Run                               |
| `Cmd-S`       | Stop                              |
| `Cmd-L`       | Manual Live Edit                  |
| `Cmd--`       | Toggle Folding                    |
| `Cmd-T`       | Terminal Tool Window              |
| `Cmd-U`       | Run Tool Window                   |
| `Cmd-P`       | Problems Tool Window              |
| `Ctrl-Cmd-O`  | Optimize Imports                  |
| `Ctrl-Cmd-M`  | Reformat Code                     |
| `Cmd-Enter`   | Quick Documentation               |
| `Shift-Tab`   | Switcher                          |
| `Ctrl-Esc`    | Hide Active Tool Window           |
| `Cmd-W`       | Jump to Last Tool Window          |
| `Cmd-Shift-N` | New Kotlin Class/File             |


Disabled shortcuts (in order to prevent conflicts with custom shortcuts above):

| Shortcut     | Action                     | Conflicting Action            |
|:-------------|:---------------------------|:------------------------------|
| `Cmd-R`      | Replace                    | Run                           |
| `Cmd-L`      | Go to Line                 | Manual Live Edit              |
| `Cmd-T`      | New Terminal Tab           | Terminal Tool Window          |
| `Cmd-W`      | Close Tab                  | Jump to Last Tool Window      |
| `Cmd-U`      | Go to Super Method         | Run Tool Window               |
| `Cmd-S`      | Save All                   | Stop                          |
| `Cmd-Enter`  | Split Line                 | Quick Documentation           |

## Configuration

### Change default package name for new projects

For some reason, this can't be changed in the UI, so it has to be done as follows:

1. Close Android Studio
1. Open the following file:
   ```
   ~/Library/Application\ Support/Google/AndroidStudio2023.2/options/other.xml
   ```
1. Adapt the value of the `SAVED_ANDROID_PACKAGE` entry

## Tips

- Enable _IdeaVim: Track Action Id_ in Search to find out Action IDs
- Press `Esc` to move focus from tool window back to editor window
- Use `Ctrl-Shift-J` to join a multi-line statement to a single line
