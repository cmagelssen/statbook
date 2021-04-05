

# Bygge statistisk modeller

## Introduksjon til modellbygging

Når vi har samlet inn dataen vi trenger blir vår neste oppgave å bygge statistiske modeller som representerer denne dataen. Fordelen med disse modellene er at den gjør dataen mer forståelig. For eksempel er det mye enklere å si hva gjennomsnittet var i en treningsgruppe enn å ramse opp alle de enkelte observasjonene i datasettet. Forståelig nok ønsker vi å bygge modeller som representerer dataen godt, og vi vil bruke helt eksplisitte kriterier for å vurdere disse modellene 

Modellene vi skal bygge vil alltid være en variant av ligningen under. Vi bare bytter ut det i parantesen med en spesifikk modell som vi ønsker å bygge.

$$
data_i = (modell) + error_i
$$


<div class="warning">
Mange frykter ligninger. Vi også. Men det er ikke så ille når man blir vant til det. Vi kommer til å bruke den samme ligningen til alle være statistiske tester. Dessuten hjelper ligninger oss til å huske informasjon bedre.

</div>

La oss bryte denne ligningen over:

* **Data** er den faktiske observasjonen et individ har på den avhengige variablen, som i vårt tilfelle % fremgang i 1RM underkroppsøvelser. 

* **Modell** er egentlig bare en representasjon av denne dataen-

* **Error** er hvor mye modellen bommer fra den faktisk observasjonen (dvs. data).

<div class="info">
Legg merke til den lille <sub>i</sub>-en som står bak data og error i ligningen. <sub>i</sub>-en betyr individ og betyr bare at vi kan bruke en modell til å si noe om hva et individ hadde på den avhengige variabelen. Vi kan erstatte <sub>i</sub>-en med <sub>3</sub> eller <sub>8</sub>. Da betyr det bare at vi kan bruke en modell til å si noe om individ 3 og 8. Vi bruker <sub>i</sub> for å holde det generelt
</div>


<span style="font-size: 22px; font-weight: bold; color: var(--purple);">Ligningen i praksis</span>

Ligningen over blir mer oppklarende om vi bruker et eksempel:

Forestill deg at du er lege, og at du får inn en pasient som sier hun har feber. Du vet at den normale kroppstemperaturen i populasjonen er ~37, så det er naturlig å tenke at du kan bruke 37 som modell.

$$
kroppstemperatur_i = 37 + error_i
$$
Det neste du gjør er å ta en febermåling av pasienten, og du måler kroppstemperaturen til å være 40.

$$
40 = 37 + error
$$
Modellen din bommer med 3 grader, fordi 40-37 = 3. Vi kaller slike feil for error.

$$
40 = 37 + 3
$$
Formelt sett regner vi error for en hvilken som helst modell ved å få error i ligningen alene, ved å reorganisere ligningen. 

$$
data_i = modell + error_i
$$
$$
error_i = data_i - modell
$$
$$
3 = 40 - 37
$$

<span style="font-size: 22px; font-weight: bold; color: var(--green);">Du har bygget din første modell - Gratulerer!</span>

Du har bygget din første modell. Modellen var riktignok enkel, men du vil snart se at de andre modellene vi skal bygge er veldig like. Den største forskjellen er at modellen ikke blir bygget for å passe perfekt til ett enkelt individ, men til et helt datasett. **Dette er viktig!** I en studie hvor du har mange deltakere med, ønsker vi at modellen skal være en god representasjon av alle disse individene. Med andre ord bør erroren i modell være så liten som mulig

<span style="font-size: 22px; font-weight: bold; color: var(--purple);">Modeller</span>
Det er en mer korrekt og presis måte å skrive ligningen under på, og som du ofte ser i artikler og statistikkbøker:


<div class="info">
Vi kommer til å benytte denne måten å skrive på fordi det er den dere ser i statistikkbøker og artikler. Tolkningen er akkurat lik.
</div>

$$
data_i = (modell) + error_i
$$
$$
Y_i = (b_0) + error_i
$$
Her er $Y_i$ den avhengige variabelen for et individ, *i*. Hvis det kun står $b_0$, så betyr det at vi kun estimerer ett enkelt parameter. I slike tilfeller bruker vi kun ett enkelt parameter til å si noe om hva det enkelte individ hadde i observasjon på den avhengig variabelen, og da predikerer modellen likt for alle individene. 

