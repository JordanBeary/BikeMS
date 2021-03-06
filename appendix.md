Additional Code Not Shown in Final Report
================

Loading libraries:

    library(readr)
    library(plyr)
    library(tidyr)
    library(lubridate)
    library(tidyverse)
    library(dplyr)
    library(ggplot2)

\#Cleaning NMSS Data

## Konrad & Ramya: Cleaning donations data for 2013-2017:

Reading in the
    data:

    donations2013 <- read_csv("C:\\Users\\Konrad\\Desktop\\ETM 527\\Donations\\2013 Bike Donations Date Fixed.csv")
    donations2014 <- read_csv("C:\\Users\\Konrad\\Desktop\\ETM 527\\Donations\\2014 Bike Donations Date Fixed.csv")
    donations2015 <- read_csv("C:\\Users\\Konrad\\Desktop\\ETM 527\\Donations\\2015 Bike Donations Date Fixed.csv")
    donations2016 <- read_csv("C:\\Users\\Konrad\\Desktop\\ETM 527\\Donations\\2016 Bike Donations Date Fixed.csv")
    donations2017 <- read_csv("C:\\Users\\Konrad\\Desktop\\ETM 527\\Donations\\2017 Bike Donations Date Fixed.csv")

Comparing column names to make sure the data is in the right order and
all fields are the same:

    cols2013 <- colnames(donations2013)
    cols2014 <- colnames(donations2014)
    cols2015 <- colnames(donations2015)
    cols2016 <- colnames(donations2016)
    cols2017 <- colnames(donations2017)
    
    
    identical(cols2013, cols2014)
    identical(cols2013, cols2015)
    identical(cols2013, cols2016)
    identical(cols2013, cols2017)
    
    
    remove(cols2013, cols2014, cols2015, cols2016, cols2017)

Changing some columns to factors:

    cols <- c(1, 2, 3, 4, 6, 7, 10:19, 21:32, 35, 36, 38, 39, 44:49)
    donations2013[,cols] <- lapply(donations2013[,cols], factor)
    donations2014[,cols] <- lapply(donations2014[,cols], factor)
    donations2015[,cols] <- lapply(donations2015[,cols], factor)
    donations2016[,cols] <- lapply(donations2016[,cols], factor)
    donations2017[,cols] <- lapply(donations2017[,cols], factor)

### Refactoring certain columns:

#### Donor Gender:

    #summary(donations2013$`Donor Gender`)
    levels(donations2013$`Donor Gender`) <- list(Female=c("Female", "F", "Feiale"), Male=c("Male", "M", "Iale"))
    #summary(donations2013$`Donor Gender`)
    
    
    #summary(donations2014$`Donor Gender`)
    levels(donations2014$`Donor Gender`) <- list(Female=c("Female", "F", "Feiale"), Male=c("Male"))
    #summary(donations2014$`Donor Gender`)
    
    
    #summary(donations2015$`Donor Gender`)
    levels(donations2015$`Donor Gender`) <- list(Female=c("Female", "F", "Femala"), Male=c("Male"))
    #summary(donations2015$`Donor Gender`)
    
    
    #summary(donations2016$`Donor Gender`)
    levels(donations2016$`Donor Gender`) <- list(Female=c("Female", "F", "Femala"), Male=c("Male"))
    #summary(donations2016$`Donor Gender`)
    
    
    #summary(donations2017$`Donor Gender`)
    levels(donations2017$`Donor Gender`) <- list(Female=c("Female", "F", "Femala", "Famale"), Male=c("Male", "M"))
    #summary(donations2017$`Donor Gender`)

### Prior participants:

    #summary(donations2013$`Is Prior Participant`)
    levels(donations2013$`Is Prior Participant`) <- list(Yes = c("Yes"))
    #summary(donations2013$`Is Prior Participant`)
    
    
    #summary(donations2014$`Is Prior Participant`)
    levels(donations2014$`Is Prior Participant`) <- list(Yes = "Yes")
    #summary(donations2014$`Is Prior Participant`)
    
    
    #summary(donations2015$`Is Prior Participant`)
    levels(donations2015$`Is Prior Participant`) <- list(Yes = "Yes")
    #summary(donations2015$`Is Prior Participant`)
    
    
    #summary(donations2016$`Is Prior Participant`)
    levels(donations2016$`Is Prior Participant`) <- list(Yes = "Yes")
    #summary(donations2016$`Is Prior Participant`)
    
    
    #summary(donations2017$`Is Prior Participant`)
    levels(donations2017$`Is Prior Participant`) <- list(Yes = "Yes")
    #summary(donations2017$`Is Prior Participant`)

### Is Team Captain

    #summary(donations2013$`Is Team Captain`)
    levels(donations2013$`Is Team Captain`) <- list(Yes ="TRUE", No = "FALSE")
    #summary(donations2013$`Is Team Captain`)
    
    
    #summary(donations2014$`Is Team Captain`)
    levels(donations2014$`Is Team Captain`) <- list(Yes = c("TRUE", "PRUE"), No = "FALSE")
    #summary(donations2014$`Is Team Captain`)
    
    
    #summary(donations2015$`Is Team Captain`)
    levels(donations2015$`Is Team Captain`) <- list(Yes = "TRUE", No = c("FALSE", "BALSE"))
    #summary(donations2015$`Is Team Captain`)
    
    #summary(donations2016$`Is Team Captain`)
    levels(donations2016$`Is Team Captain`) <- list(Yes = c("TRUE", "PRUE"), No = "FALSE")
    #summary(donations2016$`Is Team Captain`)
    
    #summary(donations2017$`Is Team Captain`)
    levels(donations2017$`Is Team Captain`) <- list(Yes = c("TRUE"), No = c("FALSE", "BALSE", "FALSA"))
    #summary(donations2017$`Is Team Captain`)

### Gift Payment Method

``` 
#summary(donations2013$`Gift Payment Method`)
levels(donations2013$`Gift Payment Method`) <- list(Cash = "Cash", Check= "Check", `Credit Card` = "Credit Card")
#summary(donations2013$`Gift Payment Method`)


#summary(donations2014$`Gift Payment Method`)
levels(donations2014$`Gift Payment Method`) <- list(Cash = "Cash", Check= "Check", `Credit Card` = "Credit Card")
#summary(donations2014$`Gift Payment Method`)


#summary(donations2015$`Gift Payment Method`)
# No NAs or anything to refactor

#summary(donations2016$`Gift Payment Method`)
levels(donations2016$`Gift Payment Method`) <- list(Cash = "Cash", Check= "Check", `Credit Card` = c("Credit Card", "Credit Car"))
#summary(donations2016$`Gift Payment Method`)


#summary(donations2017$`Gift Payment Method`)
levels(donations2017$`Gift Payment Method`) <- list(Cash = "Cash", Check= "Check", `Credit Card` = c("Credit Card", "Credit Car"))
#summary(donations2017$`Gift Payment Method`)

```

### Gift Type

    #summary(donations2013$`Gift Type`)
    levels(donations2013$`Gift Type`) <- list(Offline=c("offline", "ofbline"), Online="online")
    #summary(donations2013$`Gift Type`)
    
    
    #summary(donations2014$`Gift Type`)
    levels(donations2014$`Gift Type`) <- list(Offline="offline", Online=c("online", "ojline"))
    #summary(donations2014$`Gift Type`)
    
    
    #summary(donations2015$`Gift Type`)
    levels(donations2015$`Gift Type`) <- list(Offline="offline", Online="online")
    #summary(donations2015$`Gift Type`)
    
    
    #summary(donations2016$`Gift Type`)
    levels(donations2016$`Gift Type`) <- list(Offline="offline", Online=c("online", "onhine", "onlina"))
    #summary(donations2016$`Gift Type`)
                 
    
    #summary(donations2017$`Gift Type`)
    levels(donations2017$`Gift Type`) <- list(Offline="offline", Online=c("online", "ojline", "onlina"))
    #summary(donations2017$`Gift Type`)

### Offline status

    summary(donations2013$`Offline Status`)
    summary(donations2014$`Offline Status`)
    summary(donations2015$`Offline Status`)
    summary(donations2016$`Offline Status`)
    levels(donations2016$`Offline Status`)<- list(confirmed = c("confirmed", "confirme`"), `Teamraiser Participant Gift` = c("(Teamraiser Participant Gift", "Teamraiser Participant Gift"))
    summary(donations2017$`Offline Status`)

