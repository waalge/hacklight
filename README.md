# hacklight
Control brightness on xubuntu when using `i3wm` and where `xbacklight` fails

## Problem

After updating to xubuntu 18.04 I couldn't change brightness when using i3wm. 
[These](https://askubuntu.com/questions/1034305/brightness-problem-ubuntu-18-04-lts) 
didn't seem to solve the problem. 

## Hack method

The brightness can be controlled by a file.
For me this was `/sys/class/backlight/intel_backlight/brightness`.

The script `hacklight` just edits this file. 

## To use 

1. Change the owner of the brightness file to you e.g. 
```
sudo chown ME brightness
```
where `ME` is you. Obvs.

2. Edit `hacklight` to change the value of the variable `brightness_file` 
to the appropriate path.

3. Put `hacklight` in a path you OS will find it.
(See [here](https://gist.github.com/nex3/c395b2f8fd4b02068be37c961301caa7))

4. Add the contents of `i3config` to your `i3` config file (likely found at `.config/i3/config`). 




