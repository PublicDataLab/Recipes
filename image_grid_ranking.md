# 🧮🔝 Image grid, by ranking and date, annotated

*Visualizing top ten images per day (week, month, year)*

This approach may be used to study how the visual representations of a particular issue changes overtime. By creating a grid in which columns represent time frames and rows represent engagement values, one is able to observe the change overtime (or lack thereof) in the type of images that create more engagement. This approach should be used with a rather small set of images (no more than 10 images per time frame).

# 🗄️ Examples

- [Top ten images per year for the query [“climate change”] on Google.com](https://docs.google.com/spreadsheets/d/1B5Waf-I1sXvrXWVZUdm14lyBIvKdxy_RBCXp_-3Nly4/edit?usp=sharing)

# 🧱Input from TCAT

– “Media frequency” (grouped per hour, day, week, month, or year)

# 📃 Steps

1. Open csv with media frequency and urls in Google spreadsheet
2. Sort by media frequency
3. Filter by first time frame (e.g. month of August 2019)
4. Copy first 10 urls in a new sheet (in column A)
5. Filter by second time step (e.g. month of September 2019)
6. Repeat steps 4 and 5 for each time slot (with new column for each set)
7. For each column: create an empty column, fill it with formula `=IMAGE(URL)`
8. Hide columns with URLs, only showing columns with images
9. Style grid (add time stamps in headers, define colors and fonts for headers, set the size of columns and rows)
10. Make a screenshot
11. Annotate screenshot with [Vectr.com](https://vectr.com/)

![](https://i.imgur.com/dvsRJZN.gif)
