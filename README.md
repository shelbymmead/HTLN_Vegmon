# HTLN_Vegmon
Vegetation Monitoring overstory, regeneration, and canopy analysis code for Heartland Inventory and Monitoring parks. Code relies on data from the VegMon Access database that is exported as flat files and uploaded in the R script. 
Instructions on how to run this Rms are found in the readme file. 

These are the calculations done:
Calculate Basal Area m2/ha (run for live and dead separately).  
1.	Sort by year, location, species code---
2.	Assign class to each tree: =IF(E2<15,1,IF(E2<25,2,IF(E2<35,3,IF(E2<45,4,(IF(E2>44.9,5))))))
3.	Calculate basal area for each tree =DBH2*(0.00007854)  
4.	Convert each measurement to ha: =(DBH2*(0.00007854))/0.1
5.	Filter snags (D or SD trees: condition code)
6.	Sum all trees for a site by class
7.	Average to park by dividing site basal area by number of sites. Do this for the aggregate of all trees and for each class.
8.	Graph trend over time.
NOTE: if using a subplot fraction: 0.02 is the conversion to ha (not 0.1)

Calculate Density (stems/ha) (run for live and dead separately).  

1.	Filter snags.  Sort by Condition (D or SD not just snags because some dead trees are ID to species.)
2.	Assign class to each tree: =IF(E2<15,1,IF(E2<25,2,IF(E2<35,3,IF(E2<45,4,(IF(E2>45,5))))))
3.	Sum number of stems per size class per site/year (by counting basal area).
4.	Convert sums to area density =sum/0.1  stems/ha
5.	Average stem density for park by taking site stem density/#sites (do this for the aggregate of all trees and for each class)
6.	Graph trend over time.

For species wise analysis
1.	Calculate mean basal area by species, year, site
2.	Calculate percent change  % change from 1st year to current year e.g.,
3.	 
4.	Calculate mean density by species, year, site [a. Count basal area by year, site, species. B. Then scale to ha. C. Calculate mean density by summing density by year site species, then divide by #sites]
5.	Produce table with species BA or density for each year monitored and percent change from 1st read to last read. Arrow graph may be better for this. See sample below. Also Manley woods report 2020.

 


Canopy cover
1.	Filter any -1 values
2.	Multiply observations by 1.04.
3.	Calculate plot mean (N=4 in most cases). 
4.	Calculate Site mean (N=10 in most cases). You can also average the whole pool of values together as long as you’ve converted them to percentage first (*1.04). 
5.	Calculate park mean and CI.
6.	Create table. 
7.	Analyze further if needed.
Regeneration
Cleaning: 
•	Aggregate oaks, hickories, ash, elm to genus level
•	Filter out any -1 values
Aggregate summation: by type (seedlings, small sapling, large sapling)
1.	From vegmon export: Sum all species for a site/year combination.
2.	Scale values by multiplying by a factor of 10.
3.	Calculate mean park density: For each year sun site stems/ha for each class. Divide by #sites. Don’t use the averaging function because if there are 0 values, it won’t calculate properly.
By species-type:
1.	For each species at a site: convert stems to hby a by *10.
2.	Sort by Species for each year. Sum stems/ha by class and divide by #sites. (don’t use average function, won’t account for 0 values or missing species.)
3.	Calculate % change by species and type: 
[(Current year density – first year density)/first year density]*100
Display in table or other format.

