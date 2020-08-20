# custom-color-palettes
This repository serves as a documentation of the color palettes I customly made along various datavisualisation projects.

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
