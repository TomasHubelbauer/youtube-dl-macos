# `youtube-dl` macOS

First install as per the official instructions:
https://ytdl-org.github.io/youtube-dl/download.html

1. `sudo curl -L https://yt-dl.org/downloads/latest/youtube-dl -o /usr/local/bin/youtube-dl`
2. `sudo chmod a+rx /usr/local/bin/youtube-dl`

At this point `youtube-dl` will use Python 2 not Python 3 as that is the default
Python version on macOS.

This will not work:

```diff
- sudo ln -s /usr/bin/python3 /usr/local/bin/python
```

I guess macOS has some protections against remapping the binaries in `/usr`.

Do this instead each time running `youtube-dl`:

```diff
+ /usr/bin/python3 /usr/local/bin/youtube-dl "https://www.youtube.com/watch?v=…"
```

The path to Python 3 can be found using `which python3` but it is the same on
all macOS installations.

This has the advantage of not making Python 3 the global default which could
break other software.

Or use `brew` or `pip` if you have them as per the official instructions above.
I don't and I don't want to install them just for `youtube-dl`.