### Dealing with dates

  - Date format was changed in Excel \* to eg 08/12/13 to enable easy
    conversion of
    dates.

<!-- end list -->

    #Since each dataset is the same, can identify all date fields from just 2013 data
    date_cols <- which(names(donations2013)%in%c("Event Date", "Date Recorded", "Donor Opt-out Date", "Registration Date", "Team Creation Date"))
    
    donations2013[, date_cols] <- lapply(donations2013[, date_cols], as.Date, "%m/%d/%y")
    donations2014[, date_cols] <- lapply(donations2014[, date_cols], as.Date, "%m/%d/%y")
    donations2015[, date_cols] <- lapply(donations2015[, date_cols], as.Date, "%m/%d/%y")
    donations2016[, date_cols] <- lapply(donations2016[, date_cols], as.Date, "%m/%d/%y")
    donations2017[, date_cols] <- lapply(donations2017[, date_cols], as.Date, "%m/%d/%y")

### Writing out Formatted Donations Data to an RDS file

``` 
saveRDS(donations2013, "C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2013.rds")
saveRDS(donations2014, "C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2014.rds")
saveRDS(donations2015, "C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2015.rds")
saveRDS(donations2016, "C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2016.rds")
saveRDS(donations2017, "C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2017.rds")

```

## Konrad: Cleaning Bike Teams Data

    teams <- read_csv("C:\\Users\\Konrad\\Desktop\\ETM 527\\Bike Teams\\2013-2017 Bike Teams Date Format Fixed.csv")

    #summary(teams)
    factor_cols <- c(1:5, 7, 8, 10, 11, 20:22, 26)
    teams[ ,factor_cols] <- lapply(teams[ ,factor_cols], factor)
    
    # Removed time from team creation date and Event Date (in Excel)!!! 
    
    teams$`Team Creation Date` <- as.Date(teams$`Team Creation Date`, format = '%m/%d/%y')
    teams$`Event Date` <- as.Date(teams$`Event Date`, format = '%m/%d/%y')
    
    summary(teams$`Team Division`)
    
    levels(teams$`Team Division`) <- list(Association = "Association", Brewery="Beer/Brewery", `Bike Club`="Bike Club", `Bike Shop` = c("Bike Shop", "Bike Shops"), `Civic Team` = "Civic Team", `Club/Organization` = "Club/Organization", Corporate = c("Corporate", "Corporation"), `Family/Friends` = c("Family and Friends", "Family/Friends", "Frien`s and Family", "Friend and Family", "Friends and Family"), Ohana = "Ohana", `Ohana/Friends` = "Ohana and Friends", Open = "Open", `Open Team` = "Open Team", Organization = c("Organization", "Organization (Clubs, Civic Groups, etc.)", "Organization (Clubs; Civic Groups; etc.)", "Organization (Clubs; Civic Groups; Place of Worship; etc.)"), Other = "Other", `Place of Worship` = c("Place of Worship", "Place of worship", "Religious"), School = "School", `Small Business` = "Small Business", `Volunteer Group` = "Volunteer Group")

    #summary(teams$`Event Type`)
    #summary(teams$`Internal Event Name`)
    #summary(teams$`Event ID`)
    #summary(teams$`Team Creation Date`)
    
    #summary(teams$`Captain Email Domain`)
    #summary(teams$Company)
    #summary(teams$`Team Name`)
    #summary(teams$`Number of Participants`)

    saveRDS(teams, "C:/Users/Konrad/Desktop/ETM 527/RDS Data/Bike Teams/teams.rds")

## Ramya: Cleaning Bike Events

    BikeEvents<-read.csv("C:\\Users\\Konrad\\Desktop\\ETM 527\\Events\\2013-2017 Bike Events.csv")

    str(BikeEvents)

    levels(BikeEvents$City)

    #Cleaning cities
    BikeEvents$City[BikeEvents$City == 'Athens, AL ']<- "Athens"
    
    BikeEvents$City[BikeEvents$City == 'Cherry Hill, NJ with alternate start locations']<-"Cherry Hill"
    #as.factor(BikeEvents$City[BikeEvents$City == 'Ridgeland, MS']<- "Ridgeland")
    
    BikeEvents$City[BikeEvents$City == 'St. Augustine ']<-"St. Augustine"
    
    BikeEvents$City[BikeEvents$City == 'Sioux Falls area']<-"Sioux Falls"
    
    BikeEvents$City[BikeEvents$City == 'Schodack ']<-"Schodack"
    
    BikeEvents$City[BikeEvents$City == 'San Antonio ']<-"San Antonio"
    
    BikeEvents$City[BikeEvents$City == 'New York City']<-"New York" 
    
    BikeEvents$City[BikeEvents$City == 'New Albany ']<-"New Albany"
    
    BikeEvents$City[BikeEvents$City == 'Keuka Park ']<-"Keuka Park"
    BikeEvents$City[BikeEvents$City == 'Hollidaysburg, PA to State College']<-"Hollidaysburg" 
    BikeEvents$City[BikeEvents$City == 'Duluth to White Bear Lake']<-"Duluth"
    BikeEvents$City[BikeEvents$City == 'Duluth to the Twin Cities']<-"Duluth"
    BikeEvents$City[BikeEvents$City == 'Fargo area']<-"Fargo"
    BikeEvents$City[BikeEvents$City == 'Dallas ']<-"Dallas"
    BikeEvents$City[BikeEvents$City == 'DeKalb']<-"Dekalb"
    BikeEvents$City[BikeEvents$City == 'DeKalb ']<-"Dekalb"

    summary(BikeEvents$Event.Date)

    #Date Conversion in R
    datecols_bikeevents<-which(names(BikeEvents)%in%c("Event.Created.Date", "Event.Date"))
    
    for (i in datecols_bikeevents) {
      BikeEvents[,i] = as.Date(BikeEvents[,i], '%m/%d/%y')
    }

## Saving the work

    saveRDS(BikeEvents, "C:/Users/Konrad/Desktop/ETM 527/RDS Data/Bike Events/Bike Events.rds")

## Jordan: Cleaning Bike Participants

### Import data

    participants <- read_csv("C:\\Users\\Konrad\\Desktop\\ETM 527\\Participants\\2013-2017 Bike MS Participants.csv")

### Basic data exploration

    class(participants)
    dim(participants)
    glimpse(participants)
    head(participants, n = 5)
    tail(participants, n = 5)
    summary(participants)

Able to see that some fields need to be converted from integers to
characters. Also, easily able to identify which fields will need to be
rid of NA values.

    # need to change fields from int to char 
    participants$`Team ID` <- as.character(participants$`Team ID`)
    class(participants$`Team ID`)
    participants$`Contact ID` <- as.character(participants$`Contact ID`)
    participants$`Address -  Participant ZIP/Postal Code` <- as.character(participants$`Address -  Participant ZIP/Postal Code`)
    participants$`Event ID` <- as.character(participants$`Event ID`)
    summary(participants)
    
    #change event date from character to date-time
    participants$`Event Date` <- mdy_hm(participants$`Event Date`)
    class(participants$`Event Date`)
    head(participants$`Event Date`, n = 5)

    # acknowledge NA's 
    map(participants, ~sum(is.na(.)))

## Writing out Jordan’s work

    saveRDS(participants, "C:/Users/Konrad/Desktop/ETM 527/RDS Data/Participants/Participants.rds")

    library(readr)
    library(dplyr)
    library(ggplot2)
    
    donations2013 <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2013.rds")
    donations2014 <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2014.rds")
    donations2015 <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2015.rds")
    donations2016 <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2016.rds")
    donations2017 <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2017.rds")
    
    participants <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Participants/Participants.rds")
    
    str(participants)

# Creating Data Aggregations

