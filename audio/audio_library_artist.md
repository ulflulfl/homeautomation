# Audio Library: Artist

How Music Assistant handles artist specific infos (image, biography text, ...) when using the filesystem providers and how to add artist data locally.

State(2024.07): This page is based on my current understanding of Music Assistant (version 2.2.0b0), both may improve over time ...

The following page focuses on the "Filesystem (local disk)" and "Filesystem (remote share)" providers. Artist infos from online providers (Spotify, Deezer, ...) will not be described here as I don't use these.

A general overview how Music Assistant fetch metadata is at: https://github.com/orgs/music-assistant/discussions/543 (beware: The posting is from 2022 and might be slightly outdated)

Please discuss improvements of this page at the Music Assistant "filesystem" discord channel or send a pull request with page updates to me.

## Online Automatic Downloads "often fail"

Music Assistant tries to download artist information automatically from fanart.tv or TheAudioDB.

**The online ressources for MA automatic downloads are VERY limited by the online databases "20 slots per day", so getting artist infos automatically often takes a VERY long time (if it works at all).**

When I set up my audio library it felt a bit like a lottery. Even after a few days of usage, I got less than 10 out of 100 artists with a picture and some biography text.

Providing the artist information with local files is optional, but infos will be available MUCH faster and under your control.

## Offline File Location

If you use the "common" structure artist/album/song, place the artist related files directly in the artist folder. The artist folders must be on the root level of the filesystem provider.

**If you use a different folder structure than artist/album/song, the artist related files will probably not be found and ignored.**

Example file tree:

- artist 1
  - **artist.jpg**
  - **artist.nfo**
  - **fanart.jpg**
  - album 1
    - **album.nfo**
    - **folder.jpg** (or cover.jpg)
    - song 1.mp3
    - ...
  - album 2
    - **album.nfo**
    - **folder.jpg** (or cover.jpg)
    - disc 1
      - **folder.jpg** (or cover.jpg)
      - song 1.mp3
      - ...
    - disc 2
      - ...
- artist 2
  - ...

... png or jpeg instead of jpg should also work.

As I understand what happens internally (beware: guesswork!): The filesystem providers read all the audio files and reads the artist name from the files "id3 tags". Then the providers search at the file system root for a folder that matches the artist name exactly. Seems the MusicBrainz id is not used for this matching. TODO: Is this true or does more / something else happen?

TODO: How to handle e.g. AC/DC where this will not work?

Hint: Music Assistant don't use a special ArtistInfo folder as described in the Kodi documentation.

## Offline Files

### artist image

The artist image is displayed on the artists list page and on the artist page.

As long as the image file is placed in the right artist folder, the actual file name doesn't really matter: artist.jpg, cover.jpg, folder.jpg or ... will probably do. TODO: Reading the docs and source code again, probably only specific filenames will work?

Finding the image file is probably based on the file extension. I've successfully used the file extensions: .jpg, .jpeg, .png and .gif (others: bmp and webm are not supported)

The image should have a square ratio (roughly, TODO: otherwise it will be croppped?).

TODO: If multiple image files exist in the folder, which one is used?

TODO: Does a local image file takes precedence over infos fetched online?

Online sources for image files:
* https://fanart.tv/
  * e.g. Sting: https://fanart.tv/artist/7944ed53-2a58-4035-9b93-140a71e41c34/sting/
* https://www.theaudiodb.com/
  * e.g. Sting: https://www.theaudiodb.com/artist/111600-Sting

Kodi recommendations (e.g. pixel sizes) at: https://kodi.wiki/view/Artwork_types#Artist

### fanart image

If you place a fanart.jpg in the artist folder, it will be used as a basis to create the banner on the artist and album page.

### artist.nfo

The artist.nfo file contains meta data like a biography text and genre infos.

MA will read the artist.nfo file and use some of the data to improve the displayed infos on the corresponding artist page and elsewhere.

MUCH more detailed infos about the artist.nfo file at: [audio_library_artist.nfo.md](audio_library_artist.nfo.md)

TODO: Does the infos from artist.nfo takes precedence over infos fetched online?

## Updates

**After you've added or edited the artist files, the changes will NOT immediately show up in the UI.**

Use "Refresh item" and/or "Remove from library" on the artists page (top right "...") to trigger an update (or wait up to three hours for the sync to run automatically). However, this doesn't work all the time for me and the old data is still shown.

A somewhat tedious sequence - but works all the time:

* Move artist folder completely away from MA
* Trigger an update (as mentioned above or on the artists list page)
* Wait until the artist disappears from the artists list (browser page refresh from time to time), may take a minute or two
* -> now the artist should be removed from the internal database completely
* Move artist folder back in place
* Trigger an update
* Wait until the artist appears at the artists list again

Pro tip: If you are using MA in a docker container and also Portainer, go to the MA container Logs to see what's happening in real time. This will only be real useful, if you enable the log level DEBUG.

**... if the image won't refresh its probably cached in the browser. Try a different browser or clear the browser cache (e.g. Shift+"Reload page icon" on Firefox)!**

## Source Code

* _get_local_images(): https://github.com/music-assistant/server/blob/main/music_assistant/server/providers/filesystem_local/base.py#L1035