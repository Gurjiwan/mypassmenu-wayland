# mypassmenu-wayland

A simple extension of `passmenu` script which is part of [pass][] password-store package to add support for wmenu in addition to dmenu-wl on wayland.

Support added for pass plugin pass-otp. we can invoke pass-otp using `passmenu --otp` and type it using `passmenu --otp --type` commands.

# Usage

`passmenu [--otp] [--type] [dmenu/wmenu arguments...]`
`passmenu [--type] [dmenu/wmenu arguments...]`
`passmenu [--otp] [dmenu/wmenu arguments...]`

Note:
We cannot use `--type` option before `--otp` . As of now only the above examples are valid.

# Dependencies

`passmenu` requires one of the following packages to function:
1. [dmenu][] (simple menu for Xorg)
2. [dmenu-wl][] (wayland port of dmenu)
3. [wmenu][] (wayland alternative to dmenu)

In addition for using the `--type` (auto-type) option we require one of :
1. [xdotool][] (xorg)
2. [ydotool][] (xorg + wayland)

Similarly, `--otp` option require optional dependency :
1. [pass-otp][] (extension of pass to generate otp using totp secrets)

# Background

passmenu is a [dmenu][]-based interface to [pass][], the standard Unix
password manager. This design allows you to quickly copy a password to the
clipboard without having to open up a terminal window if you don't already have
one open. If --type is specified, the password is typed using [xdotool][]
instead of copied to the clipboard.

On wayland [dmenu-wl][] is used to replace dmenu and [ydotool][] to replace xdotool.
Note that the latter requires access to the [uinput][] device, so you'll probably
need to add an extra udev rule or similar to give certain non-root users permission.

In addition to [dmenu-wl], by using this version of script we can use [wmenu][] in wayland.
Further added support for [pass-otp][] extension.

Original passmenu script can be found under /contrib/dmenu in the original [pass-repo][] repository.

[dmenu]: http://tools.suckless.org/dmenu/
[xdotool]: http://www.semicomplete.com/projects/xdotool/
[pass]: http://www.zx2c4.com/projects/password-store/
[dmenu-wl]: https://github.com/nyyManni/dmenu-wayland
[ydotool]: https://github.com/ReimuNotMoe/ydotool
[uinput]: https://www.kernel.org/doc/html/v4.12/input/uinput.html
[wmenu]: https://codeberg.org/adnano/wmenu
[pass-repo]: https://git.zx2c4.com/password-store/tree/
