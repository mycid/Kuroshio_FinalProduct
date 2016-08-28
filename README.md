# Kuroshio_FinalProduct

All useful scripts here were made for research on the Kuroshio Frontal Extension microplanton community ecology. All work was produced under the supervision of Dr. Sophie Clayton within the Armbrust lab of the Department of Oceanography and is ultimately a freely available product of the University of Washington. 

The files uploaded here have been entirely written and produced by myself, Trevor Eakes. 

All scripts have been incorperated into Rmd. files for ease of use and improved functionality. The resulting html products of each Rmd. files are also included slong with the requisite data which these scripts process, allowing all results to be easily replicated and independently analized by the general scientific community as desired. 

##BY READING THIS DOCUMENT AND DOWNLOADING THE PROVIDED RMD FILES AND CSV FILES YOU WILL BE ABLE TO PRECISELY REPLICATE AND UNDERSTAND ALL FIGURES AND RESULTS.

To immediately view the products of my analyses in R. check out the html files, which include relavent figures. To download and manipulate figures you will need to follow the given instructions, download all necesisary files and run each Rmd. file. 

The scripts included in each Rmd file are designed to work independently of other Rmd codes contained within this repository. However, certain csv files required by a given Rmd. file may themselves be produced by a different Rmd. file. To circumvent any issues that might arise with running Rmd. files in a specific order I have also included all necissary csv. files for all the Rmd. files, even those which are the product of a different Rmd. file. These csv. files are listed at the end of this document. This means that any Rmd. file may be run if you download all csv. files uploaded to this repository and store them in your working directory. If you would like to see how the original data is manipulated, added to, and organized sequentially you may follow the list showing the order by which data.frames are built and analized. 

Almost every line of code within the Rmd. files has a comment which describes it's function and/or specifies it's use (especially in the case of homemade functions). These may be used along with descriptive text included in the Rmd. to understand specific lines or sections of code. 

##A note on Rmd. files: 
Rmd. files are designed to produce html, word, or pdf documents, but are also fully functional scripts which can be ran from within the R. Studio environment. A chunk may be ran individually as with a script or together with all chunks in an Rmd. file. These Rmd. files are seperated by related subject matter. The lines of code within an Rmd. file are together because they rely upon each other and are connected by a central goal like understanding community organization or manipulating phytoplankton dataframes so that they may be easily used in later scripts. Within an Rmd. document you will find metadata, a brief description of the concepts utilized, and sections of code called chunks. Each chunk performs a specific task and is usually described. Chunks are written in sequential order so that they may build upon each other. Within a chunk, individual lines of code have helpful comments and can be run seperately with the run command.  

Finally a script is also included in this repository with functions I have built to streamline the scripts in the Rmd. files. It is called TrevNifftyFunctions.R

#ORDER OF OPERATIONS: 

###1st~ Diversity_DataframeConstruction.Rmd
    This file calculates diversity indices, estimates chlorohpyll concentration for each sample, clusters samples in groups, cleans up the data, and converts microplankton abundance into centiliters instead of liters. All edited dataframes are exported as csv. files automatically with set names. These files will be the basis for future analysis by later Rmd. files.

  REQUIRED: 
-TrevNiffyFunctions.R
-KuroAlldata.csv
-Allbigstuff.csv
-Kuroshio_Phytoplankton.csv
-origin.csv

###2nd~ Species_Spatial_Correlations.Rmd
    Mantel and Partial Mantel tests are calculted from dissimilarity diversity indices and distance matrices and results are plotted. However, Mantel tests are no longer a statistically supported method in this case and the most advanced statistical methods currently available should be employed instead. By replacing all instances of the centitest.csv with centiorigin.csv one can repeat this code using all phytonplanton sampled. 

REQUIRED: 
-Adiv.abiotic.csv
-centitest.csv

###3rd~ Rarefaction_Heatmap.Rmd
    Samples are grouped by salinity and temperature using a clustering method and Rarefaction curves are calculated from seperate groups using the latests developments in ecology. In addition a heat map is made showing total abundance of species for a given group. By replacing all instances of the centitest.csv with centiorigin.csv one can repeat this code using all phytonplanton sampled.

REQUIRED:
-centitest.csv
-Adiv.abiotic

