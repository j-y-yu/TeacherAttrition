## [data](data)
Cleaning all raw data

## [docs](docs)
Project related documents

## [src/processing](src/processing)
Cleaned raw data are saved under [data_clean](data/data_clean) folder. Integrated data go through Exploratory Data Analysis to explain data in detail, then Features Selection to reduce dimensionality of data for Modeling step. 

### Data Integration

 Data | Component | Shape |
| ----------- | ----------- | ----------- | 
| [SASS_99_00_S2a_v1_0.csv](data/SASS_1999-00_TFS_2000-01_v1_0_CSV_Datasets/SASS_99_00_S2a_v1_0.csv) | Public Principal | (1582, 473) | 
| [SASS_99_00_S3a_v1_0.csv](data/SASS_1999-00_TFS_2000-01_v1_0_CSV_Datasets/SASS_99_00_S3a_v1_0.csv) | Public School | (2309, 814) | 
| [SASS_99_00_S4a_v1_0.csv](data/SASS_1999-00_TFS_2000-01_v1_0_CSV_Datasets/SASS_99_00_S4a_v1_0.csv) | Public Teacher | (3912, 1335) | 
| [SASS_99_00_T2_v1_0.csv](data/SASS_1999-00_TFS_2000-01_v1_0_CSV_Datasets/SASS_99_00_T2_v1_0.csv) | Former Teacher | (1679, 404) | 
| [SASS_99_00_T3_v1_0.csv](data/SASS_1999-00_TFS_2000-01_v1_0_CSV_Datasets/SASS_99_00_T3_v1_0.csv) | Current Teacher | (2477, 618) | 

- [Data_Integration.ipynb](src/processing/Data_Integration.ipynb): All cleaned data are integrated into single dataframe (3640, 128)
  - Labeling: Teachers from TFS Former Teacher (T2) survey are "Former Teacher", and Teachers from TFS Current Teacher (T3) survey are "Current Teacher"
  - Data have 124 attributes (excluding 3 control numbers) with 107 categorical attributes, and 17 numerical attributes for the 3640 teachers (2176 current, 1464 former teachers).

### Exploratory Data Analysis
- [EDA.ipynb](src/processing/EDA.ipynb)
   1. Number of teachers, schools
    1. Teacher retention per region
    1. Public Teacher
        - gender, gender, race/ethnicity
        - marriage, earning, dependents, union
        - degree, major(STEM)
        - certificaiton
        - years, new teacher, subjects(STEM), grades
        - class organization, full-time/part-time
    1. Public School
        - type, level, urbanicity, minority students
        - minority teachers, student-teacher Ratio
        - Title 1
        - Free or Reduced-price Lunch (FRPL), National Lunch Program (NLP)
    1. Public Principal
        - age, race/ethnicity
        - gender, degree, salary
        - years of experience
    1.  Public District (available from Public School)
        - incentive Policy

### Feature Selection
- [Feature_Selection_1.ipynb](src/processing/Feature_Selection_1.ipynb): Data set is reduced to (3640, 53) with 39 categorical and 14 numerical using correlation filtering 
- [Feature_Selection_2.ipynb](src/processing/Feature_Selection_2.ipynb): 9 approaches below were used to score feature importance automatically and select the best features predicting Teacher Attrition:
* Filter Methods
	* Variance Threshold
* Embedded Methods
	* L1 Regularized Logistic Regression (Lasso)
	* Random Forest Feature Importance
* Wrapper Methods
	* Recursive Feature Elimination (RFE) with Random Forest
	* Recursive Feature Elimination (RFE) with Ridge Regression
	* Permutation Importance with Random Forest
	* Permutation Importance with Ridge Regression
	* Sequential Feature Selection (SFS) with KNN
	* Sequential Feature Selection (SFS) with Ridge Regression

## [src/modeling](src/modeling)
Prediction modeling and analysis on Teacher Attrition due to COVID-19 in math and reading go through 4 phases: State-of-an-art modeling, Gradient boosting modeling, Teacher attrition prediction analysis for unlabeled data, and Gradient boosting experimenting with raw data.

### State-of-an-art modeling 
* 5 models were trained to predict Teacher Attrition in [Modeling_BL.ipynb](src/modeling/Modeling_BL.ipynb) with comparing 10 feature sets selected from [Feature_Selection_2.ipynb](src/processing/Feature_Selection_2.ipynb)
  * Ridge Regression
  * SVM (Linear, Kernel)
  * KNN
  * Random Forest
  * Grandient Boosting

### Advanced gradient boosting modeling 
* 4 models were trained to predict Teacher Attrition in [Modeling_GB.ipynb](src/modeling/Modeling_GB.ipynb) with comparing 10 feature sets selected from [Feature_Selection_2.ipynb](src/processing/Feature_Selection_2.ipynb)
  * XGBoost
  * LightGBM
  * CatBoost
  * HistGradientBoost

### Teacher attrition prediction analysis for unlabeled data
* Unlabeled data have been integrated to predict Teacher Attrition for teachers whom did not participate TFS in [Unlabeled_Data_Integration.ipynb](src/modeling/Unlabeled_Data_Integration.ipynb)
* Teacher Attrition is predicted with the unlabeled data using the best gradient boosting model in [Unlabeled_Modeling_GB.ipynb](src/modeling/Unlabeled_Modeling_GB.ipynb)

### Experimenting advanced gradient boosting models with raw data.
* The same 4 models were trained using raw data without feature engineering in [Modeling_NA_GB.ipynb](src/modeling/Modeling_NA_GB.ipynb) 
