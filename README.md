There are the scripts I use to discover music on [Jamendo][jam], a website for musics under Creative Commons licenses.

I like to play the whole Jamendo catalog in random order with [mpd][mpd] and just switch to the next song when I'm not interested in the current.
When I find something exciting, I want to have more informations, and then I end up on the corresponding album/artist page at Jamendo.

There is the purpose of these scripts:
 - [jamendo-playlist][jpl] builds a huge playlist listing all the track of Jamendo's catalog
 - [jamendo-mpd-get2][jgm2] gets infos on the played track in mpd via the [Jamendo Get2 API][jamget2api]
 - [gojam][gojam] opens the album page of the current track in the default web-browser

## Build the playlist
When invoked without option, [jamendo-playlist][jpl] will download the [Jamendo database xml dump][jamxml] (approx. 15 Mb), extract it (approx. 150 Mb) and parse it to generate a playlist.

The generated playlist is really huge (something like 350,000 tracks) and your must edit the default mpd configuration to be able to load it:

In the file `/etc/mpd.conf`, locate the comment indicating a "Resource Limitations" section. Uncomment and set the value of `max_playlist_length` to something appropriate (e.g.: 400000).
Restart mpd. You can then load the playlist from your favorite mpd client.

## Requirements
The command line program `mpc` is used to communicate with mpd (to get current track url).
You would already have the others external tools involved (wget, gunzip and perl).

[jpl]: http://github.com/PotatoesMaster/jamendo-tools/blob/master/jamendo-playlist
[jgm2]: http://github.com/PotatoesMaster/jamendo-tools/blob/master/jamendo-mpd-get2
[gojam]: http://github.com/PotatoesMaster/jamendo-tools/blob/master/gojam

[jam]: http://www.jamendo.com/
[jamxml]: http://developer.jamendo.com/fr/wiki/NewDatabaseDumps
[jamget2api]: http://developer.jamendo.com/fr/wiki/Musiclist2Api

[mpd]: https://en.wikipedia.org/wiki/Music_Player_Daemon
