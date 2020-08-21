# custom-color-palettes
This repository serves as a documentation of the color palettes I customly made along various datavisualisation projects. <br/>
The plots I show are not meant to be meaningful data-wise but just should showcase the palette a bit.

**1. eco_river**<br/>
Running the following hex codes:
````
library(scales)

eco_river_pal <- c("#d0ece7", "#a9dfbf", "#73c6b6", "#27ae60", "#117a65", "#145a32")

show_col(eco_river_pal, borders = NA)

````
...gives you this palette:

![eco_river](https://user-images.githubusercontent.com/65813696/90793330-e71ffc80-e30b-11ea-961f-8d0eb15c96e0.png)

Example on how the palette looks on a simple scatter plot with discrete variables:

````
library(ggplot2)
library(hrbrthemes)
library(ggthemes)


#read in penguins dataset (as opposed to the problematic Iris dataset) to show a sample plot:
penguins <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-07-28/penguins.csv')

#simple scatter plot
ggplot(penguins, aes(x = bill_depth_mm, y = body_mass_g, color = species)) +
  geom_point() +
  geom_smooth(method = "lm")+
  scale_color_discrete(type = c("#d0ece7", "#27ae60", "#117a65")) +
  ggtitle("eco_river_pal on scatter")+
  hrbrthemes::theme_ft_rc() +
  ggsave("eco_river_scatter.png", dpi = 300, width = 14, height = 15, units = "cm")
````
Which gives the follwing result:<br/>
![eco_river_scatter](https://user-images.githubusercontent.com/65813696/90796791-0caf0500-e310-11ea-96d2-574b18de7007.png)

Example on how palette looks like on a jitterplot with a continuous variable:
````
ggplot(penguins, aes(x = island, y = species, color = flipper_length_mm)) +
  scale_color_gradientn(colors = eco_river_pal) +
  geom_jitter(height = .4, width = .3) +
  ggtitle("eco_river_pal on jitter") +
  hrbrthemes::theme_ft_rc() +
  ggsave("eco_river_jitter.png", dpi = 100, width = 13, height = 13, units = "cm")

````

![eco_river_jitter](https://user-images.githubusercontent.com/65813696/90797193-9bbc1d00-e310-11ea-9890-ffa84bb7fd00.png)
</br>


**2. sugar_cake** <br/>
Following hexcodes produces this palette:</br>
````
sugar_cake_pal <- c("#af7ac5", "#2e86c1", "#16a085", "#f1c40f", "#ba4a00","#212f3d")

show_col(sugar_cake_pal, borders = NA)
````
![sugar_cake](https://user-images.githubusercontent.com/65813696/90883420-0e2f0a80-e3ae-11ea-9b49-54402723ebcf.png) <br/>

Some plot code:
````
library(nycflights13)
library(dplyr)
library(ggforce)

#filter for smaller dataset: some airlines in january 2013
flights_dat=flights %>%
  filter(carrier %in% c("UA", "AA", "B6", "EV", "US", "HA") & month  == 1 & day == 1)

#plot 
ggplot(flights_dat, aes(x=origin, fill = carrier, color = carrier))+
  geom_histogram(stat = "count", position = "dodge") +
  scale_fill_discrete(type = sugar_cake_pal) +
  scale_color_discrete(type = sugar_cake_pal) +
  ggtitle("sugar_cake on bars")+
  theme_tinyhand() +
  ggsave("sugar_cake_scatter.png", dpi = 200, width = 10, height = 10, units = "cm")
````

Example on a discrete variable plot: <br/>
![sugar_cake_scatter](https://user-images.githubusercontent.com/65813696/90883644-885f8f00-e3ae-11ea-9088-b821d539c765.png)
