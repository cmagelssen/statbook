# Sammenligne modeller



Nå som vi har bygget de to statistiske modellene - **en null-modell** og **en alternativ modell** - hvor går veien videre? Det vi sitter igjen med er en **error** (les sum of squared error) for null-modellen og en error for alternative modellen. Vår neste oppgave er å finne en måte å **sammenligne disse modellene** på. For å gjøre det helt eksplisitt og tydelig, skal vi nå sammenligne om modellen til høyre er bedre enn modellen til venstre. 

<div class="info">
Når vi sier at en modell er bedre, så mener vi at den vertikale avstanden fra linjen til datapunktene er kort. Hvis det er stor vertikal avstand fra datapunktet til linjen for mange individer, kan det tyde på at vi har en dårlig modell.
</div>

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{05-sammenligne_files/figure-latex/unnamed-chunk-2-1} 

}

\caption{Modeller med forskjellig b1}(\#fig:unnamed-chunk-2)
\end{figure}
## ANOVA-tabell (variansanalyse)
En måte vi kan sammenligne modeller på er å bruke en ANOVA-tabell, der vi legger inn erroren vi har regnet for de ulike modellene. Dette er en ganske vanlig tabell som dere kommer til å se flere ganger. 

**ANOVA-tabell**

Modell | SS | *df* | MS | *F* | $R^2$ | *p*-verdi
------------- | ------------- | ------------- | ------------- | ------------- | -------------
The model sum of squares (SS<sub>M</sub>) | <input class='solveme nospaces' size='6' data-answer='["2527.5"]'/> |  | | |  |
The residual sum of squares (SS<sub>R</sub>) | <input class='solveme nospaces' size='8' data-answer='["716.2875"]'/> | | | | |
The total sum of squares (SS<sub>T</sub>) | <input class='solveme nospaces' size='8' data-answer='["3243.784"]'/> | | | | |

<span style="font-size: 22px; font-weight: bold; color: var(--pink);">Oppgave</span>

a. Hva er sum of squared error for null-modellen? 

<div class="info">
Sett dette inn i total sum of squares (SS<sub>T</sub>
</div>

b. Hva er sum of squared error for den alternative modellen?

<div class="info">
Sett dette inn i residual sum of squares (SS<sub>R</sub>). Dette er error som er igjen etter at man har brukt den alternative-modellen. Man kaller dette for *residuals*
</div>

c. Hvor mye sum of squared error er redusert ved å bruke den alternative modellen i forhold null-modellen?

<div class="info">
Sett dette inn i residual sum of squares (SS<sub>M</sub>).Dette kalles The model sum of squares (SS<sub>M</sub>) eller regression i statistiske programmer. Dere regner dette ved å ta (SS<sub>T</sub>-SS<sub>M</sub>).  
</div>

<span style="font-size: 22px; font-weight: bold; color: var(--green);">Godt jobbet!</span>

Det er ønskelig at SS<sub>M</sub> er stor fordi det betyr at den alternative modellen vår forklarer mye error. Det kan ofte være lurt å lage figurer for å se dette visuelt. Det er flere måter å gjøre dette på. Vi liker å plotte dette i et stolpediagram, slik vi har gjort i figuren under. På denne måten er det enkelt å se om modellen vår (SS<sub>M</sub>) er en god eller dårlig modell; hvis høyden på stolpen som representerer SS<sub>M</sub> er høy betyr det at modellen forklarer mye error. I figuren til venstre ser du modellene vi har bygget, og et eksempel på en modell der SS<sub>M</sub> er høy. Figuren til høyre er ment som et sammenligningsgrunnlag, der vi viser et eksempel på en dårlig modell.


\begin{figure}

{\centering \includegraphics[width=0.6\linewidth]{05-sammenligne_files/figure-latex/unnamed-chunk-3-1} 

}

\caption{SS for de ulike modellene}(\#fig:unnamed-chunk-3)
\end{figure}

* SS<sub>T</sub> representerer den totale erroren (dvs. erroren vi fikk ved å bruke null-modellen)
* SS<sub>R</sub> representerer hvor mye error som er igjen etter at vi brukte den alternative modellen. 
* SS<sub>M</sub> er hvor mye error som modellen vår klarte å forklare. 


d. Hvis du sammenligner med figuren til venstre (vår modell) med figuren til høyre (som kun er brukt et eksempel), vil du si at vår alternative modell er god?

<select class='solveme' data-answer='["ja"]'> <option></option> <option>ja</option> <option>nei</option></select>. 

e. Hva er (SS<sub>T</sub>) - (SS<sub>R</sub>)? 

<input class='solveme nospaces' size='6' data-answer='["2527.5"]'/>

f. Hva er (SS<sub>R</sub>) + (SS<sub>M</sub>)? 

<input class='solveme nospaces' size='8' data-answer='["3243.784"]'/>

Med erroren vi har tilgjengelig kan vi regne noe som heter proporsjonal feilreduksjon (proportional reduction in error (PRE)). Hvis vi multipliserer dette tallet med 100 (* 100) får vi hvor mange % modellen vår har redusert error med, i forhold til null-modellen. Dette er en effektstørrelse som ofte blir rapoortert sammen med ANOVA eller regresjonsanalyser. I ANOVA ser du at man rapporterer denne som $n^2$, mens man i regresjonsanalyser kaller denne for $R^2$. Vi regner ut det på følgende måte:

$$
R^2 = \frac{(SS_T - SS_R)}{SS_T} * 100
$$

e. Hvilken verdi får du hvis du regner (SS<sub>M</sub>/ (SS<sub>T</sub>)) * 100?

<input class='solveme nospaces' size='2' data-answer='["78"]'/> (uten %-tegnet)

<div class="info">
Det er dessverre mange forskjellige navn på denne verdien. Du vil se at folk bruker PRE, $n^2$. Vit at de mener det samme.
</div>


<span style="font-size: 22px; font-weight: bold; color: var(--green);">Ferdig - Bra jobbet!</span>

## Teste (statistisk) om vår alternative modell forklarer mer varians enn null-modellen
En error-reduksjon på 2527.5 ($SS_M$), eller 78 % ($(R^2)*100$), kan virke mye. Men et problem med disse størrelsene er at de begge er garantert å øke i takt med antall parametere vi legger til i modellen. 

<div class="info">
Dere har ikke lært dette enda, men vit at vi kunne bygget en modell der vi inkluderer kjønn, alder, treningsstatus som prediktorvariabler. Da ville dere fått en mer kompleks modell:

$$
Y_i  = b_0 + b_1(Gruppe_i) + b_2(Kjønn_i) + b_3(Treningstatus_i) + b_4(Alder_i)
$$
</div>

Derfor er det mer interessant å regne ut gjennomsnittlig $SS_M$ per parameter vi har lagt til i modellen (i forhold til null-modellen). Dette kalles **Mean Squared Model (MSM)**, eller gjennomsnittlig squared error for den alternative modellen, og regnes på følgende måte:

$$
\text{ Mean Squared Model } (MS_M) = SS_M / df_M
$$

$df_m$ står for antall frihetsgrader som er lagt til i modellen utover null-modellen. Null-modellen har kun ett parameter ($b_0$), som er mean, mens vår alternative modell har to parametere ($b_0$ og $b_1$). Derfor blir $df_M$ = (2-1) = 1. 

<span style="font-size: 22px; font-weight: bold; color: var(--pink);">Oppgave</span>


a. Regn ut Mean Squared Error ($MS_M$) og sett det verdien inn i ANOVA-tabellen vår

**ANOVA-tabell**

Modell | SS | *df* | MS | *F* | $R^2$ | *p*-verdi
------------- | ------------- | ------------- | ------------- | ------------- | -------------
The model sum of squares (SS<sub>M</sub>) | 2527.5 |  |  <input class='solveme nospaces' size='6' data-answer='["2527.5"]'/> || 0.78 |
The residual sum of squares (SS<sub>R</sub>) | 716.2875 | | | | |
The total sum of squares (SS<sub>T</sub>) | 3243.784 | | | | |

<div class="info">
Det vi ønsker at dere tar med dere fra denne oppgaven er at en høy $SS_M$ eller $R^2$ er **mer imponerende hvis vi kun har lagt til ett ekstra parameter enn hvis vi hadde lagt til f.eks. 10 parametere**. Enig?
</div>

<span style="font-size: 22px; font-weight: bold; color: var(--green);">Bra!</span>

Det siste vi skal gjøre er å sammenligne $MS_M$ med $MS_R$. **$MS_R$** er $SS_R$, den erroren som er igjen etter at vi har brukt den alternative modellen, **delt på antall parametere som i prinsippet kunne vill lagt til i modellen**. I prinsippet står vi fritt til å legge til så mange parametere i modellen som vi ønsker, men antall parametere kan aldri overstige antall deltakere i studien. Men fordi vi allerede har brukt to parametere i den alternative modellen, kan vi kun  legge til (24 - 2) = 22 parametere.

$$
\text{ Mean Squared Residual (MSR) }  = SS_R / df_R
$$
b. Regn ut Mean Squared Residual ($MS_R$) og sett det verdien inn i ANOVA-tabellen vår

**ANOVA-tabell**

Modell | SS | *df* | MS | *F* | $R^2$ | *p*-verdi
------------- | ------------- | ------------- | ------------- | ------------- | -------------
The model sum of squares (SS<sub>M</sub>) | 2527.5 |  | 2527.5 |  | 0.78 |
The residual sum of squares (SS<sub>R</sub>) | 716.2875 | | <input class='solveme nospaces' size='8' data-answer='["32.55852"]'/> |  | |
The total sum of squares (SS<sub>T</sub>) | 3243.784 | | | | |

<div class="info">
$MS_R$ er gjenstående error per parameter som potensielt kunne blitt lagt til i modellen. Med andre ord er det den gjennomsnittlige erroren som er igjen per parameter som kunne blitt lagt til i modellen. Enig?
</div>

<span style="font-size: 22px; font-weight: bold; color: var(--green);">Vi er endelig i mål!</span>

Nå har vi gjort alle utregningene, og vi kan bare sammenligne disse to størrelsene ($MS_M$ versus $MS_R$) med hverandre. Dette kalles en **F-test**.

$$
\text{F}  = \frac{MS_M}{MS_R}
$$

c. Regn ut vår F-verdi og sett den inn i vår ANOVA-tabell

**ANOVA-tabell**

Modell | SS | *df* | MS | *F* | $R^2$ | *p*-verdi
------------- | ------------- | ------------- | ------------- | ------------- | -------------
The model sum of squares (SS<sub>M</sub>) | 2527.5 | 1 | 2527.5 | <input class='solveme nospaces' size='5' data-answer='["77.63"]'/> | 0.78 | p < 0.001
The residual sum of squares (SS<sub>R</sub>) | 716.2875 | 22 | 32.55852 |  | |
The total sum of squares (SS<sub>T</sub>) | 3243.784 | | | | |

Vi kan se at vår F-verdi er 77.63. Denne verdien er høyere enn den kritiske verdien for 0.05 ved $df_M$ = 1 og $df_R$ = 22. Dette kan du se i figuren under. Vi sier derfor at vår modell er signifikant, hvilket vil si at den har forbedret vår evne til å predikere utfallsvariabelen. 

<div class="info">
En F-fordeling ser veldig lik ut som en z- og t-fordeling, og fungerer på samme måte: Vi regner ut en F-verdi, og spør om sannsynligheten  for å oppnå en slik verdi gitt at null-hypotesen er sann. Null-hypotesen i en F-test er at den alternative modellen ikke forklarer noe varians. Med andre ord at $R^2$ = 0.
</div>


\begin{figure}

{\centering \includegraphics[width=0.6\linewidth]{05-sammenligne_files/figure-latex/unnamed-chunk-4-1} 

}

\caption{F-test}(\#fig:unnamed-chunk-4)
\end{figure}

<span style="font-size: 22px; font-weight: bold; color: var(--green);">Done!</span>

Da er det bare å sette seg tilbake å nyte denne sangen:

<iframe width="600" height="350" src="https://www.youtube.com/embed/XHR3Rpij42Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

![F-testen](F.png)


Hvis dette ikke var forståelig foreslår jeg følgende tutorials:

- https://www.youtube.com/watch?v=eSJAjlavPwU

- https://www.youtube.com/watch?v=0xWDulRHd9M

- https://www.youtube.com/watch?v=iAE4UeoVE9A

- https://www.youtube.com/watch?v=OK4Xns4zabs


<div class="info">
Her kan du se output jeg får hvis jeg gjør den statiske analysen i R. Ser verdiene kjent ut?
</div>




```r
#aov er en forkortolse for analysis of variance (ANOVA)
#dette er funksjon som kommer mer R.
summary(aov(rm ~ dummykodet, dat))
```

```
##             Df Sum Sq Mean Sq F value   Pr(>F)    
## dummykodet   1 2527.5  2527.5   77.63 1.15e-08 ***
## Residuals   22  716.3    32.6                     
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```





