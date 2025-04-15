# Audio Library Editing
How do I edit my audio library files.

State (2024.07): While I have slow progress, still a lot of audio files to clean up ...

## History

In "former times", I played music from my disc on the Notebook simply using the file system and VLC. I sorted the albums in the file system by artist/album/tracks but didn't care much about the metadata "MP3 tags".

Music Assistant (and also other systems like Kodi) heavily depend on the tags and care much less about the directory structure and file names.

So I had to cleanup my music library ...

## Mixed Bag
I started with many varieties:

* flac, mp3, wav, mp4, webm, mkv, ...
* one file per track, one file per album, ...
* no tags, tags for album/artist/year, tags with cover, ...

So one task is to convert some videos to audio files (as Music Assistant can't handle mp4 or alike), another is to cleanup the tags.

## Backup First!

Before I started to edit any files, I made a backup so I can go back if something gets wrong.

## Audacity
[Audacity](https://www.audacityteam.org/) is a multi platform open source desktop tool intended for audio editing. It can also be used to extract the audio from video files. If "[ffmpeg for Audacity](https://support.audacityteam.org/basics/installing-ffmpeg)" is installed, you can convert the audio tracks of videos to audio files.

I just drag-n-drop the video file to Audacity, the Import takes a few seconds up to a minute, depending on the file size. Then I export the audio file (Menu: File > Audio Export) and set the Format to "FLAC", the export takes a similar time.

I use it to convert mkv, mp4 and webm to flac files. I'm still unsure if this is the best way to convert videos to audio files, but at least it works reasonably well.

## MusicBrainz Picard
[Picard](https://picard.musicbrainz.org/) is a multi platform open source desktop tool to semiautomatically add tags to audio files including covers. It is recommended by Music Assistant and other sources for "tag cleanup".

Usually it detects album track files correct, the written tags look nice including a cover.

Sometimes it detects things wrong and mixes the tracks into different/wrong albums, you need to manually fix this. Sometimes it finds covers different from the CDs I have. For "one file per album" it fails completely to detect anything. Please also note, if you have (multiple) cover(s) already in your tags, by default the "old" cover(s) will be overwritten without notice (this probably can be changed in the settings).

To get accurate tags, I let Picard analyze the files one album at a time and fix appearing detection problems.

## Mp3Tag
[Mp3Tag](https://www.mp3tag.de/en/) is a Windows/MacOS freeware desktop tool for metadata tag editing.

While the main view of Mp3Tag only shows a selection of important tags, the Tags dialog (Menu: View > Extended Tags ...) lists all tags in the loaded file(s).

I'm using Mp3Tag for manually adding tags where necessary, which is a lot of work. Usually I'm using it for "**one file per album**" and tag the following:

* Title (typically in the form: "{artist} - {year] - {album}")
* Artist
* Album
* Year
* Album Artist (typically same as artist)
* Discnumber (typically 1)
* Cover (simply drag-n-drop from File Explorer)

I haven't intensively looked around for an open source tag tool yet, as Mp3Tag is doing the job well. I've briefly checked Kid3 but then continued to use Mp3Tag.
