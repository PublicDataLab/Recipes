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

1. Import your dataset into your spreadsheet software
2. Insert new column in which to add hashtags with their cases all changed
3. Give the column a meaningful header (e.g. `lower` if you will change hashtags to lowercase)
4. In the row next to your first item, type `=LOWER()` and add the reference for the first item between the brackets.
  - So if you are adding the new cell in `C2` and your orginal case sensitive hashtag is `B2` then you can type `=LOWER(B2)` in cell `C1`.
  - This syntax should work both in [Excel](https://support.microsoft.com/en-us/office/change-the-case-of-text-01481046-0fa7-4f3b-a693-496795a7a44d) as well as in [Google Sheets](https://support.google.com/docs/answer/3094083?hl=en-GB). While lowercase may be easier to read, you could use uppercase instead if you preferred - the main thing is to get all the hashtags in the same case.
5. Press the enter key to complete and you should see case adjusted hashtag in the new column.
6. Fill down this formula for the rest of the column
   - For example by using [fill down in Excel](https://support.microsoft.com/en-us/office/copy-a-formula-by-dragging-the-fill-handle-in-excel-for-mac-dd928259-622b-473f-9a33-83aa1a63e218) or [autofill in Google Sheets](https://support.google.com/docs/answer/75509?hl=en-GB).
