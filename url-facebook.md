# 🧮 URL-Facebook Group networks

*A recipe exploring social media engagement around a given set of URLs.*

How are these links shared on Facebook? This recipe shows how you can obtain social media engagement data for a given set of URLs using Facebook's CrowdTangle tool, and to explore this data using visual network analysis with the open source Gephi software. This recipe focuses on engagement around a set of YouTube URLs on public Facebook groups but it can also be used to obtain data on social media engagement on other platforms (e.g. Reddit, Instagram) for any kinds of URLs.

# 🗄️ Examples

- [Do Facebook publics have preferred story themes?](https://fakenews.publicdatalab.org/) - from the [*Field Guide to "Fake News"*](https://fakenews.publicdatalab.org).

![](https://i.imgur.com/a7D4QSR.png)


# 🧱 Inputs from TCAT

- List of URLs

# 📃 Steps

## Step 1 - Assemble a list of URLs

- Create or obtain a list of URLs
  - 🤔 *Think carefully when assembling your list. Why these particular items? How will you be able to formulate a research question around them? To illustrate this recipe we will be using a list of URLs for deplatformed YouTube videos obtained by looking at a subset that had been removed from a broader list created using a keyword query. For more on making lists you can see [this worksheet](http://bit.ly/making-lists-worksheet) and associated resources.*

## Step 2 - Obtain social media engagement data (manual)

 - Install [CrowdTangle browser extension](https://apps.crowdtangle.com/chrome-extension).
 - Go to the URL that you wish to gather engagement data for.
 - Click the CrowdTangle extension button to display engagement data.
 - Click "Download" (in top right corner) to download engagement data.

![](https://i.imgur.com/OPqr7JI.gif)

 - Import the CSV files into a new sheet on Google Sheets.
 - Create a new master sheet to collate both URLs and associated engagement dataset.
 - Add the URL in the first column.
 - Copy and paste the engagement data to the right.
 - Fill down the URL column.
 - Repeat the process until you have gathered engagement data for every URL in your list.

![](https://i.imgur.com/X3bE5YR.gif)

## Step 2 - Obtain social media engagement data (script)

# ⚠️

*Note: This is an experimental option which depends on a script which pulls data from the CrowdTangle API using the [/links endpoint](https://github.com/CrowdTangle/API/wiki/Links). It depends on having access to the CrowdTangle API. It is possible that the script may stop working if the API changes, or if there are issues with the code on ObservableHQ. But if it works it can do the steps above much more quickly.*

 - Get a CrowdTangle account (e.g. through your university's account).
 - Get a CrowdTangle API key (see [here](https://help.crowdtangle.com/en/articles/1189612-crowdtangle-api) for instructions).
 - Go to this URL: https://observablehq.com/@iosonosempreio/crowdtangle-api-links
 - Paste in your links and your API key.

![](https://i.imgur.com/rmGYTCv.png)

 - Configure settings (including platforms, number of posts and start and end dates).
 - Click "start".
 - You can follow progress with the "status" field and see a preview of the data that has been collected so far.

![](https://i.imgur.com/aUhrom7.png)

 - Once the script has finished it will say Finished! Retrieved [x] urls"
 - You can download the data as a CSV file by clicking the three little dots to the left of the `data =` section and then selecting "Download CSV".

![](https://i.imgur.com/NjaoNeM.gif)

## Step 3 - Visualise using Gephi

We can use Gephi to explore associations between the set of URLs and the groups they are shared in.

 - Export CSV file from your spreadsheet of URLs and associated Facebook groups
 - Download and install Gephi: https://gephi.org/
   - *If you've not used Gephi before, you may refer to these videos on [installation](https://www.youtube.com/watch?v=DMOWhqp6lHQ), [first look](https://www.youtube.com/watch?v=YM_37z_uURM&) and [layouts, clusters and where to find them](https://www.youtube.com/watch?v=0LqY8OfSsKE).*
 - Go to: https://medialab.github.io/table2net/
 - Select "bipartite network (two types of nodes)"
 - Select the column with URLs as the first type of node
  - *Note: you may optionally wish to use VLOOKUP function in order to create a new column with titles instead of URLs to display on your network graph. To do this you can create a new sheet containing the video URLs and titles and turn this into a new ‘Named range’ (by clicking on the “Data” menu and then “Named ranges” then “Add a range” from the right hand menu). Use the [VLOOKUP function](https://support.google.com/docs/answer/3093318?hl=en-GB) to find the titles associated with each URL by using `=VLOOKUP([reference to cell containing URL],[name of named range], 1,FALSE)`*.
 - Select column with the name of the Facebook groups as the second type of node
 - Build the network
 - Open and visualise the resulting network file in Gephi
   - *If you have not used Gephi before you may wish to refer to the videos linked to above for a more detailed walkthrough of these steps.*
   - *Spatialise using Force Atlas 2. In this case we set scaling to 10 and turned on LinLog mode.*.
   - *Colour nodes according to type by going to appearance section and clicking nodes > paint palette > partition > select type from dropdown menu > apply.*
   - *Scaling nodes according to degree by going to appearance section and clicking nodes > concentric circles > ranking > select degree from dropdown menu > set min size to 10 and max size to 100 > apply.*
   - *Scaling text size according to degree by going to appearance section and clicking nodes > "T"s > ranking > select degree from dropdown menu > set min size to 1 and max size to 6 > apply.*
   - *To export go to "preview" workspace, click "show labels", then "refresh" at the bottom of the screen, and export as PDF.*
   - *You can then annotate your network and/or produce a walkthrough (e.g. using the [tesselle tool](https://medialab.github.io/tesselle/))*.


![](https://i.imgur.com/yOSo0hj.png)

![](https://i.imgur.com/MBWbAIl.png)


# 🐙 Inspiration, acknowledgments and contributors

*This recipe expands on a recipe in Chapter 2 of the [Field Guide to "Fake News"](https://fakenews.publicdatalab.org). It is illustrated with materials from a [Digital Methods Initiative Summer School](https://wiki.digitalmethods.net/Dmi/DmiSummerSchool) project on ["Demoting, deplatforming and replatforming COVID-19 misinformation"](https://wiki.digitalmethods.net/Dmi/SummerSchool2020ModeratingCovidMisinfo) and the 2020-2021 edition of a module on [Digital Methods for Internet Studies: Concepts, Devices and Data](https://www.kcl.ac.uk/artshums/depts/ddh/modules/level7/7aavdm28) on the theme of ["infodemic"](http://infodemic.eu/) at the [Department of Digital Humanities](https://www.kcl.ac.uk/ddh), [King’s College London](http://kcl.ac.uk/). The script was developed by [Tommaso Elli](https://densitydesign.org/person/tommaso-elli/) at [Density Design Lab](https://densitydesign.org/) in Milan.*
