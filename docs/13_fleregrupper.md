# Sammenligne flere grupper

Nå har sett om det er forskjeller mellom to grupper på èn kontinuerlig, avhengig variabel, men i flere sammenhenger ønsker vi å studere om det er **forskjeller mellom flere grupper**. Kanskje har vi gjort et eksperiment der en gruppe ikke har trent (gruppe 1), en gruppe som har trent middels mye (gruppe 2) og en tredje gruppe som har trent kjempemye (gruppe 3). Vi kan i prinsippet ha så mange grupper vi bare vil. 

For å finne ut av dette kan vi bruke en **ANOVA**. Dere er allerede kjent med ANOVA, så jeg kommer ikke til å introdusere dere for noe nytt. Eller, jo, en liten ting, en det kommer jeg tilbake til.


<iframe width="600" height="300" src="https://www.youtube.com/watch?v=98KoXQiSiDo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



<div class="info">
Siden vi har lært å bruke en lineær modell, så slipper vi å lære oss noe nytt når vi nå skal sammenligne flere grupper. Teknikken vi allerede har lært oss kan enkelt brukes til andre formål

Når dere leser dette, vennligst ofre en liten tanke til de stakkarene som må lære seg ANOVA, t-test, ANCOVA osv., som helt forskjellige statistiske tester! Da blir det mange formler å lære seg. 

</div>




## Datasett

Fordi vi nå skal undersøke om tre grupper er forskjellige, trenger vi et nytt datasett. Datasettet vi skal bruke er hentet fra masteroppgaven til Varpestuensom han leverte i 2020. Tittelen på oppgaven var:

*Effekter av 7 uker styrketrening med høyt og moderat volum på muskelstyrke, muskeltykkelse og total-RNA hos unge voksne*


Det er en veldig interessant studie der han undersøkte effekten av å trene med moderat og høyt volum på muskelstyrke, muskeltykkelse og total-RNA. 

**Eksperimentet ble gjennomført som et between-subject design med tre grupper:**

* en gruppe som ikke trente styrketrening (*null.sett*)
* en gruppe trente tre sett med styrketrening (*tre.sett*)
* en gruppe som trente seks sett med styrketrening (*seks-sett*)


Vi har ikke tilgang på dette datasettet, men vi simulert datasettet i R. Se tabellen under. Som dere kan lese fra tittelen til oppgaven, har Varpestuen undersøkt effekten av 7 uker styrketrening på **muskelstyrke**, **muskeltykkelse** og **total-RNA** i vastus lateralis hos unge voksne. Det er altså flere avhengige variabler i studien hans, men for å gjøre dette enkelt, skal vi konsentrere oss om **muskeltykkelse**. Vi kan lese i metodekapittelet at han brukte ultralyd for å måle dette og at han rapporterte dette i mm. Men siden han ville se på fremgang regnet han om dette til % frengang fra første treningsuke. 


Her ser dere datasettet som vi har simulert:



\begin{table}

