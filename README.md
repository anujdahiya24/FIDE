# 📚 Introduction

<img align="right" src="https://images.hamodia.com/hamod-uploads/2017/11/27160118/download.jpg" width="250">

<!--- ![calendar](https://print-a-calendar.com/printable-calendars/one-page-year-thumbnail.png) --->

This repository is to help all chess players utilize and work with [public chess profile data](http://ratings.fide.com/download_lists.phtml) provided by the `FIDE` organization (through December 2019). FIDE's website can be cumbersome to work with and has limited visuals about chess players. My hope is that this project helps users avoid the pain of using their website and provide interesting insights to the chess community.

The project is divided into 6 steps, which are outlined [here](https://github.com/AnujDahiya24/FIDE-Chess-Data#-lifecycle-of-data).

---

# 📈 Dashboard

To see ratings in real-time, I've created a dashboard to help chess players [here](https://anujdahiya24.shinyapps.io/apps/).

---

<img align="right" src = "https://cdn0.iconfinder.com/data/icons/Free-Icons-Shimmer-01-Creative-Freedom/256/folder.png" width="250">

# 🗺️ Where is the data?

The data is located in this [folder](https://github.com/AnujDahiya24/FIDE-Chess-Data/tree/master/Chess%20Scripts/Step%204%20-%20Cleaning/Cleaned%20csvs).

The folder contains over a hundred `.csv` files, from January 2001 to December 2019, that can be analyzed.

If you have suggestions on different data formats you'd like, please state them in [Issues](https://github.com/AnujDahiya24/FIDE/issues).

Other than that, feel free to use it as you see fit.


---


# 📊 Example data

An example of what the FIDE **Standard** Rating data looks like in December 2019: 

| ID_NUMBER | Name | Fed | Sex | Tit | WTit | OTit | FOA | Rating | Gms | K | Birthday | Flag |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 25121731 | A C J John | IND| M  |     |     |   |    | 1063 | 0  | 40 | 1987 | |
| 35077023 | A Chakravarthy | IND| M  |     |     |    |    | 1151 | 0  | 40 | 1986 | i  |
| 10207538 | A E M, Doshtagir | BAN| M  |     |     |    |    | 1840 | 0  | 40 | 1974 | i  |
| 10680810 | A hamed Ashraf, Abdallah  | EGY| M  |     |     |     |    | 1728 | 0  | 40 | 2001 |    |
| 5716365  | A Hamid, Harman | MAS| M  |     |     | NI            |    | 1325 | 0  | 40 | 1970 | i  |

---

# 🗄️ Metadata information

From the [FIDE Download Rating List page (old)](http://ratings.fide.com/download.phtml), we can understand each column a bit more:

<center>
 
| Column name | Meaning | Example |
| --- | :--- | --- |
| ID_NUMBER | a FIDE player's ID | 123456 |
| Name | a FIDE player's name | Carlsen, Magnus |
| Fed | a FIDE player's federation | USA |
| Sex | a FIDE player's sex | M, F |
| Tit | a FIDE player's title | GM, IM, FM, etc. |
| OTit | a FIDE player's other title(s)** | IA, FT, NI, etc.|
| FOA | a FIDE player's FOA*** titles | AGM, AIM, AFM, etc. |
| Rating | a FIDE player's rating | 2168 |
| Gms | # of games played in a month | 46 |
| K | a FIDE player's K-factor | 40 |
| Birthday | a FIDE player's birth year | 1993 |
| Flag | a FIDE player's level of activity | i, wi |

</center>

###### ** IA - International Arbiter,  FT - FIDE Trainer, NI - National Instructor
###### *** Fide Online Arena


---

# 🧬 Lifecycle of data

The lifecycle of the data is divided into 6 steps (below).

All 6 steps are done through R and Python.

You can click each step below for more information.

| <img src="http://shs-seniorproject.weebly.com/uploads/1/9/5/4/19541383/3steps-20140326042407248_orig.jpg" width="60"> | <img src="https://seohackercdn-seohacker.netdna-ssl.com/wp-content/uploads/2011/07/Link-Searching.jpg" width = "50"> |
| --- | --- |
|Step #1| [Download the data](https://github.com/AnujDahiya24/FIDE/tree/master/Chess%20Scripts/Step%201%20-%20Download)|
|Step #2| [Reformating the data](https://github.com/AnujDahiya24/FIDE/tree/master/Chess%20Scripts/Step%202%20-%20Reformat)|
|Step #3| [Scraping country data](https://github.com/AnujDahiya24/FIDE/tree/master/Chess%20Scripts/Step%203%20-%20FIDE%20Country%20Codes)|
|Step #4| [Cleaning the data](https://github.com/AnujDahiya24/FIDE-Chess-Data/tree/master/Chess%20Scripts/Step%204%20-%20Cleaning)|
|Step #5| [Visualizing the data](https://github.com/AnujDahiya24/FIDE-Chess-Data/tree/master/Chess%20Scripts/Step%205%20-%20Analysis)|
|Step #6| [Future Work](https://github.com/AnujDahiya24/FIDE-Chess-Data/tree/master/Chess%20Scripts/Step%206%20-%20Experimental%20work)|

---

# ♟️ Why did I do this?

I chose to work on this project because of several reasons:

- FIDE's publically available data is in an unorganized layout. There is no "download all datasets" button to acquire all of their data. FIDE also doesn't publically list data prior to February 2015 on the new download page when there is actually data going back as early as 2001. As a result, site visitors may find FIDE's website frustrating to work with and I wanted to help overcome their struggles.

- Chess players like to see visuals of themselves, friends, competitors, top players and players across various demographics. I wanted to provide these visuals.

- I wanted to improve my skills in 2 programming languages.

- I've always taken an interest in any data about chess that has not been extensively analyzed. My curiosity drives me.

---

# ✂️ Clone repo

You can clone this repo with the following:

```
$ git clone https://github.com/AnujDahiya24/FIDE-Chess-Data
```

---

# ❓ Questions?

Please post inquiries about the data in [Issues](https://github.com/AnujDahiya24/FIDE/issues).