## From donations data

    gen_2013 <- summary(donations2013$`Donor Gender`)
    gen_2014 <- summary(donations2014$`Donor Gender`)
    gen_2015 <- summary(donations2015$`Donor Gender`)
    gen_2016 <- summary(donations2016$`Donor Gender`)
    gen_2017 <- summary(donations2017$`Donor Gender`)
    
    
    gender_year <- tibble(c(2013, 2014, 2015, 2016, 2017), 
                              c(gen_2013[1], gen_2014[1], gen_2015[1], gen_2016[1], gen_2017[1]), 
                              c(gen_2013[2], gen_2014[2], gen_2015[2], gen_2016[2], gen_2017[2]), 
                              c(gen_2013[3], gen_2014[3], gen_2015[3], gen_2016[3], gen_2017[3]))
                              
    colnames(gender_year) <- c("Year", "Female", "Male", "NA")
    
    
    year_num <- tibble(2013:2017, c(nrow(donations2013), nrow(donations2014), nrow(donations2015), nrow(donations2016), nrow(donations2017)))
    colnames(year_num) <- c("Year", "Number of Participants")
    
    
    tot_gifts2013 <- sum(donations2013$`Gift Amount($)`, na.rm = TRUE)
    tot_gifts2014 <- sum(donations2014$`Gift Amount($)`, na.rm = TRUE)
    tot_gifts2015 <- sum(donations2015$`Gift Amount($)`, na.rm = TRUE)
    tot_gifts2016 <- sum(donations2016$`Gift Amount($)`, na.rm = TRUE)
    tot_gifts2017 <- sum(donations2017$`Gift Amount($)`, na.rm = TRUE)
    
    med_gifts2013 <- median(donations2013$`Gift Amount($)`, na.rm = TRUE)
    med_gifts2014 <- median(donations2014$`Gift Amount($)`, na.rm = TRUE)
    med_gifts2015 <- median(donations2015$`Gift Amount($)`, na.rm = TRUE)
    med_gifts2016 <- median(donations2016$`Gift Amount($)`, na.rm = TRUE)
    med_gifts2017 <- median(donations2017$`Gift Amount($)`, na.rm = TRUE)
    
    tot_donations <- tibble(2013:2017,
                                c(tot_gifts2013, tot_gifts2014, tot_gifts2015, tot_gifts2016, tot_gifts2017),
                                c(med_gifts2013, med_gifts2014, med_gifts2015, med_gifts2016, med_gifts2017))
    
    colnames(tot_donations) <- c("Year", "Total Donations", "Median")
    
    add_tot_gifts2013 <- sum(donations2013$`Additional Gift Amount($)`, na.rm = TRUE)
    add_tot_gifts2014 <- sum(donations2014$`Additional Gift Amount($)`, na.rm = TRUE)
    add_tot_gifts2015 <- sum(donations2015$`Additional Gift Amount($)`, na.rm = TRUE)
    add_tot_gifts2016 <- sum(donations2016$`Additional Gift Amount($)`, na.rm = TRUE)
    add_tot_gifts2017 <- sum(donations2017$`Additional Gift Amount($)`, na.rm = TRUE)
    
    add_med_gifts2013 <- median(donations2013$`Additional Gift Amount($)`, na.rm = TRUE)
    add_med_gifts2014 <- median(donations2014$`Additional Gift Amount($)`, na.rm = TRUE)
    add_med_gifts2015 <- median(donations2015$`Additional Gift Amount($)`, na.rm = TRUE)
    add_med_gifts2016 <- median(donations2016$`Additional Gift Amount($)`, na.rm = TRUE)
    add_med_gifts2017 <- median(donations2017$`Additional Gift Amount($)`, na.rm = TRUE)
    
    add_donations <- tibble(2013:2017,
      c(add_tot_gifts2013, add_tot_gifts2014, add_tot_gifts2015, add_tot_gifts2016, add_tot_gifts2017), 
      c(add_med_gifts2013, add_med_gifts2014, add_med_gifts2015, add_med_gifts2016, add_med_gifts2017))
    
    colnames(add_donations) <- c("Year", "Additional Donations", "Median")

## Plotting donations data

``` 
ggplot(data = subset(donations2013, !is.na(`Donor Gender`))) + 
  geom_bar(aes(`Donor Gender`, fill = `Donor Gender`), na.rm = TRUE) + 
  xlab("Donor Gender") + 
  ylab("Count") + 
  ggtitle("2013 NMS Participants by gender")

ggplot(data = subset(donations2013, !is.na(`Gift Payment Method`))) + 
  geom_bar(aes(`Gift Payment Method`, fill = `Donor Gender`)) + 
  xlab("Gift Payment Method") + 
  ylab("Dollars") + 
  ggtitle("2013 NMS Gift Payment Method Types by Gender")

library(scales)
ggplot(tot_donations, aes(Year, `Total Donations`/1000000)) + 
  geom_bar(stat = "identity") + 
  scale_y_continuous(labels=dollar_format(prefix="$")) + 
  ylab("Gift Amount ($M)") + 
  ggtitle("Gift amounts have fallen every year since 2014") + 
  theme(plot.title = element_text(hjust = 0.5)) + 
  ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Gift amounts have fallen.png")


ggplot(add_donations, aes(Year, `Additional Donations`/1000000)) + 
  geom_bar(stat = "identity") + 
  scale_y_continuous(labels=dollar_format(prefix="$")) + 
  ylab("Additional gift Amount ($M)") + 
  ggtitle("Additional gift amounts were increasing but fell in 2017") + 
  theme(plot.title = element_text(hjust = 0.5)) + 
  ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Additional gift amounts were increasing.png")




colnames(add_donations)


ggplot() + 
  geom_bar(data = tot_donations, aes(Year, `Total Donations` / 1000000), stat = "identity") +
  geom_bar(data = add_donations, aes(Year, `Additional Donations` /1000000), stat = "identity", fill = "red", alpha = 0.6)  
  

participants <- tibble(2013:2017, c(nrow(donations2013), nrow(donations2014), nrow(donations2015), nrow(donations2016), nrow(donations2017)))

colnames(participants) <- c("Year", "Participants")

ggplot(participants) + 
  geom_bar(aes(x = Year, y = Participants), stat = "identity") + 
  ylim(0, 1000000) + 
  scale_y_continuous(labels= comma) +
  ggtitle("Number of participants has fallen every year since 2013") + 
  theme(plot.title = element_text(hjust = 0.5)) + 
  ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Number of participants has fallen.png")

  
don_per_part = tibble(2013:2017, tot_donations$`Total Donations` / participants$Participants)
colnames(don_per_part) <- c("Year", "Average Donation")

ggplot(don_per_part, aes(Year, `Average Donation`)) + 
  geom_bar(stat = "identity") + 
  ylab("Averate Gift Amount") + 
  ggtitle("Average gift per participant has increased every year since 2013") + 
    theme(plot.title = element_text(hjust = 0.5)) + 
  ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Average gift per participant has increased.png")


```

## Ramya’s Bike Events Data Aggregation

    #Average amount by total participants in all the states
    Amount_by_States<-aggregate(BikeEvents$Total.From.Participant..., by=list(State = BikeEvents$State), FUN = mean)
    head(Amount_by_States)

    #Amount raised by participants from 2013-2017
    Amount_by_year <-aggregate(BikeEvents$Total.From.Participant..., by = list(year = BikeEvents$Fiscal.Year), sum)
    Amount_by_year

    #selft donars over
    Donors_by_year <-aggregate(BikeEvents$Total.From.Participant..., by = list(year = BikeEvents$Fiscal.Year), sum)
    Donors_by_year

    #Active registrations overs the years
    Active_registrations <-aggregate(BikeEvents$Active.Registrations, by = list(year = BikeEvents$Fiscal.Year), sum)
    Active_registrations

## Ramya’s Plots

    library('ggplot2')
    Amounts_ggplot<-ggplot(Amount_by_States, aes(x=Amount_by_States$State,y=Amount_by_States$x))+ 
      theme(axis.text.x = element_text(face = "bold", size = 8, angle = 90))+
      geom_bar(stat = 'identity', fill = "blue")+
      ggtitle("Average amount raised by Bike Events participants across all the states") + 
      labs(x ='States', y = 'Average amount')

    Amounts_ggplot
    ggsave(filename="D:/527- Data Mining/TUN Data Challenge/Data Visualizations/Amounts_ggplot.pdf", plot=Amounts_ggplot)

    ggplot(Amount_by_year, aes(x = Amount_by_year$year, y = Amount_by_year$x)) +
      geom_bar(stat = 'identity', fill = "blue")+ggtitle("Participants amount to Bike events slightly decreasing since 2014") + 
      labs(x ='Year', y = 'Total amount')

