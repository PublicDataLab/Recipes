# 📈 Visualising hashtags over time with rankflow diagrams

*A recipe exploring hashtag usage over time with rankflow diagrams.*

How have different hashtags been used over time? This recipe shows how you can visualise and explore this using the [RankFlow](http://labs.polsys.net/tools/rankflow/) tool and data from the [Twitter Capture and Analysis Toolset (DMI-TCAT)](https://github.com/digitalmethodsinitiative/dmi-tcat). It can be used with hashtag data from other platforms and sources as long as it is formatting in accordance with the templates below.

# 🗄️ Examples

- [What are the most prominent hashtags per day associated with Amazon fires on Twitter (over a 10 day period from 2019-08-01 to 2020-03-08)?](https://i.imgur.com/rYYNZZu.jpg)

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


# 🧱 Inputs from TCAT

- Export “hashtag frequency” data from TCAT

# 📃 Steps

1. Export “hashtag frequency” data from TCAT
  - 🤔 *Think carefully when you choose the range of dates. Why these particular dates? Does anything notable happen within this period? Or is it an arbitrary selection of dates (e.g. X days, a week, a month)?*
  - *Remember that what you will see is not the overall use of these hashtags over the period you have chosen, but their frequency of occurrence within the dataset that you are starting with and how certain hashtags co-occur with the original keywords and/or hashtags that you have chosen.*
2. Make a copy of the CSV file and remove the top row
  - *It is good practice to keep the original TCAT export somewhere for reference (e.g. in a "TCAT exports" folder) and to make a copy that you can edit and work with.*
  - *The top row of the CSV file will contain something like "Hashtag frequency for [dataset name] from [start date] to [end date]". If you directly import the TCAT export directly to OpenRefine it may not import correctly, so you can delete the top row. The new top row should contain three headers for your data: "date", "frequency" and "hashtag".*
3. Normalise data and harmonise cases of hashtags using OpenRefine.
  - *Sometimes hashtags may have different cases which may mean they are counted separately in graphs created using the RankFlow tool. For example, #AmazonFires, #amazonfires, #Amazonfires and #AmaZonFirEs might be treated as separate hashtags. To prevent this we can transform the hashtags so they are all in the same case.*
  - *Download and install [OpenRefine](https://openrefine.org/). After installation it should open up a browser window.*
  - *Click "choose files" and find the CSV file that you have downloaded from TCAT and then click "Next". (CSV stands for ["comma-separated values"](https://en.wikipedia.org/wiki/Comma-separated_values) and this is a simple, widely used format for storing tabular data and moving it between different applications and services.)*
  - *Check that the data has been "parsed" correctly and then click "Create Project".*
  - *Once the data has loaded you can click the small down arrow next to the column containing your hashtags and click "Edit cells" > "Common transforms" > "To lowercase".*
  - *Finally you can click "Export" in the top right hand corner and select "Comma separated value" to re-export the data as a CSV file that you can then work with in a spreadsheet.*
    ![](https://i.imgur.com/nyLW15F.gif)
4. Re-organise data into columns of top hashtags per day for 10 day period.
  - *By default the TCAT export will have three columns: "date", "frequency" and "hashtag". These need to reformatted as per the [example provided with the RankFlow tool](http://labs.polsys.net/tools/rankflow/). The TCAT export should be sorted by date and by frequency.*
  - *You can import your data to Google Sheets for collaborative work. Keep your original TCAT export in sheet 1. You can use filters to select each of the days and then obtain the most frequently used hashtags per day and copy them into sheet 1 as per the data format required for the RankFlow tool. For an example of this see [this spreadsheet](https://docs.google.com/spreadsheets/d/1LZ17LekrMHDVxY87AoAZqa_9kPgL47E2vK36pXXSnrE/edit?usp=sharing), [this screen recording](https://i.imgur.com/9MYEoFn.mp4) and the following screenshots.*
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
  - *In this example we will be making a visualisation which has a width of 2000, and height of 1000, specifying these in the boxes and then clicking "generate visualisation".*
  - *Click "show labels" to display the hashtags in the visualisation.*
  - *Once your visualisation is finalised, you can click "generate SVG of current visualisation".*
  - *For finishing touches, you can also add annotations and a legend using graphics editing software.*
    ![](https://i.imgur.com/SY9BhwD.gif)


# 🐙 Inspiration, acknowledgments and contributors


*This recipe documents how to use the [RankFlow tool](http://labs.polsys.net/tools/rankflow/) created by [Bernhard Rieder](http://thepoliticsofsystems.net/about/) and the [Twitter Capture and Analysis Toolset (DMI-TCAT)](https://github.com/digitalmethodsinitiative/dmi-tcat) from the [Digital Methods Initiative](https://digitalmethods.net/), University of Amsterdam. It draws on materials from the 2019-2020 edition of a module on [Digital Methods for Internet Studies: Concepts, Devices and Data](https://www.kcl.ac.uk/artshums/depts/ddh/modules/level7/7aavdm28) convened by [Liliana Bounegru](https://lilianabounegru.org/) and [Jonathan Gray](http://jonathangray.org/) at the [Department of Digital Humanities](https://www.kcl.ac.uk/ddh), [King’s College London](http://kcl.ac.uk/), as well as subsequent collaborations with [Gabriele Colombo](https://densitydesign.org/person/gabriele-colombo/) at [DensityDesign Lab](https://densitydesign.org/) and the [European Forest Institute](https://www.efi.int/).*
