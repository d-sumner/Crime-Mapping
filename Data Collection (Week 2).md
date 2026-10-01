- First, I collected archival data from Greater Manchester Police. Due to a major ongoing digital infrastructure issue, full updates have been not been available for the last eight years. As such, I am using data spanning the period of June 2018 to June 2019. 
	- This was provided in a compressed archive containing monthly data from every regional force from August 2019 onwards. I used R to collect the relevant data in a new folder.
		- I saved the data in a subfolder of my workspace ("R Workspace/data/police_data"). 
		- Using the tidyverse package "fs", I defined my initial and destination directories ("base_dir" and "dest_dir") and had it create the latter. 
		- I then defined "all_folders" with list.dirs and defined "target_folders" as those between 2018_06 and 2019_05. 
		- I defined "manchester_files" as those in "target_folders" with "manchester" in the name and copied them to dest_dir. 
		- Finally, I included a file count to ensure that I had the three files from each month over a 12 month period.
		![[data_collection_1.png]]
		![[data_collection_2.png]]
- I now had a folder with three separate .csv files for each month. One was for stop and search which, although potentially helpful separately, did not include common details such as a crime ID reference number. I read the remaining datasets into R using readr (along with purrr for bulk file processing and fs for parsing filenames), then used dplyr's "left_join" function to match them up them into a single dataframe along the "Crime ID" axis.
	- ![[rstudio_4TwkAQAvU0.png]]
- A shapefile for Manchester LSOAs was sourced from the UK Data Service's Boundary Data Selector tool.
- 