``` 
#Donars by year
ggplot(Donors_by_year, aes(x = Donors_by_year$year, y = Donors_by_year$x))+
  geom_bar(stat = 'identity', fill = "blue")+ggtitle("Self donors gradually decreasing since 2014 ") + 
  labs(x ='Year', y = 'Total amount')

```

    #Donars by year
    ggplot(Active_registrations, aes(x = Active_registrations$year, y = Active_registrations$x)) +
      geom_bar(stat = 'identity', fill = "blue")+ggtitle("Active registrations have fallen since 2013 ") + 
      labs(x ='Year', y = 'No of registrations')

## Participants EDA

    # some basic data viz
    barplot(table(participants$`Participant Occupation`), ylab = "Count", main = "Occupations of our Participants",
            ylim = c(0,2500), las = 2, col=rgb(0.2,0.4,0.6,0.6))
    
    occ.count <- table(participants$`Participant Occupation`)
    occ.count
    occupation.viz <- ggplot(data = participants, aes(x = participants$`Participant Occupation`)) + 
      geom_bar(aes(y = (..count..), fill = `Participant Gender`)) +
      theme(axis.text.x = element_text(angle = 90, vjust = 0.5))
    
    occupation.viz + labs(x = "Occupations") + 
      labs(title = "Frequency of Participant Occupation") + 
      labs(y = "Count")

    library(readr)
    library(dplyr)
    library(ggplot2)
    library(scales)
    
    donations2013 <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2013.rds")
    donations2014 <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2014.rds")
    donations2015 <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2015.rds")
    donations2016 <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2016.rds")
    donations2017 <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Donations/Donations2017.rds")
    
    participants <- readRDS("C:/Users/Konrad/Desktop/ETM 527/RDS Data/Participants/Participants.rds")
    
    #summary(donations2017$`Donor Gender`)
    #levels(donations2017$`Donor Gender`) <- list(Male = "Male", Female = "Female", None = "")

# Creating Data Aggregations

## From donations data

    # gen_2013 <- summary(donations2013$`Donor Gender`)
    # gen_2014 <- summary(donations2014$`Donor Gender`)
    # gen_2015 <- summary(donations2015$`Donor Gender`)
    # gen_2016 <- summary(donations2016$`Donor Gender`)
    # gen_2017 <- summary(donations2017$`Donor Gender`)
    # 
    # 
    # gender_year <- tibble(c(2013, 2014, 2015, 2016, 2017), 
    #                           c(gen_2013[1], gen_2014[1], gen_2015[1], gen_2016[1], gen_2017[1]), 
    #                           c(gen_2013[2], gen_2014[2], gen_2015[2], gen_2016[2], gen_2017[2]), 
    #                           c(gen_2013[3], gen_2014[3], gen_2015[3], gen_2016[3], gen_2017[3]),
    #                           c(gen_2013[4], gen_2014[4], gen_2015[4], gen_2016[4], gen_2017[4]))
    #                           
    # colnames(gender_year) <- c("Year", "Female", "Male", "None", "NA")
    # 
    # 
    # year_num <- tibble(2013:2017, c(nrow(donations2013), nrow(donations2014), nrow(donations2015), nrow(donations2016), nrow(donations2017)))
    # colnames(year_num) <- c("Year", "Number of Participants")
    # 
    # 
    # tot_gifts2013 <- sum(donations2013$`Gift Amount($)`, na.rm = TRUE)
    # tot_gifts2014 <- sum(donations2014$`Gift Amount($)`, na.rm = TRUE)
    # tot_gifts2015 <- sum(donations2015$`Gift Amount($)`, na.rm = TRUE)
    # tot_gifts2016 <- sum(donations2016$`Gift Amount($)`, na.rm = TRUE)
    # tot_gifts2017 <- sum(donations2017$`Gift Amount($)`, na.rm = TRUE)
    # 
    # med_gifts2013 <- median(donations2013$`Gift Amount($)`, na.rm = TRUE)
    # med_gifts2014 <- median(donations2014$`Gift Amount($)`, na.rm = TRUE)
    # med_gifts2015 <- median(donations2015$`Gift Amount($)`, na.rm = TRUE)
    # med_gifts2016 <- median(donations2016$`Gift Amount($)`, na.rm = TRUE)
    # med_gifts2017 <- median(donations2017$`Gift Amount($)`, na.rm = TRUE)
    # 
    # mean_gifts2013 <- mean(donations2013$`Gift Amount($)`, na.rm = TRUE)
    # mean_gifts2014 <- mean(donations2014$`Gift Amount($)`, na.rm = TRUE)
    # mean_gifts2015 <- mean(donations2015$`Gift Amount($)`, na.rm = TRUE)
    # mean_gifts2016 <- mean(donations2016$`Gift Amount($)`, na.rm = TRUE)
    # mean_gifts2017 <- mean(donations2017$`Gift Amount($)`, na.rm = TRUE)
    # 
    # 
    # tot_donations <- tibble(2013:2017,
    #                             c(tot_gifts2013, tot_gifts2014, tot_gifts2015, tot_gifts2016, tot_gifts2017),
    #                             c(med_gifts2013, med_gifts2014, med_gifts2015, med_gifts2016, med_gifts2017), 
    #                             c(mean_gifts2013, mean_gifts2014, mean_gifts2015, mean_gifts2016, mean_gifts2017))
    # 
    # colnames(tot_donations) <- c("Year", "Total Donations", "Median", "Mean")
    # 
    # add_tot_gifts2013 <- sum(donations2013$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_tot_gifts2014 <- sum(donations2014$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_tot_gifts2015 <- sum(donations2015$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_tot_gifts2016 <- sum(donations2016$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_tot_gifts2017 <- sum(donations2017$`Additional Gift Amount($)`, na.rm = TRUE)
    # 
    # add_med_gifts2013 <- median(donations2013$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_med_gifts2014 <- median(donations2014$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_med_gifts2015 <- median(donations2015$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_med_gifts2016 <- median(donations2016$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_med_gifts2017 <- median(donations2017$`Additional Gift Amount($)`, na.rm = TRUE)
    # 
    # add_mean_gifts2013 <- mean(donations2013$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_mean_gifts2014 <- mean(donations2014$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_mean_gifts2015 <- mean(donations2015$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_mean_gifts2016 <- mean(donations2016$`Additional Gift Amount($)`, na.rm = TRUE)
    # add_mean_gifts2017 <- mean(donations2017$`Additional Gift Amount($)`, na.rm = TRUE)
    # 
    # 
    # add_donations <- tibble(2013:2017,
    #   c(add_tot_gifts2013, add_tot_gifts2014, add_tot_gifts2015, add_tot_gifts2016, add_tot_gifts2017), 
    #   c(add_med_gifts2013, add_med_gifts2014, add_med_gifts2015, add_med_gifts2016, add_med_gifts2017), 
    #   c(add_mean_gifts2013, add_mean_gifts2014, add_mean_gifts2015, add_mean_gifts2016, add_mean_gifts2017))
    # 
    # colnames(add_donations) <- c("Year", "Additional Donations", "Median", "Mean")
    # 
    # 
    # write_rds(tot_donations, "C:/Users/Konrad/Desktop/ETM 527/Calculated/Gift Amounts.rds")
    # write_rds(add_donations, "C:/Users/Konrad/Desktop/ETM 527/Calculated/Additional Amounts.rds")
    # write_rds(gender_year, "C:/Users/Konrad/Desktop/ETM 527/Calculated/Yearly Gender Breakdown.rds")
    # 
    # gen_tot_2013_gifts <- aggregate(donations2013$`Gift Amount($)`, by = list(donations2013$`Donor Gender`), FUN = sum)
    # gen_med_2013_gifts <- aggregate(donations2013$`Gift Amount($)`, by = list(donations2013$`Donor Gender`), FUN = median)  
    # gen_mean_2013_gifts <- aggregate(donations2013$`Gift Amount($)`, by = list(donations2013$`Donor Gender`), FUN = mean)
    # 
    # gen_tot_2014_gifts <- aggregate(donations2014$`Gift Amount($)`, by = list(donations2014$`Donor Gender`), FUN = sum)
    # gen_med_2014_gifts <- aggregate(donations2014$`Gift Amount($)`, by = list(donations2014$`Donor Gender`), FUN = median)  
    # gen_mean_2014_gifts <- aggregate(donations2014$`Gift Amount($)`, by = list(donations2014$`Donor Gender`), FUN = mean)
    # 
    # gen_tot_2015_gifts <- aggregate(donations2015$`Gift Amount($)`, by = list(donations2015$`Donor Gender`), FUN = sum)
    # gen_med_2015_gifts <- aggregate(donations2015$`Gift Amount($)`, by = list(donations2015$`Donor Gender`), FUN = median)  
    # gen_mean_2015_gifts <- aggregate(donations2015$`Gift Amount($)`, by = list(donations2015$`Donor Gender`), FUN = mean)
    # 
    # gen_tot_2016_gifts <- aggregate(donations2016$`Gift Amount($)`, by = list(donations2016$`Donor Gender`), FUN = sum)
    # gen_med_2016_gifts <- aggregate(donations2016$`Gift Amount($)`, by = list(donations2016$`Donor Gender`), FUN = median)  
    # gen_mean_2016_gifts <- aggregate(donations2016$`Gift Amount($)`, by = list(donations2016$`Donor Gender`), FUN = mean)
    # 
    # gen_tot_2017_gifts <- aggregate(donations2017$`Gift Amount($)`, by = list(donations2017$`Donor Gender`), FUN = sum)
    # gen_med_2017_gifts <- aggregate(donations2017$`Gift Amount($)`, by = list(donations2017$`Donor Gender`), FUN = median)  
    # gen_mean_2017_gifts <- aggregate(donations2017$`Gift Amount($)`, by = list(donations2017$`Donor Gender`), FUN = mean)
    # 
    # gender_year_totals <- rbind(gen_tot_2013_gifts, gen_tot_2014_gifts, gen_tot_2015_gifts, gen_tot_2016_gifts, gen_tot_2017_gifts)
    # 
    # gender_year_med <- rbind(gen_med_2013_gifts, gen_med_2014_gifts, gen_med_2015_gifts, gen_med_2016_gifts, gen_med_2017_gifts)
    # 
    # gender_year_mean <- rbind(gen_mean_2013_gifts, gen_mean_2014_gifts, gen_mean_2015_gifts, gen_mean_2016_gifts, gen_mean_2017_gifts)
    # 
    # gender_totals <- tibble(rep(2013:2017, each = 3), 
    #                         rep(c("Female", "Male", "None"), times = 5), 
    #                         gender_year_totals$x, 
    #                         gender_year_med$x, 
    #                         gender_year_mean$x)
    # 
    # colnames(gender_totals) <- c("Year", "Gender", "Total Gifts", "Median", "Mean")
    # 
    # write_rds(gender_totals, "C:/Users/Konrad/Desktop/ETM 527/Calculated/Gender Year Totals Breakdown.rds")

    tot_donations <- read_rds("C:/Users/Konrad/Desktop/ETM 527/Calculated/Gift Amounts.rds")
    add_donations <- read_rds("C:/Users/Konrad/Desktop/ETM 527/Calculated/Additional Amounts.rds")
    gender_year <- read_rds("C:/Users/Konrad/Desktop/ETM 527/Calculated/Yearly Gender Breakdown.rds")
    gender_totals <- read_rds("C:/Users/Konrad/Desktop/ETM 527/Calculated/Gender Year Totals Breakdown.rds")

