# 🟦 ➡️ 🖼️ Downloading images from a list of Facebook posts

*A recipe for downloading images from a list of Facebook post URLs.*

Collecting data from Facebook with available tools (such as [CrowdTangle](https://www.crowdtangle.com/)) usually results in a list of post URLs. In order to donwload images associated with each post, one needs to click on each link and manually donwload each image. This recipe describes a workaround to get images in batch from a list of Facebook posts.


# 🧱 Inputs

- Export a csv with Facebook posts data from Crowdtangle
- Any list of Facebook posts URLs

# 📃 Steps

## Prepare the list of Facebook posts
  1. Import the csv from Crowdtangle in Google Spreadsheet
  2. Locate the column with post URLs (if you are using CrowdTangle data, it's the column "Link")
  3. Keep this file ready
## Open each post in a Chrome tab
  1. Download and install the Chrome extension [Open Multiple URLs](https://chrome.google.com/webstore/detail/open-multiple-urls/oifijhaokejakekmnjmphonojcfkpbbh/related?hl=en)
  2. Go to the Google spreadsheet tab
  3. Copy the column with post links
  4. Open the extension Open Multiple URLs
  5. Paste in the text box the list of post URLS
  6. ⚠️ Click "Open URLs" ⚠️ (This step will prompt your browser to open A LOT of posts at the same time: Consider to divide your post in chunks) 

![](https://i.imgur.com/GxX5swj.png)

## Download images from open tabs
 1. Download and install the Chrome extension [DownThemAll!](https://chrome.google.com/webstore/detail/downthemall/nljkibfhlpcnanjgbnlnbjecgicbjkge)
  2. Open DownThemAll!
  3. Choose DownThemAll! - All tabs
  4. In the Download Manager, choose "media"
  5. In the "Rapid filter" box, write ".jpg"
  6. Choose the subfolder where you want your images to be downloaded
  7. Click Download

![](https://i.imgur.com/4xq2nd4.png)
