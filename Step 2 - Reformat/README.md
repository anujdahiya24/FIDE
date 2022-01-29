# 📚 Introduction

The second step has us modifying all of the text files from FIDE's website. In order to modify all of the files quickly, we will utilize parallel processing: It's a big time saver.

If you want to:

1. View the .csv files, see the `Data (all csv files)` hyperlink below.
2. View the process of the data downloading, then see the `Tutorial` below
3. Run the script yourself, then you should download the `R-Markdown file` below and run it on your local machine.

# ⚡ Quick Links

- [Data (all csv files)](https://github.com/AnujDahiya24/FIDE-Chess-Data/tree/master/Chess%20Scripts/Step%202%20-%20Reformat/Data%20csvs)
- [Tutorial](https://github.com/AnujDahiya24/FIDE-Chess-Data/blob/master/Chess%20Scripts/Step%202%20-%20Reformat/Reformat%20Scripts/Reformat.pdf)
- [R-Markdown file](https://github.com/AnujDahiya24/FIDE-Chess-Data/blob/master/Chess%20Scripts/Step%202%20-%20Reformat/Reformat%20Scripts/Reformat.Rmd)

# ⚠️ Issues

After downloading the files in Step 1, I wasn't able to import text files downloaded from [FIDE's data download page](http://ratings.fide.com/download_lists.phtml), into R. A typical `read.csv()` statement will not work because the data has no defined delimiter to parse columns on.  

For example, the earliest dataset on FIDE's website is from January 2001. Let's take a moment to look at the first few rows of the raw text file.

```
ID_NUMBER NAME                             TITLE COUNTRY JAN01 GAMES FLAG
 
 1701991  Aaberg, Anton                          SWE     2300    0   i   
 1401815  Aagaard, Jacob                   m     DEN     2374   18       
 1406248  Aage, Bjarke                           DEN     2063    0       
```

There are several issues with working with the data, but the most pressing one is that there is no clear delimiter to import the files on. A regular comma delimiter will not work because the text does not contain commas to separate the columns. Whitespace and tab delimiters won't work either.

One [github user](https://github.com/xdurana/fider/blob/master/R/zzz.R) has imported FIDE data via fixed widths. This works quite well for most, if not all of the data and I'll look into reading in the text files faster using this [stackoverflow post's](https://stackoverflow.com/questions/24715894/faster-way-to-read-fixed-width-files) benchmarking results.

When I first started working on this project, I didn't quite understand it required fixed-width functions such as `read_fwf()`. I was new to R and my main motivation was I wanted to learn R and Python in a creative setting.

There are several other issues with the rest of the text files (Text files run from January 2001 through December 2019). Just to name a few (shown with table visuals):

### Some have misspelled columns and ever-changing column names over time

```
ID NUMBER NAME                             TIT  Fed     JAN   GMs FLAG
 
 1701991  Aaberg, Anton                         SWE     2300    0   i       
 1401815  Aagaard, Jacob                   m    DEN     2374   18       
 1406248  Aage, Bjarke                          DEN     2063    0       
```  
- `ID NUMBER` is not `ID_NUMBER`, which is problematic for various programmatic reasons.
- `TIT` is different from `TITLE`
- `FED` is different from `Country`.
- `GMs` is different from `Games`
- `JAN` should be `JAN01`

### Some have their columns out of line or missing columns labels outright


```
ID_NUMBER   NAME                        TITLE   COUNTRYJAN01        FLAG
 
 1701991  Aaberg, Anton                          SWE     2300    0   i   
 1401815  Aagaard, Jacob                   m     DEN     2374   18       
 1406248  Aage, Bjarke                           DEN     2063    0       
```
- `NAME` is out of position
- `COUNTRY` and `JAN01` are one word instead of being separated into two
- `GAMES` is missing

### Some have blank & missing rows

```
ID_NUMBER NAME                             TITLE COUNTRY JAN01 GAMES FLAG
 
 1701991  Aaberg, Anton                          SWE     2300    0   i   

 1406248  Aage, Bjarke                           DEN     2063    0       
```
- The entire 2nd row is missing (Jacob Aagaard's information is missing).

### Some don’t even have column headers

```  
 1701991  Aaberg, Anton                          SWE     2300    0   i   
 1401815  Aagaard, Jacob                   m     DEN     2374   18       
 1406248  Aage, Bjarke                           DEN     2063    0       
```
- The column headers aren't even included in the data.

# 🧹 Reformat files

![](https://www.howtogeek.com/wp-content/uploads/blogs/files/2008/07/310.png)

As a result, our next step is to work through each file and transform them into a usable format. The approach I took was to insert delimiters at each index (based on the column line) where a space followed by a character occurred. For example, the data, after inserting `*` delimiters, would look something like this:

```
ID_NUMBER*NAME                            *TITLE*COUNTRY*JAN01*GAMES*FLAG
 
 1701991 *Aaberg, Anton                   *     *SWE    *2300 *  0  *i   
 1401815 *Aagaard, Jacob                  *m    *DEN    *2374 * 18  *    
 1406248 *Aage, Bjarke                    *     *DEN    *2063 *  0  *    
```
where we can clearly see `*` delmiters have been inserted at indexes where a whitespace occured and was one index before another character.

**Note:** Approximately ~14000 observations contain faulty Title and Flag/Activity information. These will be addressed in future iterations of the project.

The `multi_processing()` function below is the general wrapper that weaves everything together (importing, inserting delimiters, export reformatted data to `.csv` format.

```
#run All_files_fwrite() in parallel

multi_processing <- function(Year_num){
                    functions = ls(globalenv())
                    cl <- makeCluster(detectCores())
                    clusterExport(cl, functions)
                    registerDoParallel(cl)
                    foreach(i = Year_num,
                            .export = functions,
                            .packages = c("dplyr",
                                          "data.table",
                                          "Kmisc")) %dopar% {All_files_fwrite(i)}
                    stopCluster(cl)
                                      }
```
After this function is executed on every one of the `.txt` files, they will become usable `.csv` files.


# ⌚ Time Length

**Note:** The files (through December 2019) take some time to process and modify (5 minutes) on my computer, which runs on 8 cores.

# ❓ Questions?

Please post inquiries in [Issues](https://github.com/AnujDahiya24/FIDE/issues).
