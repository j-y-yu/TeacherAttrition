# data-SASS
  
* June Yu: CS 5395 Project
* Daniel Payan: undergraduate researcher 

1.	Data Gathering
* Download ascii data from [link](https://nces.ed.gov/surveys/sass/dataprod9901.asp) to downloads folder
  * if the original file is larger than 50MB, split it in few files e.g. SASS_99_00_S4a_v1_0.csv or save as h5
 
2.	Data Processing
  2.1. Merge public teacher (former and current) files with public school, and public principal data files. 
	* The principal control number is represented by CNTLNUM
      * so is the teacher control number, and school district control number so we will need help from Dr. Feng or her student on data merging procedures. 
	* The school control number is represented by SCHCNTL. 
	* add scripts to [scripts](../scripts/) folder for 
	      * reading ascii to csv 
	      * cleaning up data and creating data frames
	      * saving as h5 files
	* Save intermediate results in [data](../data/). If csv is larger than 50MB, save it as h5 file 

  2.2.  Add 2000-2001 current/former teacher data [SASS](https://nces.ed.gov/surveys/sass/dataprod9901.asp)
	* Individual problem: based on school data and on labeled data, can we predict the probability of a teacher from school X leaving (one of 80K not labelef) 
	* add scripts for reading ascii to csv to scripts folder
	* add scripts for cleaning up data and creating data frames to scripts folder
	* Save intermediate results in [data](../data/). If csv is larger than 50MB, save it as h5 file 
  

3.	Basic EDA illustrating teacher retention rate per school district in the dataset 
	* 1999-2000data visualization 1: 
		* 8000 job adds by school, visualize percentage of empty slots per school 
	* save python notebook work in [notebooks](../notebooks/) folder
	* Feature correlation: age, sex, race and ethnicity, college majors, graduate degrees or not, years of teaching experience, subjects taught(STEM, special education or others), grade taught (public teacher), school level, school poverty rate, share of minority students, Title I status, urban or rural status (public school), principal years of experience, age, race and ethnicity (public principal). 
    * Save intermediate results in [data](../data/) and figures in [figures](../figures/). 

4.	Modeling 

*	Predict teacher’s status (stay at a particular school=1 and 0 if she or he left teaching or moved to a different school) in test data using the following feature space: age, sex, race and ethnicity, college majors, graduate degrees or not, years of teaching experience, subjects taught(STEM, special education or others), grade taught (public teacher), school level, school poverty rate, share of minority students, Title I status, urban or rural status (public school), district size, district revenue (public district), principal years of experience, age, race and ethnicity (public principal).  
	i. Prior work with SASS dataset:  Nguyen et al.  "The correlates of teacher turnover: An updated and expanded Meta-analysis of the literature", https://www.sciencedirect.com/science/article/pii/S1747938X19305597, full text [link]( https://drive.google.com/file/d/1QYU3Kx9FFMmQoHOifDa6_qAwgqdNO96E/view?usp=sharing)
*	How well can we predict a teacher’s retention rate based on (a) per school and per district. 
    i.      Modeling in a is predicting outcome (class label)
    ii.      Modeling in b is  regression (retention rate) for the district

* save python notebook work in [notebooks](../notebooks/)and figures in [figures](../figures/) folder. 
* save intermediate results in [data](../data/) 