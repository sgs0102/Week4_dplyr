# Week4_dplyr
Week4 dplyr assignment


#Week 4: dplyr package
getwd()
setwd("C:/Users/Shreyesh Shetty/Documents/R_ANA-500")

#Task: Write the function to get a dataset from Base R: HairEyeColor
#and give the dataset a new name of your choice

HairEyeColor
hair_eye_color<-data.frame(HairEyeColor)

#See the top rows of the data
#TASK: Write the function to see the top rows of the data

head(hair_eye_color)

#Install and call the package dplyr
#TASK: Write the functions to install and call dplyr
install.packages("dplyr")
library(dplyr)

#Let's just see the hair and sex columns
#Task: Write the function to 'select' just the hair and sex columns 
#(hint: use the 'select' function)

hair_eye_color %>% select(Hair,Sex)

#Let's name the dataset with just the two columns, Hair and Sex
#TASK: Write the function to save the two columns as a new dataset
#and give it a name

Hair_sex<- hair_eye_color %>% select(Hair,Sex)

#Let's get rid of the Sex column in the new dataset created above
#TASK: Write the function that deselects the sex column
#(hint: use the 'select' function to not select a -column)


Hair_sex %>% select(!Sex)

#Let's rename a column name
#TASK: Write the function that renames 'sex' to 'gender'

Hair_sex %>% rename(Gender = Sex)
hair_eye_color%>% rename(Gender = Sex)


#Let's make a new dataset with the new column name
#TASK: Write the function that names a new dataset that includes the 'gender' column

hair_eyecolor=rename(hair_eye_color,Gender=Sex) 
View(hair_eyecolor)

#Let's 'filter' just the males from our dataset
#TASK: Write the function that includes only rows that are 'male'

Male_hair_eye_color<- hair_eyecolor%>% filter(Gender =="Male")

#Let's 'group' our data by gender
#TASK: Write the function to group the data by gender (hint: group_by)

group_data<-group_by(hair_eyecolor,Gender)

#Let's see how many students were examined in the dataset (total the frequency)
#TASK: replace 'datasetname' with the name of your dataset and get the total
#After you run it, write the total here:313
total=mutate(group_data, total=cumsum(Freq))


#Since we have a males dataset, let's make a females dataset
#TASK: Write the function that includes only rows that are 'female'

Female_hair_eye_color<- hair_eyecolor%>% filter(Gender =="Female")

#And now let's join the males and females
#TASK: Write the function that joins the male and female rows 
#(hint: try using 'union' or 'bind_rows')

total_haireyecolor<- union_all(Male_hair_eye_color,Female_hair_eye_color)

#Optional Task: add any of the other functions 
#you learned about from the dplyr package

total_haireyecolor %>% relocate(Gender:Freq,.before=Eye)
