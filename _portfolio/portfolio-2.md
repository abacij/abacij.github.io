---
title: "R Package"
excerpt: Developing a Package in R to Test the Presence of Momentum in Sports Data<br/><img src='/images/screen.jpg' style="width:400px;">
collection: portfolio
---

Understanding momentum in sports has long been a subject of interest, with implications for strategy, performance evaluation, and fan engagement. While the notion of a “hot hand” is largely considered a fallacy with no empirical basis, spectators and media outlets continue to alter their expectations for a future win if a player or team has been on a consistent positive streak. Kent (2006) defines this momentum as “the positive or negative change in cognition, affect, physiology, and behavior caused by an event or series of events that affects either the perceptions of the competitors or, perhaps, the quality of performance and the outcome of the competition.” 

Given the common influence of cognitive illusions and flawed judgment, it is essential to employ statistical methods to accurately discern whether outcomes in a sequence are genuinely random or influenced by preceding events. The aim of this project was to address the need for a tool facilitating efficient and reproducible analyses of binary data in this context. Using R, we developed a package tailored for analyzing binary data sequences, aiming to detect momentum or non-random patterns in sports data. By providing a tool for analyzing sports data, this project contributes to advancing our understanding of momentum in sports and supports informed decision-making in sports analytics.

You can find the package on my github repository, titled "Momentum-Package"

You can download and install the package by running these lines of code: 

```r
install.packages("devtools")
devtools::install_github("abacij/Momentum-Package", force = TRUE)
library(MomentumTest)