##### Total Donations

    ggplot(tot_donations, aes(Year, `Total Donations`)) + 
      geom_bar(stat = "identity") + 
      scale_y_continuous(labels = comma) + 
      ylab("Participants") + 
      ggtitle("The number of participants has fallen every year since 2014") + 
      theme(plot.title = element_text(hjust = 0.5)) +
      theme(plot.title = element_text(size = 18, face = "bold")) #+
      #ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Participant numbers fallen.png")
    
    ggplot(participants, aes(`Fiscal Year`)) + 
      geom_bar() + 
      scale_y_continuous(labels = comma) + 
      ylab("Participants") + 
      xlab("Fiscal Year") + 
      ggtitle("Number of participants has decreased every year") + 
      theme(plot.title = element_text(hjust = 0.5)) + 
      theme(plot.title = element_text(size =18, face = "bold")) #+
      #ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Number of participants decreased every year.png", width = 10)

## Sum of Donations

    ggplot(tot_donations, aes(Year, `Total Donations`/1000000)) + 
      geom_bar(stat = "identity") + 
      scale_y_continuous(labels=dollar_format(prefix="$")) + 
      ylab("Gift Amount ($M)") + 
      ggtitle("Total gift amounts have fallen every year since 2014") + 
      theme(plot.title = element_text(hjust = 0.5)) #+ 
      #ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Gift amounts have fallen.png")

### Mean Donations

    ggplot(tot_donations, aes(Year, Mean)) + 
      geom_bar(stat = "identity") + 
      scale_y_continuous(labels=dollar_format(prefix="$")) + 
      ylab("Gift Amount") + 
      ggtitle("Mean gift amount continues to rise") + 
      theme(plot.title = element_text(hjust = 0.5)) #+ 
      #ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Gift amounts have fallen.png")

### Median Donations

    ggplot(tot_donations, aes(Year, Median)) + 
      geom_bar(stat = "identity") + 
      scale_y_continuous(labels=dollar_format(prefix="$")) + 
      ylab("Gift Amount") + 
      ggtitle("Median gift amount remains unchanged") + 
      theme(plot.title = element_text(hjust = 0.5)) #+ 
      #ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Gift amounts have fallen.png")

##### Gender Totals

``` 
ggplot(gender_totals[order(gender_totals$Gender),], aes(Year, `Total Gifts`/1000000, fill = Gender)) + 
  geom_bar(stat = "identity") + 
  scale_y_continuous(labels=dollar_format(prefix="$", suffix = "M")) + 
  scale_fill_manual(values=c("#A92A2A", "#205A8F", "#B4BFC3")) +
  ylab("Gift Amount (M)") + 
  ggtitle("Total gift amount has decreased") + 
  theme(plot.title = element_text(hjust = 0.5)) +
  theme(plot.title = element_text(size =18, face = "bold")) #+
  #ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Total gift amounts by gender.png", width = 12)

ggplot(gender_totals, aes(Year, Median, fill = Gender)) + 
  geom_bar(stat = "identity", position = "dodge") + 
  scale_y_continuous(labels=dollar_format(prefix="$")) + 
  scale_fill_manual(values=c("#A92A2A", "#205A8F", "#B4BFC3")) +
  ylab("Gift Amount ($)") + 
  ggtitle("Median gift amount remains unchanged") + 
  theme(plot.title = element_text(hjust = 0.5)) + 
  theme(plot.title = element_text(size =18, face = "bold")) #+
  #ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Median gift amounts by gender.png", width = 12)


ggplot(gender_totals, aes(Year, Mean, fill = Gender)) + 
  geom_bar(stat = "identity", position = "dodge") + 
  scale_y_continuous(labels=dollar_format(prefix="$")) +  
  scale_fill_manual(values = c("#A92A2A", "#205A8F", "#B4BFC3")) +
  ylab("Gift Amount ($)") + 
  ggtitle("Mean gift amount has fluctuated") + 
  theme(plot.title = element_text(hjust = 0.5)) + 
  theme(plot.title = element_text(size =18, face = "bold")) #+
  #ggsave("C:\\Users\\Konrad\\Desktop\\ETM 527\\Mean gift amounts by gender.png", width = 12)

```

    library(dplyr)
    library(magrittr)
    library(tidyr)
    library(knitr)
    library(tibble)
    library(readxl)
    library(graphics)
    library(ggplot2)
    library(scales)
    library(RColorBrewer)

    nt <-
    read_excel("C:/Users/eva/Documents/ETM 527/Data Challenge 2018/National Teams/2013-2017 National Team Activity.xlsx", skip = 1, na = c("NA", " ", "-999"),
               col_types = c("text", "text", "text", 
                             "text", "text", "text", "date", "text", 
                             "numeric", "numeric", "numeric", 
                             "numeric", "numeric", "text", "text", 
                             "text", "text", "text", "text", "text", 
                             "text", "numeric", "text", "text", 
                             "text", "text", "text"))
    
    dim(nt)

    #Removing the "Corporate Name" field as it was blank for all recornt
    nt$'Corporate Name' <- NULL
    str(nt)