Vi kan også bruke en mer kompleks modell, som i ligningen under:

$$
Y_i = (b_0 + b_1X_i) + error
$$
**X_i** er dette individets faktiske måling på variabel, X, som vi ofte kaller for prediktorvariabel. Prediktorvariabelen har også $b_1$ hektet på seg. Denne forteller oss forholdet mellom prediktorvariabelen (X<sub>i</sub>) og den avhengig variabelen (Yi). b_0 blir her vår prediksjon når X<sub>i</sub> er **null** og **0**. 

<div class="info">
,,,
</div>


## Visualisering av ulike statistiske modeller

Vi skal nå visualisere ulike modeller for å få en bedre forståelse av hva hva ulike modeller sier oss. I figurene under ser tre ulike modeller med uinteressante X og Y variabler. Alle har samme b<sub>0</sub>, mens de har forskjellig b<sub>1</sub>. Husk at b<sub>1</sub> forteller om relasjonen mellom X og Y.

<div class="warning">
Måten du skal tolke på b<sub>1</sub> på: For **hver enhets økning i X**, dvs. gå fra 1 til 2, 3 til 4, eller 6 til 7, **forventer vi at Y øker med verdien på b<sub>1</sub>**. På norsk kalles b1 for **stigningstallet**. Hvis b<sub>1</sub> er 0, er det ingen relasjon mellom X og Y i vårt datasett.
</div>

* I **modell A** ser du at når X øker, øker Y med 0.4 **for hver enhets økning i X**. 

* I **modell B** er det ingen relasjon mellom X og Y, så for en enhets økning i X, vil vi forvente at Y forblir den samme. 

* I **modell C** er det en negativ relasjon mellom X og Y. Denne modellen sier at for en enhets økning i X, vil vi forvente at Y går ned med 0.4 (siden den er negativ).


\begin{figure}

{\centering \includegraphics[width=1\linewidth]{04-modellbygging_files/figure-latex/unnamed-chunk-2-1} 

}

\caption{Modeller med forskjellig b1}(\#fig:unnamed-chunk-2)
\end{figure}


**Oppgave**

**a.** La oss si at vi hatt med et målt et individ sin **X** til å være 8. Hvis du bruker modell A, hva vil du forvente at denne personen har på *Y*?

<input class='solveme nospaces' size='3' data-answer='["9.2"]'/>.

I figuren ser du tre modeller som har forskjellige b<sub>0</sub>, men samme b<sub>1</sub>. b<sub>0</sub> er verdien på Y når X er 0. 

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{04-modellbygging_files/figure-latex/unnamed-chunk-3-1} 

}

