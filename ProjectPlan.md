# Overview
The overall goal of our project is to construct a unified database combining open-access datasets from the Art Institute of Chicago and The Metropolitan Museum of Art (The Met) in New York, with an artist dataset including artists who have artworks in both the Art Institute and The Met. Using these datasets, the project aims to evaluate how historical representation differs across popular cultural institutions, focusing on artist prominence and key movements featured at each museum.

The methods needed for this project are data acquisition, data extraction, record linkage, and comparative analysis. First, the metadata records for the museums will be retrieved from the Art Institute of Chicago’s data dumps API that uses JSON and CSV files and The Metropolitan Museum of Art’s open access API, both found on GitHub. The artists dataset can be accessed by submitting on the Getty Vocabularies website. During the extraction and cleaning phase, unstructured fields will be processed, such as standardizing dates, creating schemas that can be used for querying across all collections. To combine these distinct datasets, record linkage and entity resolution will be used between the Art Institute and artists datasets, and The Met and artists datasets. This process will provide additional information on artists featured at the museums.

Following data cleaning, comparative analysis will evaluate the institutional collection patterns. Examples that the analysis will track are museum acquisition trends and representation patterns for prominent artists across all three institutions, highlighting differences in how major cultural institutions document and honor legendary artists.

# Team Roles
Tiffany Chang: Evaluator

Erin Farraday: Data cleaning

Livia Lin: GitHub and project management

Carlee White: Data acquisition and research design

# Research / Business Questions
1. How does the distribution of artworks across various historical periods differ from museum to museum?
2. How does the representation of prominent artists differ across the museums based on the number of artworks that are attributed to each artist?
3. How does the distribution of artistic mediums, such as painting, sculpture, and photography vary across the institutions?
4. Are the acquisition dates of the artworks during or after the artist’s lifetime?


# Datasets
The Art Institute of Chicago provides multiple options for how to download their data, and we chose to use a pre-prepared JSONL file, which includes every art piece, but limited features about the piece. The features provided are title, main reference number, department, and artist title. The main reference number is comprised of the accession year of the piece, a period, and a number which makes it uniquely identifying.

The Metropolitan Museum of Art (The Met) provides an open-access dataset that contains information about over 470,000 pieces in its collection. The MetObjects.csv includes information such as the titles of artworks, artist names, nationalities, creation dates, and mediums. This will allow us to compare the representation of artists across museums and evaluate differences in artist naming conventions, as well as the completeness of artist information across sources. The features provided are as follows:
'Object Number', 'Is Highlight', 'Is Timeline Work', 'Is Public Domain',
'Object ID', 'Gallery Number', 'Department', 'AccessionYear’,
'Object Name', 'Title', 'Culture', 'Period', 'Dynasty', 'Reign',
'Portfolio', 'Constituent ID', 'Artist Role', 'Artist Prefix',
'Artist Display Name', 'Artist Display Bio', 'Artist Suffix',
'Artist Alpha Sort', 'Artist Nationality', 'Artist Begin Date',
'Artist End Date', 'Artist Gender', 'Artist ULAN URL',
'Artist Wikidata URL', 'Object Date', 'Object Begin Date',
'Object End Date', 'Medium', 'Dimensions', 'Credit Line',
'Geography Type', 'City', 'State', 'County', 'Country', 'Region',
'Subregion', 'Locale', 'Locus', 'Excavation', 'River', 'Classification',
'Rights and Reproduction', 'Link Resource', 'Object Wikidata URL',
'Metadata Date', 'Repository', 'Tags', 'Tags AAT URL',
'Tags Wikidata URL'. 
This list of features includes the same four features as the Art Institute of Chicago’s dataset, with the “main reference number” being called the “Object ID” in this dataset. 

The Getty Union List of Artist Names (ULAN) is a structured vocabulary that contains identifying and biographical information about different artists. We exported the results of a query into a CSV file which contains artist names, biographies, nationalities, and record types. ULAN differs from the Art Institute of Chicago and Metropolitan Museum datasets because it focuses on individual artist identities rather than artwork records. We plan to use this specific dataset to support record linkage and entity resolution by matching artist names across the museum collections. The standardized format of ULAN’s information will help us identify potential matches, note differences in naming conventions, and supplement the museum datasets with artist-level information.