\caption{(\#tab:unnamed-chunk-2)Simulert datasett (Varpestuen 2020)}
\centering
\begin{tabular}[t]{rlr}
\toprule
individ & gruppe & vl\_tykkelse\\
\midrule
1 & null.sett & 3\\
2 & null.sett & 6\\
3 & null.sett & 1\\
4 & null.sett & 1\\
5 & null.sett & -2\\
\addlinespace
6 & null.sett & -5\\
7 & null.sett & 7\\
8 & null.sett & 14\\
9 & null.sett & 9\\
10 & null.sett & -2\\
\addlinespace
11 & null.sett & 4\\
12 & null.sett & 10\\
13 & null.sett & 5\\
14 & null.sett & 1\\
15 & null.sett & 5\\
\addlinespace
16 & null.sett & 6\\
17 & null.sett & 1\\
18 & null.sett & 4\\
19 & null.sett & 1\\
20 & null.sett & 3\\
\addlinespace
21 & tre.sett & 18\\
22 & tre.sett & 12\\
23 & tre.sett & 16\\
24 & tre.sett & 10\\
25 & tre.sett & 9\\
\addlinespace
26 & tre.sett & 11\\
27 & tre.sett & 16\\
28 & tre.sett & 14\\
29 & tre.sett & 8\\
30 & tre.sett & 12\\
\addlinespace
31 & tre.sett & 8\\
32 & tre.sett & 1\\
33 & tre.sett & 16\\
34 & tre.sett & 16\\
35 & tre.sett & 15\\
\addlinespace
36 & tre.sett & 9\\
37 & tre.sett & 14\\
38 & tre.sett & 6\\
39 & tre.sett & 10\\
40 & tre.sett & 11\\
\addlinespace
41 & seks.sett & 17\\
42 & seks.sett & 26\\
43 & seks.sett & 25\\
44 & seks.sett & 22\\
45 & seks.sett & 29\\
\addlinespace
46 & seks.sett & 17\\
47 & seks.sett & 26\\
48 & seks.sett & 6\\
49 & seks.sett & 18\\
50 & seks.sett & 15\\
\addlinespace
51 & seks.sett & 12\\
52 & seks.sett & 19\\
53 & seks.sett & 15\\
54 & seks.sett & 14\\
55 & seks.sett & 15\\
\addlinespace
56 & seks.sett & 22\\
57 & seks.sett & 30\\
58 & seks.sett & 16\\
59 & seks.sett & 19\\
60 & seks.sett & 19\\
\bottomrule
\end{tabular}
\end{table}

Før du går videre er det greit at du gjør deg kjent med datasettet som vi har generert. Studer datasettet og svar på følgende spørsmål:

a) Hvor mange kolonner er det i tabellen over? <input class='solveme nospaces' size='1' data-answer='["3"]'/>
b) Hvor mange deltakere var med i studien? <input class='solveme nospaces' size='2' data-answer='["60"]'/>


## Oppsummere og visualisere dataen
Det er alltid lurt å starte med å visualisere dataen. 

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{13_fleregrupper_files/figure-latex/unnamed-chunk-3-1} 

}

\caption{**CAPTION THIS FIGURE!!**}(\#fig:unnamed-chunk-3)
\end{figure}
<span style="font-size: 22px; font-weight: bold; color: var(--pink);">Oppgave</span>

a) Hvem hadde mest fremgang  <select class='solveme' data-answer='["seks.sett"]'> <option></option> <option>tre.sett</option> <option>seks.sett</option></select>


## Dummykoding
Vi sa at vi ikke skulle introdusere dere for noe nytt. Vi løy. En ting er forskjellig når vi skal bruke en ANOVA til å sammenligne flere grupper, og det er hvordan vi skal kode variablene. Dere husker kanskje at vi ikke kunne legge tekst inn i de statistiske modellene våre? Derfor bruke vi **dummykoding**. Da vi brukte dummykoding sist, ga lagde vi en dummyvariabel der vi ga baseline-gruppen verdien 0, mens vi ga treatment-gruppen verdien 1. Dere tror kanskje at det bare er å fortsette denne prosedyren slik at vi gir den siste gruppen verdien 2? Feil. Dummykoding tillater ikke dette. Grunnen er at da at vi antar at det er et lineært forhold mellom disse gruppene, hvilket det kanskje ikke er. Dummykoding sier at vi må løse denne på følgende måte: **VI MÅ LAGE EN DUMMYVARIABEL TIL**. Det vil si at vi har to Dummyvariabler. I tabellen under ser du oppsettet vi skal bruke:

**Dummykoding**

Treningsgruppe | Dummy1 | Dummy2 
------------- | ------------- | ------------- 
Null sett | 0 | 0 |
Tre sett | 1 | 0 |
Seks sett  | 0| 1 |

<span style="font-size: 22px; font-weight: bold; color: var(--pink);">Oppgave</span>

