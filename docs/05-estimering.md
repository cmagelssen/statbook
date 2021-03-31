# Hvordan finne linjen i modellen?
Nå som vi har fått en forståelse for hvordan vi kan bygge statistiske modeller og teste disse er tid for å finne hvilken linje vi skal bruke. Frem til nå har dere fått $ b_0 $ og $ b_1 $ av meg. Sannheten er at linjen (les modellen) er plassert slik at den reduserer Sum of Squared Error mest mulig. Men hvordan skal vi plassere linjen slik at den reduserer error så mye? En tilnærming kan være å gjette seg fram til hva $b_0$ og $b_1$ skal være. Vi kan teste ut ulike verdier for b0 og b1, og evaluere hvor mye sum of Squared Error disse gir. Vi prøver dette:


\begin{figure}

{\centering \includegraphics[width=1\linewidth]{05-estimering_files/figure-latex/unnamed-chunk-1-1} 

}

\caption{**CAPTION THIS FIGURE!!**}(\#fig:unnamed-chunk-1)
\end{figure}
Vi kan holde på slik frem og frem og tilbake til vi finner vi faktisk den linjen som reduserer error mest mulig. Det er bare å teste nok verdier. **Minste kvadraters metode** garanterer oss at vi finne linjen som reduserer error mest mulig. Vi ser at linjen til venstre ga oss en error på. Jeg har laget en video som viser hvordan jeg kan gjøre dette.

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
 













