# Regresjon og korrelasjon

I dette kapittelet skal vi lære hvordan vi kan se om det er en relasjon mellom to kontinuerlige variabler. Tidligere har vi sett om det er relasjoner mellom en avhengig variabel som er kontinuerlig og en variabel som er kategorisk. Men nå skal altså begge være kontinuerlige. 

<iframe width="600" height="400" src="https://www.youtube.com/embed/t-wemxX4O6A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Før vi begynner, la oss repetere hvordan vi kan se om det er en relasjon mellom to variabler. Ta en titt i figuren under: 

<span style="font-size: 16px; font-weight: bold; color: var(--pink);"> - I figur A er det en positiv relasjon mellom X og Y. For hver enhets økning i X, så stiger den forventede verdien av Y med 0.4</span>

<span style="font-size: 16px; font-weight: bold; color: var(--pink);">- I figur B er det ingen relasjon mellom X og Y. Linjen er helt flat</span>

<span style="font-size: 16px; font-weight: bold; color: var(--pink);">- I figur C er det en negativ relasjon mellom X og Y. For hver enhets økning i X, så faller den forventede verdien av Y med -0.4. </span>

Enig? Dette bør være kjent stoff.

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{14_relasjoner_files/figure-latex/unnamed-chunk-1-1} 

}