a) Hva har vi kodet  null.sett gruppen med på Dummyvariabel 1?  <select class='solveme' data-answer='["0"]'> <option></option> <option>1</option> <option>0</option></select>
b) Hva har vi kodet  null.sett gruppen med på Dummyvariabel 2?  <select class='solveme' data-answer='["0"]'> <option></option> <option>1</option> <option>0</option></select>
c) Hva har vi kodet  tre.sett gruppen med på Dummyvariabel 2?  <select class='solveme' data-answer='["0"]'> <option></option> <option>1</option> <option>0</option></select>
d) Hva har vi kodet  seks.sett gruppen med på Dummyvariabel 2?  <select class='solveme' data-answer='["1"]'> <option></option> <option>0</option> <option>1</option></select>
e) Hva har vi kodet  seks.sett gruppen med på Dummyvariabel 1?  <select class='solveme' data-answer='["0"]'> <option></option> <option>1</option> <option>0</option></select>


La oss ta en titt hvordan dette ser ut i tabellen vår:



\begin{table}

\caption{(\#tab:unnamed-chunk-5)Dummykoding}
\centering
\begin{tabular}[t]{rlrrr}
\toprule
individ & gruppe & vl\_tykkelse & dummy1 & dummy2\\
\midrule
1 & null.sett & 3 & 0 & 0\\
2 & null.sett & 6 & 0 & 0\\
3 & null.sett & 1 & 0 & 0\\
4 & null.sett & 1 & 0 & 0\\
5 & null.sett & -2 & 0 & 0\\
\addlinespace
6 & null.sett & -5 & 0 & 0\\
7 & null.sett & 7 & 0 & 0\\
8 & null.sett & 14 & 0 & 0\\
9 & null.sett & 9 & 0 & 0\\
10 & null.sett & -2 & 0 & 0\\
\addlinespace
11 & null.sett & 4 & 0 & 0\\
12 & null.sett & 10 & 0 & 0\\
13 & null.sett & 5 & 0 & 0\\
14 & null.sett & 1 & 0 & 0\\
15 & null.sett & 5 & 0 & 0\\
\addlinespace
16 & null.sett & 6 & 0 & 0\\
17 & null.sett & 1 & 0 & 0\\
18 & null.sett & 4 & 0 & 0\\
19 & null.sett & 1 & 0 & 0\\
20 & null.sett & 3 & 0 & 0\\
\addlinespace
21 & tre.sett & 18 & 1 & 0\\
22 & tre.sett & 12 & 1 & 0\\
23 & tre.sett & 16 & 1 & 0\\
24 & tre.sett & 10 & 1 & 0\\
25 & tre.sett & 9 & 1 & 0\\
\addlinespace
26 & tre.sett & 11 & 1 & 0\\
27 & tre.sett & 16 & 1 & 0\\
28 & tre.sett & 14 & 1 & 0\\
29 & tre.sett & 8 & 1 & 0\\
30 & tre.sett & 12 & 1 & 0\\
\addlinespace
31 & tre.sett & 8 & 1 & 0\\
32 & tre.sett & 1 & 1 & 0\\
33 & tre.sett & 16 & 1 & 0\\
34 & tre.sett & 16 & 1 & 0\\
35 & tre.sett & 15 & 1 & 0\\
\addlinespace
36 & tre.sett & 9 & 1 & 0\\
37 & tre.sett & 14 & 1 & 0\\
38 & tre.sett & 6 & 1 & 0\\
39 & tre.sett & 10 & 1 & 0\\
40 & tre.sett & 11 & 1 & 0\\
\addlinespace
41 & seks.sett & 17 & 0 & 1\\
42 & seks.sett & 26 & 0 & 1\\
43 & seks.sett & 25 & 0 & 1\\
44 & seks.sett & 22 & 0 & 1\\
45 & seks.sett & 29 & 0 & 1\\
\addlinespace
46 & seks.sett & 17 & 0 & 1\\
47 & seks.sett & 26 & 0 & 1\\
48 & seks.sett & 6 & 0 & 1\\
49 & seks.sett & 18 & 0 & 1\\
50 & seks.sett & 15 & 0 & 1\\
\addlinespace
51 & seks.sett & 12 & 0 & 1\\
52 & seks.sett & 19 & 0 & 1\\
53 & seks.sett & 15 & 0 & 1\\
54 & seks.sett & 14 & 0 & 1\\
55 & seks.sett & 15 & 0 & 1\\
\addlinespace
56 & seks.sett & 22 & 0 & 1\\
57 & seks.sett & 30 & 0 & 1\\
58 & seks.sett & 16 & 0 & 1\\
59 & seks.sett & 19 & 0 & 1\\
60 & seks.sett & 19 & 0 & 1\\
\bottomrule
\end{tabular}
\end{table}


<span style="font-size: 22px; font-weight: bold; color: var(--pink);">Oppgave</span>
La samme oppsett selv, men husk at dere egentlig ikke trenger å gjøre dette fordi Jamovi gjør dette automatisk for dere, enten dere vil eller ikke. 


## ANOVA - er modellen vår bedre enn null-modellen?
Denne gangen starter vi må å teste om modellen vår, som består av de to Dummykodede prediktorvariablene Dummy1 og Dummy2, er en bedre enn null-modellen som sier at vi like greit kan bruke gjennomsnittet for de 60 individene til å predikere en person sin skår. Her har jeg gjort dette for dette i R:




```r
summary(aov(vl_tykkelse ~ gruppe, dat))
```

```
##             Df Sum Sq Mean Sq F value   Pr(>F)    
## gruppe       2   2403  1201.7    49.3 3.72e-13 ***
## Residuals   57   1389    24.4                     
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
```


<span style="font-size: 22px; font-weight: bold; color: var(--pink);">Oppgave</span>

a) Hva er f-verdien? <input class='solveme nospaces' size='4' data-answer='["49.3"]'/>
b) Er modellen vår signifikant?  <select class='solveme' data-answer='["Ja"]'> <option></option> <option>Nei</option> <option>Ja</option></select>
c) Hvor mye error er det i null-modellen? <input class='solveme nospaces' size='4' data-answer='["3792"]'/> (hint: her må du legge sammen to verdier)