``` 
nt$`Event Chapter` <- as.factor(nt$`Event Chapter`)
nt$`Event Category` <- as.factor(nt$`Event Category`)
nt$`Event Type` <- as.factor(nt$`Event Type`)
nt$`Local Team Name` <- as.factor(nt$`Local Team Name`)
nt$`Event Name` <- as.factor(nt$`Event Name`)
nt$Location <- as.factor(nt$Location)

cols_to_factor <- 12:ncol(nt)

nt[, cols_to_factor] <- lapply(nt[, cols_to_factor], as.factor) 
```

    # Fill down team names
    for (i in 2:nrow(nt))
    {
      if (is.na(nt$`National Team Name`[i]) & !is.na(nt$`National Team Name`[i-1]))
      {
        nt$`National Team Name`[i] <- nt$`National Team Name`[i-1]
      }
    }
    View(nt)

``` 
# add NA in the Team Name where applicable
nt$`National Team Name` <- as.factor(nt$`National Team Name`)
summary(nt$`National Team Name`)

nt$`National Team Name`[nt$`National Team Name` == "N/A"] <- NA  #selects all matching rows and changes to NA
summary(nt$`National Team Name`)

```

``` 


Not.National.Team = subset(nt, is.na(nt$`National Team Name`), select =`National Team Name`:`Primary Connection To MS`)
Not.National.Team = Not.National.Team[,c(5,6,2,3,4,7:26)]

nt <- nt[which(!is.na(nt$`National Team Name`)),]
nt <- nt[which(!is.na(nt$`Local Team Name`)),]
```

    NameLocation <- nt$Location
    summary(NameLocation)
    BlankLocation <- nt[which(is.na(nt$Location)), ]
    View(BlankLocation)

``` 


```

``` 

View(nt)

sink("C:/Users/eva/Documents/ETM 527/Data Challenge 2018/National Teams/National Teams Basic Exploration.txt")
class(nt)
dim(nt)
glimpse(nt)
head(nt)
tail(nt)
summary(nt)
str(nt)
sink()
```

    library(dplyr)
    teams.count = count(nt,team =nt$`National Team Name`)
    teams.count$team = factor(teams.count$team, levels = teams.count$team[order(teams.count$n)])
    filter.top.count = filter(teams.count,n>15)

    ggplot(filter.top.count, aes(team,n)) + 
      geom_bar(stat = "identity", aes(`team`, fill = `team`)) + coord_flip()+theme(axis.text=element_text(size=7),
            axis.title=element_text(size=14,face="bold"))+
      ylab("Count") + 
      xlab("National Team") + 
      ggtitle("2013 NMSS National Team Participation")+
      scale_size_continuous()
    ggsave("C:/Users/eva/Documents/ETM 527/Data Challenge 2018/National Teams/National Team Participation.png")

    Teams.Revenue = nt[c(1, 9)]
    Teams.Revenue = aggregate(Teams.Revenue$`Revenue Raised`, by=list(`National Team Name`=Teams.Revenue$`National Team Name`), FUN=sum)
    names(Teams.Revenue) = c("National Team Name", "Total Revenue Raised")
    Teams.Revenue$`National Team Name` = factor(Teams.Revenue$`National Team Name`, levels = Teams.Revenue$`National Team Name`[order(Teams.Revenue$`Total Revenue Raised`)])
    filter.top.revenue = filter(Teams.Revenue,`Total Revenue Raised`>100000)

    ggplot(filter.top.revenue, aes(`National Team Name`, `Total Revenue Raised`/10000))+ 
      geom_bar(stat = "identity", aes(`National Team Name`, fill = `National Team Name`)) +
      scale_y_continuous(labels=dollar_format(prefix="$"))+
      ylab("Total Revenue Raised (in 10 thousands)") + 
      xlab("National Team Name") +   coord_flip()+ 
      ggtitle("2013 NMSS Top Fundraising National Teams")+ scale_fill_discrete(breaks = rev(levels(filter.top.revenue$`National Team Name`)))
    scale_size_continuous()
    ggsave("C:/Users/eva/Documents/ETM 527/Data Challenge 2018/National Teams/Visuals/Top Funraising National Team.png")

    Connection = count(Not.National.Team, pcms=Not.National.Team$`Primary Connection To MS`)
    Connection2 = count(nt, pcms=nt$`Primary Connection To MS`)
    
    Connection$pcms = factor(Connection$pcms, levels = Connection$pcms[order(Connection$n)])
    Connection2$pcms = factor(Connection2$pcms, levels = Connection2$pcms[order(Connection2$n)])
    
    connect <- cbind(Connection,Connection2)
    connect <- cbind(Connection, Connection2[,2])
    
    Connect <- rowSums(connect[2:3]) 
    connect <- cbind(connect,Connect)
    
    connect <- connect[,c(1,4)]
    connect$Connect <- as.integer(connect$Connect)
    connect$pcms = factor(connect$pcms, levels = connect$pcms[order(connect$Connect)])
    connect <- arrange(connect, desc(Connect))
    
    names(connect) = c("Primary Connection to MS", "Number of Participants")

``` 
ggplot(connect, aes(`Primary Connection to MS`, `Number of Participants`))+
   geom_bar(stat =  "identity", aes(`Primary Connection to MS`, fill = `Primary Connection to MS`))+
   xlab("Primary Connection To MS") +
   ylab("Number of Team Members") + coord_flip() + theme(axis.text=element_text(size=7),
        axis.title=element_text(size=14,face="bold"))+
   ggtitle("2013 NMSS Primary Connection to MS National & Not National Teams")+
   scale_size_continuous()+ scale_y_continuous()
ggsave("C:/Users/eva/Documents/ETM 527/Data Challenge 2018/National Teams/Visuals/Primary Connection to MS.png")

```

    # SaveRDS
    saveRDS(nt,"National_Teams_cleaned")
    saveRDS(Not.National.Team,"Not_Nationa_Team_from_NT")

# Business question : What is the common denominator for our top performing corporate teams?

\#(Is it industry, culture, executive involvement, connection to MS,
other?)

    library(tidyverse)
    library(ggpubr)
    library(ggplot2)
    library(magrittr)

# just want corporate teams

    corp <- teams %>%
      select(everything()) %>%
      filter(`Team Division` == "Corporate")

# clean up

    corp$`Fiscal Year` <- as.factor(corp$`Fiscal Year`)
    corp$`Team Goal($)` <- as.numeric(corp$`Team Goal($)`)
    corp$`Number of Participants` <- as.numeric(corp$`Number of Participants`)
    corp$Company[corp$Company == "Team BP"] <- "BP"

# try some correlations

    corp.goal.part <- cor(corp$`Team Goal($)`, corp$`Number of Participants`, method = "pearson", use = "complete.obs")
    summary(corp.goal.part)
    
    plot(x, y, main = "Correlation : Team Goal Increase with More Team Members",
         xlab = "Number of Participants", ylab = "Total Team Gift",
         pch = 19, frame = FALSE)
    abline(lm(y ~ x, data = corp), col = "blue")

# number of participats

    corp.event <- corp %>%
      select(`Internal Event Name`, `Fiscal Year`, `Number of Participants`, Company) %>%
      group_by(`Fiscal Year`, Company) %>%
      filter(!is.na(Company))
    
    corp.event.participants <- corp.event %>%
      select(`Fiscal Year`, `Number of Participants`, Company) %>%
      group_by(`Fiscal Year`, Company) %>%
      summarise(sum(`Number of Participants`))
    
    colnames(corp.event.participants)[3] <- "N"
    
    year.participants <- corp.event.participants %>%
      select(`Fiscal Year`, `N`) %>%
      group_by(`Fiscal Year`) %>%
      summarise(sum(N))

