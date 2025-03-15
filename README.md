

# Bihar Facility Health Assessment 

### Report Link : https://drive.google.com/file/d/1LxUWknTUSrOIF7lbGOlJr9NkAkxP6Jns/view?usp=sharing
## Overview

This Power BI dashboard presents the findings of a Bihar health facility assessment of Health Sub-Centers (HSCs), encompassing 38 districts, 531 blocks, and 10,716 facilities. The dashboard highlights infrastructure gaps within the HSCs. Less than 60% of the HSCs were found to be functional, and 25% of existing buildings require reconstruction. Regarding demography and location, one-third of the HSCs serve populations exceeding ten thousand, and nearly half are located more than 10km from the nearest primary health center. Basic amenities, such as power, water supply, and toilets, were lacking in three out of five HSCs. Nearly half of the HSCs exhibited damaged ceilings or seepage. Despite the availability of Auxiliary Nurse Midwives (ANMs), many HSCs did not offer Antenatal Care (ANC) services.
 A significant disparity exists between service availability and the availability of delivery tables and kits. While over 75% of services like ANC, Village Health, Sanitation and Nutrition Day (VHSND), and Outpatient Department (OPD) are available, only 3% of delivery tables and kits were present. Internet access, room availability, and bed availability were each above 70%.

### Steps followed 
 Data ETL and Visualization Steps:

1. Data Cleaning and Preparation: Data was compiled from 38 districts in Bihar into a single spreadsheet, requiring extensive cleaning and modification.

2. Data Loading: The Excel dataset was loaded into Power BI Desktop, selecting the data transformation mode before uploading.

3. Handling Missing Values: Over 60% of the columns contained null values. To address this, the following methods were used: 
• Deletion of rows with entirely null values.
• Imputation using mean, mode, and median.
• Development of a predictive model to estimate and replace missing values.

4. Outlier Detection and Treatment: Univariate outliers were identified and treated using imputation and other statistical methods.

5. Duplicate Removal: 2% of the rows were found to be duplicates and were removed using the "Remove Rows" function.

6. Theme Selection: A theme was selected in the report view under the "View" tab.

7. Key Metric Display: Card visuals were used to display key numerical values, including the number of districts covered, total facilities covered, and mean HSCs per district/block.

8. Categorical Data Visualization (Building Ownership and Recommendations): Pie charts were used to visualize categorical data related to building ownership and recommendations, highlighting the need for new HSC construction and land availability.

9. Bar Graph Usage (Demographic and Location Data): Bar graphs were used to display: 
• Distance of HSCs from Primary Health Centers (PHCs) and the farthest village.
• Population served by HSCs and marginalized populations.

10. Bar Chart Usage (Basic Amenities): A bar chart was added to the report to represent the availability of basic amenities. This chart revealed that basic amenities such as power, water supply, and toilets were lacking in three out of five HSCs, and nearly half of the HSCs had damaged ceilings or seepage.

11. Sunburst Chart Usage (Hierarchy and Insights): Sunburst charts were used to: 
• Visualize internet availability and categorization.
• Represent building conditions and recommendations.

12. Donut Chart Usage (Room and BMW Disposal Availability): Two donut charts were added to show the availability of rooms and biomedical waste (BMW) disposal, revealing that 72% of facilities had only up to two rooms available.

13. Bar Chart Usage (Human Resources and Service Availability): A bar chart was used to analyze human resource availability and correlate it with service availability, revealing that despite the presence of Auxiliary Nurse Midwives (ANMs), many HSCs did not offer Antenatal Care (ANC) services.

14. District-Level Filtering: A district-wise filter option was added to enable the analysis of individual district performance and identify gaps.


To prepare this report, Power BI's built-in functions were utilized, which facilitated the data modification, binning and cleaning. Additionally, various DAX formulas were applied to create a separate Measure table containing over 30 calculated measures. Some of these are shown below.

* A snapshot of the new calculated column used to convert numerical values to categorical values