<span style="font-size: 22px; font-weight: bold; color: var(--green);">Gratulerer</span>

Yes! Vår modell er bedre enn null-modellen fordi denne var signifikant. Med andre ord, hvis hadde dyttet en helt random prediktorvariabel i modellen vår, så er det veldig usannsynlig å få en så stor som F-verdi som det vi har fått. Kult, la oss feire! **VENT** **VENT** **VENT**. Vi vet jo ikke hvilke grupper som er forskjellige. Det må vi også finne ut.

## Hvilke grupper er forskjellige? (post-hoc testing)
For å finne ut av dette må vi kjøre en en post-hoc prosedyre. Outputen under burde se veldig kjent ut, hvis ikke bør dere virkelig gå tilbake til forelesninger eller lese boken


```r
summary(lm(vl_tykkelse ~ dummy1 + dummy2, dat))
```

```
## 
## Call:
## lm(formula = vl_tykkelse ~ dummy1 + dummy2, data = dat)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -13.100  -2.600  -0.350   3.025  10.900 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)    3.600      1.104   3.261  0.00188 ** 
## dummy11        8.000      1.561   5.124  3.7e-06 ***
## dummy21       15.500      1.561   9.928  4.9e-14 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 4.937 on 57 degrees of freedom
## Multiple R-squared:  0.6337,	Adjusted R-squared:  0.6208 
## F-statistic:  49.3 on 2 and 57 DF,  p-value: 3.719e-13
```
Det første dere ser er hvilken modell vi har kjørt. Denne sier at vi predikerer vl_tykkelse med de to Dummykodede prediktorvariablene våre. Testen sier at vår F-verdie er 49., og at vår $R^2$ er 0.6337. Med andre ord: vår modell forklarer hele 63 % av erroren i dataen. Det er mye! Videre sier den at den estimerer de ulike koeffisientene våre til å være 8 og 15.5. Og at intercepten er 3.600. Alle disse var signifikante ved t-tester. Men hva er egentlig disse verdiene for noe? 

