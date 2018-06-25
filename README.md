# NHK
Nested Keybinds for sxhkd

# What is NHK?
Currently, most peoples' sxhkd keybinds revolve around a single "super" key which acts as a modifier for most of their bspwm keybinds. Although this works reasonably well, it has a few drawbacks. First and foremost, such configurations are often not very memorable or intuitive. For example, it's not clear to the average user why Mod+Shift+q closes a work space. Additionally, modifier-based keybinds are often difficult to execute, requiring the user to stretch their hand across the keyboard multiple times to execute what should be a quick and easy task.

For these reasons, I've implemented a new way of registering keybinds which is 100% backwards-compatible with the current sxhkd layout.

# How does NHK work?
In addition to the current modifier keys which can be applied to an sxhkd keybind, keybinds can now be sorted into nested "modes". This allows for sequential, multi-key, shortcuts. For example, numpad plus key might move the user into an "add" mode in which they can simply press any combination of other numpad keys to open windows. Chains such as this allow for much more complicated keybind set ups.

A ```mode``` script and ```show-menu``` binary are shipped with nhk. The ```mode``` script handles the changing from one mode to another by storing the current mode in a modefile, which is typically stored in ~/.cache. The ```mode``` script calls a ```show-menu``` program whose purpose is to display a grid of icons in the corner of the screen. The provided icons.yml file can be edited to specify which icons to show when a given mode is activated. This icon grid provides a visual aid for long, multi-stage shortcut chains.

# Dependencies
Currently, the only dependencies NHK requires (other than sxhkd) are Node.js and [yaml2json](https://github.com/bronze1man/yaml2json). The provided js script is entirely dependency-free/portable and does not require the installation of any outside modules.

# Installation
After installing the dependencies mentioned above, move the provided ```mode```, ```nhk```, and ```show-menu``` files to your PATH and add execution permissions to all three. Then, after creating an NHK config file, use the ```nhk``` command to compile it into a valid sxhkdrc file.
