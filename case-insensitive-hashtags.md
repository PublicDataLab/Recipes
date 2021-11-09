# 🧮 Case insensitive hashtag counting

*How to do case insensitive counts of hashtags or other texts...*

In digital methods research you may sometimes end up with a list of hashtags where small variations in case and capitalisation are counted as separate items, such as in the following table:

| date | item              | value |
| ---- | ----------------- | ----- |
| 2021 | ESEAHM2021        | 179   |
| 2021 | ESEAhm2021        | 46    |
| 2021 | eseahm2021        | 44    |
| 2021 | ESEA              | 16    |
| 2021 | Earth2Air         | 13    |
| 2021 | ESEAHM            | 13    |
| 2021 | ESEAHeritageMonth | 11    |
| 2021 | NIW2021           | 10    |
| 2021 | TheMSGpod         | 8     |
| 2021 | MoongateMix       | 8     |

There are many ways of addressing this with different tools and scripts (e.g. OpenRefine, pandas).

This recipe shows one simple approach using spreadsheets.

# 🧱 Inputs

- A dataset of hashtags where case variations are counted separately (as above)

# 📃 Steps

## Converting hashtags to one case

In order to convert your hashtags to one case you can...

1. Import your dataset into your spreadsheet software
2. Insert new column in which to add hashtags with their cases all changed
3. Give the column a meaningful header (e.g. `lower` if you will change hashtags to lowercase)
4. In the row next to your first item, type `=LOWER()` and add the reference for the first item between the brackets.
    - So if you are adding the new cell in `C2` and your orginal case sensitive hashtag is `B2` then you can type `=LOWER(B2)` in cell `C1`.
    - This syntax should work both in [Excel](https://support.microsoft.com/en-us/office/change-the-case-of-text-01481046-0fa7-4f3b-a693-496795a7a44d) as well as in [Google Sheets](https://support.google.com/docs/answer/3094083?hl=en-GB). While lowercase may be easier to read, you could use uppercase instead if you preferred - the main thing is to get all the hashtags in the same case.
5. Press the enter key to complete and you should see case adjusted hashtag in the new column.
6. Fill down this formula for the rest of the column
    - For example by using [fill down in Excel](https://support.microsoft.com/en-us/office/copy-a-formula-by-dragging-the-fill-handle-in-excel-for-mac-dd928259-622b-473f-9a33-83aa1a63e218) or [autofill in Google Sheets](https://support.google.com/docs/answer/75509?hl=en-GB).

![2021-11-09 12 37 29](https://user-images.githubusercontent.com/1321827/140927840-ab7622c7-d23c-4912-ad7d-2045982daef8.gif)

## Recounting the new column

Now you should have a table something like the following:

| date | item              | lower             | value |
| ---- | ----------------- | ----------------- | ----- |
| 2021 | ESEAHM2021        | eseahm2021        | 179   |
| 2021 | ESEAhm2021        | eseahm2021        | 46    |
| 2021 | eseahm2021        | eseahm2021        | 44    |
| 2021 | ESEA              | esea              | 16    |
| 2021 | Earth2Air         | earth2air         | 13    |
| 2021 | ESEAHM            | eseahm            | 13    |
| 2021 | ESEAHeritageMonth | eseaheritagemonth | 11    |
| 2021 | NIW2021           | niw2021           | 10    |
| 2021 | TheMSGpod         | themsgpod         | 8     |
| 2021 | MoongateMix       | moongatemix       | 8     |

You'll see that the first three hashtags are still separate. How can we combine these?

To recount the new column you can:

1. Create a pivot table
    - There are slightly different ways of doing this in [Excel](https://support.microsoft.com/en-us/office/create-a-pivottable-to-analyze-worksheet-data-a9a84538-bfe9-40a9-a8e9-f99134456576) and [Google Sheets](https://support.google.com/docs/answer/1272900?hl=en-GB).
2. Select your new column (in this case `lower`) for the rows
3. Select the column with the counts (in this case `value`) for the values
4. Summarise and sort by the `SUM` of the column with counts in (in this case `value`)

![2021-11-09 12 59 17](https://user-images.githubusercontent.com/1321827/140929384-a4424a86-83b0-4357-9fff-4368a582e226.gif)

If you have a `date` column and multiple different years for the hashtags, you can also add the date to the pivot table to ensure that multiple years are not merged together.

![2021-11-09 13 07 27](https://user-images.githubusercontent.com/1321827/140929751-16db4ac5-b9c8-4046-8da7-1885b736ef3e.gif)

You should now have a table with case insensitive counts of your hashtags, which you can export into a new csv file for further analysis. 🎊

Note the difference in counts between this new table and the tables above (which is why case insensitive counts can matter for analysis)! 😲

| date | lower             | SUM of value |
| ---- | ----------------- | ------------ |
| 2021 | eseahm2021        | 270          |
| 2021 | esea              | 18           |
| 2021 | eseahm            | 17           |
| 2021 | earth2air         | 13           |
| 2021 | eseaheritagemonth | 12           |
| 2021 | niw2021           | 10           |
| 2021 | beseakidlit       | 9            |
| 2021 | themsgpod         | 8            |
| 2021 | moongatemix       | 8            |
| 2021 | londonpodfest     | 7            |
