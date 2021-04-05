
# Koding av kategoriske prediktorvariabler
I tabellen på forrige kan du se at vi har en tabell med tre kolonner: en kolonne for hver variabel vi har i vårt datasett. 

* Variabelen **gruppe** er en kategorisk vaiabel som har to ulike verdier: "ett.sett" og "tre.sett". Dette er de to gruppene som vi skal teste om er forskjellige. I programmeringsverdenen kalles dette for et tekstobjekt, en string eller character. Uansett navn er problemet at vi ikke kan legge ord inn i en statistisk modell. Vi er nødt til å omkode den kategoriske variabelen med tallverdier. Det er flere måter å gjøre dette på, og måten man gjør det på har stor betydning for outfallet av den statistiske analysen.

<div class="danger">
De forskjellige måtene å kode de kategoriske prediktorvariablene på gir forskjellige resultater. En veldig vanlig måte å gjøre dette på er å bruke **dummykoding**. Dette kan fungere godt når du bygger en statistisk modell slik vi skal gjøre nå. Men dummykoding fungerer ikke hvis du har flere grupper du ønsker å sammenligne, og du ikke ønsker å sammenligne disse gruppene mot en baseline gruppe. Da vil **kontrastkoding** være bedre egnet. 

SPSS, R, Jamovi bruker dummykoding som standard, så når du legger disse kategoriske prediktorvariabler inn i slike modeller. Det er viktig å vite!

</div>




## Dummykoding
En vanlig metode kalles **dummykoding** eller **treatment-koding**. Den går ut på å lage en eller flere variabler med 0 og 1 som de to mulige verdiene. Antall variabler vi trenger avhenger av antall grupper vi vil sammenligne. Siden vårt datasett kun inneholder to grupper, så trenger vi kun en variabel. Vi kan den ene gruppen og den andre 1. Hovedregelen er at vi gir 0 til baselinegruppe og 1 til den eksperimentelle gruppen. Vi gir derfor 0 til 1.sett-gruppen og 1 til 3.sett-gruppen. Gjør dette før du går videre.



I R og Jamovi kan du gjøre det med følgende if/else statement. I R kan du bruke følgende kode:


```r
#lager et nytt objekt som heter dummykodet.dat
dummykodet.dat <- dat %>%
  # her lager jeg en ny kolonne som heter dummykoder. If gruppe == 'ett.sett', gi verdien 0, else gi de 1.
  mutate(dummykodet = if_else(gruppe == "ett.sett", 0, 1))
```


\begin{table}

\caption{(\#tab:unnamed-chunk-4)Dummykodet datasett}
\centering
\begin{tabular}[t]{rlrr}
\toprule
individ & gruppe & rm & dummykodet\\
\midrule
1 & tre.sett & 40.46704 & 1\\
2 & tre.sett & 49.07223 & 1\\
3 & tre.sett & 47.94131 & 1\\
4 & tre.sett & 44.51389 & 1\\
5 & tre.sett & 52.28750 & 1\\
\addlinespace
6 & tre.sett & 40.01750 & 1\\
7 & tre.sett & 49.48425 & 1\\
8 & tre.sett & 29.21048 & 1\\
9 & tre.sett & 40.59293 & 1\\
10 & tre.sett & 37.58676 & 1\\
\addlinespace
11 & tre.sett & 35.42651 & 1\\
12 & tre.sett & 42.49354 & 1\\
13 & ett.sett & 17.70576 & 0\\
14 & ett.sett & 17.07181 & 0\\
15 & ett.sett & 18.26811 & 0\\
\addlinespace
16 & ett.sett & 25.42594 & 0\\
17 & ett.sett & 32.70313 & 0\\
18 & ett.sett & 19.10226 & 0\\
19 & ett.sett & 22.23827 & 0\\
20 & ett.sett & 22.27148 & 0\\
\addlinespace
21 & ett.sett & 26.17889 & 0\\
22 & ett.sett & 20.34857 & 0\\
23 & ett.sett & 23.52773 & 0\\
24 & ett.sett & 17.95966 & 0\\
\bottomrule
\end{tabular}
\end{table}

I jamovi ville jeg sett følgende video: 

<iframe width="797" height="457" src="https://www.youtube.com/embed/iITxK27LfZk" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

