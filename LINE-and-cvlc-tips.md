# LINE and cvlc tips

## LINE tip

Here in Thailand, the predominant social networking app is LINE. While
there is a LINE desktop client for Windows, there isn't one for Linux -
totally understandable given the small fraction of Linux desktop users
who are also LINE users and vice-versa.

However, like all things in life, there is a solution if you look hard
enough. There exists a LINE extension in Google Chrome - which is my the
leading reason for running Chrome.

And so, for the longest time, I've been starting Google Chrome, waiting
for it to load and then clicking on the LINE extension. Until, one day,
I discovered that that you could start these extensions independently.

So, here's a little script (sanitized) to do that:

    #!/usr/bin/bash
    ID=<YOUR LINE EXTENSION ID HERE>
    firejail google-chrome --app=chrome-extension://${ID}/index.html &

You need to find out the ID of your LINE extension or for that matter
any extension. And I use `firejail` to restrict Google Chrome to a small
set of directories though I'm pretty sure it can be broken by someone
determined enough.

## cvlc tip

`cvlc` is a command line program to control VLC, which, is a media
player. Lately I've discovered that you can play just a particular
segment of an audio file, for example:

    cvlc some-audio.mp3 --start-time 1530 --stop-time 1560

The command above plays `some-audio.mp3` starting at 25:30 (1530s) and
stops 30 seconds later.

This is helpful to bookmark a particular segment in an audio (or video)
file. So, for example, I'm making notes about a talk and need a way to
point to the part in the audio.

