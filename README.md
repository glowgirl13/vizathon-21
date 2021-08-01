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







