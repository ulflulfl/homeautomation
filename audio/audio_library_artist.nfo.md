# Audio Library: artist.nfo

The file artist.nfo stores metadata information (e.g.: biography, genre, ...) about artists.

The following page focuses on the artist.nfo as used in Music Assistant, which itself orients on the artist.nfo documentation of Kodi (and MusicBrainz).

State(2024.07): The page is based on my current understanding of Music Assistant (version 2.2.0b0), both may improve over time ...

Please discuss improvements of this page at the Music Assistant "filesystem" discord channel or send a pull request to me.

## Music Assistant usage

TODO: Rework this section

Music Assistant tries to download artist information automatically from fanart.tv or TheAudioDB. However, the online ressources for this are VERY limited "20 slots per day", so getting artist infos may take a VERY long time. Providing the artist information locally in an artist.nfo file will be available MUCH faster and under your control.

MA will use artist.nfo with the "Filesystem (local disk)" and "Filesystem (remote share)" providers. MA will read the artist.nfo file and use some of the data to improve the displayed infos on the corresponding artist page and elsewhere. MA will not write or change the artist.nfo file.

**If you use the "common" folder/file structure artist/album/track, place the artist.nfo file in the artist folder. If you use a different folder structure, the artist.nfo file will probably not be found and ignored. The artist folders must be on the root level of the filesystem provider.** Music Assistant doesn't use a special ArtistInfo folder as described in the Kodi documentation.

**After you've added or edited the artist.nfo file, the changes will NOT immediately show up in the UI. Use "Refresh item" and/or "Remove from library" on the artists page (top right "...") to trigger an update (or wait up to three hours for the sync to run automatically).**

TODO: Does the infos from artist.nfo takes precedence over infos fetched online?

TODO: Seems the artist name from the id3 tags must match the folder name exactly. Is the MusicBrainz arid used here? How to handle e.g. AC/DC?

## Example File Content for "A Flock of Seagulls"
```
<?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
<artist>
    <name>A Flock of Seagulls</name>
    <musicBrainzArtistID>aaa436da-b331-4e58-a0fd-3d64d090c120</musicBrainzArtistID>
    <sortname></sortname>
    <type>Group</type>
    <gender></gender>
    <disambiguation></disambiguation>
    <genre>New Wave</genre>
    <style></style>
    <mood></mood>
    <yearsactive>1979-1986</yearsactive>
    <yearsactive>1988-present</yearsactive>
    <born></born>
    <formed>1979</formed>
    <biography>
A Flock of Seagulls are an English new wave band formed in Liverpool in 1979. The group, whose best-known line-up comprised Mike Score, Ali Score, Frank Maudsley and Paul Reynolds, hit the peak of their chart success in the early 1980s.
The group had a string of international hit singles including "I Ran (So Far Away)" (1982), "Space Age Love Song" (1982), "Wishing (If I Had a Photograph of You)" (1982), and "The More You Live, the More You Love" (1984). Their video for "I Ran (So Far Away)" received airplay on MTV during the Second British Invasion. The band won a Grammy Award in 1983 for their instrumental "D.N.A." (1982).
In 2018, the members of the original lineup assembled to record the album Ascension with the Prague Philharmonic Orchestra. In 2021, the original lineup again reunited temporarily to record another album with the Prague Philharmonic Orchestra, String Theory.
https://en.wikipedia.org/wiki/A_Flock_of_Seagulls
	</biography>
    <died></died>
    <disbanded></disbanded>
    <thumb spoof="" cache="" aspect="thumb" preview="artist.jpg">artist.jpg</thumb>
    <thumb spoof="" cache="" aspect="banner" preview="banner.jpg">banner.jpg</thumb>
</artist>
```

As the first line suggest, use UTF-8 file encoding. TODO: Windows CR/LF or Linux (LF only) line endings?

## Tag Overview

Seems that every program (Music Assistant, Kodi, Jellyfin, ...) supports a different set of artist.nfo tags.

