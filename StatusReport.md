# Status Report

## Task Updates 
### Data Cleaning
We were able to successfully import the data into python, and started cleaning the data in python. However, after some beginning work we decided it would be easier to pull the data into OpenRefine to do the initial cleaning. 

We did this for the Met Dataset, where the input was ([MetObjects.csv from the Met's GitHub](https://github.com/metmuseum/openaccess/blob/master/MetObjects.csv)), we removed unnecessary columns and cleaned the Accession Year and Object Title, with history recorded here ([met-OpenRefine-history.json](https://github.com/livialin1/LECT_IS477/blob/main/Data/met-OpenRefine-history.json)), and ending up with ([Cleaned-Met-Objects.csv](https://github.com/livialin1/LECT_IS477/blob/main/Data/Cleaned-Met-Objects.csv)) at the end. 

The Chicago Dataset was imported into python as ([AIofChicago.jsonl](https://github.com/livialin1/LECT_IS477/blob/main/Data/AIofChicago.jsonl)), from the Art Institute of Chicago’s [github](https://github.com/art-institute-of-chicago/api-data/blob/main/getting-started/allArtworks.jsonl). The main cleaning needed was to extract the Accession Year from the Main Reference Number. This cleaning was done in ([Data-Cleaning-Record-Linkage.ipynb](https://github.com/livialin1/LECT_IS477/blob/main/Data/Data-Cleaning-Record-Linkage.ipynb)). 

There is still cleaning to be done in our Artists dataset ([Artists.csv](https://github.com/livialin1/LECT_IS477/blob/main/Data/Artists.csv)), which will likely be performed in OpenRefine as well.

### Record Linkage
After making progress on data cleaning, we began working on the code for record linkage that can be reproduced after final cleaning. For preprocessing, the artist names in all three datasets were standardized, removing any punctuation that was included that could have prevented us from linking the artists. Then, the link datasets and get matched pairs functions were defined to aid the record fusion process. Lastly, the fuse records function was defined and executed to fuse the Art Institute of Chicago and The Metropolitan Museum of Art datasets with the artists dataset, creating two new datasets with information on the artists included in the Art Institute and the artists included in The Met.

## Timeline
<li>November 15th: Prototype Record Linkage - Completed</li>
<li>November 19th: Milestone 3 Status Report - Completed</li>
<li>November 23rd: Data Acquisition & Cleaning - In Progress</li>
<li>November 26th: Schema Integration & Final Record Linkage - In Progress</li>
<li>December 1st: Finish Analysis - Not Started</li>
<li>December 8th: Complete Project Report - Not Started</li>
<br>

While our initial data imports, prototype record linkage code, and our November 19th status report have been completed, we are currently finishing the remaining data cleaning for the Met and artist datasets, which we aim to wrap up by November 23rd. This includes extracting accession dates from record numbers, identifying missing or incorrect data, etc. After all datasets are fully cleaned, we will perform schema integration to align their differing structures and replicate our record linkage workflow on the updated datasets by November 26th. Once the datasets are combined, we will aim to finish the analysis by December 1st, giving us seven days to focus on completing the final project report by December 8th.


## Changes to Project Plan
While we had no visible feedback on the Canvas rubric to implement for our third milestone, we did make a few changes to our approach based on challenges that we encountered as we cleaned the data and performed record linkage.

We now plan to incorporate schema integration into our project which will allow us to more accurately align the different structures and attributes of our three datasets. In our original plan outlined in milestone 2, we had planned to use record linkage, but we first need to standardize corresponding fields across the three datasets before we attempt to combine them. By doing this, we will ensure that all information contained in the Art Institute of Chicago, The Met, and Getty ULAN can be consistently integrated.

We also plan to use OpenRefine, particularly to help us with The Met dataset and its data quality. It is a very large dataset and the accession year formatting is inconsistent, which makes cleaning it challenging. OpenRefine will be useful because it will allow us to identify various inconsistencies in the data, cluster similar values, and apply standardized transformations efficiently.

We have adjusted our overall timeline to accommodate the additional cleaning and integration work that must be completed. We are working through cleaning The Met and Getty artists datasets, and will then apply our linkage process to the finalized data. By making these adjustments, we are improving the consistency and accuracy of our integrated dataset before proceeding with comparative analysis and taking the final steps toward answering our research questions.


## Challenges
A challenge we encountered was that the data was a lot messier than expected. In the Met’s database there were about 4000 missing values (0.82%)  in the Accession Year column. This is a fairly small proportion, but we expected cleaning to be easy using the Object Number, which we expected to have the Accession Year at the beginning. However,  a lot of the Object Numbers deviated from the expected forms. We were able to pull some additional Accession Years from the Credit Line information, which credited the source who gave the object to the museum. We tried to clean this in python initially, but pivoted to using OpenRefine when we realized it was more complex than we thought. 

The cleaning was made more difficult by a lower data quality than we were expecting in both datasets. We were expecting the data to be very standard since the sources (The Art Institute and The Met) are both very esteemed institutions, but there were many deviations within it. 


## Team Member Contributions
### Carlee
Contributed to project planning, evaluated progress, and documented changes to our methodology and overall approach to data cleaning and integration. 

### Erin
Imported and cleaned datasets in python and OpenRefine. Helped organize files in GitHub.

### Livia
Produced record linkage code and described the process in task updates.

### Tiffany
Updated the project timeline to reflect current task statuses and target completion dates. Also outlined the remaining deliverables needed to finalize our pipeline.
