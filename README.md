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

DATA
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

In this section, descriptive statistics and data visualization techniques will be employed to understand the data better. Statistical inference will also be used to test if the observed values are statistically significant. Some of the key metrics that will be computed include:

Distributions
counts
relationship between species
conservation status of species
observations of species in parks.
Evaluation
Lastly, it's a good idea to revisit the goals and check if the output of the analysis corresponds to the questions first set to be answered (in the goals section). This section will also reflect on what has been learned through the process, and if any of the questions were unable to be answered. This could also include limitations or if any of the analysis could have been done using different methodologies.

Loading the Data
To analyze the status of conservation of species and their observations in national parks, load the datasets into DataFrames. Once loaded as DataFrames the data can be explored and visualized with Python.

In the next steps, Observations.csv and Species_info.csv are read in as DataFrames called observations and species respectively. The newly created DataFrames are glimpsed with .head() to check its contents.

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

Analysis
This section will begin analyzing the data after the initial exploration. First task will be to clean and explore the conservation_status column in species.

The column conservation_status has several possible values:

Species of Concern: declining or appear to be in need of conservation
Threatened: vulnerable to endangerment in the near future
Endangered: seriously at risk of extinction
In Recovery: formerly Endangered, but currently neither in danger of extinction throughout all or a significant portion of its range
In the exploration, a lot of nan values were detected. These values will need to be converted to No Intervention.

Next is to checkout the different categories that are nested in the conservation_status column except for the ones that do not require an intervention. There is both the table and chart to explore below.

For those in the Endangered status, 7 were mammals and 4 were birds. In the In Recovery status, there were 3 birds and 1 mammal, which could possibly mean that the birds are bouncing back more than the mammals.

In conservation
The next question is if certain types of species are more likely to be endangered? This can be answered by creating a new column called is_protected and include any species that had a value other than No Intervention.

Once the new column is created, group by category and is_protected to show the break down of each species type and protection status.

It's easy to see that Birds, Vascular Plants, and Mammals have a higher absolute number of species protected.

Absolute numbers are not always the most useful statistic, therefore it's important to calculate the rate of protection that each category exhibits in the data. From this analysis, one can see that ~17 percent of mammals were under protection, as well as ~15 percent of birds.

Statistical Significance
This section will run some chi-squared tests to see if different species have statistically significant differences in conservation status rates. In order to run a chi squared test, a contingency table will need to be created. The contingency table should look like this:

protected	not protected
Mammal	?	?
Bird	?	?
The first test will be called contingency1 and will need to be filled with the correct numbers for mammals and birds.

The results from the chi-squared test returns many values, the second value which is 0.69 is the p-value. The standard p-value to test statistical significance is 0.05. For the value retrieved from this test, the value of 0.69 is much larger than 0.05. In the case of mammals and birds there doesn't seem to be any significant relationship between them i.e. the variables independent.

The next pair, is going to test the difference between Reptile and Mammal.

The format is again is like below:

protected	not protected
Mammal	?	?
Reptile	?	?
This time the p-value is 0.039 which is below the standard threshold of 0.05 which can be take that the difference between reptile and mammal is statistically significant. Mammals are shown to have a statistically significant higher rate of needed protection compared with Reptiles.

Species in Parks
The next set of analysis will come from data from the conservationists as they have been recording sightings of different species at several national parks for the past 7 days.

The first step is to look at the the common names from species to get an idea of the most prevalent animals in the dataset. The data will be need to be split up into individual names.

Conclusions
The project was able to make several data visualizations and inferences about the various species in four of the National Parks that comprised this data set.

This project was also able to answer some of the questions first posed in the beginning:

What is the distribution of conservation status for species?
The vast majority of species were not part of conservation.(5,633 vs 191)
Are certain types of species more likely to be endangered?
Mammals and Birds had the highest percentage of being in protection.
Are the differences between species and their conservation status significant?
While mammals and Birds did not have significant difference in conservation percentage, mammals and reptiles exhibited a statistically significant difference.
Which animal is most prevalent and what is their distribution amongst parks?
the study found that bats occurred the most number of times and they were most likely to be found in Yellowstone National Park.

Further Research
This dataset only included observations from the last 7 days which prohibits analyze changes over time. It would be curious to see how the conservation status for various species changes over time. Another piece that is missing is the Area of each park, it can be assumed that Yellowstone National Park might be much larger than the other parks which would mean that it would exhibit more observations and greater biodiversity. Lastly, if precise locations were recorded, the spatial distribution of the species could also be observed and test if these observations are spatially clustered.