# top 10 corps

    top.10.corp <- corp %>%
      select(everything()) %>%
      group_by(Company) %>%
      filter(!is.na(Company)) %>%
      summarise(sum(`Total Confirmed Gifts in Team History($)`)) %>%
      top_n(10)

# dataframe of vars for top corps

    top.corps <- top.10.corp$Company
    
    top.corps.common <- corp %>%
      select(everything()) %>%
      filter(Company %in% top.corps)

# trying to time series

    corp$`Event Date` <- as.Date(corp$`Event Date`, "%m/%d/%Y")
    top.corps.common$`Date` <- as.Date(top.corps.common$`Event Date`, "%m/%d/%Y")
    top.corps.common$DateYear <- lubridate::year(top.corps.common$Date)
    
    corp.gift.ts <- ts(corp$`Team Total Confirmed ($)`, frequency = , start = 2013)
    
    tsData <- top.corps.common[,28]
    decomposeRes <- decompose(tsData, type = "additive")

# ggplot number of participants for top corp teams

    corp.event.viz <- ggplot(top.corps.common, aes(x = `Date`, y = `Number of Participants`, fill = Company)) +
      geom_area()
    corp.event.viz

# plotly avg number of participants for top corporate teams

    avg.participants.top.corps <- top.corps.common %>%
      select(Company, `Number of Participants`) %>%
      group_by(Company) %>%
      summarise(avg = mean(`Number of Participants`))
    
    density <- density(avg.participants.top.corps$`avg`)
    
    overall.avg.number.participants <- plotly::plot_ly(x = ~density$x, y = ~density$y, type = 'scatter', mode = 'lines', fill = 'tozeroy') %>%
      layout(xaxis = list(title = 'Number of Participants'),
             yaxis = list(title = 'Density'))
    overall.avg.number.participants

# area for each company

    top.corps.participants <- top.corps.common %>%
      select(Company, `Event ID`, `Number of Participants`) %>%
      filter(Company %in% top.corps) %>%
      group_by(Company,`Event ID`) %>%
      summarise(sum = sum(`Number of Participants`))
    
    Company %in% top.corps
    
    team1 <- top.corps.common[which(top.corps.participants$Company == "BP"),]
    density1 <- density(team1$`Number of Participants`)
    
    team2 <- top.corps.common[which(top.corps.participants$Company == "Calpine Corporation"),]
    density2 <- density(team2$`Number of Participants`)
    
    team3 <- top.corps.common[which(top.corps.participants$Company == "CGG"),]
    density3 <- density(team3$`Number of Participants`)
    
    team4 <- top.corps.common[which(top.corps.participants$Company == "ConocoPhillips"),]
    density4 <- density(team4$`Number of Participants`)
    
    team5 <- top.corps.common[which(top.corps.participants$Company == "ExxonMobil Cycling Team"),]
    density5 <- density(team5$`Number of Participants`)
    
    team6 <- top.corps.common[which(top.corps.participants$Company == "Noble Drilling Services Inc."),]
    density6 <- density(team6$`Number of Participants`)
    
    team7 <- top.corps.common[which(top.corps.participants$Company == "Saint Arnold Brewing Company"),]
    density7 <- density(team7$`Number of Participants`)
    
    team8 <- top.corps.common[which(top.corps.participants$Company == "Salesforce Bike MS"),]
    density8 <- density(team8$`Number of Participants`)
    
    team9 <- top.corps.common[which(top.corps.participants$Company == "Team Shell"),]
    density9 <- density(team9$`Number of Participants`)
    
    team10 <- top.corps.common[which(top.corps.participants$Company == "The Houstonian Club, Hotel and Spa"),]
    density10 <- density(team10$`Number of Participants`)
    
    top.corps.participants.viz <- plot_ly(x = ~density1$x, y = ~density1$y, type = 'scatter', mode = 'lines', name = 'BP', fill = 'tozeroy') %>%
      add_trace(x = ~density2$x, y = ~density2$y, name = 'Calpine Corporation', fill = 'tozeroy') %>%
      add_trace(x = ~density3$x, y = ~density3$y, name = 'CGG', fill = 'tozeroy') %>%
      add_trace(x = ~density4$x, y = ~density4$y, name = 'ConocoPhillips', fill = 'tozeroy') %>%
      add_trace(x = ~density5$x, y = ~density5$y, name = 'ExxonMobil Cycling Team', fill = 'tozeroy') %>%
      add_trace(x = ~density6$x, y = ~density6$y, name = 'Noble Drilling Services Inc.', fill = 'tozeroy') %>%
      add_trace(x = ~density7$x, y = ~density7$y, name = 'Saint Arnold Brewing Company', fill = 'tozeroy') %>%
      add_trace(x = ~density8$x, y = ~density8$y, name = 'Salesforce Bike MS', fill = 'tozeroy') %>%
      add_trace(x = ~density9$x, y = ~density9$y, name = 'Team Shell', fill = 'tozeroy') %>%
      add_trace(x = ~density10$x, y = ~density10$y, name = 'The Houstonian Club, Hotel and Spa', fill = 'tozeroy') %>%
      layout(xaxis = list(title = 'Number of Participants per Event'),
             yaxis = list(title = 'Density'),
             main)
    top.corps.participants.viz

# stream plots

    corp.density.link = api_create(top.corps.participants.viz, filename="Participant Density for Top Corporate Teams")
    corp.density.link

    east.health.viz <- ggplot(east.health, aes(x = reorder(`Participant State`, -Count), 
                                               y = `Count`,
                                               fill = `Participant State`)) + 
      geom_bar(stat = "identity")
    east.health.viz +
      labs(x = "Number of Participants",
           y = "State",
           title = "Number of Cyclists Working in Healthcare Within the Target Region")

# mean donation for each event

    gender.gifts <- gender.vip %>%
      select(`Participant Gender`, `Event Date`, `Total From Participant($)`) %>%
      group_by(`Participant Gender`, `Event Date`)
    gender.gifts$`Event Date` <- as.Date(gender.gifts$`Event Date`)
    gender.gifts <- aggregate(gender.vip, by = list(gender.vip$`Participant Gender`, gender.vip$`Event Date`), FUN = mean)
    gender.gifts <-gender.gifts[,c(1,2,9)]
    colnames(gender.gifts) <- c("Gender", "Event Date", "Gift Amount")
    gender.gifts
    
    gender.gifts$`Event Date` <- as.Date(gender.gifts$`Event Date`)
    gender.gif <- aggregate(gender.gifts, by = list(gender.gifts$`Gender`, gender.gifts$`Event Date`), FUN = mean)
    gender.gif <-gender.gif[,c(1,2,5)]
    colnames(gender.gif) <- c("Gender", "Event Date", "Gift Amount")

