# Hvordan finne linjen i modellen?
Nå som vi er kjent med hvordan vi kan bygge og teste statistiske modeller, er det på tide å vise hvordan vi finner regresjonslinjen som vi skal bruke. Mer presist, hvilke verdier skal vi ha for *b*<sub>0</sub> og *b*<sub>1</sub> som beskriver denne linjen? Hittil har dere fått disse verdiene av meg, men det vi skal lære nå er hvordan vi kan regne ut disse verdiene for hånd. En viktig sannhet om denne linjen er at regresjonslinjen (les modellen) er plassert slik at den reduserer Sum of Squared Error mest mulig. Med andre ord, verdiene på *b*<sub>0</sub> og *b*<sub>1</sub> (som beskriver denne linjen) er slik at det er umulig å redusere error mer. Spørsmålet er hvordan vi finner verdiene på *b*<sub>0</sub> og *b*<sub>1</sub> som beskriver denne linjen. En tilnærming kan være å gjette seg fram til hva $b_0$ og $b_1$ skal være. Vi kan teste ut ulike verdier for b0 og b1, og evaluere hvor mye sum of Squared Error disse gir. I figuren under har jeg prøvd tre ulike modeller, og regner ut hvor mye sum of squared error disse gir.

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{05-estimering_files/figure-latex/unnamed-chunk-1-1} 

}

\caption{**CAPTION THIS FIGURE!!**}(\#fig:unnamed-chunk-1)
\end{figure}
**Oppgave**
a) Hvilken av modellene over gir mest sum of squared error? (SS<sub>Model</sub>)

<select class='solveme' data-answer='["b0=30 b1=7"]'> <option></option> <option>b0=30 b1=7</option> <option>b0=25 b1=28</option> <option>b0=10 b1=30</option></select>

Vi kan holde på slik med slik prøving-og-feiling til vi faktisk finner linjen som reduserer error mest. Det er bare å teste nok verdier. **Minste kvadraters metode** garanterer oss å alltid gi oss er svar. Jeg har laget en video til dere som viser vi kan prøve-og-feile til vi kommer frem til en løsning (se denne):

<iframe width="798" height="457" src="https://www.youtube.com/embed/kWVtce7YDsg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Det er en mer effektiv måte å løse dette problemet på. For å finne **b<sub>1</sub>** kan vi bruke følgende formel: 

$$ b_1 = \frac{SCP}{SS_x} $$
Her var det et nytt begrep, **SCP**. SCP står for sum of cross-product deviations. Det brukes til å finne relasjonen mellom to variabler, og er grunnlaget for en rekke utregninger i statistikken, så det kan være lurt å lære seg. SCP finner ut av om en person som er over eller under gjennomsnittet på en variabel, også er over eller under gjennomsnittet på den andre variabelen. 

$$ b_1 = \frac{SCP = \sum_{n=1}^N (x_i - \bar{x})(y_i - \bar{y})}{SS_x} $$
$\bar{x}$ er gjennomsnittet på x-variabelen (gruppe), mens $\bar{y}$ er gjennomsnittet for y-variabelen (1RM). I tabellen under ser du hvordan vi regner dette. Kolonnen CrossProduct er $(x_i - \bar{x})(y_i - \bar{y})$. 


\begin{table}

