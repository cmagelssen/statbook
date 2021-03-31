# Finne verdiene 

For å estimere parameterne i modellen kan vi bruke verktøy vi allerede har lært. Vi gir likevel en grundig innføring her. Målet er at disse modelene er selvstendige, slik at du ikke trenger å gå tilbake til andre kapitler. Med andre ord, absolutt alt du trenger skal finnes her. 

I den enkleste modellen (null-hypotesen) estimerte vi kun ett enkelt parameter, memlig **mean**. Den modellen sa at vi kun trenger mean til å predikere individenes fremgang i RM. 

$$
Y_i = b0 + error_i
$$
Vi kan nå spørre oss om det er en relasjon mellom prediktorvariabelen vår (Gruppe) og fremgang i 1RM. Vi kan da bruke til lineære modellen som vi har brukt tidligere.  
$$
Y_i = (b0 + b1) + error_i
$$
Denne ligningen sier at et individs skår kan bli prediktert fra  modell som består av b0 og b1, pluss error. b1 kvantifiserer relasjonen mellom en prediktovariabelelen og utfallet - både hvor **sterkt** og hvilken **retning** dette forholdet har. Mens b0 sier hvilken verdi utfallet har når utfallsvariabelen er null eller 0.

I figuren under ser du tre modeller som har samme b0, men forskjellige b1. Studer figurene og svar på spørsmålene under.
\begin{figure}

{\centering \includegraphics[width=1\linewidth]{06-finneb_files/figure-latex/unnamed-chunk-1-1} 

}

\caption{**CAPTION THIS FIGURE!!**}(\#fig:unnamed-chunk-1)
\end{figure}


```r
library(webex)
```
<select class='solveme' data-answer='["2"]'> <option></option> <option>1</option> <option>2</option> <option>3</option></select> Nå vet dere hva b1 representerer.  






\begin{figure}

{\centering \includegraphics[width=1\linewidth]{06-finneb_files/figure-latex/unnamed-chunk-3-1} 

}

\caption{**CAPTION THIS FIGURE!!**}(\#fig:unnamed-chunk-3)
\end{figure}



SCP is the relationship between two variables





```r
relationship <- dummykodet.dat %>%
  mutate(avg.x = mean(dummykodet),
         x.avg.x = dummykodet - avg.x,
         avg.rm = mean(rm),
         rm.avg.rm = rm - avg.rm, 
         ssc = x.avg.x * rm.avg.rm, 
         sum.ssc = sum(ssc),
         ssx = sum(x.avg.x^2),
         tot = sum.ssc / ssx
         )
relationship
```

```
## # A tibble: 24 x 12
##    individ gruppe    rm dummykodet avg.x x.avg.x avg.rm rm.avg.rm   ssc sum.ssc
##      <int> <chr>  <dbl>      <dbl> <dbl>   <dbl>  <dbl>     <dbl> <dbl>   <dbl>
##  1       1 "tre.~  40.5          1   0.5     0.5   32.2      8.30  4.15    123.
##  2       2 "tre.~  49.1          1   0.5     0.5   32.2     16.9   8.45    123.
##  3       3 "tre.~  47.9          1   0.5     0.5   32.2     15.8   7.89    123.
##  4       4 "tre.~  44.5          1   0.5     0.5   32.2     12.4   6.18    123.
##  5       5 "tre.~  52.3          1   0.5     0.5   32.2     20.1  10.1     123.
##  6       6 "tre.~  40.0          1   0.5     0.5   32.2      7.86  3.93    123.
##  7       7 "tre.~  49.5          1   0.5     0.5   32.2     17.3   8.66    123.
##  8       8 "tre.~  29.2          1   0.5     0.5   32.2     -2.95 -1.48    123.
##  9       9 "tre.~  40.6          1   0.5     0.5   32.2      8.43  4.22    123.
## 10      10 "tre.~  37.6          1   0.5     0.5   32.2      5.42  2.71    123.
## # ... with 14 more rows, and 2 more variables: ssx <dbl>, tot <dbl>
```
