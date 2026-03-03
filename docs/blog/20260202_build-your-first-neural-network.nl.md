# Bouw Je Eerste Neurale Netwerk

*2 februari 2026*

## Een speelgoed dat je alles leert

De Wilesco D6 is een miniatuur stoommachine. Hij heeft een hoogglans gepolijste en vernikkelde messing ketel, een oscillerende cilinder, een kijkglas om het waterniveau te controleren, en een vliegwiel van 70mm dat met een tevreden gebrom draait. Hij past op je bureau.

![Wilesco D6 miniatuur stoommachine](images/wilesco_d6_miniature_steam_engine.png)

Hij is, praktisch gezien, nutteloos. Hij kan geen fabriek aandrijven of een locomotief laten rijden. Maar als je de Industriële Revolutie wilt begrijpen — hoe druk beweging wordt, hoe warmte arbeid wordt — steek je de brander aan, kijkt hoe de stoom zich opbouwt, en plotseling wordt het abstracte tastbaar. De principes die de wereld hebben veranderd zitten daar, in dat draaiende vliegwiel.

MNIST is de Wilesco D6 van het AI-tijdperk.

Het is een dataset van 70.000 handgeschreven cijfers — kleine afbeeldingen van 28×28 pixels van de getallen 0 tot en met 9. Het kan geen auto besturen of poëzie schrijven. Maar als je wilt begrijpen hoe machines leren, is MNIST waar je het vuur ontsteekt.

## Van biologie naar code

Je brein heeft ongeveer 86 miljard neuronen. Elk neuron ontvangt signalen via zijn dendrieten, verwerkt ze in het cellichaam, en stuurt een output via zijn axon. Dat is het — invoer, verwerking, uitvoer.

![Biologisch neuron versus kunstmatig neuron](images/neuron_comparison.png)

Een kunstmatig neuron doet hetzelfde, maar dan met wiskunde. Het neemt een reeks getallen als invoer, vermenigvuldigt elk met een gewicht (hoe belangrijk is deze invoer?), telt ze op, en beslist: vuren of niet vuren. Die beslissing — 0 of 1 — is de uitvoer.

## De uitdaging: handgeschreven cijfers lezen

Sommige cijfers zijn netjes, andere slordig — net een echt handschrift.

![MNIST cijfervoorbeelden](images/mnist_samples.png)

Elke pixel wordt een getal tussen 0 (wit) en 1 (zwart). Een afbeelding van 28×28 wordt een lijst van 784 getallen. Dat is onze invoer — de stoom die de cilinder binnenkomt.

![Pixelraster gekoppeld aan neuroninvoer](images/pixel_inputs.png)

De afbeelding hierboven is ter illustratie. Hier is het 18x18 en wordt het een lijst van 324 getallen

## De verbinding maken

Een enkel neuron kan niet veel — net zoals een enkele zuiger nog geen motor is. Maar lagen van neuronen wel. Ons netwerk heeft drie delen:

1. **Invoerlaag** — 784 neuronen, één per pixel
2. **Verborgen laag** — een kleine groep neuronen die patronen leert herkennen
3. **Uitvoerlaag** — 10 neuronen, één voor elk cijfer (0–9)

![Netwerkarchitectuur](images/network_architecture.png)

Wanneer we een afbeelding van een "8" invoeren, verwerkt het netwerk deze door alle lagen. Als alles goed gaat, vuurt het neuron met label "8" het sterkst. Druk wordt beweging.

## Tijd om de stoommachine te laten draaien
<div style="max-width: 350px; margin: 1em 0;">
  <iframe width="315" height="560" src="https://www.youtube.com/embed/p6tdFc0CNWg" frameborder="0" allowfullscreen></iframe>
</div>

## Tijd om het neurale netwerk te laten leren
Om de code te bekijken heb je alleen een browser nodig, om de code uit te voeren heb je een Google-account nodig. We gebruiken Google Colab. Google Colab biedt een online geïntegreerde ontwikkelomgeving (IDE) voor Python die geen installatie vereist en volledig in de cloud draait. Het biedt gratis toegang tot rekenkracht, inclusief GPU's en TPU's, waardoor het populair is bij onderzoekers en studenten die werken aan deep learning en data science projecten.

Bovendien kun je aan Google Colab, via geïntegreerde Gemini, specifiek om uitleg vragen waar je naar zit te kijken.

[Michael Nielsen MNIST](http://neuralnetworksanddeeplearning.com/)

[Google Colab Michael Nielsen MNIST](https://colab.research.google.com/drive/1GLwV2w9LsZp_3d1EwVugNGcSJXYerQ4k?usp=sharing)

![Google Colab Colab neuraal netwerk en deep learning](images/colab-neural-network-and-deep-learning.png)

Met een eenvoudig netwerk van 784 invoerneuronen, 30 verborgen neuronen en 10 uitvoerneuronen, getraind gedurende 30 rondes — bereik je ongeveer **95% nauwkeurigheid**. Niet slecht voor een paar dozijn regels code.


Hier dezelfde uitdaging vanuit een andere hoek

[Numpy Tutorial MNIST](https://numpy.org/numpy-tutorials/tutorial-deep-learning-on-mnist/)

[Google Colab Numpy Tutorial MNIST](https://colab.research.google.com/drive/1v5TdyysqPh_zZ0ZF6KYJV7TM9lxG6boF?usp=sharing)

## Wat is er zojuist gebeurd?

Het netwerk heeft, volledig zelfstandig, geleerd welke pixelpatronen bij welke cijfers horen. Niemand heeft het verteld dat een "7" een horizontale streep bovenaan heeft. Het heeft dat zelf ontdekt door naar duizenden voorbeelden te kijken en zijn gewichten aan te passen — telkens een klein beetje — totdat het beter werd.

Dat is het kernidee achter alle moderne AI. Al het andere zijn variaties op dit thema: meer lagen, meer data, slimmere trucs. Maar de basis? Gewogen invoer, opgeteld, met een beslissing aan het eind. Net als een neuron.

De Wilesco D6 zal geen fabriek aandrijven. Maar als je dat vliegwiel eenmaal hebt zien draaien, begrijp je stoom. En als je eenmaal een netwerk op MNIST hebt getraind, begrijp je iets over hoe machines leren zien. Soms leert de kleinste machine de grootste les.
