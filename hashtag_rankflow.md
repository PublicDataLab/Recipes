# 📈 Visualising hashtags over time with rankflow diagrams

*A recipe exploring hashtag usage over time with rankflow diagrams.*

How have different hashtags been used over time? This recipe shows how you can visualise and explore this using the [RankFlow](http://labs.polsys.net/tools/rankflow/) tool and data from the [Twitter Capture and Analysis Toolset (DMI-TCAT)](https://github.com/digitalmethodsinitiative/dmi-tcat). It can be used with hashtag data from other platforms and sources as long as it is formatting in accordance with the templates below.

# 🗄️ Examples

- What are the most prominent hashtags per day associated with Amazon fires on Twitter (over a 10 day period from 2019-08-01 to 2020-03-08)?
  - [Rankflow with top 100 hashtags](https://i.imgur.com/rYYNZZu.jpg)
  - [Rankflow with top 10 hashtags](https://i.imgur.com/5HZGyXp.png)

![](https://i.imgur.com/rYYNZZu.jpg)

Findings:

- There are different (sometimes competing) ways of articulating the Amazon fires issue on Twitter with different affective dimensions and invitations to action (e.g. “pray” vs “save” vs “act”). For example, the most popular hashtag is initially #prayforamazonia (days 1-2), then #savetheamazon (day 3), before moving onto the more general framings of #amazonfires (days 4-8, 10) and #amazonrainforest (day 9).
- There is a substantive drop-off in public attention over the course of the 10 day period. For example, there is a twenty fold drop in frequency of most engaged with hashtag on 25th August #prayforamazonia (34,216) to most engaged with hashtag on 1st September #amazonrainforest (1,662). This gives a sense of the rhythm and temporality of online engagement around the hashtags.
- The hashtags indicate some of the many different ways in which the Amazon fires come to matter for different actors in different settings, and the materials and relations through which attention is invited and organised.
- One can observe a wide variety of associated issues, including Amazon rainforest fires as:
  - Climate issue (e.g. #climateaction, #climatecrisis, #climateemergency, #extinctionrebellion, #unitebehindthescience, #greennewdeal, #malizia)
  - Environmental issue (e.g. #nature, #biodiversity)
  - Food issue (e.g. #beef, #vegan, #govegan, #meatfreelaborday)
  - International/transnational political issue (e.g. #G7, #g7summit, #g7biarritz, #Macron, #macronlies, #bolivia, #sosbolivia, #buenosaires)
  - Faith issue (e.g. #popefrancis)
  - Brazilian political issue (e.g. #bolsonaro, #bolsonaroensueur, #brazil, -#illegitimatepresident, #forabol卐onaro)
  - US political issue (e.g. #trump, #yanggang, #fauxcahontas)
  - Local community issue (#indigenous
  - Celebrity issue (e.g. #armyhelptheplanet, #army, #방탄소년단, #boywithluv, #bts, #leonardodicaprio, #armypurpleearth)
  - Consumer issue (e.g. #fashionblogger
  - News issue (e.g. #msnbc)
  - Fact-checking/misinformation issue (e.g. #fakenews)


# 🧱 Inputs

- Export “hashtag frequency” data from Twitter (e.g. from TCAT, 4CAT, twarc or other Twitter data collection tools)

# 📃 Steps

1. Export “hashtag frequency” data
  - 🤔 *Think carefully when you choose the range of dates. Why these particular dates? Does anything notable happen within this period? Or is it an arbitrary selection of dates (e.g. X days, a week, a month)?*
  - *Remember that what you will see is not the overall use of these hashtags over the period you have chosen, but their frequency of occurrence within the dataset that you are starting with and how certain hashtags co-occur with the original keywords and/or hashtags that you have chosen.*
2. Make a copy of the CSV file and remove the top row
  - *It is good practice to keep the original Twitter data export somewhere for reference (e.g. in a "data exports" folder) and to make a copy that you can edit and work with.*
  - *The top row of the CSV file will contain something like "Hashtag frequency for [dataset name] from [start date] to [end date]". If you directly import the Twitter data export directly to OpenRefine it may not import correctly, so you can delete the top row. The new top row should contain three headers for your data: "date", "frequency" and "hashtag".*
3. Normalise data and harmonise cases of hashtags.
  - *Sometimes hashtags may have different cases which may mean they are counted separately in graphs created using the RankFlow tool. For example, #AmazonFires, #amazonfires, #Amazonfires and #AmaZonFirEs might be treated as separate hashtags. To prevent this we can transform the hashtags so they are all in the same case. [Here](/case-insensitive-hashtags.md) is a recipe showing how to do this with spreadsheets or OpenRefine.*
4. Re-organise data into columns of top hashtags per day for 10 day period.
  - *The Twitter data export will likely have columns such as "date", "frequency" and "hashtag". These need to reformatted as per the [example provided with the RankFlow tool](http://labs.polsys.net/tools/rankflow/). The Twitter data export should be sorted by date and by frequency.*
  - *You can import your data to Google Sheets for collaborative work. Keep your original Twitter data export in sheet 1. You can use filters to select each of the days and then obtain the most frequently used hashtags per day and copy them into sheet 1 as per the data format required for the RankFlow tool. For an example of this see [this spreadsheet](https://docs.google.com/spreadsheets/d/1LZ17LekrMHDVxY87AoAZqa_9kPgL47E2vK36pXXSnrE/edit?usp=sharing), [this screen recording](https://i.imgur.com/9MYEoFn.mp4) and the following screenshots.*
  - *How many hashtags you include will depend on your research question and on the dataset. The more hashtags you include the harder it may be to see them in your visualistion (e.g. 1000 will likely be too many to see clearly!). If you only include a few hashtags it may be harder to see change over time (e.g. if you only include 5 hashtags, then you might not be able to see the ries and fall of other hashtags which are not amongst these most prominent set). You may also wish to experiment and iterate a bit - to see what kinds of thresholds result in a clear, readable visualisation.*
  - *Say you wanted to select the top 100 hashtags per day and copy and paste them into ten columns. It can take some patience to do this manually. As an optional step to speed things you can use a Google Sheets macro to select the correct number of cells for copying and pasting. Click "Tools" > "Script Editor" and then copy and paste the script below into the editor. Then click "Tools" > "Import" and choose "Select200items". When you run this it will select two columns of 100 items from whichever cell the cursor is in. The numbers can be adjusted to fit your inquiry. You can speed things up even more by clicking "Tools" > "Macros" > "Manage Macros" and creating a keyboard shortcut.*
    ```
    /** @OnlyCurrentDoc */
    function Select200items() {
      var spreadsheet = SpreadsheetApp.getActive();
      spreadsheet.getCurrentCell().offset(0, 0, 100, 2).activate();
    };
    ```
    ![](https://i.imgur.com/HyYkYLM.png)
    ![](https://i.imgur.com/EBaLrOF.png)
5. Create visualisation using RankFlow tool
  - *Once you have formatted your data, you can copy and paste the data into the [RankFlow tool](http://labs.polsys.net/tools/rankflow/).*
  - *In this example we will be making a visualisation which has a width of 2000, and height of 1000, specifying these in the boxes and then clicking "generate visualisation". 2000x1000 is just an example, you may want the visualisation to be bigger or smaller or different dimensions depending on its size and what you would like to study.*
  - *Click "show labels" to display the hashtags in the visualisation.*
  - *Once your visualisation is finalised, you can click "generate SVG of current visualisation".*
  - *For finishing touches, you can also add annotations and a legend using graphics editing software.*
    ![](https://i.imgur.com/SY9BhwD.gif)

# 🐙 Inspiration, acknowledgments and contributors


*This recipe documents how to use the [RankFlow tool](http://labs.polsys.net/tools/rankflow/) created by [Bernhard Rieder](http://thepoliticsofsystems.net/about/) and the [Twitter Capture and Analysis Toolset (DMI-TCAT)](https://github.com/digitalmethodsinitiative/dmi-tcat) from the [Digital Methods Initiative](https://digitalmethods.net/), University of Amsterdam. It draws on materials from the 2019-2020 edition of a module on [Digital Methods for Internet Studies: Concepts, Devices and Data](https://www.kcl.ac.uk/artshums/depts/ddh/modules/level7/7aavdm28) convened by [Liliana Bounegru](https://lilianabounegru.org/) and [Jonathan Gray](http://jonathangray.org/) at the [Department of Digital Humanities](https://www.kcl.ac.uk/ddh), [King’s College London](http://kcl.ac.uk/), as well as subsequent collaborations with [Gabriele Colombo](https://densitydesign.org/person/gabriele-colombo/) at [DensityDesign Lab](https://densitydesign.org/) and the [European Forest Institute](https://www.efi.int/).*
