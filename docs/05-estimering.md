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

$$ SCP = \frac{\sum_{n=1}^N (x_i - \bar{x})(y_i - \bar{y})}{SS_x} $$
$\bar{x}$ er gjennomsnittet på x-variabelen (gruppe), mens $\bar{y}$ er gjennomsnittet for y-variabelen (1RM).






Vi kan også en generell formell for å løse dette problemet på. Det første vi må gjøre er å regne noe som heter **sum of cross-product deviations (SCP)**. Formelen for dette er others are negative, so they’ll cancel out. Instead we
square the deviances before adding them up. We want to do something similar here, but at the
same time gain some insight into whether the deviations for one variable are matched by similar
deviations in the other. The answer is to multiply the deviation for one variable by the corresponding
deviation for the other. If both deviations are positive or negative then this will give us
a positive value (indicative of the deviations being in the same direction), but if one deviation is
positive and the other negative then the resulting product will be negative (indicative of the
deviations being opposite in direction). The deviations of one variable multiplied by the corresponding
deviations of a second variable are known as the cross-product deviations. If we want
the total of these cross-product deviations we can add them up, which gives us the sum of crossproduct
 $\sum_{n=1}^N (x - \bar{x})(y- \bar{y})$ Hva denne gjør er 
 
 
 Det neste er å faktor inn hvor mye 
 
 
 
 of deviation from the mean, if it varies a lot, we would expect the outcome
to show a lot of deviation from its mean too. Conversely, if the predictor deviates only a little from
its mean (it has little variance) then the outcome should likewise show only small deviations from
its mean. Therefore, what we expect to happen with the outcome depends on how much the predictor
deviates from its mean. If the predictor deviates a little from the mean, then the SCP should be
smaller than if the predictor deviates a lot from the mean. Therefore, we need to factor in how much
the predictor deviates from its mean: we want the regression coefficient to reflect the total relationship
between the predictor and outcome relative to how much the predictor deviates from its mean.
For a single variable, how do we quantify the total degree to which it deviates from its mean?’
 













