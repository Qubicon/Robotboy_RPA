# Playlist migration

Robot that automatically migrates a playlist from Spotify to YouTube.

## How it works

* The robot opens the Spotify desktop app, and performs login based on the credentials stored in an asset. If the user is already logged in, the workflow throws an exception and it is terminated.
* The robot opens the search tab, and with an input dialog, it searches for the input provided by the user. If the most relevant result is not a playlist, the robot clicks on the "Playlists" tab and selects the first item returned. Then, it opens the playlist.
* After opening the playlist, data scraping is performed, which retrieves the songs contained in the playlist, along with the album and other details. The results are saved in an Excel file.
* The robot opens the YouTube website, performs login using the credentials stored in an asset.
* The Excel file created previously is read, and every song is searched on YouTube and added to the playlist. After doing this, for each song, the status is written in the Excel file: if it was added successfully to the playlist or not.
* The robot sends an email with the generated Excel file and the Config.xlsx file that contains the URL to the new Youtube playlist.

## Dependencies

    "UiPath.Excel.Activities": "[2.17.0-preview]",
    "UiPath.Mail.Activities": "[1.18.2]",
    "UiPath.System.Activities": "[22.10.4]",
    "UiPath.Testing.Activities": "[22.12.0-preview]",
    "UiPath.UIAutomation.Activities": "[22.12.0-preview]"