\caption{(\#tab:unnamed-chunk-2)Utregning av Sum of Cross Product (SCP)}
\centering
\begin{tabular}[t]{rrrrrrrr}
\toprule
individ & gruppe & gj.snitt.x & error.x & rm & gj.snitt.y & error.y & CrossProduct\\
\midrule
1 & 1 & 0.5 & 0.5 & 40.46704 & 32.16231 & 8.3047301 & 4.1523651\\
2 & 1 & 0.5 & 0.5 & 49.07223 & 32.16231 & 16.9099106 & 8.4549553\\
3 & 1 & 0.5 & 0.5 & 47.94131 & 32.16231 & 15.7789994 & 7.8894997\\
4 & 1 & 0.5 & 0.5 & 44.51389 & 32.16231 & 12.3515740 & 6.1757870\\
5 & 1 & 0.5 & 0.5 & 52.28750 & 32.16231 & 20.1251864 & 10.0625932\\
\addlinespace
6 & 1 & 0.5 & 0.5 & 40.01750 & 32.16231 & 7.8551872 & 3.9275936\\
7 & 1 & 0.5 & 0.5 & 49.48425 & 32.16231 & 17.3219362 & 8.6609681\\
8 & 1 & 0.5 & 0.5 & 29.21048 & 32.16231 & -2.9518368 & -1.4759184\\
9 & 1 & 0.5 & 0.5 & 40.59293 & 32.16231 & 8.4306117 & 4.2153059\\
10 & 1 & 0.5 & 0.5 & 37.58676 & 32.16231 & 5.4244472 & 2.7122236\\
\addlinespace
11 & 1 & 0.5 & 0.5 & 35.42651 & 32.16231 & 3.2641906 & 1.6320953\\
12 & 1 & 0.5 & 0.5 & 42.49354 & 32.16231 & 10.3312265 & 5.1656133\\
13 & 0 & 0.5 & -0.5 & 17.70576 & 32.16231 & -14.4565510 & 7.2282755\\
14 & 0 & 0.5 & -0.5 & 17.07181 & 32.16231 & -15.0905068 & 7.5452534\\
15 & 0 & 0.5 & -0.5 & 18.26811 & 32.16231 & -13.8942055 & 6.9471027\\
\addlinespace
16 & 0 & 0.5 & -0.5 & 25.42594 & 32.16231 & -6.7363771 & 3.3681886\\
17 & 0 & 0.5 & -0.5 & 32.70313 & 32.16231 & 0.5408147 & -0.2704074\\
18 & 0 & 0.5 & -0.5 & 19.10226 & 32.16231 & -13.0600552 & 6.5300276\\
19 & 0 & 0.5 & -0.5 & 22.23827 & 32.16231 & -9.9240435 & 4.9620217\\
20 & 0 & 0.5 & -0.5 & 22.27148 & 32.16231 & -9.8908322 & 4.9454161\\
\addlinespace
21 & 0 & 0.5 & -0.5 & 26.17889 & 32.16231 & -5.9834246 & 2.9917123\\
22 & 0 & 0.5 & -0.5 & 20.34857 & 32.16231 & -11.8137453 & 5.9068726\\
23 & 0 & 0.5 & -0.5 & 23.52773 & 32.16231 & -8.6345853 & 4.3172926\\
24 & 0 & 0.5 & -0.5 & 17.95966 & 32.16231 & -14.2026514 & 7.1013257\\
\bottomrule
\end{tabular}
\end{table}


$$ b_1 = \frac{SCP = 20.52436}{SSx} $$
Nå som vi har regnet SCP er det bare å regne SS<sub>x</sub> (sum of squared error for prediktorvariabelen) er fordi man ønsker å ta høyde for hvor mye prediktorvariabelen avviker fra mean. Jeg har dessverre ikke noen supergod forklaring, og jeg synes heller ikke Field forklarer dette godt. Så jeg bare vet at jeg må gjøre det.

$$ b_1 = \frac{SCP = 20.52436}{6} $$
$$ b_1 = 20.52436 $$



Nå gjenstår det bare å finne **b_0**. Denne er enkel å finne når vi først har funnet **b<sub>0</sub>**. Husk at modellen vår er en ligning, så ved enkelt finne **b<sub>0</sub>** ved omorganisere ligningen: trekker vi fra $b_1X_i$ på hver side av likhetstegnet får vi **b<sub>0</sub>** alene:

$$
Y_i = (b_0 + b_1X_i)
$$

$$
Y_i - b_1X_i = (b_0)
$$

Men må ligningen med verdier. Og da bruker man gjennomsnittet for Y variabelen og gjennomsnittet for X variabelen.

$$
32.16231	 - (20.52436*0.5) = (21.90013)
$$






