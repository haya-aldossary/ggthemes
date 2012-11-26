

# ggthemes

Some extra geoms, scales, and themes for
[ggplot](http://had.co.nz/ggplot2/), including

## Geoms

- ``geom_tufterangeframe`` : Tufte's range frame
- ``geom_tufteboxplot``: Tufte's box plot

## Themes 

- ``theme_tufte``: a minimal ink based on Tufte's *The Visual Display of
Quantitative Information*.
- ``theme_solarized``: a theme using the [solarized](http://ethanschoonover.com/solarized) color palette.
- ``theme_stata``: themes based on [Stata](http://stata.com/) graph schemes.
- ``theme_economist``: a theme based on the plots in the [The Economist](http://www.economist.com/) magazine.
- ``theme_excel``: a theme replicating the classic ugly gray charts in Excel
- ``theme_wsj``: a theme based on the plots in the [The Economist](http://www.economist.com/) magazine.
- ``theme_few``: theme from Stephen Few's ["Practical Rules for Using Color in Charts"](http://www.perceptualedge.com/articles/visual_business_intelligence/rules_for_using_color.pdf).

## Scales

- ``scale_color_solarized``: [Solarized](http://ethanschoonover.com/solarized) colors
- ``scale_color_economist``: colors used in plots in plots in *The Economist*.
- ``scale_color_stata``, ``scale_shapes_stata``, ``scale_linetype_stata``: color, shape, and linetype palettes from Stata graph schemes.
- ``scale_color_excel10``, ``scale_color_excel2003``: colors from new and old Excel.
- ``scale_color_tableau``, ``scale_shape_tableau``: color and shape palettes from [Tableau](http://www.tableausoftware.com/).
- ``scale_shape_cleveland``, ``scale_shape_tremmel``, ``scale_shape_circlefill``: shape scales from classic works in visual perception: Cleveland, 
  Tremmel (1995), and Lewandowsky and Spence (1989).
- ``scale_color_few``: color palettes from Stephen Few's ["Practical Rules for Using Color in Charts"](http://www.perceptualedge.com/articles/visual_business_intelligence/rules_for_using_color.pdf).

# Install 

To install the newest version use 

```r
library("devtools")
install_github("ggthemes", "jrnold")
```

Make sure that you have installed the *newest* version of
**devtools**. 

Or download the source package
[ggthemes_1.1.0.tar.gz](https://github.com/downloads/jrnold/ggthemes/ggthemes_1.1.0.tar.gz),
and install it from **R**,

```r
install.packages("/path/to/downloaded/ggthemes_1.1.0.tar.gz")
```

Or download the [zip ball](https://github.com/jrnold/ggthemes/zipball/master) or [tar ball](https://github.com/jrnold/ggthemes/tarball/master), decompress and run `R CMD INSTALL` on it.

Windows users also must first install [Rtools](http://cran.rstudio.com/bin/windows/Rtools/).

# Contribute

Contributions are welcome! If you would like to add a theme, scales,
etc., fork the repository, add your theme, and submit a pull request.

# Examples


```r
library("ggplot2")
```

```
## Use suppressPackageStartupMessages to eliminate package startup messages.
```

```r
library("ggthemes")
dsamp <- diamonds[sample(nrow(diamonds), 1000), ]
```


## Tufte theme and geoms

Minimal theme and geoms based on plots in *The Visual Display of
Quantitative Information*.


```r
(ggplot(mtcars, aes(wt, mpg)) + geom_point() + geom_rangeframe() + theme_tufte())
```

![plot of chunk tufte-rangeframe](http://i.imgur.com/s8Omh.png) 


The Tufte minimal boxplot.


```r
(ggplot(mtcars, aes(factor(cyl), mpg)) + theme_tufte(ticks = FALSE) + geom_tufteboxplot())
```

![plot of chunk tufteboxplot](http://i.imgur.com/8iijf.png) 


## Economist theme

A theme that approximates the style of plots in The Economist
magazine.


```r
(qplot(carat, price, data = dsamp, colour = cut) + theme_economist() + scale_colour_economist() + 
    ggtitle("Diamonds Are Forever"))
```

![plot of chunk economist](http://i.imgur.com/3Dqh0.png) 


## Solarized theme

A theme and color and fill scales based on the Solarized palette.

The light theme.


```r
(qplot(carat, price, data = dsamp, colour = cut) + theme_solarized() + scale_colour_solarized("blue"))
```

![plot of chunk solarized-light](http://i.imgur.com/gyMSX.png) 


The dark theme.


```r
(qplot(carat, price, data = dsamp, colour = cut) + theme_solarized(light = FALSE) + 
    scale_colour_solarized("red"))
```

![plot of chunk solarized-dark](http://i.imgur.com/lbTCe.png) 


## Stata theme 

Themes and scales (color, fill, linetype, shapes) based on the graph
schemes in Stata.


```r
(qplot(carat, price, data = dsamp, colour = cut) + theme_stata() + scale_colour_stata() + 
    ggtitle("Plot Title"))
```

![plot of chunk stata](http://i.imgur.com/gd5Tz.png) 


## Excel 2003 theme

For that classic ugly look and feel. For ironic purposes only. 3D bars
and pies not included. Please never use this theme.


```r
(qplot(carat, price, data = dsamp, colour = cut) + theme_excel2003() + scale_colour_excel2003())
```

![plot of chunk excel1](http://i.imgur.com/Z5qND.png) 



```r
(ggplot(diamonds, aes(clarity, fill = cut)) + geom_bar() + scale_fill_excel2003() + 
    theme_excel2003())
```

![plot of chunk excel2](http://i.imgur.com/qYFO7.png) 


## Inverse Gray Theme

Inverse of `theme_gray`, i.e. white plot area and gray background.


```r
(qplot(carat, price, data = dsamp, colour = cut) + theme_igray())
```

![plot of chunk igray](http://i.imgur.com/NqZ2q.png) 



## Tableau Scales

Color, fill, and shape scales based on those used in the Tableau softare.


```r
(qplot(carat, price, data = dsamp, colour = cut) + theme_igray() + scale_colour_tableau())
```

![plot of chunk tableau](http://i.imgur.com/UU2bo.png) 



```r
(qplot(carat, price, data = dsamp, colour = cut) + theme_igray() + scale_colour_tableau("colorblind10"))
```

![plot of chunk tableau-colorbind10](http://i.imgur.com/C7bZA.png) 


## Stephen Few's Practical Rules for Using Color ...

Color palette and theme based on Stephen Few's ["Practical Rules for Using Color in Charts"](http://www.perceptualedge.com/articles/visual_business_intelligence/rules_for_using_color.pdf).


```r
(qplot(carat, price, data = dsamp, colour = cut) + theme_few() + scale_colour_few())
```

![plot of chunk few](http://i.imgur.com/6WyZ5.png) 


## Wall Street Journal

Theme and some color palettes based on plots in the *The Wall Street Journal*.


```r
(qplot(carat, price, data = dsamp, colour = cut) + theme_wsj() + scale_colour_wsj("colors6", 
    "") + ggtitle("Diamond Prices"))
```

```
## Error: could not find function "theme_wsj"
```

