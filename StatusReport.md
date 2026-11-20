# Status Report

## Task Updates 
### Data Cleaning
In progress... trouble with accession year in Met dataset

### Record Linkage
After making progress on data cleaning, we began working on the code for record linkage that can be reproduced after final cleaning. For preprocessing, the artist names in all three datasets were standardized, removing any punctuation that was included that could have prevented us from linking the artists. Then, the link datasets and get matched pairs functions were defined to aid the record fusion process. Lastly, the fuse records function was defined and executed to fuse the Art Institute of Chicago and The Metropolitan Museum of Art datasets with the artists dataset, creating two new datasets with information on the artists included in the Art Institute and the artists included in The Met.

## Timeline
<li>November 15th: Prototype Record Linkage - Completed</li>
<li>November 19th: Milestone 3 Status Report - Completed</li>
<li>November 23rd: Data Acquisition & Cleaning - In Progress</li>
<li>November 26th: Schema Integration & Final Record Linkage - In Progress</li>
<li>December 1st: Finish Analysis - Not Started</li>
<li>December 8th: Complete Project Report - Not Started</li>

While our initial data imports, prototype record linkage code, and our November 19th status report have been completed, we are currently finishing the remaining data cleaning for the Met and artist datasets, which we aim to wrap up by November 23rd. This includes extracting accession dates from record numbers, identifying missing or incorrect data, etc. After all datasets are fully cleaned, we will perform schema integration to align their differing structures and replicate our record linkage workflow on the updated datasets by November 26th. Once the datasets are combined, we will aim to finish the analysis by December 1st, giving us seven days to focus on completing the final project report by December 8th.


## Changes to Project Plan
While we had no visible feedback on the Canvas rubric to implement for our third milestone, we did make a few changes to our approach based on challenges that we encountered as we cleaned the data and performed record linkage.

We now plan to incorporate schema integration into our project which will allow us to more accurately align the different structures and attributes of our three datasets. In our original plan outlined in milestone 2, we had planned to use record linkage, but we first need to standardize corresponding fields across the three datasets before we attempt to combine them. By doing this, we will ensure that all information contained in the Art Institute of Chicago, The Met, and Getty ULAN can be consistently integrated.

We also plan to use OpenRefine, particularly to help us with The Met dataset and its data quality. It is a very large dataset and the accession year formatting is inconsistent, which makes cleaning it challenging. OpenRefine will be useful because it will allow us to identify various inconsistencies in the data, cluster similar values, and apply standardized transformations efficiently.

We have adjusted our overall timeline to accommodate the additional cleaning and integration work that must be completed. We are working through cleaning The Met and Getty artists datasets, and will then apply our linkage process to the finalized data. By making these adjustments, we are improving the consistency and accuracy of our integrated dataset before proceeding with comparative analysis and taking the final steps toward answering our research questions.


## Challenges

## Team Member Contributions
### Carlee

### Erin

### Livia
Produced record linkage code and described the process in task updates.

### Tiffany