The Art Institute of Chicago, Metropolitan Museum of Art, and Getty Union List of Artist Names datasets complement each other through their shared information about various artists. The Art Institute and Met datasets focus more on the artworks, while ULAN provides standardized info about the artists. We plan to use record linkage to identify artists that appear across multiple datasets, starting with available identifiers and names. For uncertain matches we may use additional biographical information such as nationality or birth date. The integrated dataset will allow us to compare artist representation across the museums and evaluate how artist information is recorded.

The Art Institute of Chicago’s dataset is available through their github repository (https://github.com/art-institute-of-chicago/api-data). The specific dataset we accessed is not their full dataset, but one that includes all of their artworks, with limited features. It is available as a JSONL file here: https://github.com/art-institute-of-chicago/api-data/blob/main/getting-started/allArtworks.jsonl. To read a JSONL file into python, you can use `pd.read_json("filename", lines = True)`. The data in this dataset has varying licenses based on data type and source, which we will investigate as we explore the dataset more. 

The Met’s dataset is also available through their github repository (https://github.com/metmuseum). The specific file accessed is their open access dataset, which includes over 470,000 artworks, available as a CSV here: https://github.com/metmuseum/openaccess/blob/master/MetObjects.csv The Met’s open access dataset is licensed under the Creative Commons Zero license.

Finally, the Getty Union List of Artist Names dataset is available through the Getty Vocabularies Website (https://vocab.getty.edu/). The dataset of artists we will be using is from an example query provided here: [5.19  Artists with Name, Bio, Nationality, Type](https://vocab.getty.edu/queries?toc=Artists_with_Name_Bio_Nationality_Type&query=select+%3Fx+%3Fname+%3Fbio+%3Fnationality+%3Ftype+%7B%0A++%3Fx+gvp%3AbroaderExtended+ulan%3A500000002.+%23+Persons%2C+Artists%0A++optional+%7B%3Fx+gvp%3AagentTypePreferred+%5Bgvp%3AprefLabelGVP+%5Bxl%3AliteralForm+%3Ftype%5D%5D%7D%0A++optional+%7B%3Fx+foaf%3Afocus+%5Bgvp%3AnationalityPreferred+%5Bgvp%3AprefLabelGVP+%5Bxl%3AliteralForm+%3Fnationality%5D%5D%5D%7D%0A++optional+%7B%3Fx+gvp%3AprefLabelGVP+%5Bxl%3AliteralForm+%3Fname%5D%7D%0A++optional+%7B%3Fx+foaf%3Afocus+%5Bgvp%3AbiographyPreferred+%5Bschema%3Adescription+%3Fbio%5D%5D%7D%0A%7D&implicit=true&equivalent=false#Artists_with_Name_Bio_Nationality_Type), then saved as a CSV file. This data is released under the Open Data Commons Attribution License.


# Timeline
November 6th: Data acquisition and cleaning

November 15th: Record linkage

November 19th: Status report

December 1st: Finish analysis

December 8th: Complete project report

From submission until November 6th, we will be working on cleaning the datasets. Each dataset has around five days to be cleaned and reviewed by another team member. After the datasets are cleaned, we can begin combining the datasets with the help of record linkage. After this is done, we will have a few days to finish the status report of our progress. Then, we will aim to finish the analysis by December 1st, giving seven days to focus on completing the project report.

# Constraints
Constraints we would face in this project comes mostly from limitations relating to data completeness, consistency, and comparability across the different dataset collections. Due to the fact that each dataset/institution uses different metadata formats and classification systems, fields (like artist names, historical periods, etc.) may not align perfectly. The Getty artist vocabulary may help with standardizing artist names and identify matching entities, but not every artist in the museum collections may have a corresponding record.

Some records may also contain missing or incomplete metadata, making record linkage less reliable. Additionally, differences in collection size and acquisition history may influence the results, meaning that artwork counts may not fully reflect an artist’s prominence or historical importance. To address these challenges, our project will standardize relevant fields, document missing data, and interpret the results with these limitations in mind.

# Gaps
Some additional input is needed to determine how well the Getty artist vocabulary can be linked to different artist records in the Art Institute of Chicago and The Metropolitan Museum of Art datasets. We may need more input on how to handle artists with multiple name variations, missing identifiers, or no matching Getty records. We will also need to confirm which metadata fields are available and sufficiently complete across the museum datasets to support our research questions. Additional input may be helpful in determining how we can classify historical periods and measure artist representation fairly across museums with different acquisition histories.