![Image](https://github.com/user-attachments/assets/c879e709-7e81-4873-86e2-4ba1dc69235a)

* New measure was created to find total count of facility 

Following DAX expression was written for the same,
        
        Total district = DISTINCTCOUNT(HSC[Name of District])
        
A card visual was used to represent count of customers.

![Image](https://github.com/user-attachments/assets/91b176b5-be4f-4914-b69e-4e7903a76afa)

        
 * New measure was created to find mean number of HSC per block
 
 Following DAX expression was written
 
         Mean HSC per Block = AVERAGEX(VALUES(HSC[Block]), CALCULATE(COUNTA(HSC[Facility Type])))
 
 A card visual was used to represent this mean number
 
 Snap of mean number of HSC per block
 
 ![Image](https://github.com/user-attachments/assets/5e9200c1-27d4-473a-bc64-40a311b9bfde)

 
*  New measure was created to calculate total distance of HSC from the PHC (Primar Health Centre)
 
 Following DAX expression was written
 
         HSC from PHC>=5 = CALCULATE(COUNTROWS(HSC),HSC[Distance_PHC ]>=5)/COUNTROWS(HSC)
    
 A Bar graph visual was used to represent this distance.
 
 
 ![Image](https://github.com/user-attachments/assets/8552057d-5284-4573-9d8b-afa0d4b6d451)
 
* New measure was created to calculate three major amenities (Water, Electricity and Toilet) were available. 
 
 Following DAX expression was written

      All three aminities available = CALCULATE(COUNTROWS(HSC),HSC[Electricity available]=1, HSC[Running water availability]=1,HSC[Toilet facility available]=1)/COUNTROWS(HSC)
 
 A Bar graph visual was used to represent this distance.

 ![Image](https://github.com/user-attachments/assets/117d8078-2083-4c55-8c02-ea30bae00733)
 

 * New measure was created to calculate the recommendation of the building 

Following DAX expression was written

    Building Recommendation = SWITCH(TRUE(),HSC[Recommendation of the building]= "BUILDING CONDITION IS OK", "Building is OK",
"Building is not OK")

A Sunburst chart was used to represent this subcategorization

![Image](https://github.com/user-attachments/assets/398389b1-7e75-45ab-b0f6-c80056c0bcde)

* The report was then published to Power BI Service.
 

![Image](https://github.com/user-attachments/assets/881ca1b1-d6ec-4ac5-922c-259b1ffc5c09)

# Snapshot of Dashboard (Power BI Service)

![Image](https://github.com/user-attachments/assets/cd529268-004d-4ead-b4a2-87b3de95989c)
 

 # Report Snapshot (Power BI DESKTOP)

 
![Image](https://github.com/user-attachments/assets/67687ca0-9bfc-4b02-819e-c018264ab06a)

# Insights

A three pages report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Total coverage

 a) District- 38 

 b) Block- 531

 c) Total facility- 10716

 e) Mean number of HSC per district - 282

 f) Mean numbe of HSC per block- 20
 

    Thus, the mean number of HSCs per district/block is low
           
### [2] Building infrastructure status

 a) 60% of the facilities are still not under government health ownership

 b)  60% of the facilities require new construction, and 47% of those lack available land.

 c) 48% of buildings showed damaged ceilings or visible seepage.

 d)  Only 45% of the facilities have road connectivity.

 e) 97% of the facilities have no biomedical waste management system

    Thus, Bihar's health facilities need urgent improvements in ownership, construction, and waste management. 
  
  ### [3] Basic amenities available in the HSCs
 a) Toilet availability - 30% 

 b) Water availability - 29%

 a) Electricity availability - 36%

 d) All are available- 26%

 e) None are available- 62%

 f) Internet service available- 80%

 g) upto 2 rooms available- 72%

 h) No beds available - 89%

    Basic infrastructure and bed availability are severely lacking in Bihar's health facilities, despite relatively high internet access.

 ### [4] Service availability
 
 ### Human Resources
 
 a) Community health offer- 13%

 b) Accredited Social Health Activist (ASHA) - 75%

 c) ASHA facilitator- 59%

 d) Auxiliary Nurse Midwife (ANM)- 91%

 ### Basic services

 a) Outpatient Department (OPD)- 61%

 b) Absolute Neutrophil Count (ANC)- 75%

 c) Village Health Sanitation and Nutrition Day (VHSND)- 93%


    While ANM and VHSND services show strong availability, community health officers and OPD services are significantly lacking in HSCs


### Thus, Bihar's healthcare system is at risk of worsening due to widespread infrastructure and staffing shortages, likely leading to reduced access and poorer health outcomes without urgent intervention.
