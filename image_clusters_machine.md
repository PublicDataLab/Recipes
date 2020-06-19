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

## Download images locally and resize them

1. Install [Tab Save Chrome extension](https://chrome.google.com/webstore/detail/tab-save/lkngoeaeclaebmpkgapchgjdbaekacki)
2. Copy and paste URLs list in Tab Save
3. Download images from URLs list with [Tab Save](https://chrome.google.com/webstore/detail/tab-save/lkngoeaeclaebmpkgapchgjdbaekacki)
4. Go to [Bulk Resize Photos](https://bulkresizephotos.com)
5. Drag images
6. Resize by 50%
7. Unzip folder

## Prepare edges table for Gephi

1. Import csv output of Image tagging tool in Google spreadsheet
2. Rename headers: url → Source; concept → Target; confidence → Weight
3. Export edges csv from Google Spreadsheet

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
5. In the new column “Image”, transform URLs strings into file names:
  a. Sort column “Image” alphabetically
  b. There are different types of urls, but all of them ends with the image name. The goal is to delete every character before the image name with the Find and Replace tool. Proceed by group of similar URLs.
  c. Select column “Image”
  d. Edit → find and replace
  e. Find a string such as `https://pbs.twimg.com/media/` and replace with nothing (be sure that you are doing the search only in a “specific range”, which in this case is the column “Image”)
  f. Repeat for each type of URL, until you only have image names and no URLs
6. Export node csv from Google Spreadsheet

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
9. Export png
10. Import png in [Vectr.com](https://vectr.com/)
11. Annotate custers
