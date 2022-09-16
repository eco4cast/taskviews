# Visualization 

## Overview  

Curators: Libby Mohr^1^, Matthew Brousil^2^, Kelly Heilman^3^, Hassan Moustahfid^4^, Leah Johnson^5^, David LeBauer^3^, Rob Kooper^6^, Cee Nell^7^, Josh Cullen^8^, Jake Zwart^7^, Jody Peters^9^, Quinn Thomas^5^, Mike Dietze^10^

*^1^Montana State University, ^2^Washington State University, ^3^University of Arizona, ^4^NOAA, ^5^Virginia Tech, ^6^National Center for Supercomputing Applications, ^7^USGS, ^8^Florida State University, ^9^University of Notre Dame, ^10^Boston University*


As the old adage goes

> “A picture is worth a thousand words.” 

At the end of any data gathering endeavor, one is faced with the task of dissemination. This step determines how the end-user consumes the information buried within the data. Often these data sets are complex and require creative strategies to communicate information accurately and effectively.  Science, policy and planning rely on reliable and unbiased communications. Data visualizations and graphics are a powerful means to communicate. They have great impact on how we perceive environmental problems, their solutions, and if we consider policies legitimate.  Over the last two decades, more and more studies have demonstrated that visualization plays a role in data-communication, influences decision making, public perception, public participation, and knowledge cocreation ([Metze 2020](https://doi.org/10.1080/1523908X.2020.1798751)).
A famous example of a great data visualization is Charles Joseph Minard’s [diagram of Napoleon’s march](https://www.edwardtufte.com/tufte/posters) to Moscow, which clearly shows the disastrous number of lives lost in this military campaign. Such an image readily conveys a message “at a glance” that sticks to memory and is difficult to forget. Another example of influential visualizations is the diagram of the ‘Burning Embers’ from the IPCC report in 2001 (updated in 2009; Figure 1). This diagram visualizes the risks coming from the heating up of the earth. Studies show how these embers have been adapted and contested over time ([Wardekker & Lorenz 2019](https://doi.org/10.1007/s10584-019-02522-6)).

![Burning Embers Figure 1 from [Smith et al 2009](https://doi.org/10.1073/pnas.0812355106), shared with permission from lead author Joel Smith.](images/burning-embers.png)

Data visualization has a long history in scientific communication. Simple forms include pie charts, line graphs and more complex network diagrams. Newer techniques use larger datasets and allow users to interact with data to create their own visualizations “on demand”. For example, the large dataset that pertains to COVID-19 and its impact on various populations across the globe clearly demonstrates the impact of data visualization on science on policy ([Johns Hopkins COVID-19 Dashboard](https://coronavirus.jhu.edu/)).

Data visualization requires an appreciation for how to convey relationships, categories, and magnitude through the creative use of lines, colors, symbols, position and size. Data visuals help tell a story, starting with a compelling problem or question, using data to provide perspective, and giving the reader some insight or solution. Yet creators must respect the limits in datasets. For example, maps of climate change show bands of color with projected changes in temperature or precipitation, but they are limited by the scarcity of weather observation stations across the developing world (see [figure SPM.1](https://apps.ipcc.ch/report/sr15/fig1/index.html) in the Summary for Policymakers of the IPCC’s Special Report on Global Warming of 1.5℃).

To inform policy, data visualization is beginning to enrich our understanding of the challenges facing society. Evidence-based illustrations, or infographics, help convey complex policy issues and the potential trade-offs in greater depth than long reports or other media ([Mclnerny et al. 2014](https://doi.org/10.1016/j.tree.2014.01.003)). Finally, when subject matter is intangible (e.g., due to scale, complexity, or abstraction), visualizations have a fundamental role in exploring information and generating understanding. In addition to an open scientific infrastructure, visualization and graphics should be among the main priorities for developing modern science and science policy.

The following Visualiztion Task View first provides guiding principles for creating visualizations and applications with static or interactive features, then provides examples and tools to create static, animated, interactive, and spatial visuals as well as resources for visualizing uncertainty. 

## Guiding Principles

### Overview
Project [design](#Design), [co-development](#Co-development), and [sustainability](#Product Sustainability), are all important aspects to consider when creating visualizations.  The following principles can apply to a range of visualizations and applications ranging from scientific publications to user interface and decision support applications.  Although often unseen by users, how one generates the information and visualizations used to convey that information is just as important as the science behind the information being shared.  Here is an [EFI Bibliography Zotero Library](https://www.zotero.org/groups/2545778/ecological_forecasting_initiative_bibliography/library) with books and papers on visualization best practices. In Zotero, use the Filter Tags section in the lower left-hand corner to select "EFI Visualization Paper" to bring up the references. Additional resources, specifically for web applications for visualizing scientific data can be found in this [scientificwebapps Zotero Bibliography](http://zotero.org/groups/2845330/scientificwebapps).

### Design
When developing visualizations, determine the intended purpose, use case, and motivation for the resources being developed. Will you be using the resource to conduct exploratory data analysis, to be used in a publication, or to allow an audience that is internal or external to the project to interact with the output? Think about who wants the information, what information is important, how important is that information, and what outcome or takeaways do you want the audience to grasp.  Your target audience and intended outcomes will shape the development process and the design of the visualization tool.
One way to brainstorm visualizations is to think about user stories, a concept from computer science. User stories are informal, general explanations of a software feature (but apply to visualizations as well) written from the perspective of the end-user. See [Max Rehkopf’s 2022 user story template and examples](https://www.atlassian.com/agile/project-management/user-stories) to further consider how a visualization, app, or tool provides value to the end-user.

[Table 1 (below)](#Table-1) provides suggestions and considerations when working with end-users, thinking about the life expectancy and sustainability of a visualization or application, using interfaces, communicating with end-users through visualization or application, and what kind of maintenance is needed. Table 1 comes from the [sciwebapps project](https://github.com/trashbirdecology/sciwebapps/tree/main/learning-resources) that is creating an open source and community-driven repository for resources, information, discussions, and suggested practices for creating, communicating, and improving Scientific Web Applications. 

In [this 10-minute YouTube video](https://youtu.be/dK3GgLNby2o), EFI Steering Committee member, Melissa Kenney provides three examples of how considering the design of visuals leads to  “Improving Decision-maker Usability of Forecast Data Products.”

### Co-development 
Depending on the type of visualization product you are creating and your audience, you may be collaborating with other users or parties on project development. If so, it is important to consider the co-development process. Co-development or co-production of a visualization or application takes place when Information Users and Information Providers collaborate to generate scientific resources. Ideally, the co-development process aims to build and sustain partnerships, acknowledging differences in what each party needs from the partnership and the project, and what the partners’ strengths and limitations are regarding their contributions. Co-production can take different forms depending on the project or funding ranging from projects with limited to no community participation (e.g., Contractual) to community members having authority over the research process (e.g., Collaborative, Collegial, Indigenous) ([David-Chavez and Gavin, 2018](https://iopscience.iop.org/article/10.1088/1748-9326/aaf300/meta)). 
Additional information about co-production definitions, papers, info sheets, and frameworks and assessment tools that was shared by three panelists from a seminar on co-production hosted by the EFI Partners & Knowledge Transfer Working Group in May 2021 can be [found here](https://ecoforecast.org/knowledge-transfer-partners/co-production-actionable-science-panel/#co-productionresources).


### Product Sustainability 
Best practices include identifying the intended lifespan of the product and the available resources (e.g. time, funding, computing resources) for maintaining and hosting the product. An important consideration for public-facing tools is how much traffic they can handle and what resources are needed to maintain or increase their scale or user base.


## How We Make Visuals
### Digital Accessibility (a11y)
Digital accessibility, also referred to as ‘a11y’, is used in Web development to enable as many people as possible to use Web sites no matter an individual’s physical and cognitive abilities. See [Burnett et al. 2021](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1009574) for a brief discussion of a11y with respect to scientific web applications. 
[Table 2 (below)](#Table-2) provides a list of a11y resources with general information, standards and evaluation, assessment tools, and communities of practice that are useful to explore when creating web applications or other user interfaces.


#### Color Vision Evaluation and Accessibility Tools
* Tools for evaluating graphics with color vision simulators:
  + [Color Oracle](https://colororacle.org/) standalone free color blindness simulator for Windows, Mac and Linux that shows in real time what people with common color vision impairments will see.
  + [Colorblindly](https://chrome.google.com/webstore/detail/colorblindly/floniaahmccleoclneebhhmnjgdfijgg?hl=en) Chrome extension web browser tool that simulates colorblindness on a web browser.

* Tools for creating colorblind friendly graphics include: 
  + [Colorspace](https://cran.r-project.org/web/packages/colorspace/vignettes/colorspace.html) R and Python package that provides a toolbox for selecting individual colors or color palettes, manipulating these colors, and employing them in various kinds of visualizations.
  + [Color Brewer](https://colorbrewer2.org/#type=sequential&scheme=BuGn&n=3) provides color options for making maps in R with a range of data classes in multiple color schemes and with colorblind, printer and photocopy safe options 
  + [Viridis](https://cran.r-project.org/web/packages/viridis/index.html) is an R package that provide a series of color maps that are designed to improve graph readability for readers with common forms of color blindness and/or color vision deficiency
      + [Tutorial](https://cran.r-project.org/web/packages/viridis/vignettes/intro-to-viridis.html)


#### Alternative Text
Alternative text are written descriptions of images and videos that can be read out loud so that the visual is not required. Captions or transcripts may be necessary for video animations with sound. See [Writing Alt Text for Data Visualization](https://nightingaledvs.com/writing-alt-text-for-data-visualization/) for suggestions on how to write alt text for different types of data visualization, how to add alt text in a number of applications, and links to other resources

#### Motion Sensitivity
* To accommodate motion sensitivity, the [WCAG](https://www.digitala11y.com/understanding-sc-2-2-2-pause-stop-hide/) advises: 

> “For any moving, blinking or scrolling information that (1) starts automatically, (2) lasts more than five seconds, and (3) is presented in parallel with other content, there is a mechanism for the user to pause, stop, or hide it unless the movement, blinking, or scrolling is part of an activity where it is essential.” 

* Video animations are preferred over GIFs for more complex animations because it gives playback control to users, it does not autoplay or loop infinitely, and it can be easily opted out of. Avoiding flashes, bouncing, and slower animations with short durations helps make motion more accessible. 

#### Accessibility Considerations for Interactive Visualizations
* Some interactive features can be difficult to navigate for people navigating with a keyboard or using magnification software.
* Avoid making important information only available on hover
* Display pop-up content upon both hovering with a pointer and focusing with a keyboard
* More tips about pop-up content displayed by mouse hovers and keyboard focus [here](https://accessuse.eu/en/Content-hover-focus.html) 

### Static Visuals
Static visuals are those that don’t change with time or user-input. Such plots are useful for exploratory data analysis (e.g. deciding if and how to include variables in a forecast model), visualizing forecasts and associated uncertainty (see the [Uncertainty Visualization Section](#Uncertainty-Visualization)), and assessing model performance. Whereas animated and interactive graphics allow for additional complexity and exploration, static visuals are well-suited for clearly conveying simple messages.

In this section, we briefly describe common types of static plots used in forecasting. For each plot type, we list the tools that can be used to make them. **We focus on tools in R, specifically those within base R and the [ggplot2](https://ggplot2.tidyverse.org/) ecosystem.** 
We also provide examples of each static plot created using data from the [EFI RCN NEON Ecological Forecasting Challenge](https://ecoforecast.org/efi-rcn-forecast-challenges/).  

<details>
<summary>Click here to see the code for the R packages and NEON data used to create the plots below.</summary>

```r
knitr::opts_chunk$set(echo = TRUE, message = FALSE, warning = FALSE) # Show code and plots
# Load packages
library(tidyverse)
```

```
## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
```

```
## ✔ ggplot2 3.3.6     ✔ purrr   0.3.4
## ✔ tibble  3.1.7     ✔ dplyr   1.0.9
## ✔ tidyr   1.2.0     ✔ stringr 1.4.0
## ✔ readr   2.1.2     ✔ forcats 0.5.1
```

```
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
```

```r
library(lubridate)
```

```
## 
## Attaching package: 'lubridate'
```

```
## The following objects are masked from 'package:base':
## 
##     date, intersect, setdiff, union
```

```r
library(here)
```

```
## here() starts at C:/Users/jmurray7/Documents/TaskViews/taskviews
```

```r
library(neon4cast)
#neon4cast can be installed with: 
#install.packages("remotes")
#remotes::install_github("eco4cast/neon4cast")
library(cowplot)
```

```
## 
## Attaching package: 'cowplot'
```

```
## The following object is masked from 'package:lubridate':
## 
##     stamp
```

```r
library(patchwork)
```

```
## 
## Attaching package: 'patchwork'
```

```
## The following object is masked from 'package:cowplot':
## 
##     align_plots
```

```r
library(ggtext)
library(colorspace)
library(viridis)
```

```
## Loading required package: viridisLite
```

```r
library(ggridges)
library(GGally)
```

```
## Registered S3 method overwritten by 'GGally':
##   method from   
##   +.gg   ggplot2
```

```r
library(ggdist)
```

```
## 
## Attaching package: 'ggdist'
```

```
## The following objects are masked from 'package:ggridges':
## 
##     scale_point_color_continuous, scale_point_color_discrete,
##     scale_point_colour_continuous, scale_point_colour_discrete,
##     scale_point_fill_continuous, scale_point_fill_discrete,
##     scale_point_size_continuous
```

```r
library(ggExtra)
# Get target data
aquatics_targets <- readr::read_csv("https://data.ecoforecast.org/targets/aquatics/aquatics-targets.csv.gz")
```

```
## Rows: 10281 Columns: 10
```

```
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (1): siteID
## dbl  (8): oxygen, temperature, chla, oxygen_sd, temperature_sd, chla_sd, dep...
## date (1): time
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

```r
terrestrial_daily_targets <-
readr::read_csv("https://data.ecoforecast.org/targets/terrestrial_daily/terrestrial_daily-targets.csv.gz", guess_max = 1e6)
```

```
## Rows: 19670 Columns: 4
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (1): siteID
## dbl  (2): nee, le
## date (1): time
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

```r
pheno_targets <- readr::read_csv("https://data.ecoforecast.org/targets/phenology/phenology-targets.csv.gz")
```

```
## Rows: 42120 Columns: 6
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (1): siteID
## dbl  (4): gcc_90, rcc_90, gcc_sd, rcc_sd
## date (1): time
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

```r
tick_targets <- readr::read_csv("https://data.ecoforecast.org/targets/ticks/ticks-targets.csv.gz")
```

```
## Rows: 477 Columns: 4
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (1): siteID
## dbl  (2): mmwrWeek, amblyomma_americanum
## date (1): time
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

```r
beetle_targets <- readr::read_csv("https://data.ecoforecast.org/targets/beetles/beetles-targets.csv.gz", guess_max = 1e6)
```

```
## Rows: 3182 Columns: 4
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (1): siteID
## dbl  (2): abundance, richness
## date (1): time
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```
</details>

\
For visualizing data in **Python**, we recommend checking out the commonly-used [Matplotlib](https://matplotlib.org/stable/index.html), [Pandas](https://pandas.pydata.org/pandas-docs/stable/user_guide/visualization.html#), and [Seaborn](https://seaborn.pydata.org/) libraries. 

In **Julia**, the [Plots.jl](https://docs.juliaplots.org/stable/) metapackage provides a common interface to several plotting [Backends](https://docs.juliaplots.org/stable/backends/) and the [StatsPlots](https://github.com/JuliaPlots/StatsPlots.jl) package provides additional functionality needed to produce many of the plots described below. 

Spreadsheet platforms (e.g. [Microsoft Excel](https://www.microsoft.com/en-us/microsoft-365/excel) and [Google sheets](https://www.google.com/sheets/about/)) also provide interactive tools for making simple static plots. 

Additional references for R, Python, and Julia are provided at the end of this section.


#### Distributions 
When developing forecasts it is often useful to examine the **distribution** of a single variable or parameter. Such visualizations can be used to examine 1) how data are distributed and 2) uncertainty in parameter estimates or other estimated quantities. There are a few different “flavors” of distribution plots, depending on the application.

##### Histograms
**Histograms** are generated by breaking the data up into several bins and then counting the number of data points that fall into each bin.

* `hist` - function in base R
* `geom_histogram` - in [ggplot2](https://ggplot2.tidyverse.org/) 
* `geom_bar() + scale_x_binned()` - in [ggplot2](https://ggplot2.tidyverse.org/)
* `stat_histinterval` - from the [ggdist](https://mjskay.github.io/ggdist/) package
* `geom_bin_2d` - in [ggplot2](https://ggplot2.tidyverse.org/) - creates a 2D histogram showing joint distribution of two variables by binning observations into squares in a Cartesian plane
* `geom_hex` - in [ggplot2](https://ggplot2.tidyverse.org/) - creates a 2D histogram showing joint distribution of two variables by binning observations into hexagons in a Cartesian plane
* `ggMarginal` - drop-in function [ggMarginal](https://www.rdocumentation.org/packages/ggExtra/versions/0.10.0/topics/ggMarginal) adds marginal histograms to existing ggplots.

<details>
<summary>Click here to see an example of geom_bar code and plot.</summary>

```r
terrestrial_daily_targets %>%
  drop_na(nee) %>%
  filter(siteID == "KONZ",
         month(time) == 2) %>%
  ggplot(aes(x = nee)) + 
  geom_bar(width = 0.9, fill = "#588B8E")+
  scale_x_binned()+
  theme_minimal_hgrid()+
  xlab("net ecosystem exchange (g C m<sup>-2</sup> day<sup>-1</sup>)")+
  ylab("number of days")+
  theme(axis.title.x = element_markdown())
```

<div class="figure">
<img src="visualization_files/figure-html/histogram-1.png" alt="Histogram of daily net ecosystem exchange of carbon dioxide (NEE) in February at the Konza Prairie Biological Station NEON site, 2019-2022" width="672" />
<p class="caption">(\#fig:histogram)Histogram of daily net ecosystem exchange of carbon dioxide (NEE) in February at the Konza Prairie Biological Station NEON site, 2019-2022</p>
</div>
</details>
\
<details>
<summary>Click here to see an example of geom_hex and ggMarginal code and plot.</summary>

```r
p <- ggplot(pheno_targets, aes(x = gcc_90, y = rcc_90)) +
  geom_hex(bins = 30)+
  geom_point(color = "transparent")+
  ylab("greenness index") + 
  xlab("redness index")+
  theme_cowplot()+
  scale_fill_continuous_sequential(palette = "BurgYl")+
  theme(legend.position = c(0.8, 0.8))
ggMarginal(p,type = "histogram", fill = "grey80", color = "white", bins = 30)
```

<div class="figure">
<img src="visualization_files/figure-html/histogram2D-1.png" alt="Hexagonal heatmap showing the joint distribution of greenness chromatic coordinate and redness chromatic coordinate at the six NEON sites in the phenology forecast challenge." width="672" />
<p class="caption">(\#fig:histogram2D)Hexagonal heatmap showing the joint distribution of greenness chromatic coordinate and redness chromatic coordinate at the six NEON sites in the phenology forecast challenge.</p>
</div>
</details>

##### Density Plot
A **Density Plot** is a smoothed, continuous version of a histogram that displays the estimated probability distribution of a variable or parameter. Density plots are often used to visualize Bayesian prior and posterior distributions. When data or MCMC samples are involved, probability density is typically estimated using the “kernel density estimation” method, where the smoothness and shape of the density curve are controlled by the choice of bandwidth parameter and kernel, respectively (see [Wilke, 2019: Visualizing distributions: Histograms and density plots](https://clauswilke.com/dataviz/histograms-density-plots.html)).

* `geom_density` - in [ggplot2](https://ggplot2.tidyverse.org/) - plots density estimates for a single variable
* `geom_density_2d` - in [ggplot2](https://ggplot2.tidyverse.org/) - plots contours resulting from a 2D kernel density estimation
* `geom_function` - in [ggplot2](https://ggplot2.tidyverse.org/) - plots a function (e.g. dnorm)
* `geom_area` - in [ggplot2](https://ggplot2.tidyverse.org/) - can be used for a filled density plot
* `slab` and `halfeye`-  This vignette describes the [slab+interval geoms](https://mjskay.github.io/ggdist/articles/slabinterval.html#roadmap-it-all-starts-with-slabinterval-) and stats in [ggdist](https://mjskay.github.io/ggdist/).


<details>
<summary>Click here to see an example of geom_area code and plot.</summary>

```r
ggplot() +
  geom_area(data = tibble(x = seq(0.01, 4, 0.01), y = dlnorm(seq(0.01, 4, 0.01))), aes(x = x, y = y), fill = "grey80", color = "grey40")+
  xlim(c(0,4))+
  theme_minimal_hgrid()+
  ylab("probability density")+
  theme(axis.title.x = element_blank())
```

<div class="figure">
<img src="visualization_files/figure-html/density-1.png" alt="Density plot for a log-normal distribution with mean = 0 and standard deviation = 1" width="672" />
<p class="caption">(\#fig:density)Density plot for a log-normal distribution with mean = 0 and standard deviation = 1</p>
</div>
</details>


##### Dotplots
**Dotplots** show the individual observations of a distribution, either as continuous values or as part of binned intervals (similar to histograms). This type of visualization provides the finest scale of visualization for distributions that may be lost when using other common methods (i.e., histograms, density plots, boxplots). **Quantile Dotplots** are similar, except that the data are broken into quantiles, which are then binned and plotted such that each dot represents a single quantile rather than a single observation. Quantile dotplots are a way of visualizing distributions and uncertainty with a “frequency frame”, and have been shown to aid people in making decisions in the face of uncertainty ([Kay et al., 2016](https://dl.acm.org/doi/10.1145/2858036.2858558)).

* `geom_jitter` in [ggplot2](https://ggplot2.tidyverse.org/) - adds small amounts of variation to the location of each point to avoid overplotting when visualizing observations of a quantitative variable.
* `geom_dotplot` in [ggplot2](https://ggplot2.tidyverse.org/) - bins up observations and plots a single point for each observation.
* `stat_dots` from the [ggdist](https://mjskay.github.io/ggdist/) package - plots a single point for each binned observation by default, or produces a quantile dotplot if the quantiles argument is specified.

<details>
<summary>Click here to see an example of stat_dots code and plot.</summary>

```r
set.seed(123)
tempSample <- tibble(temp = rnorm(10000, mean = 17.7, sd = 1))
ggplot(tempSample, aes(x = temp, fill = stat(x > 19), color = stat(x > 19))) + 
  stat_dots(quantiles = 30)+
  geom_vline(xintercept = 19, linetype = 2, color = "gray50")+
  theme_cowplot() +
  xlab("Temperature (°C)")+
  scale_fill_manual(values = c("#517AC9", "#C05D5D"))+
   scale_color_manual(values = c("#517AC9", "#C05D5D"))+
  theme(legend.position = 'none',
        axis.title.y = element_blank(),
        axis.text.y = element_blank(),
        axis.line.y = element_blank(), 
        axis.ticks.y = element_blank())
```

<div class="figure">
<img src="visualization_files/figure-html/qdotplot-1.png" alt="Quantile dotplot showing the probability of temperature exceeding 19 °C for a theoretical, normally-distributed temperature forecast with mean = 17.7 °C and sd = 1" width="672" />
<p class="caption">(\#fig:qdotplot)Quantile dotplot showing the probability of temperature exceeding 19 °C for a theoretical, normally-distributed temperature forecast with mean = 17.7 °C and sd = 1</p>
</div>
</details>


##### Boxplots
**Boxplots** display common summary statistics for a distribution, which include the minimum, first quartile, median, third quartile, and maximum values. The ‘box’ displays the middle 50% of the distribution while the ‘whiskers’ display the remaining 50% in the tails of the distribution. Any values that fall outside of 1.5 times the length of the ‘box’ are typically drawn as points beyond the whiskers and are typically referred to as outliers. Similarly, **interval plots** typically show the median as a point and one or more lines or boxes whose widths represent quantiles of the distribution. Whereas the plots described above are useful for visualizing single distributions, boxplots, interval plots, violin plots, and ridgeline plots can display multiple distributions in the same plot ([Wilke, 2019](https://clauswilke.com/dataviz/)).

* `boxplot` in base R
* `geom_boxplot` in [ggplot2](https://ggplot2.tidyverse.org/)
* `interval` and `pointinterval` from the [ggdist](https://mjskay.github.io/ggdist/) package create stand-alone interval plots, whereas several other stats from the stat_slabinterval family allow one to add intervals to other plot types, including density plots, violin plots, histograms, and dotplots.

<details>
<summary>Click here to see an example of geom_boxplot code and plot.</summary>

```r
terrestrial_daily_targets %>% 
  drop_na(le) %>%
  filter(month(time) == 5,
         siteID %in% c("BART", "CLBJ", "KONZ", "ORNL", "OSBS")) %>%
  ggplot(aes(x = siteID, y = le))+
  geom_boxplot(fill = "#78A481") +
  theme_minimal() +
  xlab("NEON site") +
  ylab("latent heat flux (W m<sup>-2</sup>)")+
  theme(axis.title.y = element_markdown())
```

<div class="figure">
<img src="visualization_files/figure-html/boxplot-1.png" alt="Distributions of daily latent heat flux during May at 5 NEON sites shown as boxplots." width="672" />
<p class="caption">(\#fig:boxplot)Distributions of daily latent heat flux during May at 5 NEON sites shown as boxplots.</p>
</div>
</details>


##### Violin Plots
**Violin plots** are an extension of a density plot where the density plot is mirrored and shows the minimum and maximum values, as well as the maximum point density region(s). Since they can show greater detail of a distribution, violin plots have often been used as a replacement for boxplots more recently.

* `geom_violin` in [ggplot2](https://ggplot2.tidyverse.org/)
* `pirateplot` from the [yarrr](https://bookdown.org/ndphillips/YaRrr/pirateplot.html) package
* `stat_eye` from the [ggdist](https://mjskay.github.io/ggdist/) package

<details>
<summary>Click here to see an example of geom_violin code and plot.</summary>

```r
terrestrial_daily_targets %>% 
  drop_na(le) %>%
  filter(month(time) == 5, 
         siteID %in% c("BART", "CLBJ", "KONZ", "ORNL", "OSBS")) %>%
  ggplot(aes(x = siteID, y = le))+
  geom_violin(fill = "#78A481") +
  theme_minimal() +
  xlab("NEON site") +
  ylab("latent heat flux (W m<sup>-2</sup>)")+
  theme(axis.title.y = element_markdown())
```

<div class="figure">
<img src="visualization_files/figure-html/violin-1.png" alt="Distributions of daily latent heat flux during May at 5 NEON sites shown violin plots." width="672" />
<p class="caption">(\#fig:violin)Distributions of daily latent heat flux during May at 5 NEON sites shown violin plots.</p>
</div>
</details>


##### Ridgeline Plots
**Ridgeline plots** show offset density plots for multiple variables. This can be useful for making comparisons of a given variable over space or time, as well as for comparing among a number of groups. However, it is not possible to directly compare the values on the y axis among density plots due to the three dimensional effect of this type of plot. Therefore, this method may be more useful when interested in relative (rather than absolute) densities.

* `geom_density_ridges` from the [ggridges](https://wilkelab.org/ggridges/) package
* `stat_halfeye` from the [ggdist](https://mjskay.github.io/ggdist/) package

<details>
<summary>Click here to see an example of geom_density_ridges code and plot.</summary>

```r
terrestrial_daily_targets %>% 
  drop_na(le) %>%
  filter(month(time) == 5, 
         siteID %in% c("BART", "CLBJ", "KONZ", "ORNL", "OSBS")) %>%
  ggplot(aes(x = le, y = siteID))+
  geom_density_ridges(fill = "#78A481") +
  theme_minimal() +
  ylab("NEON site") +
  xlab("latent heat flux (W m<sup>-2</sup>)")+
  theme(axis.title.x = element_markdown())
```

<div class="figure">
<img src="visualization_files/figure-html/ridgeline-1.png" alt="Distributions of daily latent heat flux during May at 10 NEON sites shown as staggered density plots or 'ridgeline' plots." width="672" />
<p class="caption">(\#fig:ridgeline)Distributions of daily latent heat flux during May at 10 NEON sites shown as staggered density plots or 'ridgeline' plots.</p>
</div>
</details>
\

#### Point and line plots 
##### Scatterplots
**Scatterplots** are handy for visualizing relationships between two continuous variables. This includes **time series**, where the variable on the x-axis is time. The following tools are commonly used for making scatterplots: 

* The `plot` function from the base package in R defaults to producing a scatter plot 
* With [ggplot2](https://ggplot2.tidyverse.org/), the geometric object `geom_point` can be used

<details>
<summary>Click here to see an example of geom_point code and plot.</summary>

```r
aquatics_targets %>% 
  filter(year(time) <= 2020, 
         year(time) >= 2019,
         siteID == "POSE") %>%
  ggplot(aes(x = temperature, y = oxygen))+
  geom_point(size = 1.2)+
  ylim(c(7.5, 13.0))+
  xlim(c(0,25))+
  theme_minimal_grid()+
  ylab(expression(paste("dissolved oxygen (mg ", L^-1, ")")))+
  xlab("Temperature (°C)")
```

<div class="figure">
<img src="visualization_files/figure-html/scatterplot-1.png" alt="Scatterplot of dissolved oxygen concentrations vs. temperature at the Posey Creek NEON site, 2019-2020" width="672" />
<p class="caption">(\#fig:scatterplot)Scatterplot of dissolved oxygen concentrations vs. temperature at the Posey Creek NEON site, 2019-2020</p>
</div>
</details>


##### Line Graphs
**Line Graphs** connect data points sequentially and are also commonly used for visualizing **time series**. It’s also possible to add lines to existing scatter plots to emphasize connections between the data while emphasizing the data themselves with points. The tools below are often used to create line graphs or add lines to existing plots:

* The `plot` function from the base package in R generates a line plot with the argument `type = “l”`
* The `lines` function in base R adds a line to an existing plot.
* With [ggplot2](https://ggplot2.tidyverse.org/), the geometric object `geom_line` (or `geom_path`) can be used to add lines.

<details>
<summary>Click here to see two examples of geom_line, with and without geom_point code, and the  plots.</summary>

```r
aquatics_targets %>% 
  filter(year(time) <= 2020, 
         year(time) >= 2019,
         siteID == "POSE") %>%
  ggplot(aes(x = time, y = oxygen))+
  geom_line()+
  theme_minimal_grid()+
  ylab(expression(paste("dissolved oxygen (mg ", L^-1, ")")))+
  theme(axis.title.x = element_blank())
```

<div class="figure">
<img src="visualization_files/figure-html/line-1.png" alt="Line graph of mean daily dissolved oxygen concentrations at the Posey Creek NEON site, 2019-2020" width="672" />
<p class="caption">(\#fig:line)Line graph of mean daily dissolved oxygen concentrations at the Posey Creek NEON site, 2019-2020</p>
</div>



```r
aquatics_targets %>% 
  filter(year(time) == 2021, 
         month(time) == 6,
         siteID == "POSE") %>%
  ggplot(aes(x = time, y = oxygen))+
  geom_line()+
  geom_point()+
  theme_minimal_grid()+
  ylab(expression(paste("dissolved oxygen (mg ", L^-1, ")")))+
  theme(axis.title.x = element_blank())
```

<div class="figure">
<img src="visualization_files/figure-html/pointline-1.png" alt="Line graph with dots showing dissolved oxygen concentrations at the Posey Creek NEON site, June 2021" width="672" />
<p class="caption">(\#fig:pointline)Line graph with dots showing dissolved oxygen concentrations at the Posey Creek NEON site, June 2021</p>
</div>
</details>


##### Pairs Plots and Correlograms
**Pairs Plots** and **Correlograms** are useful for quickly visualizing relationships and correlations between several variables at once. These plots are typically used for exploratory data analysis.

* `pairs` function from base R - creates scatterplot for each combination of variables
* `ggpairs` from the [GGally package](https://cran.r-project.org/web/packages/GGally/index.html) - by default, displays the correlation between each combination of variables in the top right corner, a scatter plot for each combination of variables in the lower left corner, and a density plot for each variable on the diagonal. Several customization options are available.
* `corPlot` from the [psych package](https://cran.r-project.org/web/packages/psych/index.html) - displays the correlation between each combination of variables in a box, where the color hue of the box indicates whether the correlation is positive or negative and the color value indicates the strength of the correlation.

<details>
<summary>Click here to see an example of ggpairs code and plot.</summary>