\caption{Modeller med forskjellig b0}(\#fig:unnamed-chunk-3)
\end{figure}
**Oppgave**
**b.** La oss si at vi hatt med et målt et individ sin **X** og **Y** (du kan bytte ut X og Y med hvilken som helst variabel (f.eks. høyde, vekt), hvis du vil). Individet sitt mål på X er 3. Hvis du bruker modell B, hva vil du forvente at denne personen har på *Y*?

<input class='solveme nospaces' size='3' data-answer='["4.2"]'/>.

I figuren under ser du vært datasett. På Y-aksen har vi plottet % fremgang i RM for deltakerne våre. På X-aksen har vi plottet de to gruppene våre som vi har dummykodet med 0 og 1.


\begin{figure}

{\centering \includegraphics[width=1\linewidth]{04-modellbygging_files/figure-latex/unnamed-chunk-4-1} 

}

\caption{Vår data}(\#fig:unnamed-chunk-4)
\end{figure}

**c.** Med utgangspunkt i figuren, hvordan vil du omtrent beskrive en modell som kan passe denne dataen godt? 

<select class='solveme' data-answer='["Modellen vår ser ut til å ha en b0 på ~20 og en b1 på ~ 20"]'> <option></option> <option>Det er ingen relasjon mellom vår dummykodede variabel og % fremgang 1RM</option> <option>Modellen vår ser ut til å ha en b0 på ~20 og en b1 på ~ 20</option> <option>Modellen vår ser ut til å ha en b0 på ~10 og en b1 på ~ 40</option> <option>Det er en negativ relasjon mellom vår dummykodede variabel og % fremgang 1RM</option></select>. 


## Modellbygging med 'Null-Hypothesis Significance Testing (NHST)'
Nå som du har en fått en innføring i hvordan du kan bygge modeller er det på tide at vi begynner å spesifisere hvilke modeller vi skal bygge. Som du sikkert er kjent med jobber forskere innenfor et paradigme som kalles for **Null-Hypothesis Significance Testing (NHST)**. Dette går ut på at forskeren fremstiller to hypoteser:

1. **H0**: En null-hypotese som sier at det ikke er noen effekt (f.eks. ingen forskjeller mellom grupper, ingen sammenheng mellom variablene)
2. **H1**: En alternativ/eksperimentell hypotese som sier at det er en effekt (f.eks. det er en forskjell mellom gruppene)

**For å teste disse hypotesene må forskeren bygge to modeller:** 
* en modell for null-hypotesen (vi kaller denne for **null-modellen**) 
* en alternativ-modell som sier det at det er en relasjon eller forskjeller mellom grupper.

Vi regner ut hvor mye error det er i hver av disse modellene for å se hvilke av disse modellene vi gjør det lurt å benytte. Husk at målet er å benytte modeller som er gode og som har lite error. Hvis null-modellen er god nok, så er det ikke noe poeng å bruke den alternative modellen. Men hvis den alternative modellen er mye bedre enn null-modellen, da bør benytte denne. 

Statistikken hjelper oss med å ta en beslutning om hvilke av disse modellene vi skal bruke. Forskeren gjennomfører deretter en **statistisk test** som representerer den alternative hypotesen. Utfallet av testen er en **verdi**, for eksempel en *z-verdi*, *t-verdi* eller *f-verdi*, som vi kan bruke til å regne ut sannsynligheten (*p*-verdi)for, gitt at null-hypotesen er sann. Forskjellige tester opererer med forskjellige navn på verdiene sine (sorry, men det er bare slik det er). 


### Null-modellen (null-hypotesen)
I vår studie ønsker vi å teste om det er forskjeller mellom de to gruppene som har blitt disponert for ulikt treningsopplegg (3 versus 1 sett). Husk at vi har laget en variabel hvor vi har kodet disse som 0 og 1; 0 hvis de trente med ett sett og 1 hvis de trente tre sett.  Null-hypotesen er at det ikke er noen forskjeller mellom gruppene. I så fall er gjennomsnittet 1 RM fremgang av alle deltakerne kanskje en god modell. Dette er modellen som representerer null-hypotesen. Med andre ord vår null-modell

$$
Y_i = (b_0) + error
$$
$$
fremgang.1RM = (mean) + error
$$ 
Det er ofte enklere å se denne modellen i tabellform, slik som dere ser under.




<table>
<caption>(\#tab:unnamed-chunk-6)Null-modellen (mean)</caption>
 <thead>
  <tr>
   <th style="text-align:right;"> individ </th>
   <th style="text-align:left;"> gruppe </th>
   <th style="text-align:right;"> rm </th>
   <th style="text-align:right;"> modell.mean </th>
   <th style="text-align:right;"> error </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> 1 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 40.467 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 8.305 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 2 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 49.072 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 16.910 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 3 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 47.941 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 15.779 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 4 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 44.514 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 12.352 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 5 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 52.288 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 20.125 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 6 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 40.018 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 7.855 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 7 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 49.484 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 17.322 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 8 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 29.210 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -2.952 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 9 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 40.593 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 8.431 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 10 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 37.587 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 5.424 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 11 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 35.427 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 3.264 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 12 </td>
   <td style="text-align:left;"> tre.sett </td>
   <td style="text-align:right;"> 42.494 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 10.331 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 13 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 17.706 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -14.457 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 14 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 17.072 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -15.091 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 15 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 18.268 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -13.894 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 16 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 25.426 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -6.736 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 17 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 32.703 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> 0.541 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 18 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 19.102 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -13.060 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 19 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 22.238 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -9.924 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 20 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 22.271 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -9.891 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 21 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 26.179 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -5.983 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 22 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 20.349 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -11.814 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 23 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 23.528 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -8.635 </td>
  </tr>
  <tr>
   <td style="text-align:right;"> 24 </td>
   <td style="text-align:left;"> ett.sett </td>
   <td style="text-align:right;"> 17.960 </td>
   <td style="text-align:right;"> 32.162 </td>
   <td style="text-align:right;"> -14.203 </td>
  </tr>
</tbody>
</table>


**Oppgave**

La oss prøve hvordan denne modellen virker. For individ 1 målte vi en fremgang i 1RM underkropp på **40.467**, men modellen vår sa **32.162**. Så modellen bommet med 8.305, dvs. en error på **8.305**.
$$
fremgang.1RM = (mean) + error
$$
$$
40.467 = 32.162 + 8.305
$$ 

a. Prøv modellen du også: For individ nr. 8, sier modellen at individet hadde en skår på <input class='solveme nospaces' size='6' data-answer='["32.162"]'/>, men denne personen hadde faktisk en skår på <input class='solveme nospaces' size='6' data-answer='["29.210"]'/>. Modellen bommet derfor med <input class='solveme nospaces' size='6' data-answer='["-2.952"]'/>. 

>>Vi kan fortsette slik for alle deltakerne vi har hatt med i studien. Husk at vi ikke er interessert i hvir mye bommer for hvert enkelt individ, men for alle indivene. 

b. Hva får du hvis du summerer  all erroren for alle indidene?  <select class='solveme' data-answer='["null","0"]'> <option></option> <option>null</option> <option>0</option> <option>3</option> <option>-3</option></select>. 

>>tenk over hvorfor du får dette svaret før du leser videre. 

>>Som du så i forrige oppgave blir det feil å summere alle erroren, vi kan løse dette effektivt ved ved å regne **Sum of Squared Error**. Det vi gjør er å gange error med seg selv (error^2) før vi summerer alt dette sammen.

c. Hvis vi regner ut  **Sum of Squared Error** for null-modellen fpr vi: <input class='solveme nospaces' size='8' data-answer='["3243.784"]'/>

>>Dette tallet er viktig! Dette er null-hypotesen vår! Hvis det ikke er noen forskjell mellom de to treningsgruppene våre er det like greit å bruke denne null-modellen. Men hvis vi finner ut at modellen vår blir bedre (dvs. reduserer Sum of Squared Error) ved å legge til en prediktorvariabel som består er av gruppevariabelen vår, da bør vi gjøre dette. 




Før du går videre er det greit å visualisere hvordan null-hypotesen ser ut rent visuelt. Den prikkete streken i figuren under representerer modellen vår som er mean. Som du ser, så gjør den ingen justeringer for de ulike individene. Erroren er avstanden fra den linjen og opp til hvert datapunkt. Så hvis vi får til å bygge en bedre modell så vil denne avstanden reduseres for alle individene.

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{04-modellbygging_files/figure-latex/unnamed-chunk-8-1} 

}

\caption{Modeller med forskjellig b1}(\#fig:unnamed-chunk-8)
\end{figure}


### Alternativ modell (alternativ hypotese)
I forrige avsnitt sa vi at **null-hypotesen (H0)** reresenterer en en modell som gir samme prediksjon for alle deltakerne som var med i studien uavhengig av hvilken treningsgruppe de tilhører. Vi kalte denne for null-modellen. Vi regnet oss også frem til at denne modellen ga oss en Som of Squared error på 3243.784.

Spørsmålet vi skal stille i dette nå er om vi kan redusere error fra denne ved å benytte en mer kompleks modell som benytter (vår dummykodede kategoriske variabel) som prediktorvariabel:
$$
Y_i = (b_0 + b_1X_i) + error
$$ 
Prediktorvariabelen b1 er en gruppevariabelen vår som vi dummykodet med tallene 0 og 1. 

$$
Fremgang.1RM_i = b_0 + b_1(Gruppe) + error_i
$$ 
For å holde dette på et overordnet nivå, så vil jeg gi dere de estimerte verdiene for b0 og b1. Målet er å vise dere hvordan denne modellen fungerer. Senere skal gå gjennom hvordan vi regner ut disse verdiene. Trykk her hvis du ønsker å finne ut hvoran du regner ut disse verdiene med en gang.

$$
Fremgang.1RM_i = b_0(21.90) + b_1(20.52*Gruppe) + error_i
$$ 
Modellen sier at vår b0 er 21.90. Dette er den forventede verdien på Y (Fremgang.1RM) når prediktorvariabelen er 0. Modellen sier også at b1 er 20.52.  Med andre ord den forventede økning i Y for en enhets økning i X (også kalt stigningstallet). Husk at vi lagde en gruppe-variabel der vi kodet de to gruppene våre med 0 og 1. Så hvis et individ tilhørte gruppe 0, blir vår prediksjon:

$$
Fremgang.1RM_i = 21.90 + b_1(20.52*0) + error_i
$$ 
Fordi 0*20.52 = 0, blir stående igjen med b0. Vår prediksjon av et individ som tilhører gruppe 0 blir 

$$
Fremgang.1RM_i = 21.90 + 0 + error_i
$$ 
$$
Fremgang.1RM_i = 21.90 + error_i
$$ 
Hvis individet derimot tilhører 1 predikerer modellen at individet sin skår blir 42.48.

$$
Fremgang.1RM_i = 21.90 + b1(20.52*1) + error_i
$$ 
$$
Fremgang.1RM_i = 42.48 + error_i
$$ 
Visualisert fremstilt blir modellen vår seendes slik ut:

\begin{figure}

{\centering \includegraphics[width=1\linewidth]{04-modellbygging_files/figure-latex/unnamed-chunk-9-1} 

}

\caption{Modeller med forskjellig b1}(\#fig:unnamed-chunk-9)
\end{figure}


**Oppgave**
Tabellen under viser 6 individer som tilhørte treningsgruppe. Du ser deres faktiske fremgang i 1RM kolonnen. La oss bruke det vi har lært til å predikere disse personene sin fremgang. Vi bruker samme modell som over

$$
Fremgang.1RM_i = b_0(21.90) + b_1(20.52*Gruppe) + error_i
$$ 
a. Hva predikerer modellen at individ nummer 3 hadde i skår? (to desimaler)

<input class='solveme nospaces' size='5' data-answer='["42.42"]'/>

b, Hva hadde individ nr i skår?

<input class='solveme nospaces' size='6' data-answer='["47.941"]'/>

c. hvor mye error blir det? 

<input class='solveme nospaces' size='5' data-answer='["5.521"]'/>

d. i Squared Error blir denne erroren?

<input class='solveme nospaces' size='8' data-answer='["30.48144"]'/>

e. nå som du har jobbet med denne modellen, så lurer jeg på om det er noe kjent med disse verdiene i modellen. Gå tilbake til [link] hvis du trenger et hint.

f. bo er <input class='solveme nospaces' size='14' data-answer='["gjennomsnittet"]'/> (norskt ord) for gruppen som er kodet med 0. 

g. b1 er <input class='solveme nospaces' size='11' data-answer='["forskjellen"]'/> (norsk ord) mellom gruppen som er kodet med 0 og gruppen som er kodet med 1. 

h. b0 + b1 er <input class='solveme nospaces' size='14' data-answer='["gjennomsnittet"]'/> (norsk ord) for gruppen som er kodet med 1.




\begin{table}

\caption{(\#tab:unnamed-chunk-11)Dummy koding}
\centering
\begin{tabular}[t]{r|l|r|r}
\hline
individ & gruppe & rm & dummykodet\\
\hline
1 & tre.sett & 40.467 & 1\\
\hline
2 & tre.sett & 49.072 & 1\\
\hline
3 & tre.sett & 47.941 & 1\\
\hline
4 & tre.sett & 44.514 & 1\\
\hline
5 & tre.sett & 52.288 & 1\\
\hline
6 & tre.sett & 40.018 & 1\\
\hline
\end{tabular}
\end{table}

I forrige oppgave regnet du ut error for ett enkelt individ. Men vi er interessert i den totale erroren for modellen. Formelen for denne er: 

total error in den alternative modellen:


SS_R = $\sum_{n=1}^N (observert_i - modell_i)^2$ 

Med andre ord er det kvadraten av den faktiske observasjonen - hva modellen sa. Bruk formelen til å regne ut dette. (to desimaler

<input class='solveme nospaces' size='7' data-answer='["2527.50"]'/>