# mean donation for each fiscal year

    gender.gifts.year <- aggregate(gender.vip, by = list(gender.vip$`Participant Gender`, gender.vip$`Fiscal Year`), FUN = mean)
    gender.gifts.year <-gender.gifts.year[,c(1,2,9)]
    colnames(gender.gifts.year) <- c("Gender", "Year", "Gift Amount")
    gender.gifts.year
      
    g.gift.year.viz <- ggplot(data = gender.gifts.year, 
                         aes(x = gender.gifts.year$Year, y = gender.gifts.year$`Gift Amount`, fill = gender.gifts.year$Gender)) +
      geom_bar(stat = "identity", position = "dodge")
    g.gift.year.viz +
      labs(title = "Mean Participant Donation per Year by Gender") +
      labs(x = "Fiscal Year") +
      labs(y = "Gift Amount")

    event.gifts <- aggregate(gender.vip, by = list(gender.vip$`Event Name`, gender.vip$`Fiscal Year`), FUN = mean)
    event.gifts <- event.gifts[,c(1,3,9)]
    as.data.frame(event.gifts)
    colnames(event.gifts) <- c("Event", "Date", "Gift Amount")
    
    event.gifts$Year <- format(event.gifts$Date, "%Y")
    event.gifts$Month <- format(event.gifts$Date, "%b")
    event.gifts$Day <- format(event.gifts$Date, "%d")
    event.gifts$CommonDate <- as.Date(as.character(as.POSIXct(event.gifts$Date)))
    
    event.viz <- ggplot(data = event.gifts, mapping = aes(x = CommonDate, y = `Gift Amount`, shape = Year, colour = Year)) +
        geom_point() +
        geom_line(aes(group = 1))
    event.viz <- event.viz + 
      facet_wrap(~Year, ncol = 1, scales = "free_x") + theme_bw() + 
      theme(axis.text.x = element_text(angle = 90, vjust = 0.5)) +
      scale_y_continuous() +
      scale_x_date(labels = date_format("%d-%b"), breaks = date_breaks("2 weeks"))
    event.viz

    participants.event <- as.data.frame(
      participants %>%
        select(`Member ID`, `Internal Event Name`) %>%
        group_by(`Internal Event Name`) %>%
        tally()
    )
    participants.event <- arrange(participants.event, desc(n))
    participants.event
    
    participants.annual <- as.data.frame(
      participants %>%
        select(`Member ID`, `Fiscal Year`) %>%
        group_by(`Fiscal Year`) %>%
        tally()
    )
    participants.annual

    class(participants)
    dim(participants)
    glimpse(participants)
    head(participants, n = 5)
    tail(participants, n = 5)
    summary(participants)

    # acknowledge NA's 
    map(participants, ~sum(is.na(.)))

    participants.dt <- data.table(gender.vip)
    
    setkey(participants.dt, `Participant Occupation`, `Total From Participant($)`)
    
    participants.dt[,print(.SD), by = `Participant Occupation`]
    
    #participants.dt <- participants.dt[,.[(-`Total From Participant($)`)],
    #                                   by=list(`Participant Occupation`, `Total From #Participant($)`)]
    
    total.occ.gift <- participants.dt[,.(Total.Gift=sum(`Total From Participant($)`)), by = `Participant Occupation`][order(-Total.Gift)]
    
    occ.total <- ggplot(total.occ.gift, aes(x = `Participant Occupation`)) +
      geom_bar(stat = "identity", aes(y = Total.Gift))
    occ.total
    
    avg.occ.gift <- participants.dt[,(Avg.Gift=mean(`Total From Participant($)`)),by=.(`Participant Occupation`)][order(-V1)]
    
    # std.dev for each participant grouped by occupation
    setkey(participants.dt, `Participant Occupation`)
    participants.dt["Retail Wholesale",(Sd.V3=sd(`Total From Participant($)`))]
    participants.dt["Retail Wholesale",]
    
    # employer
    setkey(participants.dt, `Participant Employer`)
    participants.dt[,.N, by = `Participant Employer`][order(-N)]
    setorder(setDT(participants.dt), -`Participant Employer`)[, head(.SD, 10), keyby][,.N, by = `Participant Employer`]
    employer <- ggplot(participants.dt, aes(x = `Participant Employer`)) +
      geom_bar()
    employer

# some basic data viz

    barplot(table(participants$`Participant Occupation`), ylab = "Count", main = "Occupations of our Participants",
            ylim = c(0,2500), las = 2, col=rgb(0.2,0.4,0.6,0.6))
    occ.count <- table(participants$`Participant Occupation`)
    occ.count
    
    occupation.omitNA <- data.table(occupation.omitNA)
    setkey(occupation.omitNA, `Participant Occupation`, `Participant Gender`)
    occupation.omitNA <- participants[!is.na(participants$`Participant Occupation`),]
    occ.count.omit.na <- occupation.omitNA[,.N, by=.(`Participant Occupation`,`Participant Gender`)]
    occ.count.omit.na <- occ.count.omit.na[!is.na(`Participant Gender`)][order(-`N`)]
    setnames(occ.count.omit.na, old = "V1", new = "Occupation")

# Occupation Demographic

    top20.occupations.viz <- ggplot(data = occ.count.omit.na, aes(x = occupation.omitNA$`Participant Occupation`)) + 
      geom_bar(na.rm = TRUE, aes(y = (..count..), fill = `Participant Gender`)) +
      theme(axis.text.x = element_text(angle = 90, vjust = 0.5))
    top20.occupations.viz <- top20.occupations.viz + 
      labs(x = "Occupations") + 
      labs(title = "Frequency of Participant Occupation") + 
      labs(y = "Count")
    top20.occupations.viz

# Occupation Demographic

    top20.occupations.viz <- ggplot(data = occ.count.omit.na, aes(x = reorder(`Participant Occupation`, -`N`), 
                                                                  y = `N`, fill = `Participant Gender`)) + 
      geom_bar(stat = "identity") +
      theme(axis.text.x = element_text(angle = 90, vjust = 0.5))
    top20.occupations.viz <- top20.occupations.viz + 
      labs(x = "Occupations") + 
      labs(title = "Frequency of Participant Occupation") + 
      labs(y = "Count")
    top20.occupations.viz

# Prior Participant? Yes - No?

    prior.par.bar <- barplot(table(participants$`Is Prior Participant`), ylab = "Count", main = "Count of Prior Participants",
            ylim = c(0,300000), las = 2, col=rgb(0.2,0.4,0.6,0.6))

# Team division bar plot

    team.division.bar <- barplot(table(participants$`Team Division`), ylab = "Count", main = "Team Division Demographic",
            ylim = c(0,30000), las = 2, col=rgb(0.2,0.4,0.6,0.6))

    g.year.viz <- ggplot(data = gender.year, 
                         aes(x = Year, y = Count))+
      geom_bar(stat = "identity", position = "dodge")
    g.year.viz +
      labs(title = "Annual Participant Count") +
      labs(x = "Event Year") +
      labs(y = "Count")
    
    gt.count <- aggregate(gender.vip$`Participant Gender` ~ gender.vip$`Fiscal Year`, data = gender.vip, FUN = length)
    colnames(gt.count) <- c("Year", "Count")
    gt.count

### prep for voronoi

    topEvents18 <- read_csv("C:\\Users\\J-Blazer\\Documents\\ETM 527\\topEvents18.csv")
    cities.proj <- mapproject(topEvents18$Lon, topEvents18$Lat, "albers", param=c(30,40))
    par(mar=c(0,0,0,0))
    plot(cities.proj, asp=1, type="n", bty="n", xlab="", ylab="", axes = FALSE)
    points(cities.proj, pch=20, cex=0.1, col="red")
    topEventsVorn <- deldir(cities.proj$x, cities.proj$y)
    plot(topEventsVorn, wlines="tess", wpoints="none", number=FALSE, add=TRUE, lty=1)

### Can we quantify the effect competing events are having in our top markets?

    library(dplyr)
    library(ggplot2)

    Bike_events = readRDS("D:/527- Data Mining/TUN Data Challenge/Datasets/Bike_Events.rds")

    # these are top markets in  terms of active registrations pulled from Bike events
    markets = c("TX","PA","MN","NY","MA","NC","CO","OH","CA","KS","MO","WA","CA","IL","NJ")
    
    #retrieving active registrations for top markets
    All.events.registrations = Bike_events%>%
      select(Security.Category.Name,Fiscal.Year,State,Active.Registrations)%>%
      group_by(Security.Category.Name,Fiscal.Year,State)%>%
      summarise(sum(Active.Registrations))%>%
      filter(State %in% markets)
    write.table(All.events.registrations,"Events.registrations.State.csv", sep = ",")

    All.events.funds = Bike_events%>%
      select(Security.Category.Name,Fiscal.Year,Total.of.All.Confirmed.Gifts...,Total.Event.Gifts...,Total.From.Participant...,Total.Team.Gifts...,Total.Not.From.Participant...,City,State)%>%
      group_by(Security.Category.Name,Fiscal.Year,State)%>%
       filter(State %in% markets)

    All.events.funds$TotalAmount = rowSums(All.events.funds[,3:7])

    All.events.funds=All.events.funds%>%
      select(Security.Category.Name,Fiscal.Year,Total.of.All.Confirmed.Gifts...,Total.Event.Gifts...,Total.From.Participant...,Total.Team.Gifts...,Total.Not.From.Participant...,City,State,TotalAmount)%>%
      group_by(Security.Category.Name,Fiscal.Year,State)%>%
      summarise(sum(TotalAmount))

    write.table(All.events.funds,"All.events.funds.csv", sep = ",")
