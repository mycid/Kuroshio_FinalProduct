# Kuroshio_FinalProduct
All useful scripts here were made for research on the Kuroshio Frontal extension microplanton ecology. All work was produced under the supervision of Dr. Sophie Clayton within the Armbrust lab of the Department of Oceanography and is ultimately a freely available product of the University of Washington. 

The files uploaded here have been entirely written and produced by myself, Trevor Eakes. 

All scripts have been incorperated into Rmd files for ease of use and improved functionality. The resulting html products of each Rmd files are also here included. Also included is the requisite data which these scripts process so that all results may be easily replicated and independently analized by the general scientific community as desired. 

BY READING THIS DOCUMENT AND DOWNLOADING THE PROVIDED RMD FILES AND CSV FILES YOU WILL BE ABLE TO PRECISELY REPLICATE AND UNDERSTAND ALL FIGURES AND RESULTS.

To immediately view the products of my analyses in R check out the html files, which include relavent figures. To download and manipulate figures you will need to follow the given instructions, download all necesisary files and run each Rmd file. 

The scripts included in each Rmd file are designed to work independently of other Rmd codes contained within this repository. However, certain csv files required by a given Rmd file may themselves be produced by a different Rmd file. To circumvent any issues that might arise with running Rmd files in a specific order I have also included all necissary csv. files for all the Rmd files, even those which are the product of a given Rmd file. This means that any Rmd file may be run if you download all csv files uploaded to this repository and store them in your working directory. If you would like to see how the original data is manipulated, added to, and organized sequentially you may follow the list showing the order by which data.frames are built and analized. 

Almost every line of code within the Rmd files has a comment which describes it's function and/or specifies it's use (especially in the case of homemade functions). These may be used along with descriptive text included in the Rmd to understand specific lines or sections of code. 

A note on Rmd. files: 
Rmd. files are designed to produce html, word, or pdf documents but are also fully functional scripts which can be ran from within the R Studio environment. A chunk may be ran individually as with a script or together with all chunks in an Rmd. file. These Rmd. files are seperated by related subject matter. The lines of code within an Rmd. file are together because they rely upon each other and are connected by a central goal like understanding community organization or manipulating phytoplankton dataframes so that they may be easily used in later scripts. Within an Rmd. document you will find metadata, a brief description of the concepts utilized, and sections of code called chunk. Each chunk performs a specific task and is described. Chunks are written in sequential order so that they may build upon each other. Within a chunk individual lines of code have helpful comments.  

Finally a script is also included in this repository with functions I have built to streamline the scripts in the Rmd. files. It is called TrevNifftyFunctions.R

ORDER OF OPERATIONS: 

1st Diversity_DataframeConstruction.Rmd
This file calculates diversity indices, estimates chlorohpyll concentration for each sample, clusters samples in groups, cleans up the data, and converts microplankton abundance into centiliters instead of liters. All edited dataframes are exported as csv. files automatically with set names. These files will be the basis for future analysis by later Rmd. files.

  REQUIRED: 
-TrevNiffyFunctions.R
-KuroAlldata.csv
-Allbigstuff.csv
-Kuroshio_Phytoplankton.csv
-origin.csv

2nd Species_Spatial_Correlations.Rmd
Mantel and Partial Mantel tests are calculted from dissimilarity diversity indices and distance matrices and results are plotted. However, Mantel tests are no longer a statistically supported method in this case and the most advanced statistical methods currently available should be employed instead. By replacing all instances of the centitest.csv with centiorigin.csv one can repeat this code using all phytonplanton sampled. 

REQUIRED: 
-Adiv.abiotic.csv
-centitest.csv

3rd Rarefaction_Heatmap.Rmd
Samples are grouped by salinity and temperature using a clustering method and Rarefaction curves are calculated from seperate groups using the latests developments in ecology. In addition a heat map is made showing total abundance of species for a given group. By replacing all instances of the centitest.csv with centiorigin.csv one can repeat this code using all phytonplanton sampled.

REQUIRED:
-centitest.csv
-Adiv.abiotic

4th Antarctic_Rarefaction.Rmd
Raw icroplankton abundance data from Yamamoto 1986 is prepared and analized using the rarefaction package iNEXT  as in the Rarefaction_Heatmap.Rmd. Because of the large number of individuals Rarefaction using abundance may not be the apropriate method and is very computationally intensive. This file will take several hours to run on the average computer. 
Yamamoto, Tamiji. "Small-scale variations in phytoplankton standing stock and productivity across the oceanic fronts in the Southern Ocean." Memoirs of National Institute of Polar Research. Special issue 40 (1986): 25-41.

REQUIRED:
-AntarcticOceandatasheet.csv

5. NeutralTest.Rmd
A test of neutrality is constructed built upon Jabot 2011's research on tests of neutrality. The test is also expanded upon using bootstrap techniques. 
REQUIRED: 
-centiorigin.csv
-"CleanTetame.csv"

6th TestoftheNeutralTest
An explenation is provided for various statistical techniques used in scripts designed to simmulate and subsequently test for the occurance of neutrality or not, as defined in the The Neutral Theory of Biodiversity and examples are given. This is a helpful document for better understand the test of neutrality. 

REQURIED: 
-ctfsAbund.csv

7th PlottingforMers contains instructions for creating figures for the MERS journal and some formatting codes. It is not designed to be built as an html or ran as a script. 

LIST OF CSV FILES AND SOURCES:

  
