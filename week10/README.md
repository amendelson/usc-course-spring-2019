# Week 10
This week, we're diving into data analysis in R. 

---

### Lecture

No lecture. All coding!

---

### Hands-on

**1. Getting started**
 
Alright, fire up Terminal or PowerShell. Let's navigate to where you want to save your code, and fire up a Jupyter Notebook:

```
juptyer notebook
```

Let's install and load a couple packages we'll need today.

```
install.packages("tidyverse")
install.packages("gapminder")
```

Installing them doesn't make them available, however. We need to load them.

```
library(tidyverse)
library(gapminder)
```

Let's use some of the commands we learned last week to figure out what `gapminder` is.

```
head(gapminder)
summary(gapminder)
str(gapminder)
```

Let's try a new one

```
arrange(gapminder, pop)
```

Interesting. What does this do?

```
arrange(gapminder, desc(pop))
```


This lesson is adapted from Hadley Wickham's great [Data Science In Tidyverse](https://github.com/hadley/data-science-in-tidyverse/blob/master/slides/02-Transform.pdf) workshop.

**2. How can we work with only the data we want?**

Like, we probably don't want to review the data for every nation at once. How can we ask more focused, targeted questions?

<img src ="imgs/1.png" width = 600>
<img src ="imgs/2.png" width = 600>

Let's try it out.

```
filter(gapminder, country == "United States")
```

What do these do.

```
filter(gapminder, continent == "Americas")
filter(gapminder, year > 1980)
filter(gapminder, pop > 20000000 & pop < 100000000)
filter(gapminder, pop > 20000000 & continent == "Americas" & gdpPercap <= 4000)
filter(gapminder, pop > 20000000 & continent != "Americas" & gdpPercap <= 4000)

```

How would you look for countries in Asia with high life expectancies?

**3. Select**

**4. Charting**


---

### Links

---

### Homework

