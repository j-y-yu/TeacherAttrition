## Data Sources

The Schools and Staffing Survey (SASS) was conducted by NCES seven times between 1987 through 2011 to study and provide descriptive data for public and private school districts, schools, principals, and teachers regarding the context of elementary and secondary education. Teacher Follow-Up Survey (TFS) was conducted the year after SASS administration to determine how many teachers remained in teaching, either at the same school or moved schools, or left teaching. Our data collected [1999-2000 SASS and 2000-2001 TFS public-use data](https://nces.ed.gov/surveys/sass/dataprod9901.asp) from NCES as other years are restricted-use only. Downloading csv format is available from [Online Codebook](https://nces.ed.gov/OnlineCodebook/Session/Codebook) provided by NCES.

### [SASS_1999-00_TFS_2000-01_v1_0_CSV_Datasets](SASS_1999-00_TFS_2000-01_v1_0_CSV_Datasets): raw data
* SASS_99_00_S1a_v1_0.csv: Public District (not in used due to no matching control numbers for school, principal, and teacher)
* SASS_99_00_S2a_v1_0.csv: Public Principal
* SASS_99_00_S3a_v1_0.csv: Public School
* SASS_99_00_S4a_v1_0.csv: Public Teacher (not located in the folder due to file size limit exceeding 50MB)
* SASS_99_00_T2_v1_0.csv: Former Teacher
* SASS_99_00_T3_v1_0.csv: Current Teacher

### [Codebook](Codebook): Layout files providing necessary information for the survey.
* SASS_99_00_S1A_v1_0_Codebook.txt: Codebook for all surveys
* SASS_99_00_S1A_v1_0_S1A_Layout.txt: Public District
* SASS_99_00_S2A_v1_0_S2A_Layout.txt: Public Principal
* SASS_99_00_S3A_v1_0_S3A_Layout.txt: Public School
* SASS_99_00_S4A_v1_0_S4A_Layout.txt: Public Teacher
* SASS_99_00_T2_v1_0_T2_Layout.txt: Former Teacher
* SASS_99_00_T3_v1_0_T3_Layout.txt: Current Teacher

### [Questionnaire](Questionnaire): Survey Questionnaire file in pdf format
* sass1a.pdf: Public District
* sass2a.pdf: Public Principal
* sass3a.pdf: Public School
* sass4a.pdf: Public Teacher
* sasst2.pdf: Former Teacher
* sasst3.pdf: Current Teacher


## Data Integration
All cleaned data are integrated in [Data_Integration.ipynb](../src/processing/Data_Integration.ipynb)
