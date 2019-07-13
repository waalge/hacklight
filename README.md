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

## To use (with `sudoers`) 

WARNING: Incorrect use of sudoers can be dangerous. 

1. Put `hacklight` in a path you OS will find it.
(See [here](https://gist.github.com/nex3/c395b2f8fd4b02068be37c961301caa7)). 
Something like e.g `/usr/sbin/hacklight`

2. Edit `hacklight` to point to brightness file by changing variable `brightness_file` (see default).

3. Change the owner of this file to root e.g 
```
sudo chown root:root /usr/sbin/hacklight
```

4. Let the user run `hacklight` as `root` without password. 
To do this run `sudo visudo`, and append the line giving the correct permissions.
See the `sudoers` file for an example, 
and also the [man](https://linux.die.net/man/5/sudoers)
which has examples near the end. 

5. Add the contents of `i3config` to your `i3` config file (likely found at `.config/i3/config`). 


## To use (without `sudoers`) 

WARNING: On rebooting file owner of the brighness file seems to reset. 
For this reason it seems necessary to use `sudoer` to avoid having to use a password each time. 
If you don't reboot often, or don't care to use `sudoers` then... 

1. Change the owner of the brightness file to you e.g. 
```
sudo chown ME brightness
```
where `ME` is you.
Problem: On rebooting this seems to reset to root.
You'd have to do this every time. 

2. Edit `hacklight` to change the value of the variable `brightness_file` 
to the appropriate path.

3. Put `hacklight` in a path you OS will find it.
(See [here](https://gist.github.com/nex3/c395b2f8fd4b02068be37c961301caa7))

4. Add the contents of `i3config` to your `i3` config file (likely found at `.config/i3/config`). 
Remove `sudo` in front of each command. 




