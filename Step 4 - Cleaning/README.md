# 📚 Introduction

If you want to: 

1. View the .csv files, see the `Cleaned csvs` hyperlink below.
2. View the process of the data downloading, then see the `Tutorial` below
3. Run the script yourself, then you should download the `R-Markdown file` below and run it on your local machine.

# ⚡ Quick Links

- [Cleaned csvs](https://github.com/AnujDahiya24/FIDE-Chess-Data/tree/master/Chess%20Scripts/Step%204%20-%20Cleaning/Cleaned%20csvs)
- [Tutorial](https://github.com/AnujDahiya24/FIDE-Chess-Data/blob/master/Chess%20Scripts/Step%204%20-%20Cleaning/Cleaning%20scripts/Cleaning.pdf)
- [R-Markdown file](https://github.com/AnujDahiya24/FIDE-Chess-Data/blob/master/Chess%20Scripts/Step%204%20-%20Cleaning/Cleaning%20scripts/Cleaning.Rmd)

---

# 🧹 Cleaning files

![](https://miro.medium.com/max/500/1*yWFQiGjlgHUVYeh4ELELyw.jpeg)


To clean the data, we will at some point need to modify each file's column names and values using something like the following in R:

```
#Iterate over each data.frame in list
for(i in 1:length(FIDE)){

#Rename columns in each dataset
  colnames(FIDE[[i]])[grepl("Name|NAME|name", colnames(FIDE[[i]]))] <- "Name"
  ...... more column editing ......
  ...... more column editing ......
  ...... more column editing ......
  colnames(FIDE[[i]])[grepl("OTit", colnames(FIDE[[i]]))] <- "Other_Titles"
  
 #Clean each data.frame
  FIDE[[i]] <- FIDE[[i]] %>%
               mutate(Date = as.POSIXct(names(FIDE)[i], format="%Y-%m-%d"),
                      Date_numeric = year(Date)+yday(Date)/366,
                      Rating = as.numeric(Rating),
                      Title= c(new, Title)[match(Title, c(old, Title))],
                      Country = c(codes$Country, Country)[match(Country, c(codes$Code, Country))],
                      Country = c(countries, Country)[match(Country, c(country_codes, Country))])%>%
                      filter(!Country %in% c("Fed", "Col"))%>%
                      select(-one_of("V1"))
                      
  #Write to new file
  fwrite(FIDE[[i]] , file = paste(dest, files[i], sep = ""), sep = "*")
  
}
```
I'll look to parallelize this for loop to save time moving forward. 

**Note::** The `Age_Birthday` needs a considerable amount of work. Many of the dates have differing formats, so I will need to write a function that will reformat the data.

# ⌚ Time Length

Note: The files take a few minutes to process the data and export it to the proper destination.

---

# ❓ Questions?

Please post inquiries about the data in [Issues](https://github.com/AnujDahiya24/FIDE/issues).
