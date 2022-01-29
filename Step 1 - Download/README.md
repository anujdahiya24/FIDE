# 📚 Introduction 

The first step has us downloading the profile player data (zipped text files) from [FIDE's website](http://ratings.fide.com/download_lists.phtml). Feel free to explore FIDE's [new] website. It seems as if data prior to 2015 is not being displayed anymore. Thankfully, all of the URLs still host the `.zip` files that we will download and are **not** broken.

If you want to: 

1. View the text files, see the `Data (all text files)` hyperlink below.
2. View the process of the data downloading, then see the `Tutorial` below
3. Run the script yourself, then you should download the `R-Markdown file` below and run it on your local machine.

# ⚡ Quick Links

- [Data (all text files)](https://github.com/AnujDahiya24/FIDE/tree/master/Chess%20Scripts/Step%201%20-%20Download/Downloaded%20files)
- [Tutorial](https://github.com/AnujDahiya24/FIDE/blob/master/Chess%20Scripts/Step%201%20-%20Download/Download%20Scripts/Download.pdf)
- [R-Markdown file](https://github.com/AnujDahiya24/FIDE/blob/master/Chess%20Scripts/Step%201%20-%20Download/Download%20Scripts/Download.Rmd)

# 🔄 Download the FIDE files

![Download](https://www.pngarts.com/files/2/Download-Button-Transparent-Background-PNG.png)

In order to download the player profile data, we will use something like the following snippet:

```
#R function that downloads FIDE data files and skips over non-existing URLs

download_function <- function(link, dest){
  if (!file.exists(dest)) {
    tryCatch({
      download.file(link, dest, method="auto", quiet = TRUE) 
    }, error=function(e){})
  }
} 

#Download all data files from URLs and direct them to a folder

mapply(download_function, url_vector, url_vect_destfile)
```

in order to download all files of interest and puts them into a destination folder. 

Please see the `Tutorial` and `R-Markdown` file for further reference.

# ⌚ Time Length

**Note:** The files may take some time to download depending on your internet connection speed.

# ❓ Questions?

Please post inquiries in [Issues](https://github.com/AnujDahiya24/FIDE/issues).
