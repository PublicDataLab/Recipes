# 🌾🍚🔗 URLs analysis in YouTube comments

*A recipe for extracting URLs from Youtube comments*

This recipe shows how to collect comments from a Youtube video with ([YouTube Data Tools](https://tools.digitalmethods.net/netvizz/youtube/]))and then extract URLs into a clean list (with [DMI Harvester](https://tools.digitalmethods.net/beta/harvestUrls/)) for further analysis.  



# 🧱 Inputs
This recipe can be used starting from one or more Youtube video links for which you want to analyze comments.


# 📃 Steps


## Collecting comments from a Youtube video
1. Go to YouTube Data Tools and select the Video Info and Comments Module
2. Open a video on Youtube and copy the Video Id. Video Ids can be found in URLs
e.g. https://www.youtube.com/watch?v=**aXnaHh40xnM**
3. Copy and paste the Video Id into the Video id box
4. Leave empty the "Limit to" box (if you want to retrieve all comments)
5. Launch the tool
6. The tool generates different files. Download the one ending with "comments.tab". This file contains all comments.
7. Open the file with a Text editor of your choice
8. Select everything and copy it



![](https://i.imgur.com/CPiFvCJ.png)


## Extracting URLs from comments
1. Go to the [DMI Harvester](https://tools.digitalmethods.net/beta/harvestUrls/)
2. Paste the text of the whole comments into the box
3. If you want to limit the analysis to the hosts, you can select the "Only return host names" option
4. Check the option "Add "http:// if missing from url" to homogenize URLs
5. Click Harvest URLs to start
6. When finished, you can find a .csv in the Output section at the top of the interface
7. Download the .csv (you can now import it into a spreadsheet software)

<img src="https://i.imgur.com/Dip3Ha5.png" alt="" width="500px" height="572px">