The following lists the tags as documented for Kodi (https://kodi.wiki/view/NFO_files/Artists) to get an overview "what's possible". Tags that are actually used by Music Assistant are highlighted.

| NFO (xml) Tag | Description | Tag Example | Multiple | Music Assistant Support | Notes and Futher Infos |
| --- | --- | --- | --- | --- | --- |
| **name** | **The name of a Person or Group** | The Beatles | no | **Changes the displayed name (on various pages)** | - |
| **sortname** | **name as used for sorting** | Beatles, The | no | **Will affect artist list sorting, if "Sort name" is selected** | https://wiki.musicbrainz.org/Style/Artist/Sort_Name |
| **musicBrainzArtistID** | **MusicBrainz artist id "arid"** | 66c662b6-6e2f-4930-8610-912e24c63ed1 | no | **yes (TODO: What happens?)** | https://musicbrainz.org/doc/MusicBrainz_Identifier |
| type | Person, Group, Orchestra, Choir or Other | Person | no | no | https://musicbrainz.org/doc/Artist |
| gender | Male, Female or Neither | Male | no | no | https://musicbrainz.org/doc/Artist (Groups do not have genders.) |
| disambiguation | Short hint to distinguish artists with the same name | [Randy Jackson](https://musicbrainz.org/artist/593abf14-4292-4d62-b365-79c7674cd1a5) has the disambiguation comment: "brother of Michael and Janet" | no | no | https://musicbrainz.org/doc/Disambiguation_Comment |
| **genre** | **Genre of the artist** | New Wave | yes | **Shown on artists page (multiple tags possible)** | https://musicbrainz.org/genres MusicBrainz uses all lower chars "new wave" while Kodi example uses "Soft Rock"|
| style | TODO | Soft Rock | yes | no | Some examples: https://kodi.wiki/view/NFO_files/Templates#artist.nfo_Template |
| mood | TODO | Nostalgic | yes | no | Some examples: https://kodi.wiki/view/NFO_files/Templates#artist.nfo_Template |
| yearsactive | Timespan the artist is/was active | "1988 - present" or "1960s - 2010s" | yes | no | - |
| instruments | TODO | TODO | yes | no | I couldn't even find an example for this online  |
| born | Date the Person was born | 1949-05-09 | no | no | only used for Person, not for Group, Orchestra or Choir |
| formed | First time the band was formed or the artist performed | 1979 | no | no | Example: https://kodi.wiki/view/NFO_files/Templates#artist.nfo_Template |
| **biography** | **Biography text** | see example content above | no | **Shown on artists page** | Often an excerpt from the artists Wikipedia page |
| died | Date the Person died | 2022-05-09 | no | no | only used for Person, not for Group, Orchestra or Choir |
| disbanded | TODO | TODO | no | no | I couldn't even find an example for this online. TODO: Only used for Group, Orchestra or Choir, not for Person? |
| thumb | Path to available (online) artist images | see example content above | yes | no (TODO: MA only uses local image file in the artist folder?) | Values for aspect attribute (from: https://kodi.wiki/view/NFO_files/Templates#artist.nfo_Template): thumb, clearlogo, clearart, landscape, banner, fanart |
| path | Path to this file |F:\Music\ArtistInfoKodi\Billy Joel |  no | no | - |
| album ... | List of artist albums | - | yes | no | Kodi: "Artist discography. A scraped listing not releated to the albums in the library ". I couldn't even find an example for this online |

As you can see, the number of tags supported by Music Assistant are currently pretty limited. Hopefully, this will improve in the future ...

Remarks:
* If a tag is unknown or doesn't apply, leave the tag empty \<died>\</died> (which I usually do, so I can see what's probably missing) or remove it.
* Tags for multiple languages or multiple artist.nfo files in different languages are not supported. Thie would be especially useful for the biography text.

Further tag infos:

* Kodi: https://kodi.wiki/view/NFO_files/Artists
* Kodi template & examples: https://kodi.wiki/view/NFO_files/Templates#artist.nfo_Template
* Jellyfin: https://jellyfin.org/docs/general/server/metadata/nfo/
* MusicBrainz: https://musicbrainz.org/doc/Artist (not about artist.nfo, but the "Artist properties" section provides some good explanations)

## Where to find artist infos?

So how to get artist.nfo files for my "artist collection"?

### Semi-automatic

I haven't found an easy to use solution to scrape artist.nfo from online sources yet. Two candidates maybe worth a further look:

* [Mediaelch](https://mediaelch.github.io/mediaelch-doc/about.html): Open Source, Multi platform desktop GUI app, that states: "MediaElch creates nfo files for use with Kodi. Because of extensive configuration options other media centers are supported as well. ". I had a very short look, but the UI confused me. TODO: Need to do a second try
* [beets](https://beets.io/): Open source, multi platform command line app. Seems very versatile but also very complex. Maybe together with plugins (https://github.com/beetbox/beets/pull/2569 ?!?) it can do the job?

### Manual

Creating artist.nfo files manually can be a lot of work. Here are some hints to get the data:

* MusicBrainz artist infos: On the artist page under the Details tab you'll find an xml download link of the artists "raw data" that can be helpful:
  * Details tab for Sting: https://musicbrainz.org/artist/7944ed53-2a58-4035-9b93-140a71e41c34/details
  * API
    * https://musicbrainz.org/doc/MusicBrainz_API (**if you script this, don't ignore their terms of service!**)
    * General MB API: https://musicbrainz.org/doc/MusicBrainz_API/Search
    * XML raw data for String: https://musicbrainz.org/ws/2/artist/7944ed53-2a58-4035-9b93-140a71e41c34?inc=aliases
    * Request using the MB artist id: https://musicbrainz.org/ws/2/artist/?query=arid:83d91898-7763-47d7-b03b-b92132375c47 (also includes a tag-list)
* Wikipedia: The artists page first section usually contains a good biography text.
  * Example: https://en.wikipedia.org/wiki/Sting_(musician)
  * I simply copy the text of the first few sections
  * I manually remove reference notes, like: [7]
  * Seems replacing special chars like " with &qout; isn't necessary (at least for Music Assistant)
  * I'll add the link to the page at the bottom: https://en.wikipedia.org/wiki/Sting_(musician) (unfortunately, Music Assistant will not create a clickable link of that)

### Editing

Some hints to edit the .nfo files:

* Use UTF-8 file encoding
* Use "unix style (LF)" line endings ?!? (TODO: clarify)
* Notepad++ has problems with the utf-8 coding of .nfo files (https://github.com/notepad-plus-plus/notepad-plus-plus/issues/9153)

### Music Assistant Source Code

The code to parse the artist.nfo content is at: https://github.com/music-assistant/server/blob/main/music_assistant/server/providers/filesystem_local/base.py#L924