<div class="info">
Tenk over hva 3.6, 8.0 og 15.5 er for noe før du leser videre. 
</div>

8.0 og 15.5 er stigningstallene i modellen, mens 3.6 er intercepten i modellen vår. La oss se hvordan disse koeffisientene virker i praksis. La oss si at vi ønsker å predikere en person som trente med tre sett sin skår.


$$
\text{fremgang muskeltykkelse } = b_0 + b_1(Dummy_1i) + b_1(Dummy_2i) + error_i
$$ 
Vi kan legge inn tallene i modellen vår. Siden personen trente med tre sett, og vi ga denne gruppen 1 på Dummyvariabel 1 og 0 på Dummyvariabel 0, blir vår prediksjon:

$$
\text{fremgang muskeltykkelse } = 3.6 + (8.0 * 1) + (15.5 * 0)  + error_i
$$ 
$$
\text{fremgang muskeltykkelse } = 3.6 + (8.0 * 1) + (15.5 * 0)  + error_i
$$ 
$$
\text{fremgang muskeltykkelse } = 3.6 + 8  + error_i
$$ 
$$
\text{fremgang muskeltykkelse } = 11.6  + error_i
$$ 

Vi tar et eksempel til. Hva hvis personen trente med seks sett? Denne dummykodet vi med 1 på Dymmyvariabel 1 og 0 på Dummyvariabel 1. Derfor blir vår prediksjon:

$$
\text{fremgang muskeltykkelse } = 3.6 + (8.0 * 0) + (15.5 * 1)  + error_i
$$ 
$$
\text{fremgang muskeltykkelse } = 3.6 + (15.5 * 1)  + error_i
$$ 
$$
\text{fremgang muskeltykkelse } = 3.6 + 15.5  + error_i
$$ 
$$
\text{fremgang muskeltykkelse } = 19.1 + error_i
$$ 

Dette er gjennomsnittet i gruppen som trente med seks sett. Til slutt: hva hvis du tilhørte gruppen som trente null sett? 

$$
\text{fremgang muskeltykkelse } = 3.6 + (8.0 * 0) + (15.5 * 0)  + error_i
$$ 

$$
\text{fremgang muskeltykkelse } = 3.6 + (8.0 * 0) + (15.5 * 0)  + error_i
$$ 


$$
\text{fremgang muskeltykkelse } = 3.6  + error_i
$$

Dette er gjennomsnittet i gruppen som trente med null sett. Som dere ser fra outputen over, så var denne også signifikant. I figurene under har jeg forsøkt å vise visuelt hva disse verdiene er for noe. Jeg skulle gjerne fått alt sammen i en figur, men det har jeg ikke klart å få til. Men hvis du ser i figur A, så ser du $b_0$, som er gjennomsnittet i null.sett-gruppen. Stigningstallet 8.0 reprenterer forskjellen mellom null.sett-gruppen og tre.sett-gruppen. Hvis du ser i figur B, så ser du $b_0$, som igjen er gjennomsnittet for null.sett-gruppen. Det er her linjen starter. Selve linjen representerer stigningstallet og er forskjellen mellom null.sett-gruppen og tre.sett-gruppen.
\begin{figure}

{\centering \includegraphics[width=1\linewidth]{13_fleregrupper_files/figure-latex/unnamed-chunk-9-1} 

}

\caption{**CAPTION THIS FIGURE!!**}(\#fig:unnamed-chunk-9)
\end{figure}
<div class="warning">
Når vi har dummykodet variablene våre sammenligner vi alt med en baseline-gruppe. Men vi skulle gjerne sammenlignet seks.sett gruppen med null.sett-gruppen, skulle vi ikke? Det får vi ikke gjort med dummykoding. Det er sikkert post-hoc prosedyrer som gjør dette mulig, men ingen av disse står i boken. MEN, det går an å bruke kontrastkoding. Andy Field har en fin video om dette.

</div>
