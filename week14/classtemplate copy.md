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

We could even [remake that same choropleth we made, entirely within R](https://rstudio.github.io/leaflet/choropleths.html).

But we'll try something new instead.

**2. Leaflet in R**

There's an R package that lets you make and export interactive leaflet maps. I've used it at KPCC to create [election maps](http://projects.scpr.org/maps/cd34-map/?=embed/), and maps about [housing](https://www.scpr.org/news/2018/07/31/85109/where-do-people-get-money-to-buy-california-homes/).

It's good. So let's see how it works.

Download the shapefile of states from the U.S. Census [here](https://www.census.gov/geo/maps-data/data/cbf/cbf_state.html).

Now we'll head back to our notebook and open it up. It should look something like this

```
states <- readOGR("path/to/yourfile/",
  layer = "cb_2017_us_state_500k", GDAL1_integer64_policy = TRUE)
```

Next let's select some states that are cool.

```
bestCoast <- subset(states, states$STUSPS %in% c(
  "CA","OR","WA"
))
```

And now, believe it or not, we can map it.

```
leaflet(bestCoast) %>%
  addPolygons(color = "#444444", weight = 1, smoothFactor = 0.5,
    opacity = 1.0, fillOpacity = 0.5,
    fillColor = ~colorQuantile("YlOrRd", ALAND)(ALAND),
    highlightOptions = highlightOptions(color = "white", weight = 2,
      bringToFront = TRUE))

```

Let's break down every component part of what we just did.

And once we've done that, let's figure out how to add a base layer —  a map below our shapefile that will show us where the shapefiles are relative to the rest of the world.

The code itself is `addTiles()`. How do we add that?

Now check out [other options for basemaps on the R Leaflet official site](https://rstudio.github.io/leaflet/basemaps.html). Add one of those.

**3. Bring in census data, tidily and easily**

There's a great R package for importing census data. Let's install and load it.

```
install.packages("tidycensus")
library(tidycensus)
```

To get the data from the Census' API, you need to provide the API Key you registered for.

```
census_api_key("yourAPIhere", overwrite = FALSE, install = FALSE)
```

Once you've done that, you can quickly grab data. If you want to know the median rent by state in 1990 ... now you can.

```
m90 <- get_decennial(geography = "state", variables = "H043A001", year = 1990)
```

It can also easily be plotted.

```
library(tidyverse)
m90 %>%
  ggplot(aes(x = value, y = reorder(NAME, value))) + 
  geom_point()
```

We can also grab data from the more-frequently-updated American Community Survey. It's like a rolling Census that's being conducted all the time.

Let's look at public transit.

```
transpo <- get_acs(geography = "state", variables = "B08006_008", geometry = FALSE, survey = "acs5", year = 2017)
```

```
head(transpo)
```

Interesting. But what we really want is the **rate** of transit riders. Not the raw number. So let's get that, starting with the total number of folks who commute to work.

```
transpo_total <- get_acs(geography = "state", variables = "B08006_001", geometry = FALSE, survey = "acs5", year = 2017)
head(transpo_total)

```

Alright, now we need to get these ... together in the same data frame! That's where the `join` comes in. We did some of these in QGIS. What could we use in these two datasets to link them up?

**4. A detour into joins**

All you need to join is a common column. Here's how it works in tidyverse.

```
transpo <- transpo %>% left_join(transpo_total, by = "NAME")
```

Now we can get the rate.

```
transpo$rate <- transpo$estimate.x / transpo$estimate.y * 100
head(transpo)
```

**5. Map out (after another join)**

We need to join that transportation data to our shapefile. Unfortunately, the syntax there is a little different. Fortunately, it does work.

```
states_with_rate <- sp::merge(states, transpo, by = "NAME")
```

(May need to reopen using this if we get told we're using too much data `jupyter notebook --NotebookApp.iopub_data_rate_limit=1.0e10`)

Let's try this out.

```
qpal <- colorQuantile("PiYG", states_with_rate$rate, 9)


states_with_rate %>% leaflet() %>% addTiles() %>%
  addPolygons(weight = 1, smoothFactor = 0.5, opacity = 1.0, fillOpacity = 0.5,
    color = ~qpal(rate),
    highlightOptions = highlightOptions(color = "white", weight = 2,
      bringToFront = TRUE))
```

Alright. What does each line do? Let's play around with it and see what changes.

If we have extra time, we'll work on adding [popup text](https://rstudio.github.io/leaflet/popups.html) and [a legend](https://rstudio.github.io/leaflet/legends.html).

---

### Homework

* Map a census dataset.
	* [Go here](https://censusreporter.org) to explore datasets and find their table names.
* I want to see different colors and basemaps on your map.
