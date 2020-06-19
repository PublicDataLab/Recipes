# 🌅🥞 Image stacks, by ranking, compared

*Comparing differences in formats and styles across (small) collection of images*

This approach may be used to synthesize small set of images, so as to facilitate comparison among them. By overlaying images on top of each other, one is able to produce a “visual summary” that can be used to compare multiple collections. The order in which images are placed in the stack is also relevant: images on top will be more visible than the ones on the bottom. For this reason, this approach works better with ranked images (e.g. most retweeted to less retweeted). One application could be to produce images stacks with top 10 retweeted images per month (or day), and then compare them.

# 🗄️ Examples
- [Climate Change platform visual vernaculars](https://wiki.digitalmethods.net/Dmi/MakingClimateVisible#INTRODUCTION)
Comparing smart cities architecture

# 🧱Input from TCAT
- “Media frequency”, grouped per hour, day, week, month, or year

# 📃 Steps

1. Open data with Google Spreadsheet
2. Sort data by media frequency
3. Filter data by time (e.g. images tweeted on August 2019)
4. Copy only first 10 images in a new sheet
5. Export from new sheet a csv with URLs list
6. Install [Tab Save Chrome](https://chrome.google.com/webstore/detail/tab-save/lkngoeaeclaebmpkgapchgjdbaekacki) extension
7. Copy and paste URLs list in Tab Save
8. Download images from URLs list with [Tab Save](https://chrome.google.com/webstore/detail/tab-save/lkngoeaeclaebmpkgapchgjdbaekacki)
9. Import image in [Vectr.com](https://vectr.com/) (start from less retweeted)
10. Set image opacity to 10%
11. Repeat step 7 and 8 for all images (be sure to respect the ranking, you can check that in the layer panel on the right; resize images so they are all of the same size)
12. Export stack (jpg)
13. Repeat from 3 to 9, in order to produce stacks from different months.
