# ⛰️🏂🏾 Hashtag snowballing

*A recipe for finding associated hashtags from a co-hashtag network*

This recipe illustrates a way to streamline the process of hashtag snowballing, that is, starting from one selection of hashtags, choosing other associated hashtags and creating a more extensive hashtags list. This process can be helpful to expand a list of hashtags for querying social media (Twitter or Instagram) to obtain a set of posts. This recipe assumes that you have an initial list of hashtags (provided by domain experts or otherwise compiled) which you have used to collect a co-hashtag network (i.e. network of hashtags used together). This is based on the notion of [“query snowballing” (Rogers, 2018)](https://www.researchgate.net/profile/Richard-Rogers-7/publication/326247474_Issuecrawling_Building_lists_of_URLs_and_mapping_website_networks/links/5b40a7ada6fdccbcf90761ec/Issuecrawling-Building-lists-of-URLs-and-mapping-website-networks.pdf). We will use Gephi and Google Spreadsheet to explore the co-hashtag network looking for other interesting hashtags.



# 🧱 Inputs
This recipe can be used to work with any co-hashtag network (e.g., from Twitter or Instagram). It assumes you already have a working network file that can be opened with Gephi (.gdf, .gephi, or two tables with edges and nodes data).


# 📃 Steps


## Exporting edges table and nodes table from Gephi
1. Open the co-hashtag network with Gephi. Depending on what type of file you have (.gephi, .gdf), you might need to set some import options.
2. Go to the Data Laboratory and select the edges table.
3. Click on Export Table, choose a filename and a folder and save the table in a .csv format.
4. Go to the Data Laboratory and select the nodes table.
5. Click on Export Table, choose a filename and a folder and save the table in a .csv format.


## Importing data in Google Spreadsheet
1. Create a new file in Google Spreadsheet
2. Import nodes table: File → Import → Select nodes table
3. In the import file box, remember to select “Replace current sheet”
4. In the same Spreadsheet, create a new sheet by clicking on the + button on the left bottom part of the interface.
5. In the new sheet, Import edges table: File → Import → Select edges table.
6. In the import file box, remember to select “Replace current sheet.”
7. Rename the two sheets by double-clicking on their name in the bottom part of the interface. Rename them as “nodes” and “edges” to avoid confusion

![](https://i.imgur.com/Gqpvf6H.gif)


## Adding nodes labels to the edges table

The edges table describes connections between hashtags and the strength of those connections (weight), that is, how many times two hashtags have been used together. Depending on how the network dataset is generated, this might change, but most commonly, connections among nodes in the edges table are described by a numerical Id that uniquely identifies a node. Each unique numerical Id is coupled with the hashtag name in the column Label in the nodes table. In this step, we use a spreadsheet function (i.e., vertical lookup) to copy hashtag names from the nodes table to the edges table. It will help to explore the dataset in the next step. Practically, we will add two columns in the edges table: source label and target label, and we will populate these columns with hashtags names from the nodes table.

1. Create a new empty column next to the Source column, and name it “Source Label.”
2. In the first cell of the “Source Label” column, write the following function and press enter:
`=VLOOKUP(A2,nodes!A:B,2,false)`

  (This assumes that the nodes table is in a sheet named “nodes”, and the first two columns (A and B) are the Id column and the Label column.)
3. Drag down the function from the first cell by double-clicking on the right bottom corner of the cell
4. Create a new empty column next to the Target column, and name it “Target Label.”
5. In the first cell of the “Target Label” column, write the following function and press enter:
`=VLOOKUP(C2,nodes!A:B,2,false)`
(This assumes that the nodes table is in a sheet named “nodes”, and the first two columns (A and B) are the Id column and the Label column.)
6. Drag down the function from the first cell by double-clicking on the right bottom corner of the cell

![](https://i.imgur.com/FWcWGF3.gif)

## Exploring hashtags on Google Spreadsheet
Now that we have prepared a table with co-hashtag connections and their strength (i.e. weight), we can explore hashtags and expand the list.

1. Select an interesting hashtag on the Source Label column table and filter the table
2. Order edges table by weight to identify most connected hashtags
3. When you spot an interesting hashtag from the most connected ones, you can copy it into a new sheet
4. Reiterate for multiple hashtags
