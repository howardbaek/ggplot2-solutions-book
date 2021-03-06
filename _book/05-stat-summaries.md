# Statistical Summaries





## Exercises


**1.** What binwidth tells you the most interesting story about the distribution of `carat`?


```r
diamonds %>% 
  ggplot(aes(carat)) +
  geom_histogram(binwidth = 0.2)
```

<img src="05-stat-summaries_files/figure-html/unnamed-chunk-2-1.png" width="672" />


- Highly subjective answer, but I would go with 0.2 since it gives you the right amount of information about the distribution of `carat`: right-skewed.

<br>


**2.** Draw a histogram of `price`. What interesting patterns do you see?


```r
diamonds %>% 
  ggplot(aes(price)) +
  geom_histogram(binwidth = 500)
```

<img src="05-stat-summaries_files/figure-html/unnamed-chunk-3-1.png" width="672" />

- It's skewed to the right and has a long tail. Also, there is a small peak around 5000 and a huge peak around 0.


<br>


**3.** How does the distribution of `price` vary with `clarity`?


```r
diamonds %>% 
  ggplot(aes(clarity, price)) +
  geom_boxplot()
```

<img src="05-stat-summaries_files/figure-html/unnamed-chunk-4-1.png" width="672" />

- The range of prices is similar across clarity and the median and IQR vary greatly with clarity.  


<br>


**4.** Overlay a frequency polygon and density plot of `depth`. What computed variable do you need to map to `y` to make the two plots comparable? (You can either modify `geom_freqpoly()` or `geom_density()`.)


```r
diamonds %>% 
  count(depth) %>% 
  mutate(sum = sum(n),
         density = n / sum) %>% 
  ggplot(aes(depth, density)) +
  geom_line()
```

<img src="05-stat-summaries_files/figure-html/unnamed-chunk-5-1.png" width="672" />

- Say you start off with the count of values in `depth` and you plot `geom_freqpoly()`. Then, you would want to divide each count by the total number of points to get density. This would get you the y variable needed for `geom_density()`


