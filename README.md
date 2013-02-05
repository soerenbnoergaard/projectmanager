# Projectmanager

Bash script for setting up projects, by copying folders, renaming titles and files and so om.

Requires `zenity`, `sed`, and `bash`. And is intended for linux in general.

## Setting it up

1. Clone the project to a local folder.
2. Edit the file "projectmanager"'s second line, to be the path where the project is located.

Now `./projectmanager` can be run from terminal, but that is not the main purpose!

If you use Thunar, add the script to your right click menu from the menu: `Edit->Configure custom actions`. As command, choose the `projectmanager`-file from it's location. *Optionally*, you can add the folder containing the file, to your PATH-variable, in the file `/etc/profile` (Arch Linux), and just type `projectmanager` as command.

Also give it a name and description, and add the logo (included in the same folder as `projectmanager`). Remember, also, to add `Directories` (and the other if you'd like), in the *Appearance Conditions*-tab.

You can now add new projects by right-clicking in any folder in Thunar.

## Adding more templates

You can add more templates by adding folders to the `folders` directive, and adding lines to `projectmanager` - the syntax should be quite straight-foreward.

Enjoy!
