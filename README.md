# Youtube-DL Agent
After about a year of using [ZeroQI's Youtube Agent](https://github.com/ZeroQI/YouTube-Agent.bundle) I noticed a problem. If a youtube video gets deleted, it is no longer possible to get the metadata. Which makes sense, however the entire goal of having Youtube videos on your Plex Media Server is to make sure they never get deleted. 

This resulted in me looking around at different solutions, however I could not find anything that would work for me. 

## What does this agent do differently?  
Instead of fetching the data from the Youtube API, we use the data that [Youtube-DL](https://github.com/ytdl-org/youtube-dl) stores when downloading a video. Making sure we have the metadata forever even if a video gets deleted.

## Youtube-DL integration
In order to have this agent work correctly, videos have to be downloaded with [Youtube-DL](https://github.com/ytdl-org/youtube-dl). Youtube-DL has to be set to store the metadata and thumbnail of videos. Here is an example of a configuration

```
youtube-dl {URL} --add-metadata --write-info-json--write-thumbnail -f 'bestvideo[ext=mp4]+bestaudio[ext=m4a]/mp4'-o "/youtube/%(uploader)s [%(uploader_id)s]/%(title)s[%(id)s].%(ext)s"
```

This Youtube-DL configuration is also compatible with the ZeroQI Youtube Agent.

## Installation
In order to use this Agent you need to use the [Absolute Series Scanner from ZeroQI](https://github.com/ZeroQI/Absolute-Series-Scanner), You can try using it without however plex will think files are copies when they are not.

1. Download this repository ([CLICK HERE](https://github.com/JordyAlkema/Youtube-DL-Agent.bundle/archive/master.zip))
2. Unzip the file but keep the root folder ("Youtube-DL-Agent.bundle-master")
3. Rename the folder to "Youtube-DL-Agent.bundle"
4. Move the folder into the "Plug-ins" folder in your Plex Media Server installation ([Wait where?](https://support.plex.tv/articles/201106098-how-do-i-find-the-plug-ins-folder/))
5. Create a new (or update an existing) library and select "TV Show"
6. Click on the "Advanced" tab and select
    1. Scanner: Absolute Series Scanner
    2. Agent: Youtube-DL

Now you are done. At first Plex will scan for all the files, when this is done the agent will attempt to find the metadata associated with the videos.

## Troubleshooting
If you are running in to a problem, feel free to let me know so I can attempt to help you. However make sure to send the log files otherwise I can't help.

[How do I download the Log files?](https://support.plex.tv/articles/200250417-plex-media-server-log-files/)

### What is to blame?
If videos are in the wrong season, videos are seen as copies, videos do not show up or videos are in the wrong channel this is an issue with your scanner. Contacting me is not useful because I can not help.

If a video (or TV Show) has incorrect metadata (Title, Description, Thumbnail, Rating etc.) this is an issue with the Agent. Feel free to contact me.


## Thanks to...

**[ZeroQI](https://github.com/ZeroQI)** - ZeroQI created the original Youtube Agent, the Absolute Series Scanner which this agent also uses and he has a bunch of helpful posts on the Plex forums.