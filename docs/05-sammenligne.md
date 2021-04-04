# Sammenligne modeller med en ANOVA-tabell (variansanalyse)



Nå har vi bygget to modeller og regnet ut hvor mye error det er hver av disse modellene - **null-modell** og **den alternative modellen**. Vår neste oppgave er å **sammenligne disse modellene**. For å gjøre det helt tydelig, så skal vi steste om modellen til høyre er bedre enn modellen til venstre. Når vi sier bedre, så mener vi at den har mindre error i seg.  

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{05-sammenligne_files/figure-latex/unnamed-chunk-2-1} 

}

\caption{**CAPTION THIS FIGURE!!**}(\#fig:unnamed-chunk-2)
\end{figure}

For å sammenligne disse modellene er det vanlig å bruke en ANOVA-tabell. Dette er en ganske vanlig tabell som dere kommer til å se mange ganger, så det er bare å bli vant til å se disse. Dere har allerede regnet ut all nødvendig informasjon for å lage en ANOVA-tabell, så dere kan lage den selv.


**ANOVA-tabell**

Modell | SS | *df* | MS | *F* | $R^2$ | *p*-verdi
------------- | ------------- | ------------- | ------------- | ------------- | -------------
The model sum of squares (SS<sub>M</sub>) | <input class='solveme nospaces' size='6' data-answer='["2527.5"]'/> |  | | |  |
The residual sum of squares (SS<sub>R</sub>) | <input class='solveme nospaces' size='8' data-answer='["716.2875"]'/> | | | | |
The total sum of squares (SS<sub>T</sub>) | <input class='solveme nospaces' size='8' data-answer='["3243.784"]'/> | | | | |

**Oppgave**

a. Hva var sum of squared error for null-modellen? 

>>(Sett dette inn i total sum of squares (SS<sub>T</sub>)

b. Hva var sum of squared error for den alternative modellen?

>>(Sett dette inn i residual sum of squares (SS<sub>R</sub>). Dette er error som er igjen etter at man har brukt den alternative-modellen. Men >>andre ord. Man kalles dette residuals.

c. Hvor mye sum of squared error er redusert ved å bruke den alternative modellen i forhold null-modellen?

>>Dette kalles The model sum of squares (SS<sub>M</sub>) eller regression i statistiske programmer. 

Før vi går videre er det greit å visualisere erroren som er igjen med de to modellene, pluss hvor mye error som er redusert ved å bruke den alternative modellen istf. å bruke null-modellen. I figuren under ser du de tre modellene. SS<sub>T</sub> representerer den totale erroren (dvs. erroren vi fikk ved å bruke null-modellen); SS<sub>R</sub> representerer hvor mye error som er igjen etter at vi brukte den alternative modellen.  SS<sub>M</sub> er hvor mye error som modellen vår klarte å forklare. Vil du si at den alternative modellen vår er god?

>>Hint. Hvis du summerer SS<sub>M</sub> og SS<sub>R</sub> får du SS<sub>T</sub>

Sammenlign dette med modellen til høyre. Her har vi en modell som er dårlig fordi SS<sub>M</sub> er lav og SS<sub>R</sub> er høy.

>>For sikkerhets skyld. Modellen til høyre ble bare brukt som et eksempel for at du skal forstå at vi kan vurdere hvor god modellen vår er.

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{05-sammenligne_files/figure-latex/unnamed-chunk-3-1} 

}

\caption{**CAPTION THIS FIGURE!!**}(\#fig:unnamed-chunk-3)
\end{figure}
e. Basert på det du ser i figuren over til venstre, vil du si at vår alternative modell er god?

<select class='solveme' data-answer='["ja"]'> <option></option> <option>ja</option> <option>nei</option></select>. 

d. Hva er (SS<sub>T</sub>) - (SS<sub>R</sub>)? 

<input class='solveme nospaces' size='6' data-answer='["2527.5"]'/>

e. Hva er (SS<sub>R</sub>) + (SS<sub>M</sub>)? 

<input class='solveme nospaces' size='8' data-answer='["3243.784"]'/>

Vi kan regne ut hvor mange % modellen vår har redusert error med, og dette er gange nyttig. Dette får dere vite når dere kjører en test i Jamovi eller R, men vi kan også regne det for hånd. Verdien fi vår kalles $R^2$.

$$
R^2 = \frac{(SS_T - SS_R)}{SS_T} * 100
$$

e. Hvilken verdi får du hvis du regner (SS<sub>M</sub>/ (SS<sub>T</sub>)) * 100?

<input class='solveme nospaces' size='2' data-answer='["78"]'/> (uten %-tegnet)

>>Det er dessverre mange forskjellige navn på denne verdien. Du vil se at folk bruker PRE, $n^2$. Vit at de mener det samme.

Det kan høres ut som at en errorreduksjon på 78 % er mye, og det vil vi absolutt påstå at det er! Kan vi da konkludere at den alternative modellen er bedre enn null-modellen? - det ser jo ut til at dette er mye.

## teste null-hypotesen med F
For å teste om en SSM eller en errorreduksjon på 78 % er mye eller lite skal vi bruke en F-test og en F-fordeling. En F-fordeling ser veldig lik ut som en z og t-fordeling og fungerer på samme måte: Vi regner ut en F-verdi, og spør fra sannsynligheten er for å oppnå en slik verdi gitt at null-hypotesen er sann. Null-hypotesen i en F-test er at den alternative modellen ikke forklarer noe varians. Med andre ord at $R^2$ = 0. For å teste dette må vi regne ut en F-verdi:

$$
F = \frac{(SS_M / df_M)}{SS_R / df_R}
$$
Vi har allerede regne ut, så vi kan plotte disse inn.

$$
F = \frac{(<input class='solveme nospaces' size='6' data-answer='["2527.5"]'/> / df_M)}{716.2875 / df_R}
$$
Men hva er de respektivene frihetsgradene som er i nevneren og telleren? Å forstå dette vil gi en god forståelse for hva F-verdien er. Vi fokuserer på telleren først. Modellen reduserte Sum of Squared error med 2527.5, som i grunn er mye. Men vi kunne bygget en superkompleks og lagt til haugevis av ekstra parametere. Dette kunne vi gjort ved å f.eks sammenlignet enda flere grupper. Vi har ikke lært hvordan vi gjør dette enda, men vi kan fint gjøre det. Og vi skal vise hvordan senere. Vi kunne derfor i prinsippet ha gått fra: 

$$
Y_i = b_0
$$
til:
$$
Y_i  = b_0 + b_1X_i + b_2X_i + b_3X_i + b_4X_i + b_5X_i
$$
I så fall ville vi garantert ha fått en stor Sum of squared error fordi et parameter alltid vil redusere error noe, aldri øke det. Så det vi skal gjøre i telleren i formelen er å dele på SSm / på antall parametere vi har brukt utover det null-modellen har brukt. Null-modellen hadde kun ett parameter, mens den altenative modellen hadde 2, så df blir 1. Poenget som jeg vil at dere skal huske på er at. Dette er variansen. Poenget er en SSm er mer imponerende om vi har brukt få ekstra parametere. 





Husk at når vi trekker to eller flere utvalg fra en populasjon, så vil disse utvalgene nesten alltid være forskjellige fra hverandre. 


Vi kunne bruke samme prinsipp for t-fordelingen. Null-hypotesen var disse tilfellene var at disse 

Felles for disse fordelingene er at de baserer seg på gjennomsnittet mellom utvalg. V

Da vi brukte en *z*-fordeling sa vi at 95 % av utvalgene vi trekker fra en populasjon med et gjennomsnitt på 0 og et standardavvik på 1, ville falle mellom en z-verdi på -1.96 og 1.96, gitt at de ble trukket fra denne populasjonen. Hvis vi plutselig observerte en z-skår for vårt utvalg som høyere enn 1.96 eller lavere enn -1.96, sa vi at vi hadde et signifikant funn og at utvalgene dermed ikke kommer fra samme populasjon. Vi brukte en t-fordeling på lignende måte. 

Men hvis vi brukte en z-fordeling, så sa vi at 95 % av utvalgene vi trekker fra en slik fordeling vil falle mellom en z-verdi mellom -1.96 og 1.96. Vi kan bruke en t-fordeling til å si noe lignende. Felles for z-fordelingen og t-fordelingen er de går på sample means. En f-fordeling baserer seg ikke på means, men på reduksjon i sum of squared errors. Null-hypotesen er at det ikke modellen vår reduserer noe error i det hele tatt. Men fordi forskjellige utvalg gir forskjellige, må vi forvente at det er noen fordelinger under null



Vi har allerede jobbet med to fordelinger, en z-fordeling, t-fordeling. Det vi skal jobbe med nå er en F-fordeling. En F-fordeling er nesten likt som en z-fordeling og en t-fordeling, men er litt forskjellig fra disse på den måten at en F-fordeling operer med forklart Sum of Squarered error ved modellen, mens en z-fordeling og t-fordeling operer med sample means. Med andre ord, istf. å si hva er sannsynlig for observere en t, gitt att, skal vi spørre hva er sannsynligheten for at det ikke noe explained varians. Gitt at null hypotesen er sann, dvs.. Selv om vi har explained variance i populasjonen, så vil det alltid være litt explained variance fra utvalg til utvalg. Dere husker kanskje. Så det vi må gjøre er å regne ut hvor mye hvor mye f-verdi, og så spørre oss, hva er sannsynligheten for å få en f-statistikk, så stor som denne, gitt at null hypotesen er sann. Explianed variansen av denne modellen er null. 

For å finne ut av dette må vi regne ut en f-verdi. Formelen for dette er 

## teste null-hypotesen med t





Nå har vi kun lagt til ett ekstra parameter i forhold til null-modellen; vi gikk fra:

$$
Y_i = b_0
$$
til: 

$$
Y_i = b_0 + b_1X_i
$$

Men tenk om vi hadde lagt til enda flere prediktorvariabler i modellen. Vi har ikke lært hvordan vi gjør dette enda, men vi kan fint gjøre det. Og vi skal vise hvordan senere. Vi kunne derfor i prinsippet ha gått fra: 

$$
Y_i = b_0
$$
til:
$$
Y_i  = b_0 + b_1X_i + b_2X_i + b_3X_i + b_4X_i + b_5X_i
$$
I så fall ville vi garantert ha fått en stor errorreduksjon fordi noen av disse parameterne ville vært gode. Derfor regner vi gjennomsnittlig squared error, som vi kaller for **Mean Squared Error (MSE)**. Poenget med dette er at høy errorreduksjon med en alternativ modellen er mye mer imponerende hvis vi kun har med en prediktorvariabel enn om vi har med mange. Derfor regner vi  **Mean SquaredM Model (MSE)**. MSE regnes ved å ta SS<sub>M</sub> / frihetsgrader (*df*). Frihetsgradene vi bruker til dette er antatt ektra parametere vi har lagt til i modellen vår med referanse til null-modellen. Vi hadde 2 parametere i den alternative modellen og 1 i null-modellen, så 2-1.

f. Regn ut **Mean Squared Model (MSM)** og putt den inn i ANOVA-tabellen. $MS_M=\frac{(SS_M)}{df}$. Legg samtidig antall frihetsgrader for MSE inn i ANOVA-tabellen over.

Det neste vi skal gjøre er å regne er **Mean Squared  (MSM)**

g. Det aller siste vi skal gjøre er å 


h. I cellen under har jeg kjørt en ANOVA-test. Virker resultatene kjent. Skriv *p*-verdien din inn i?


Hvis dette ikke var forståelig foreslår jeg følgende tutorials:
- https://www.youtube.com/watch?v=eSJAjlavPwU
- https://www.youtube.com/watch?v=0xWDulRHd9M
- https://www.youtube.com/watch?v=iAE4UeoVE9A
- https://www.youtube.com/watch?v=OK4Xns4zabs




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





\begin{figure}

{\centering \includegraphics[width=1\linewidth]{05-sammenligne_files/figure-latex/unnamed-chunk-6-1} 

}

\caption{**CAPTION THIS FIGURE!!**}(\#fig:unnamed-chunk-6)
\end{figure}
