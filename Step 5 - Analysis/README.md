# 📚 Introduction

Welcome to the analytical portion of this repository. There are several topics explored here, but countless more to explore over time.

A few examples of visuals in the `Tutorial` file below are:

- Total player counts over time
- Total players gained/lost over time
- Rating stability graphs
- Total player gained/lost over time by country (Countries with extreme values)
- Total titled player counts over time
- Total titled player counts by country (Latest month)
- Strongest countries by age group
- Age vs Rating by title (Latest month)

If you want to:
1. View the process of the data visualization, then see the `Tutorial` below
2. Run the script yourself, then you should download the `R-Markdown file` below and run it on your local machine.

# ⚡ Quick Links

- [Tutorial](https://github.com/AnujDahiya24/FIDE-Chess-Data/blob/master/Chess%20Scripts/Step%205%20-%20Analysis/Analysis%20%26%20Visuals/Analysis.pdf)
- [R-Markdown file](https://github.com/AnujDahiya24/FIDE-Chess-Data/blob/master/Chess%20Scripts/Step%205%20-%20Analysis/Analysis%20%26%20Visuals/Analysis.Rmd)

---

# Visuals

Below is an experimental visualization I'm working on improving. It is **not** included in the Tutorial file: it is in the `Experiments` folder in `Step 6`.

#### FIDE player (Active) rating distribution of Males & Females over time.

![](https://github.com/AnujDahiya24/FIDE-Chess-Data/blob/master/Chess%20Scripts/Step%206%20-%20Experimental%20work/Experiments/Men_women_gif.gif)

I find this graph to be interesting because it shows a few strange trends:

- The graphs look like play-dough that has been slowly compressed over time.
- There were no players rated below 2200 in many of the early datasets provided by FIDE.
- Around 2014, both the male and female distributions looked fairly Gaussian in their shape
- Since 2014, FIDE's rating floor of 1000 has prevented players from naturally falling below the floor. I will look to explore the differences between the male and female distributions (both are heavily right-skewed, but the female distribution is even more so) moving forward. There's an interesting sociological phenomenon present here that has not been vocalized in public yet.

# ⌚ Time Length

Note: The `Analysis.pdf` file take several minutes to knit because of functions like `rbindlist()` that combine all of the datasets together.

---

# ❓ Questions?

Please post inquiries about the data in [Issues](https://github.com/AnujDahiya24/FIDE/issues).
