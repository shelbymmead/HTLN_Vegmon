PARKOverstory INSTRUCTIONS

written by S. Mead 2025

************************************************

1. Make a copy of this entire folder and move it to your desired location to perform analysis (i.e. analysis folder on N drive)
2. Rename your folder with park code [i.e. WICRoverstory]
3. Open the folder, and copy your clean csv data files into the "data" subfolder
	a. The clean overstory data MUST be titled Park code + overstory.csv [i.e. WICRoverstory.csv]
	b. The clean canopy data MUST be titled Park code +canopy.csv [i.e. WICRcanopy.csv]
	c. The clean regeneration data MUST be titled Park code+ regeneration.csv [i.e. WICRregeneration.csv]
	d. tlu_Species must be exported from the database and copied here as a csv. Do not change name.
4. In your folder, click on VegmonR.Rproj to open the project in R Studio
5. Once R Studio is open, find the files tab and open the latest version of OverstoryRegenCanopy.Rmd
6. At the very top of the R markdown document you will need to edit the following line of code:
	a. LINE 9- park: your park code [i.e. park: WICR]
6. Click Ctlr+Alt+R or Navigate to Run>Run All to run the entire Rmarkdown script
7. If the script runs without errors, the "Graphs" and "Tables" in your file will be populated with you exports

*************************************************

Some things to double-check if you encounter errors running the R script:

This code was created based on datasets that were cleaned in excel after being exported from Access. Data exported directly from access will encounter errors (tlu_Species is an EXCEPTION and should be pulled directly from Access database). Check that your clean datasets include the following columns: 
YOURPARKcanopy.csv: Year, LocationID, Plot, SumOfValue 1,SumOfValue 2, SumOfValue 3, SumOfValue 4
YOURPARKoverstory.csv: ParkCode, Year, Year2, LocationID, SpeciesCode, AcceptedSpecies, Condition, DBH, Site, Year_Site
YOURPARKregeneration.csv: Year, LocationID, AcceptedSpecies,USDA_CName, Family, FamilyCommonName, Origin, SumOfSeedling, SumOfSmallSapling, SumOfLargeSapling,GrowthHabit
If column names have changed in the Access database or your clean imports there will be errors. 

You might not have some of the required packages installed. Run the following lines of code: 
install.packages("tidyverse")
install.packages("ggplot2")
install.packages("boot")
install.packages("purr")

Check that your data is named correctly (see step 3 above) including capitalization, and saved in the "data" subfolder as csv files

Check that you have correctly entered the park code and sites in the params of the code (see step 6).

