{% include toc.html %}
# Modding Guide: Custom Songs

Adding custom songs in a mod is ridiculously simple, and no recompilation or changes to the game's code are required. Just follow these steps:

1. Add your audio files to the `mods/<modid>/music/<song-id>` folder. Don't include spaces or symbols in the song ID.
2. Create a chart for your song. You can copy another song's chart as a placeholder for now. Place the charting data into the `data/songs/<song-id>` folder.
3. Add your song to the free play menu. Create the file `mods/<modid>/_append/data/freeplaySongnames.txt`.
4. Add a line like this to the file you just created:
```
dadbattle:1:dad
```

The first value is the song ID (the folder name of the song you created),

5. (Optional) Create a file `data/songs/<song-id>/_meta.json`, which looks like this. You can use this to specify an audio offset for your song's chart or specify a custom display name for the song. The custom display name can include spaces or symbols.

```
{
  "offset": 0,
  "name": "Dad Battle"
}
```

6. Your new song should be available in Free Play. If you need to replace the chart, you can do that now by selecting the song in the Free Play menu and pressing 7 to enter the Chart Editor.

If you want to use a custom character for your song, check out the guide on [Custom Characters](/docs/custom-characters).
If you want to use a custom stage for your song, check out the guide on [Custom Stages](/docs/custom-stages).
If you want to use your song in a custom week, check out the guide on [Custom Weeks](/docs/custom-weeks).