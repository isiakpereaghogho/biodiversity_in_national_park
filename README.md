# biodiversity_in_national_park
This project is about biodiversity in national parks

**INTRODUCTION**

This project is about biodiversity in national parks and has data from the National Parks Service about endangered species in different parks. It will analyze biodiversity data from the National Parks Service, particularly around various species observed in different national park locations. This project will scope, analyze, prepare, plot data, and seek to explain the findings from the analysis.

**SCOPE**

PROJECT GOALS

 This project will perform a biodiversity analysis for the National Parks Service. Some of the goals of this project includes:
-  To perform some analysis on the conservation statuses of these species and investigate if there are any patterns or themes to the types of species that become endangered.
-  To ensure the survival of at-risk species, to maintain the level of biodiversity within their parks.
-  To understand characteristics about the species and their conservations status, and those species and their relationship to the national parks.

Here are a few questions to  be discussed in this project:


What is the distribution of conservation status for species?

Are certain types of species more likely to be endangered?

Are the differences between species and their conservation status significant?

Which animal is most prevalent and what is their distribution amongst parks?

Which species were spotted the most at each park?


**DATA**


This project has two data sets that came with the package. The first csv file has information about each species and another has observations of species with park locations. This data will be used to analyze the goals of the project.

species_info.csv - contains data about different species and their conservation status

observations.csv - holds recorded sightings of different species at several national parks for the past 7 days.

The datasets provided have the following columns of data:

species_info.csv:

category - class of animal
scientific_name - the scientific name of each species
common_name - the common names of each species
conservation_status - each species’ current conservation status

observations.csv:

scientific_name - the scientific name of each species
park_name - Park where species were found
observations - the number of times each species was observed at park

**ANALYSIS**


In this section, descriptive statistics and data visualization techniques will be employed to understand the data better. Statistical inference will also be used to test if the observed values are statistically significant.

Loading the Data
To analyze the status of conservation of species and their observations in national parks, load the datasets into DataFrames. Once loaded as DataFrames the data can be explored and visualized with Python.

In the next steps, Observations.csv and Species_info.csv are read in as DataFrames called observations_df and species_df respectively. 

species
The species_info.csv contains information on the different species in the National Parks. The columns in the data set include:

category - The category of taxonomy for each species
scientific_name - The scientific name of each species
common_names - The common names of each species
conservation_status - The species conservation status
Data Characteristics
Next, there will be a check for the dimensions of the data sets, for species there are 5,824 rows and 4 columns while observations has 23,296 rows and 3 columns.

Next a count of the number of observations in the breakdown of the categories in conservation_status is done. There are 5,633 nan values which means that they are species without concerns. On the other hand there are 161 species of concern, 16 endangered, 10 threatened, and 4 in recovery.

Note: In most cases coming across nan values must be treated carefully, but the absence of data here means that these species are not under any conservation status.

observations
The next section looks at observations data. The first task is to check the number of parks that are in the dataset and there are only 4 national parks.

Here are the total number of observations logged in the parks, there are 3,314,739 sightings in the last 7 days... that's a lot of observations!


**RESULTS AND CONCLUSION**  


The project was able to make several data analysis and visualizations about the various species in four of the National Parks. I was also able to answer some of the questions posed in the goals of the project:

What is the distribution of conservation status for species?

Total species rows: 5,824.

Conservation status counts: No Status: 5,633 species (96.72%) Species of Concern: 161 species (2.76%) Endangered: 16 species (0.27%) Threatened: 10 species (0.17%) In Recovery: 4 species (0.07%)

A bar chart of this distribution was generated.

Interpretation: The vast majority of species entries have no conservation status recorded in this dataset. This large missingness strongly affects any downstream inference about the frequency of statuses.

Are certain types of species more likely to be endangered?

Proportions of Endangered by category were computed where applicable. Top proportions (if Endangered exists): e.g., Mammal and Birds had the highest endangered entries.

Are the differences between species and their conservation status significant?

I created a contingency table (species category × conservation_status_filled) ran a Chi-square test of independence on the contingency table: Test result: chi2 and p_value were computed. While mammals and Birds gave significant difference in conservation percentage, mammals and fish exhibited a statistically significant difference as well as fish and bird.

Which animal is most prevalent and what is their distribution amongst parks?

Most observed species (common name): I extracted the top species name from the observations dataset. I created a bar chart showing that species' observations across parks (top parks displayed). The study found that bats occurred the most number of times and they were most likely to be found in Yellowstone National Park.

Species spotted the most at each park? 

For each park, I found the species with the maximum total observations.

**FURTHER RESEARCH AND RECOMMENDATION**


Massive missingness in conservation_status (96.7% Not Listed).
This will bias conclusions. I recommend enriching the dataset with authoritative conservation status sources (IUCN Red List, national lists) for missing species to have robust results.

Species name matching: I used scientific_name as the join key. 

Re-run the association test excluding 'No status' and present adjusted results.

Time-trend analyses if you have temporal data:
This dataset only included observations from the last 7 days which prohibits analyze changes over time. It is recommended to see how the conservation status for various species changes over time. 

Another piece is Area of each park. Maps of species hotspots if park coordinates are available, it can be assumed that Yellowstone National Park might be much larger than the other parks which would mean that it would exhibit more observations and greater biodiversity. 
