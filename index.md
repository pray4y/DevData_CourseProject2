---
title       : A Quick Guide to "GET 24!" the Game
subtitle    : Reproducible Presentation on ShinyApp
author      : Ariel (pray4y)
job         : JHU's Developing Data Products on Coursera
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]     # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
logo        : pray4y.png
---

## Inspiration of GET 24! 

People have designed thousands of games based on Pokers. Ever since Poker cards were invented, the influence of these cards have never been faded. 

The idea of GET 24! originated from a popular game I like to play with friends. We use full suits of Poker cards to represent integers from 1 to 13. Each round, four cards are drawn randomly from the card deck. Then these cards and thus the integers they represnt are revealed to every player. Whoever first manages to construct an arithmetic expression equal to twenty-four using these integers (operands) and regular arithmetic operators is the winner of the current round. 

This is a fun and challenging game, especially when multiple players are trying to compete with each other. 

--- 

## Layout of GET 24! 

As you can see, below is a partial screenshot of GET 24!.

![Game Screenshot](gamescreenshot.png)

--- 

## Widgets of GET 24! 

The outcome of each round is displayed in the right (main) panel. Game instructions are placed below the main text output in the right panel. 

Player controls the widgets in the left (sidebar) panel. There are four dropdown lists in the left panel, each provides thirteen valid choices representing different cards in each card suit. Player gets to select one card from each dropdown list. Essentially, each card can be mapped to an integer between 1 to 13. 

To view the proper outcome, player not only needs to choose four cards but also needs to click the "Calculate" button at the bottom of the left panel. Once the button is clicked, it may take a couple of seconds for GET 24! to calculate and print the outcome at the top of the right panel. 

--- 

## Flow of GET 24!

I. Player chooses four integers in the range of 1 to 13. In GET 24!, A is mapped to 1, J to 11, Q to 12, K to 13. Integers can be repetitive.
II. GET 24! calculates all possible arithmetic expressions using these four integers and three operators from add(+), substract(-), multiply(*), and/or divide(/). (Operators can be repetitive.) A typical arithmetic expression: 

```r
set.seed(2); a <- sample(13, 4, replace = TRUE)
set.seed(4); b <- sample(4, 3, replace = TRUE)
sign <- c("+", "-", "*", "/")
cat("(", "(", "(", a[1], sign[b[1]], a[2], ")", sign[b[2]], a[3], ")", sign[b[3]], a[4], ")")
```

```
## ( ( ( 3 * 10 ) + 8 ) - 3 )
```
III. The default order of operation as secured using pairs of brackets is from left to right. If GET 24! finds one or more expressions that equals 24, it will print the first of those expressions. Otherwise, it will modify the order of operations and continue searching until it runs out of possible expressions. 

---

## Ready to have a try? 

[GET 24!](https://pray4y.shinyapps.io/Get24_DevDataProd_CP/)

This page display a set of four integers randomly selected from 1 to 13. 
It will also give a valid GET 24! equation (if existing) corresponding to these four numbers. 




```r
set.seed(24); num1 <- sample(13, 4, replace = TRUE); cat(num1, "->", get24(num1))
```

```
## 4 3 10 7 -> ( ( ( 4 + 3 ) + 10 ) + 7 ) = 24
```

```r
set.seed(2424); num2 <- sample(13, 4, replace = TRUE); cat(num2, "->", get24(num2))
```

```
## 7 10 3 7 -> ( ( ( 7 * 3 ) + 10 ) - 7 ) = 24
```

```r
set.seed(242424); num3 <- sample(13, 4, replace = TRUE); cat(num3, "->", get24(num3))
```

```
## 8 2 4 12 -> ( ( ( 8 - 2 ) - 4 ) * 12 ) = 24
```


