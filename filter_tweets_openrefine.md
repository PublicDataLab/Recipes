# 🌪️💬 Filtering tweets based on hashtags

*A recipe to extract a subset of tweets based on one or more hashtags using OpenRefine*

This recipe presents a method to export small subsets from a full Twitter dataset based on a selection of hashtags. In particular, with this recipe, one will query a Twitter dataset with one hashtag or two or more hashtags connected by basic boolean operations (i.e., OR, AND). It can be used to extract a selection of tweets to analyse later with spreadsheet software.


# 🧱 Inputs

This recipe starts from a full Twitter dataset exported from the [Twitter Capture and Analysis Toolset (DMI-TCAT)](https://wiki.digitalmethods.net/Dmi/ToolDmiTcat). Still, it can be used with any Twitter data, as long as there is a column with tweets text and one column with hashtags (which should be in the same cell and separated by semicolon).

![](https://i.imgur.com/2G3JAvI.jpeg)


# 📃 Steps

## Installing OpenRefine
  1. Download latest version of [OpenRefine from this link](https://openrefine.org/download.html)
  2. Follow instructions based on OS (Mac or Windows)
  3. Refer to the [official documentation](https://docs.openrefine.org/manual/installing) for troubleshooting errors when installing OpenRefine
  4. When installed, double click on the Open refine icon
  5. OpenRefine opens directly in your browser
  6. If the browser does not open, you can type this URL in your browser bar

## Opening the full dataset with OpenRefine
  1. Select the file from your computer and press [next]
  2. Click [create project] on the top right corner

![](https://i.imgur.com/hLjPLTH.gif)

## Creating a subset based on 1 hashtag
This step can be used to select tweets containing one specific hashtag. For example, extracting all the tweets with *#greenpeace*.

  1. On the header of the column containing the hashtags, click the small arrow next to the column name, and choose [Text filter]
  2. On the panel [hashtags] in the top left corner write the hashtag you want to filter (e.g. greenpeace)
  3. You can set the filter to be case sensitive checking the box at the bottom
  4. Note that on top of the spreadsheet you can see how many tweets match your criteria (in this case 80 tweets)
  5. Click on [Export] on the top right corner to export a csv file or Excel file

  ![](https://i.imgur.com/vlT5Neh.gif)

## Creating a subset based on 2 hashtags (OR)
This step can be used to filter tweets based on more than one hashtag. This query technique will result in a subset of all tweets mentioning at least one of the selected hashtags. For example, extracting all the tweets with *#greenpeace* or *#extinctionrebellion*.

  1. On the header of the column containing the hashtags, click the small arrow next to the column name, and choose [Text filter]
  2. On the panel [hashtags] in the top left corner, select the [regular expression] option
  3. In the same panel, write the hashtags separated by a pipe: `greenpeace|extinctionrebellion`
  4. You can set the filter to be case sensitive checking the box at the bottom
  5. Note that on top of the spreadsheet you can see how many tweets match your criteria (in this case 478 tweets)
  6. Click on [Export] on the top right corner to export a csv file or Excel file

  ![](https://i.imgur.com/AKLKhjY.gif)

## Creating a subset based on 2 hashtags (AND)
This step can be used to filter tweets based on more than one hashtag. This query technique will result in a subset of all tweets mentioning one of the selected hashtags. For example, extracting all the tweets with *#greenpeace* and *#extinctionrebellion*.

1. On the header of the column containing the hashtags, click the small arrow next to the column name, and choose [Text filter]
2. On the panel [hashtags] in the top left corner write the first hashtag you want to filter (e.g. greenpeace)
3. On the header of the column containing the hashtags, click again the small arrow next to the column name, and select [Text filter]: a new filtering panel will appear
4. In the second panel, write the second hashtag you want to filter (e.g. extinctionrebellion)
5. Note that on top of the spreadsheet you can see how many tweets match your criteria (in this case only 2 tweets)
6. Click on [Export] on the top right corner to export a csv file or Excel file

  ![](https://i.imgur.com/gvA9ZsQ.gif)
