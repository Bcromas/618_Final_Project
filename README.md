# 618_Final_Project: Analyzing and manipulating data in MIMIC-III.

The dataset I will work with is MIMIC-III which is a freely accessible database of “deidentified health-related data associated with over forty thousand patients who stayed in critical care units of the Beth Israel Deaconess Medical Center between 2001 and 2012.” The data is stored in 25 CSV files which I plan to load into a PostgreSQL database and access using Psycopg. Some of the tables I plan to leverage include:
- PATIENTS with 46,520 rows and 8 columns. Some relevant attributes and their data types are SUBJECT_ID (int64), GENDER (object), and DOB (object).
- ADMISSIONS with 58,976 rows and 19 columns. Some relevant attributes are SUBJECT_ID (int64), HADM_ID (int64), ADMITTIME (object), DEATHTIME (object), and DIAGNOSIS (object).  
- CHARTEVENTS with 330,712,483 rows and 15 columns. Some relevant attributes are SUBJECT_ID (int64), HADM_ID (int64), VALUE (object), and VALUENUM (float64).
## Exploratory questions
1. Do the number of hospital admissions differ significantly between weekdays and weekends?
2. What’s the relationship between length of stay and survival rate?
3. What relationships exist between type of admission, admission diagnosis, length of stay, age, gender, readmittance within 30 days, amount of bedside attention (e.g. patient is bathed), and occurence of sepsis?
4. Can we predict patient readmittance within 30 days based on some combination of type of admission, admission diagnosis, length of stay, age, gender, amount of bedside attention (e.g. patient is bathed), and occurence of sepsis? 
## Addressing questions
- EDA: Boxplots of average admissions during week and average admissions during weekends. The ADMISSIONS data would be segmented by date and a derived attribute indicating whether it was a weekday or weekend. Visualization: Seaborn. 
- EDA: JointGrid with a regplot for the linear regression model and a distplot for the distribution. The model would predict survival rate given length of stay. The ADMISSIONS data would be segmented by length of stay and whether the patient died at the hospital. Visualization: Seaborn.  
- EDA: Pairplot with every pairing of the eight attributes mentioned above. The data from ADMISSIONS, PATIENTS, and CHARTEVENTS would have to be merged and derived attributes added. The data would be primarily segmented by ADMISSIONS record. Visualization: Seaborn.
- ML Method: Binary classification of given patient as either ‘Yes, will be readmitted within 30 days’ or ‘No, will not be readmitted within 30 days’. The data would be segmented by ADMISSIONS and PATIENTS records.
