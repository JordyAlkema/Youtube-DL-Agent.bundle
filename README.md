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

## Thanks to...

**[ZeroQI](https://github.com/ZeroQI)** - ZeroQI created the original Youtube Agent, the Absolute Series Scanner which this agent also uses and he has a bunch of helpful posts on the Plex forums.