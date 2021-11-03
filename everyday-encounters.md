# 🥪 Exploring "everyday" encounters on Twitter

*Some starting points for the study of "everyday encounters" and "ordinary users" on Twitter.*

How can one study "ordinary" or "everyday" users and practices on Twitter? One often finds organisations, celebrities, politicians, journalists, professionals and other "power users" in event- and issue-based keyword and hashtag collections of social media data. But what about those who are not posting in a professional capacity? How might we detect more everyday encounters and situations? What kinds of methods and approaches might be used to study everyday users and practices?

There are different ways in which interest in the everyday can arise. Sometimes organisations wish to see not just their professional colleagues, partner organisations, or public institutions, but everyday publics and end users who are engaging around issues they work on.

It also might be relevant when looking for not just "issue professionals" but also non-professional publics and less prominent "communities of the affected" (e.g. for the purposes of [looking beyond the most engaged](https://ijoc.org/index.php/ijoc/article/view/6407) and the already involved). These users might have other kinds of perspectives, expertise and stakes in the issue.

There is also longstanding interest in social and cultural research in the study of "everyday life" (for histories of this see, e.g. [Highmore, 2002](https://www.routledge.com/Everyday-Life-and-Cultural-Theory-An-Introduction/Highmore/p/book/9780415223034)), everyday self-presentation (e.g. [Goffman, 1956](https://en.wikipedia.org/wiki/The_Presentation_of_Self_in_Everyday_Life), [Thumim, 2012](https://link.springer.com/book/10.1057/9781137265135)), and everyday activities and situations (e.g. [Garfinkel, 1964](https://www.jstor.org/stable/798722)).

There are different ways of understanding everydayness or ordinariness in relation to social media. Sometimes one can consider "ordinary" or "everyday" users as defined by lack of professional (paid) involvement. Some accounts of influencers and micro-celebrity describe how ordinary or everyday users can become well known through their posts about their lives. Everydayness can be considered a feature of either users or posts. It may also be considered **situated** and **relational** (in that someone who uses Twitter to post about their work may nevertheless be considered an "everyday user" in relation to an issue in which they are not professionally involved).

# 🧱 Inputs

- Keyword and/or hashtag based Twitter dataset

# 🐥 Starting points

## Manual analysis of user bios and posting activity

One starting point is to look at the **user bios**. For example, you could take a selection of tweets (e.g. sort by most retweeted) and then look up the bio associated with the users who are posting. Does their bio suggest whether they are using Twitter in personal or professional capacity? Do they mention an affiliation? Does their account suggest they could be an expert in relation to the issue you are looking at (e.g. a scientist, a policy-maker, etc)? Do they provide a URL? Bear in mind that some professional users may have more playful or non-professional personas (e.g. no mention of affiliation and no link).

If they look like or they say they are tweeting in personal capacity, does their **posting activity** support this? Here one might look for a diversity of posting activity (rather than, say, posting focused on particular professional or political themes). As Carolin Gerlitz and Bernhard Rieder [write in their analysis of 1% of Twitter](https://journal.media-culture.org.au/index.php/mcjournal/article/view/620) (2013):

> there is a large, diffuse zone in green that one could perhaps most fittingly describe as “everyday life” on Twitter, where food, birthdays,
funny images, rants, and passion can coexist. This zone – the term cluster suggesting too much coherence – is pierced by celebrity excitement (#arianarikkumacontest) or moments of social banter (#thingsidowhenigetbored, #calloutsomeonebeautiful) leading to high tweet volumes

Manually examining and/or coding user accounts and posting activity may be difficult and time consuming, but exploring this may be a way to learn about the composition of users by ["spending time with your dataset"](http://recipes.publicdatalab.org/documentation).

For example, these digital methods projects coded users according to schemes related to their research questions:
- https://wiki.digitalmethods.net/Dmi/WinterSchool2021Infodemic5G
- https://wiki.digitalmethods.net/Dmi/SummerSchool2020Conspiracytribes

## Indicators of everydayness?

As an alternative or in complement to qualitative analysis of user bios and posting activity, how might one sort, filter and explore Twitter data to identify more everyday activity?

### Less URLs?

Several researcher have suggested that ordinary (or non-professional) users can be characterised by posting proportionately less URLs than professional users.

For example, [Wu et al, 2011](https://dl.acm.org/doi/pdf/10.1145/1963405.1963504) suggest that:

> Ordinary users originate on average only about 6 URLs each, compared with over 1,000 for media users

![Screenshot 2021-11-03 at 16 08 13](https://user-images.githubusercontent.com/1321827/140098364-40ec73db-a86a-47a6-8eb6-04fa5ebab5a8.png)

In a similar vein, [Choudhury et al 2012](https://dl.acm.org/doi/pdf/10.1145/2145204.2145242) say that:

> Ordinary individuals are characterized in these events by a low proportion of URLs in their posts, and a higher proportion of interactive posts that are @-replies to others.

Thus we might try removing tweets with URLs to explore whether this surfaces more everyday accounts, posts, activities, situations or perspectives.

To do this in [OpenRefine](https://openrefine.org/):
- Import csv file as a new project
- Click the down arrow on the column with the full texts of tweets in it (in this case the "Body" column)
- Click "Text filter"
- Type "http" in the field to select tweets with links included
- Click "invert" in order to change the selection to show only those tweets without links included
- Click "export" to download your selection of data, e.g. for further collaborative analysis or interpretation

![2021-11-03 16 19 13](https://user-images.githubusercontent.com/1321827/140101941-3d3ef0dc-7e55-4a7a-9e54-03bcd480e0f2.gif)

Sometimes more everyday users may retweet organisational or professional users. To see what happens if you remove these you could use the same steps as above but adding "RT" to the field instead of "http", or by filtering on "no" in the "is_retweet" column.

### Lower post activity

Other researchers have suggested that more "everyday" users may be characterised by a greater diversity of concerns rather than posts which focus more narrowly on a set of topic or themes.

For example, [Brooker et al, 2018](https://journals.sagepub.com/doi/full/10.1177/2053951718766624) write:

> we take the term “everyday” to refer to Twitter users who are not primarily motivated around any single topic".

They filtered out tweets with an "exceptionally high average tweets-per-day count".

In the case of a dataset on "ash dieback", we may look for users who post about this, but not regularly or in high volumes (which may be an indicator of professional involvement with this issue).

To do this in [OpenRefine](https://openrefine.org/), we could use **facet counts**.

To count the number of times a given poster appears in your dataset you can:
- Import csv file as a new project
- Click the down arrow on the column with the user name of the poster (in this case the "author" column)
- Click "Facet" and then "Text facet"
- Select "count" in the panel on the left hand side to sort by count totals
- Click on the names to see their posts, and "exclude" if you wish to filter them out of your selection
- Click "[X] choices" (where X is the total number of users) in the panel on the left in order to bring up a box with a summary of the totals (which you can copy and paste into a spreadsheet or visualisation software for further analysis)
- Click "export" to download your selection of data (e.g. for further collaborative analysis or interpretation)

With this approach we can go down the list and click include or exclude,  but what if we wanted to select and export all below a certain threshold?

We can use the [General Refine Expression Language syntax for facet counts](https://docs.openrefine.org/manual/grelfunctions#facetcountchoicevalue-s-facetexpression-s-columnname) to filter the data:
- Import csv file as a new project 
- Click the down arrow on the column with the user name of the poster (in this case the "author" column)
- Click "Facet" and then "Custom text facet"
- Type `facetCount(value, "value", "author") == 1` into the text field to see posts from users who appear once in the dataset (you could also try `facetCount(value, "value", "author") <= 2` if you'd like to try users who appear two times or less – and so on)
- Click "true" in the panel on the left hand side to select the items which meet these criteria
- Click "export" to download your selection of data (e.g. for further collaborative analysis or interpretation)

![2021-11-03 17 08 47](https://user-images.githubusercontent.com/1321827/140162841-54cf8c27-e0da-4f87-8ade-43cccd428f5a.gif)

More details about working with facet counts can be found in [this tutorial](https://kb.refinepro.com/2011/11/facet-by-facet-count.html).

### Combining, exploring, experimenting, interpreting...

These are a few starting points. You could also consider exploring by sorting or filtering by engagement counts (e.g. retweets, replies, likes), whether in OpenRefine or in spreadsheet software. You could combine a few of the approaches above. What works depends on the issue you're working on and the size and the contents of the dataset you are working with.

As mentioned above everydayness in Twitter activity can be considered **situated** and **relational**. So attempting to find more everyday users and posts is likely to involve exploration, experimentation and close interpretive work rather than a set of steps which can easily be applied in all cases. You may also not succeed in finding what looks like more everyday activity, which can also tell you something.

If you have suggestions for possible approaches to try out or examples from projects you have worked on you can [email us](https://publicdatalab.org/) or [add an issue to the repository](https://github.com/PublicDataLab/Recipes/issues).