###4th~ Antarctic_Rarefaction.Rmd
    Raw icroplankton abundance data from Yamamoto 1986 is prepared and analized using the rarefaction package iNEXT  as in the Rarefaction_Heatmap.Rmd. Because of the large number of individuals Rarefaction using abundance may not be the apropriate method and is very computationally intensive. This file will take several hours to run on the average computer. 
  Yamamoto, Tamiji. "Small-scale variations in phytoplankton standing stock and productivity across the oceanic fronts in the Southern Ocean." Memoirs of National Institute of Polar Research. Special issue 40 (1986): 25-41.

REQUIRED:
-AntarcticOceandatasheet.csv

###5th~ NeutralTest.Rmd
    A test of neutrality is constructed upon Jabot (2011) research on tests of neutrality. The test is also expanded upon using bootstrap techniques. This script mainly outlines functions for testing Neutrality, simmulating a Neutral community and preparing neutral parameter results produced by the package Tetame 2.1. This script is built with the typical Tetame output format in mind and contains a function to clean up those results for use in further testing. However, other methods of calculating Neutral Parameters may be employed if organized in a readable format.
  Jabot, Franck, and Jérôme Chave. "Analyzing tropical forest tree species abundance distributions using a nonneutral model and through approximate Bayesian inference." The American Naturalist 178.2 (2011): E37-E47.
REQUIRED: 
-centiorigin.csv
-"CleanTetame.csv"

###6th~ TestoftheNeutralTest
    An explenation is provided for various statistical techniques used in scripts designed to simmulate and subsequently test for the occurance of neutrality or not, as defined in the The Neutral Theory of Biodiversity and examples are given. This is a helpful document for better understand the test of neutrality. 

REQURIED: 
-ctfsAbund.csv

###7th~ PlottingforMers contains instructions for creating figures for the MERS journal and some formatting codes. It is not designed to be built as an html or ran as a script. 

##LIST OF CSV FILES AND SOURCES:

KuroAllData.csv
        The original list of abiotic and nutrient measurements for each water sample taken during the sampling cruise. The data is organized with observations for a given sample in columns and samples in rows.
Adiv.abiotic.csv
        The KuroAllData with missing data rows removed and Chloropyll and diversity indices added.
Allbigstuff.csv
        A spreadsheet listing microplankton and picoplankton abundances for major taxonomic phytoplankton groups. Samples are by row and identified by their station and bottle number. Abundances counts are cells/liter.
Kuroshio_Phytoplankton.csv
        A spreadsheet listing microplankton abundances for Diatom and Dinoflagellate species, identified to the species level or, at times, the genus. Identification and abundance counts were done via microscopy techniques. See Clayton et al. 2014. Samples are by row and identified by their station and bottle number. Abundances counts are cells/liter. 
  Clayton, Sophie, Takeyoshi Nagai, and Michael J. Follows. "Fine scale phytoplankton community structure across the Kuroshio Front." Journal of Plankton Research (2014): fbu020.
origin.csv
        A spreadsheet listing microplankton and picoplankton abundances which includes diatoms, dinoflagellates, and other major phytoplankton groups. Major phytoplankton taxa abundance and identity was done via flow cytometry. Samples are by row and identified by their station and bottle number. Abundances counts are cells/liter.
centiorigin.csv
        The origin.csv spreadsheet with cell counts converted to centiliters (the original scale of observation), with rows with missing data removed, and with row numbers added to keep track of things.
centitest.csv
        The Kuroshio_Phytoplankton.csv spreadsheet with cell counts converted to centiliters (the original scale of observation), with rows with missing data removed, and with row numbers added to keep track of things.
centiStation.csv
        The centitest file with abundance counts of microplankton integrated by for all samples in a given station, leaving only an abundance per station. Abundances may not be whole numbers.
CleanTetame.csv
        Neutral paramemters for the Kuroshio calculated in Tetame 2.1 and simplified for ease of use. Samples with challengingly large Theta values were also removed. This cleaned dataframe was made using the CleanupTetame function.
ctfsAbund.csv
        tree abundance data by species, species identity not listed and not included. A test dataset to use for example purposes. The raw data is also included in the csv file ctfsRawData.csv.
AntarcticOceandatasheet.csv
        microplankton diatom and dinoflagellate abundances identified to the species and, at times, genus level. Phytoplankton were identified by microscopy. Samples are grouped by region of the survey. Abundances counts are cells/liter. Data taken from Yamamoto et al. (1986).


    


  
