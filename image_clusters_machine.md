# 🌁🤖 Content similarity image clusters (with computer vision), annotated

*Identifying thematic clusters inside a (rather large) image collection.*

This approach helps to cluster and visualise images in a collection, according to how machine learning algorithms classify their content. This can be used to identify thematic visual clusters inside a collection of images as well as to quantify them. It is similar to a co-hashtag analysis, but undertaken with visual content. In practice, with the help of computer vision one generates tags for each image and then uses shared tags to visually cluster similar images. There are four main phases. First, images are tagged with help of a computer vision API. Second, images are downloaded and saved locally. Third, a network of images and tags is built and visualized in Gephi. Finally, images are loaded into the network and exported. The process ends with annotation of clusters on Vector.com.

# 🗄️ Examples

- Mapping Parisian Urban Nature [Abstract](https://medialab.sciencespo.fr/productions/2017-designing-digital-methods-to-monitor-and-inform-urban-policy-the-case-of-paris-and) / [PDF](https://spire.sciencespo.fr/hdl:/2441/10ctml1egq89ro59upjajbj74n/resources/ippa-ricci-colombo-meunier-brilli.pdf) / [Composite images](https://drive.google.com/open?id=1SpDm2G_K0RejVyFymSvcHRZExoMGLaM3)

# 🧱 Inputs from TCAT

- “Media frequency”
- Or “Export all tweets from selection” → column “from_user_profile_image_url”

# 📃 Steps

## Tag images with computer vision API

1. Open data with Google Spreadsheet
2. Export csv with URLs list from Google Spreadsheet
3. Import URLs list in [image tagging tool](https://densitydesign.github.io/dd-image-tagging/)) (be sure to get your own [Clarifai API key](https://portal.clarifai.com/signup) and paste it into the tool)
4. Run tagging (click button: process input file)

![](https://i.imgur.com/JM2OaIW.gif)

## Download images locally and resize them

You can do this, for example, using a browser extension or using the command line.

### Using browser extension

1. Install [Tab Save Chrome extension](https://chrome.google.com/webstore/detail/tab-save/lkngoeaeclaebmpkgapchgjdbaekacki)
2. Copy and paste URLs list in Tab Save
3. Download images from URLs list with [Tab Save](https://chrome.google.com/webstore/detail/tab-save/lkngoeaeclaebmpkgapchgjdbaekacki)
4. Go to [Bulk Resize Photos](https://bulkresizephotos.com)
5. Drag images
6. Resize by 50%
7. Unzip folder

### Using command line

An alternative approach to downloading images is to use the [command line](https://en.wikipedia.org/wiki/Command-line_interface).

1. First you'll need to install [wget](https://www.gnu.org/software/wget/) a tool for downloading files using HTTP and other protocols. How you do this will depend on your operating system, your command line interface and your package manager. For example,
  - If you're on a Mac you can install a package manager such as [Homebrew](https://brew.sh/) and you can use `$ brew edit wget`
  - If you're on Linux you can use `$ apt-get install wget`
2. Put the image URLs into a single [csv file](https://en.wikipedia.org/wiki/Comma-separated_values)
3. Create a folder where you'd like the images to go and navigate to the folder using the command line
  - You can use `ls` to list the files at your location and `cd` to change to a given directory
4. You can download the files listed in the csv file using the command `wget -i [path to the csv file] --show-progress`
  - For further details and other options see the [wget manual](https://www.gnu.org/software/wget/manual/wget.html)
5. If this works you should have a folder full of images. 🎏
  - If you'd like to create a text file with the images which are in the folder (e.g. to check which have downloaded or to add file names to a dataset) you can use `ls -1 >> [name of your file.csv]` to generate another csv files with the names of all the files which have successfully downloaded.


## Prepare edges table for Gephi

1. Import csv output of Image tagging tool in Google spreadsheet
2. Rename headers: url → Source; concept → Target; confidence → Weight
3. Export edges csv from Google Spreadsheet

## Prepare nodes table for Gephi
*Note: you can also use [Table2Net](https://medialab.github.io/table2net/) to create graph files from csv files, but here we will do this manually to update image locations.*

1. Copy “Source” column in a new sheet
2. Rename column as “Id”
3. Make a copy of “Id” column into a new column
4. Rename the new column as “image”
5. In the new column “Image”, transform URLs strings into file names (see below for options)
6. Export node csv from Google Spreadsheet

### Adding image file names with find and replace

- Sort column “Image” alphabetically
- There are different types of urls, but all of them ends with the image name. The goal is to delete every character before the image name with the Find and Replace tool. Proceed by group of similar URLs.
- Select column “Image”
- Edit → find and replace
- Find a string such as `https://pbs.twimg.com/media/` and replace with nothing (be sure that you are doing the search only in a “specific range”, which in this case is the column “Image”)
- Repeat for each type of URL, until you only have image names and no URLs

### Adding file names with VLOOKUP

- Create new sheet called "urls" and copy and paste the image URLs into it.
- Create a new 'Named range' by clicking on the "Data" menu and then "Named ranges" then "Add a range" from the right hand menu, enter the name "url_list" and select the urls in the sheet and click "Ok" and "Done"
- Create new sheet called "images" and copy and paste the downloaded file names into it (if you used wget method above you can use `ls -1 >> [name of your file.csv]` to get a list of the downloaded files)
- Use the [VLOOKUP function](https://support.google.com/docs/answer/3093318?hl=en-GB) to find the URLs associated with each of the images in the "images" sheet by using the following formula next to the first cell on the sheet `=VLOOKUP("*"&A1,url_list, 1,FALSE)`. You can double click the small square in the bottom of the cell or drag down to lookup the rest of the images in the sheet.
- Copy the table of images and associated urls and paste into a new sheet (e.g. "image_urls_values") using "Edit" > "Paste special" > "Paste values only". Create a new named range (using the same process described above) by selecting these values and naming them "image_url_table".
- In the "nodes" sheet, create a new column called "Image" and use VLOOKUP again to find the associated URLs with the following formula `=VLOOKUP(A2,image_url_table, 2,FALSE)`. You can double click the small square in the bottom of the cell or drag down to lookup the rest of the images in the sheet.

## Import network and visualize clusters with Gephi

1. Open Gephi
2. Download and install “Image preview” plugin
3. Data laboratory → import spreadsheet
4. Import edges table
5. Data laboratory → import spreadsheet
6. Import nodes table (be sure to have checked: “append to existing workspace”)
7. Resize nodes based on “out-degree”
8. Spatialise network with Force Atlas 2

## Export image from Gephi and annotate
1. In the Finder, find one image file
2. Find path (on Mac: command + i)
3. Copy path
4. Go to Gephi → Preview window
5. Select “Render nodes as images”
6. In the field “Image Path”: paste image path
7. Set nodes opacity to 0
8. Deselect “show edges”
9. Click "Refresh" to generate image network
10. Export png
11. Import png in [Vectr.com](https://vectr.com/)
12. Annotate custers

*Note: if the images don't show up and/or the nodes continue to appear behind the images you may have to turn opacity to 100 in "Preview Settings" of the "Preview" panel and then change the node colour to white by going to "Overview" > "Appearance" > "Nodes" > "Unique" and selecting white (#ffffff) as the node colour. Upon refreshing and exporting the network you should see just clusters of images, without nodes or edges.*

# 🐙 Inspiration, acknowledgments and contributors

*This and other visual methods recipes were originally formulated by [Gabriele Colombo](https://densitydesign.org/person/gabriele-colombo/) drawing on his doctoral work exploring the [design of composite images](https://www.politesi.polimi.it/handle/10589/141266). They were [documented and refined](https://twitter.com/jwyg/status/1192814377671561218) for a module on [Digital Methods for Internet Studies: Concepts, Devices and Data](https://www.kcl.ac.uk/artshums/depts/ddh/modules/level7/7aavdm28) convened by [Liliana Bounegru](https://lilianabounegru.org/) and [Jonathan Gray](http://jonathangray.org/) at the [Department of Digital Humanities](https://www.kcl.ac.uk/ddh), [King’s College London](http://kcl.ac.uk/), leading to a set of collaborative group projects with their students and the [European Forest Institute](https://www.efi.int/). The approaches behind these recipes draw on several years of experimentation with images in the context of research and teaching at the [Visual Methodologies Collective](https://visualmethodologies.org/) (Amsterdam University of Applied Sciences), the [Digital Methods Initiative](http://digitalmethods.net/) (University of Amsterdam), [DensityDesign Lab](https://densitydesign.org/) (Politecnico di Milano), the [médialab](https://medialab.sciencespo.fr/) (Sciences Po, Paris) and beyond. You can read more about these approaches in [Colombo, 2019](https://re.public.polimi.it/retrieve/handle/11311/1075861/340493/phd2019_Rampino_Mariani_Colombo.pdf) and [Niederer & Colombo, 2019](http://ojs.uc.cl/index.php/Disena/article/view/151). Further readings can be found in the [visual methods Zotero bibliography](https://www.zotero.org/groups/visual_methods).*