\caption{Modeller med forskjellig b1}(\#fig:unnamed-chunk-1)
\end{figure}


## Datasett
Før vi begynner med korrelasjon og regresjon, trenger vi et nytt datasett. Datasettet jeg har fisket opp kommer fra *Camus et al. 1992* og inneholder 21 personer sin vo2-maks og tid på 800 meter. Hva tror dere, er det en sammenheng mellom disse variablene?

Her er datasettet:


```r
library(tidyverse)
# Vo2-maks
vo2 <- c(52.5, 50, 56.75, 57, 57.5,58,60.75, 60.5,60,63,61,64.5,64,65.75,66.75,66,68.25,68,70.5,73.25, 74)
# Tidene på 800m
lopsprestasjon <- c(159,147,153,160,143,132,130,135,137,128,121,125,130,137,141,136,122,117,119,121,116)
# Individene
individ <- seq(length(lopsprestasjon))
# Setter dette inn i en dataframe
dat <- data.frame(individ, vo2, lopsprestasjon)
```


\begin{table}

\caption{(\#tab:unnamed-chunk-3)Vo2maks og 800meter tid for 21 personer}
\centering
\begin{tabular}[t]{rrr}
\toprule
individ & vo2 & lopsprestasjon\\
\midrule
1 & 52.50 & 159\\
2 & 50.00 & 147\\
3 & 56.75 & 153\\
4 & 57.00 & 160\\
5 & 57.50 & 143\\
\addlinespace
6 & 58.00 & 132\\
7 & 60.75 & 130\\
8 & 60.50 & 135\\
9 & 60.00 & 137\\
10 & 63.00 & 128\\
\addlinespace
11 & 61.00 & 121\\
12 & 64.50 & 125\\
13 & 64.00 & 130\\
14 & 65.75 & 137\\
15 & 66.75 & 141\\
\addlinespace
16 & 66.00 & 136\\
17 & 68.25 & 122\\
18 & 68.00 & 117\\
19 & 70.50 & 119\\
20 & 73.25 & 121\\
\addlinespace
21 & 74.00 & 116\\
\bottomrule
\end{tabular}
\end{table}

## Visualisering av dataen
Det første vi bør gjøre er å visualisere dataen for å se om vi har uteliggere, og for å få et inntrykk av dataen. For data der begge variablene er kontinuerlige er det fint å bruke et **scatterplot**. Dette viser hvert individ sin observasjon på X og Y variabelen. 


```r
ggplot(dat, aes(vo2, lopsprestasjon)) +
  # legger på punkter (de stort prikkene)
  geom_point() +
  labs(x="Vo2.maks", y="800meter løp") +
  theme_bw()
```

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{14_relasjoner_files/figure-latex/unnamed-chunk-4-1} 

}

\caption{løpsprestasjon}(\#fig:unnamed-chunk-4)
\end{figure}

## Pearson's korrelasjonskoeffisient (*r*)
For å finne ut om det er en relasjon mellom to variabler, kan vi bruke Pearson's korrelasjonskoeffisient (*r*). Det er flere måter å regne ut *r* på, men jeg kommer til å bruke formelen som står i boken deres:  


$$
r = \frac{\sum_{i=1}^{n}(x_i -\bar{x})(y_i -\bar{y})} {(N-1)sd_xsd_y}
$$
Vi begynner med det som står i telleren $(x_i -\bar{x})(y_i -\bar{y})$. Dette kalles **cross-product deviations**. Det vi er interessert i å finne ut er om en person sin skår på en variabel er over eller under gjennomsnittet på denne variabelen. Det er dette $(x_i -\bar{x})$ forteller oss. Men samtidig ønsker vi å se om denne personen er over eller under gjennomsnittet på den andre variabelen $(y_i -\bar{y})$. For å finne ut av denne multipliserer vi de to, eller vi regner ut kryssproduktet. 

- Hvis det er en positiv relasjon mellom to variabler skal en person sin skår på x-variabelen være høyere enn gjennomsnittet å x-variabelen og samtidig være høyere enn gjennomsnittet på y-variabelen
- Hvis det er en negativ relasjon mellom to variabler skal en person sin skår på x-variabelen være høyere enn gjennomsnittet på x-varianelen og samtidig være lavere enn gjennomsnittet på y-variabelen


Det er enklere å se dette visuelt. I figuren under har jeg lagt på linjer som viser gjennomsnittet. Studer figuren **nøye**. Studer hvordan individene er plassert i forhold til linjene.


\begin{figure}

{\centering \includegraphics[width=1\linewidth]{14_relasjoner_files/figure-latex/unnamed-chunk-5-1} 

}

\caption{**CAPTION THIS FIGURE!!**}(\#fig:unnamed-chunk-5)
\end{figure}
Videre forteller formelen at vi skal summere all cross-production deviations, så vi gjøre dette:

$$
r = \frac{\sum_{i=1}^{n}(x_i -\bar{x})(y_i -\bar{y})} {(N-1)sd_xsd_y} = \frac{-1292.19} {(N-1)sd_xsd_y}
$$
Deretter sier formelen at vi skal dele antall N-1, multiplisert med standardavviket for x og standardavviket for y. Grunnen til at vi gjør dette er for å få en standardisert relasjon som vi kan sammenligne på tvers av studier. Legg merke til at vi også må multiplisere de to standardavvikene med hverandre før vi deler.

$$
r = \frac{\sum_{i=1}^{n}(x_i -\bar{x})(y_i -\bar{y})} {(N-1)sd_xsd_y} = \frac{-1292.19} {(20)1664.213} = -0.7764574	
$$

Jeg kan bekrefte at denne korrelasjonen stemmer.

```r
r <- cor.test(dat$vo2, dat$lopsprestasjon, method="pearson")
r
```

```
## 
## 	Pearson's product-moment correlation
## 
## data:  dat$vo2 and dat$lopsprestasjon
## t = -5.3708, df = 19, p-value = 3.497e-05
## alternative hypothesis: true correlation is not equal to 0
## 95 percent confidence interval:
##  -0.9048506 -0.5185974
## sample estimates:
##        cor 
## -0.7764574
```

Vi kan rapportere dere på følgende måte:


Det var en signifikant relasjon negativ relasjon mellom vo2maks og tid på 800 meter , *r* = −.77, 95% CI [−.90, .52], *p* = < .001


<div class="warning">
En ting som er viktig å vite er at r kun kan variere mellom -1 og 1, aldri mer. Så en r på −.77 er en stor effekt. 

Spill dette spill til dere skjønner korrelasjon:
http://guessthecorrelation.com/
</div>


## Regresjon
Vi kan også gjøre en regresjonsanalyse på samme datasett. Korrelasjon spør om det er en sammenheng eller en relasjon mellom to variabler, mens en regresjon spør om vi kan predikere noe. De to teknikkene er veldig relatert til hverandre. Alt vi har gjort i dette faget er egentlig regresjon, så det er ingenting nytt jeg kommer med nå. Vi skal regresjonsmodell for å spørre om vi kan predikere en person sin løpstid på 800meter basert på deres vo2.maks. Vi har derfor to kontinuerlige variabler som vi kan sette opp med følgende ligning:

$$
lopstid= b_0 + b_1(vo2maks_i) + error 
$$
For å undersøke om vi kan bruke vo2maks til å predikere tid på 800meter, må vi bygge to modeller:
- **NULL-modellen** (null-hypotesen som sier at vi kun trenger gjennomsnittet til å predikere tid på 800m)
- **Alternative modellen**(modellen vår som sier at kan bruke vo2maks til å predikere tid på 800m)

Disse modellene kan du se i figuren under. Figur A er null-modellen og figure B er den alternative modellen.



```
## `geom_smooth()` using formula 'y ~ x'
```

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{14_relasjoner_files/figure-latex/unnamed-chunk-8-1} 

}

\caption{**CAPTION THIS FIGURE!!**}(\#fig:unnamed-chunk-8)
\end{figure}
For å sammenligne disse modellene bruker vi nøyaktig samme prosedyre som har gjort tidligere. Gå tilbake til de andre kapitlene i boken om du ikke husker dette. Jeg kjører derfor bare modellen i R for dere.


```r
# lm står for linear model
alternativ_modell <- lm(lopsprestasjon ~ vo2, dat)
summary(alternativ_modell)
```

```
## 
## Call:
## lm(formula = lopsprestasjon ~ vo2, data = dat)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -15.603  -5.960  -1.766   7.459  16.948 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept) 234.9559    18.9327  12.410 1.47e-10 ***
## vo2          -1.6123     0.3002  -5.371 3.50e-05 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 8.499 on 19 degrees of freedom
## Multiple R-squared:  0.6029,	Adjusted R-squared:  0.582 
## F-statistic: 28.85 on 1 and 19 DF,  p-value: 3.497e-05
```

## Rapportering av regresjon
Vi fant at vo2.maks predikerte løpstid på 800m, *b* = –.161, *t* (19) = -5.37, *p* < .001. vo2 maks forklarte også en signifikant andel av variansen i løpsprestasjon, $R^2$ = .60, F(1, 19) = 28.85, *p* < .001.



