# Week TK
This week, we're going to bring together the two big halves of our class ... and do some mapping in R.

Yes, you can do GIS in R.

---

### Hands-on

**0. Why would you ever use R to do GIS work**

Thoughts?

**1. Fire up your Jupyter Notebook.**

I'm not including the command today. Do you remember it? If not, where can you find it?


Once you've got it up, run this.

```
install.packages("leaflet")
install.packages("rgdal")
```

And then this.

```
library(leaflet)
library(rgdal)
```

Wait. Doesn't leaflet sound familiar?

Well, it should. We made a leaflet map [back in Week 7](https://leafletjs.com/examples/choropleth/).

**2. Leaflet in R**

There's an R package that lets you make and export interactive leaflet maps. I've used it at KPCC to create [election maps](http://projects.scpr.org/maps/cd34-map/?=embed/), and maps about [housing](https://www.scpr.org/news/2018/07/31/85109/where-do-people-get-money-to-buy-california-homes/).

It's good. So let's see how it works.

---

### Links

---

### Homework

