# vizathon-21
**Welcome to Hoor Ulain's Vizathon submission!**

The first 2 data visualizations (bar charts) used this COVID-19 Data from Hospitals: [COVID-19_Hospital_Data_from_the_National_Hospital_Care_Survey.xls](https://github.com/glowgirl13/vizathon-21/files/6912703/COVID-19_Hospital_Data_from_the_National_Hospital_Care_Survey.xls)
The source of this data is the CDC: https://www.cdc.gov/nchs/covid19/nhcs/intubation-ventilator-use.htm

**Below is the code for the COVID-19 Hospital Data & Bar Charts, all done on RStudio!**

install.packages("ggplot2")
library(ggplot2)
install.packages("dplyr")
library(dplyr)


Data.set <-read.csv("COVID-19_Hospital_Data_from_the_National_Hospital_Care_Survey.csv")
Data.set1 <- Data.set %>% select(Indicator, Group, Subgroup, Value)

Data.set2 <- Data.set1 %>% filter(Indicator == "Total Screenings")
Data.set2 <- Data.set2['Value']
Data.set2 <- sum(Data.set2)

Data.set3 <- Data.set1 %>% filter(Indicator == "Confirmed Screenings")
Data.set3 <- Data.set3['Value']
Data.set3 <- sum(Data.set3)

Data.set4 <- Data.set1 %>% filter(Indicator == "Negative Screenings")
Data.set4 <- Data.set4['Value']
Data.set4 <- sum(Data.set4)

Data.set5 <- Data.set1 %>% filter(Indicator == "Intubation or Ventilator Use")
Data.set5 <- Data.set5['Value']
Data.set5 <- sum(Data.set5)

Data.set6 <- Data.set1 %>% filter(Indicator == "Deaths of confirmed cases with intubation or ventilator use")
Data.set6 <- Data.set6['Value']
Data.set6 <-subset(Data.set6, Value!="NA")
Data.set6 <- sum(Data.set6)

Data.set7 <- Data.set1 %>% filter(Indicator == "Deaths of confirmed cases without intubation or ventilator use")
Data.set7 <- Data.set7['Value']
Data.set7 <-subset(Data.set7, Value!="NA")
Data.set7 <- sum(Data.set7)

#Bar Plot 1 - Screenings
values <- c(Data.set2, Data.set3, Data.set4)
counts <- table(values)
barplot (values, main ="Screenings in the COVID-19 Pandemic",
         xlab="Screenings",
         ylab="Values",
         col=c("#dea5a4","#ffb347","#aec64f"),
         border="black",
         names.arg=c("Total Screenings", "Confirmed Screenings", "Negative Screenings"), cex.names=0.8)


#Bar Plot 2 - Ventilation and/or Intubation
values2 <- c(Data.set5, Data.set6, Data.set7)
counts2 <- table(values)
barplot (values, main ="Ventilation and Intubation in the COVID-19 Pandemic",
         xlab="Ventilation and/or Intubation",
         ylab="Values",
         col=c("#77dd77","#ff6961","#fdfd96","#b39eb5"),
         border="black",
        names.arg=c("Intubation or Ventilator Use", "Deaths w/ intubation or ventilator use", "Deaths w/o intubation or ventilator use"), cex.names=0.8)
![Ventilation and Intubation in the COVID-19 Pandemic](https://user-images.githubusercontent.com/88276569/127771551-f7f5c936-23b3-4937-b414-682d705d8fb0.png)
![Screenings in the COVID-19 Pandemic](https://user-images.githubusercontent.com/88276569/127771555-1491bc68-a690-4b4d-a8bd-2ddb9eac1455.png)

**That's all for the code, however I also made further visualizations through the platform Tableau!** These graphs are also bar charts, however what distinguishes them from the other bar charts is that they also show all of the other factors (outside of screenings and ventilators/intubulation), thereby providing a more holistic point of view. These visuals can be found through this link: https://public.tableau.com/app/profile/ulain.umar/viz/IndicatorsofCOVID-19fromCDCDataonHospitals/Dashboard1?publish=yes

**Further data visualizations were created on the basis of my home province Ontario!** This data was particularly interesting because it showed the disparity that exists based on geography. Firstly, I created bar charts through RStudio using the following code:

install.packages("ggplot2")
library(ggplot2)
install.packages("dplyr")
library(dplyr)

Data.set <-read.csv("region_hospital_icu_covid_data.csv")
Data.set <- Data.set %>% select(oh_region, icu_current_covid, icu_current_covid_vented, hospitalizations)

central <- Data.set %>% filter(oh_region == "CENTRAL")
central1 <- sum(central['icu_current_covid'])
central2 <- sum(central['icu_current_covid_vented'])
central3 <- sum(central['hospitalizations'])

values1 <- c(central1, central2, central3)
counts1 <- table(values1)
barplot (values1, main ="COVID-19 Patients in Different ICU Conditions in the Central Regions of Ontario",
         xlab="ICU Condition",
         ylab="Value",
         col=c("#dea5a4","#ffb347","#aec64f"),
         border="black",
         names.arg=c("ICU Patients w/ COVID", "ICU Patients w/ COVID & Ventilators", "Hospitalizations"), cex.names=0.8)


east <- Data.set %>% filter(oh_region == "EAST")
east1 <- sum(east['icu_current_covid'])
east2 <- sum(east['icu_current_covid_vented'])
east3 <- sum(east['hospitalizations'])

values2 <- c(east1, east2, east3)
counts2 <- table(values2)
barplot (values2, main ="COVID-19 Patients in Different ICU Conditions in the Eastern Regions of Ontario",
         xlab="ICU Condition",
         ylab="Value",
         col=c("#dea5a4","#ffb347","#aec64f"),
         border="black",
         names.arg=c("ICU Patients w/ COVID", "ICU Patients w/ COVID & Ventilators", "Hospitalizations"), cex.names=0.8)

north <- Data.set %>% filter(oh_region == "NORTH")
north1 <- sum(north['icu_current_covid'])
north2 <- sum(north['icu_current_covid_vented'])
north3 <- sum(north['hospitalizations'])

values3 <- c(north1, north2, north3)
counts3 <- table(values3)
barplot (values3, main ="COVID-19 Patients in Different ICU Conditions in the Northern Regions of Ontario",
         xlab="ICU Condition",
         ylab="Value",
         col=c("#dea5a4","#ffb347","#aec64f"),
         border="black",
         names.arg=c("ICU Patients w/ COVID", "ICU Patients w/ COVID & Ventilators", "Hospitalizations"), cex.names=0.8)


toronto <- Data.set %>% filter(oh_region == "TORONTO")
toronto1 <- sum(toronto['icu_current_covid'])
toronto2 <- sum(toronto['icu_current_covid_vented'])
toronto3 <- sum(toronto['hospitalizations'])

values4 <- c(toronto1, toronto2, toronto3)
counts4 <- table(values4)
barplot (values4, main ="COVID-19 Patients in Different ICU Conditions in Toronto,Ontario",
         xlab="ICU Condition",
         ylab="Value",
         col=c("#dea5a4","#ffb347","#aec64f"),
         border="black",
         names.arg=c("ICU Patients w/ COVID", "ICU Patients w/ COVID & Ventilators", "Hospitalizations"), cex.names=0.8)


west <- Data.set %>% filter(oh_region == "WEST")
west1 <- sum(west['icu_current_covid'])
west2 <- sum(west['icu_current_covid_vented'])
west3 <- sum(west['hospitalizations'])

values5 <- c(west1, west2, west3)
counts5 <- table(values5)
barplot (values5, main ="COVID-19 Patients in Different ICU Conditions in the Western Regions of Ontario",
         xlab="ICU Condition",
         ylab="Value",
         col=c("#dea5a4","#ffb347","#aec64f"),
         border="black",
         names.arg=c("ICU Patients w/ COVID", "ICU Patients w/ COVID & Ventilators", "Hospitalizations"), cex.names=0.8)


values <- c(central, east, north, toronto, west)
counts <- table(values)
barplot (values, main ="COVID-19 Patients in the ICU in Different Regions of Ontario",
         xlab="Region",
         ylab="# of COVID-19 Patients in the ICU",
         col=c("#dea5a4","#ffb347","#aec64f", "#77dd77", "#ff6961"),
         border="black",
         names.arg=c("Central", "East", "North", "Toronto", "West"), cex.names=0.8)
**That's all the code, here are the associated bar graphs:**
![COVID-19 Patients in the ICU in Different Regions of Ontario](https://user-images.githubusercontent.com/88276569/127775882-5354ed57-a407-48ed-b86a-73c06542a236.png)
![COVID-19 patients in DIfferent ICU Conditions in the Central Regions of Ontario](https://user-images.githubusercontent.com/88276569/127775894-fa068392-3743-49f4-b664-d781386a5441.png)
![COVID-19 patients in DIfferent ICU Conditions in the Eastern Regions of Ontario](https://user-images.githubusercontent.com/88276569/127775896-ada495d2-040a-433c-8d98-e9fcc571213b.png)
![COVID-19 patients in DIfferent ICU Conditions in the Northern Regions of Ontario](https://user-images.githubusercontent.com/88276569/127775897-0e072af9-5d4a-45da-8d24-dc148aa4e508.png)
![COVID-19 patients in DIfferent ICU Conditions in the Western Regions of Ontario](https://user-images.githubusercontent.com/88276569/127775898-dd6d7031-de39-4c46-a8f0-aa4698881998.png)
![COVID-19 patients in DIfferent ICU Conditions in Toronto, Ontario](https://user-images.githubusercontent.com/88276569/127775899-8ec1f840-5059-4b25-bbfd-b6243a357ef2.png)

**I also created a side-by-side comparison on Tableau, which can be found here: https://public.tableau.com/app/profile/ulain.umar/viz/ICUConditionsinDifferentRegionsofOntarioASide-by-SideComparison/Dashboard1?publish=yes**







