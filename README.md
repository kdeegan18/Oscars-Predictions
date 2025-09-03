# Oscars-Predictions
# This was a program I completed in April to predict the winner of Best Picture 2025, completed in R Studio

oscars <- read.csv("oscars.csv",header = TRUE) 
attach(oscars) 
# Create a subset to analyse the movies before 2024 
OscarsSubset <- subset(oscars, ï..Year < 2024) 
# Unexpectedly, the attached data was saving the Year column as ï..Year 

# Redefine 2s to 0s 
OscarsSubset$Ch <- ifelse(OscarsSubset$Ch == 2, 0, 1) 
# Redifine 0s and 1s 
OscarsSubset$Ch <- factor(OscarsSubset$Ch, levels = c(0, 1), labels = c("Didn't Win", "Win")) 
contrasts(OscarsSubset$Ch) <- contr.treatment(2) 
 
# To check that the leveling is correct 
str(OscarsSubset$Ch) 
table(OscarsSubset$Ch)  
contrasts(OscarsSubset$Ch) 
