# 🕸️ Co-Hashtag network analysis

*A recipe for analysing co-hashtag networks with Gephi*

This recipe illustrates how to analyse a co-hashtag network with [Gephi](https://gephi.org/). In particular, this recipe shows how to deal with very dense networks (i.e., [hairballs](https://reticular.hypotheses.org/1809)), and it focuses on which strategies may be used to detect clusters of hashtags used together. The recipe touches upon four main strategies, which can and should be used iteratively until clusters of hashtags can be identified, named and interpreted: tweaking layout parameters, resizing nodes based on frequency, filtering nodes, and colouring nodes based on a community detection algorithm.



# 🧱 Inputs

This recipe can be used to work with any co-hashtag network (e.g., from Twitter or Instagram). It assumes you already have a working network file that can be opened with Gephi (.gdf, .gephi, or two tables with edges and nodes data).



# 📃 Steps
The goal of the following procedure is to identify communities of clusters more often used together. Depending on the size and shape of the dataset, different parameters may be needed. Therefore this guide is not meant to be followed literally. You might need to go over these four strategies more than once, adjust parameters, and repeat. Moreover, it is good to embrace [ambiguity as an interpretative asset](https://journals.sagepub.com/doi/full/10.1177/20539517211018488) for visual network analysis.


## Filtering nodes
When working with particularly big networks, you need to filter out some nodes based on various parameters to find a balance between complexity and readability. In this step, we apply different filters that can be used to reduce the size of the network. Depending on your dataset, you might need to filter more or fewer nodes (or not filter any).

  1. The first thing to do is always to delete the query nodes, that is, the hashtags used for collecting the co-hashtag network. These are usually the biggest nodes in the network (as they are connected to most of the other nodes). Go to the Data Laboratory, order the column containing hashtags frequency from high to low, select the first nodes, right-click, and select Delete All.
  2. We could also filter out hashtags with a low frequency. In the Overview panel, find the Filters panel (usually on the right of the interface). In the section Attributes → Range → select the filter called like the column containing hashtags frequency. Drag the filter in the bottom panel. Using the slider at the bottom, set the minimum value of hashtags frequency you want to keep. (you can also write the number).
  3. We then calculate the [Degree](https://en.wikipedia.org/wiki/Degree_distribution) of each node. In the Statistics Panel, select Average Degree and click Run.
  4. We then filter again the network based on the calculated Degree. In the filter panel, go to In the section Attributes → Range → select Degree. Drag the filter in the bottom panel as a subfilter (over the “Drag subfilter here” button). Using the slider at the bottom, select the minimum Degree (you can also write the number)
  5. Select Filter to activate the filters


## Resizing nodes
In this step, we resize nodes based on how many times hashtags occur in the dataset. This step assumes that you have a column in the node table containing hashtags frequency.

1. In the Data Laboratory, select the node tab and locate the column containing hashtags frequency.
2. In Overview, go to the Appearance panel and select Nodes
3. In the Appearance panel, click on the Size icon (three sized circles)
4. In the Appearance panel, click on Ranking
5. From the drop-down menu, select the name of the column containing hashtag frequency
6. Set values for minimum and maximum size: Gephi will map hashtag frequency values against this numerical domain.
7. Click Apply
8. You may want to modify minimum and maximum values and click Apply again.

![](https://i.imgur.com/hLjPLTH.gif)

## Layout parameters
In this step, we apply a layout algorithm for network spatialisation. We will use [ForceAtlas2](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0098679), a force-directed layout, where nodes tend to be pushed apart, and edges attract nodes. The result is a continuous layout that seeks a balance between these two opposing forces. Parameters can be tweaked to improve the layout. For more information on reading force-directed layouts in visual network analysis, you can refer to this [paper](https://arxiv.org/pdf/1905.02202.pdf).


1. In Overview, locate the Layout panel (usually in the right bottom part of the interface)
2. From the drop-down menu, choose a layout algorithm. We will use ForceAtlas2
3. Modifying the parameters in the menu will change the layout behaviour. You can over to each with the mouse to read a detailed description. This guide focuses on the main ones.
4. Scaling and Gravity: these two parameters in combination can control how sparse or dense your network will be. Increase scaling for a more sparse graph. Increase Gravity for a denser graph.
5. LinLog mode: for very connected networks, it may be useful to check this option. The LinLog option modifies how distance is calculated, making it proportional to the logarithm of the distance (instead of linearly proportional). Choosing LinLog mode will result in more visible clusters.
6. After setting all the parameters, click Run to run the layout algorithm. As long as you do not press Stop, Gephi will continue to calculate the position of the nodes, trying to balance the forces of repulsion and attraction.
7. You may want to modify parameters according to the aspect of the network. The process may take some time to be able to identify clusters of nodes.
8. When done, press Stop to stop the layout algorithm.
9. The Prevent overlap function may be used at the end of the process to avoid overlapping nodes. Check the box and click Run again.


  ![](https://i.imgur.com/vlT5Neh.gif)

## Community detection
Community detection techniques are helpful in identifying tightly connected nodes (i.e. clusters of most-used hashtags together). In this step, we apply a community detection algorithm and colour nodes accordingly.


1. In Overview, go to the Statistics panel
2. Run Modularity
3. In the Modularity settings box, you can set resolution value: lower to get more communities and higher to get fewer bigger communities.
4. Click Ok and close the Report box
5. Go to the Appearance panel and select Nodes
6. In the Appearance panel, click on the Color icon (small icon of the colour palette)
7. Choose Partition. From the drop-down menu, select Modularity Class and Apply
