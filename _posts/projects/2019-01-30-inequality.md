---
layout: page 
title:  "Mehr Geld, mehr Gerechtigkeit?" 
subheadline: Korrelation aus der Ungleichheit und der wirtschaftlichen Entwicklung
teaser: "Korrelation aus der Ungleichheit und der wirtschaftlichen Entwicklung"
header: no
show_meta: false
categories:
    - projects
image:
    title: inequality/key_visual.jpeg
    caption: Zusammenstellung der Erkenntnisse als Poster für die iExpo
author: Daniel Kogan, Moritz Mundhenke, Patrick Lowinski-Loh, Stefan Sousa & Tim Schäfer, TODO mit oder ohne?
---

> *Die Wirtschaft wächst und wächst, aber der Spalt zwischen Arm und Reich wird nicht kleiner. Was läuft da schief?* [^fn1]


Mit dieser inhaltvollen Schlagzeile macht ein Artikel aus [DIE ZEIT](https://www.zeit.de/index/){:target="_blank"} Anfang 2018 auf eine vermeidlich herrschende Grundproblematik aufmerksam. Doch ist das wirklich so? Wird die Welt immer ungerechter, obwohl es immer mehr Ländern wirtschaftlich immer besser geht?
Im Rahmen eines studentischen Projekts an der [Hochschule Mannheim](https://www.hs-mannheim.de/){:target="_blank"} wurde dieser Sachverhalt eingehend untersucht. Die folgende Dokumentation soll die Motivation, Grundidee und Durchführung des Projekts genauer beleuchten. Es wird in den kommenden Abschnitten explizit auf die Analyse der erhobenen Daten, die Implementierung des Prototyps, und die daraus gewonnenen Erkenntnissen eingegangen.

[^fn1]: [Rudzio, Kolja: Ungleich (17.01.2018)](https://www.zeit.de/2018/04/soziale-ungleichheit-einkommen-wirtschaftswachstum-armut-reichtum)

---

# Inhalt
1. [Einführung](#einfuehrung)
2. [Motivation und Konzept](#motivation)
3. [Hypothesen](#hypothesen)
4. [Daten](#daten)  
	4.1. [Datenquellen](#datenquellen)  
	4.2. [Datenanalyse](#datenanalyse)  
	4.3. [Datenaufbereitung](#datenaufbereitung)  
5. [Prototyp](#prototyp)
6. [Fazit](#fazit)  
	6.1. [Erkenntnisse](#erkenntnisse)  
	6.2. [Ausblick](#ausblick)  

---

## Einführung <a name="einfuehrung"/>

Dieses Projekt ist im Rahmen des Moduls *Grundlagen der Informationsvisualisierung (GDV)* durchgeführt worden. Die Lehrveranstaltung steht allen Studenten eines [Informatik](https://www.informatik.hs-mannheim.de/){:target="_blank"}-Studiengangs als Wahlpflichtfach zur Verfügung. Nach einer Auseinandersetzung mit den Grundkonzepten und Methoden der Informationsvisualisierung ist es in der zweiten Hälfte des Semesters üblich, dass sich die Studierenden in Gruppen mit einem Themengebiet auseinandersetzen und gemeinsam darauf basierend ein Visualisierungsprojekt erarbeiten. Das Thema wird durch den Dozenten Herrn [Prof. Dr. Till Nagel](https://services.informatik.hs-mannheim.de/~nagel/){:target="_blank"} vorgegeben. In diesem  Semester (Wintersemester 2018/2019) bildeten die sogenannten  
"[Sustainable Development Goals](https://www.un.org/sustainabledevelopment/sustainable-development-goals/){:target="_blank"}" der Vereinten Nationen den Themenschwerpunkt. Dabei handelt es sich um 17 von der UNO definierten Ziele zur nachhaltigen Entwicklung der Welt auf wirtschaftlicher, sozialer und ökologischer Ebene, beispielsweise **Kein Hunger**, **Klimaschutz**, oder **Gute Bildung**.

<br/>
  
<figure>
	<a href="https://www.un.org/sustainabledevelopment/sustainable-development-goals/" target="_blank">
  		<img src="{{ site.urlimg }}/inequality/sustainable_development_goals.png" />
  	</a>
  <figcaption>17 Sustainable Development Goals</figcaption>
</figure>




Zu einem oder mehreren dieser SDGs sollen die Studierenden Daten aus verschiedenen Quellen auswählen und diese mit unterschiedlichen Visualisierungstechniken interaktiv sichtbar machen. Weitere Vorgaben waren nicht gegeben. Daher bot die Aufgabenstellung einen enorm großen Spielraum hinsichtlich darauf, welche SDGs ausgewählt und welche möglichen Fragestellungen und Hypothesen durch die Daten überprüft und beleuchtet werden sollen.


## Motivation und Konzept <a name="motivation"/>
Um dieses weite Themenspektrum systematisch anzugehen, bestand der erste Schritt logischerweise darin, sich mit den einzelnen SDGs auseinanderzusetzen um einen Überblick zu gewinnen. Relativ schnell gab es im Projektteam einen Konsens darüber sich mit einem wirtschaftlichen Thema zu befassen. Insbesondere war der Schwerpunkt "Arm und Reich" von besonderem Interesse, da in den Medien immer wieder die auseinandergehende Schere zwischen Arm und Reich thematisiert wird. Aus diesem Grund wurden die SDGs [Menschenwürdige Arbeit und Wirtschaftswachstum](https://www.un.org/sustainabledevelopment/economic-growth/){:target="_blank"} (Decent work and economic growth, #8) und [Verringerung der Ungleichheit](https://www.un.org/sustainabledevelopment/inequality/){:target="_blank"} (Reduced inequalities, #10) für dieses Projekt ausgewählt. Aus der Überlegung heraus, dass von einer sich entwickelnden und wachsenden Wirtschaft in einem Land die gesamte Bevölkerung davon profitieren sollte, wurden erste Gedanken für eine Hypothese abgeleitet. Parallel dazu wurden erste Ideen und Konzepte für die Endanwendung als Paper-Prototype festgehalten.  

<figure>
  <img src="{{ site.urlimg }}/inequality/scribble_gdp_growth_inequality.png" />
  <figcaption>Erste Ideen in Form eines Paper-Prototypes</figcaption>
</figure>

Im weiteren Schritt wurden [Datenquellen](#datenquellen) bezüglich den ausgewählten SDGs recherchiert. Auf der offiziellen Seite des [United Nations Development Programme (UNDP)](http://www.undp.org/){:target="_blank"} werden zahlreiche statistische Datensätze zur Verfügung gestellt, die eine weitere Analyse ermöglichen. Nach einem Vergleich der dort angebotenen Indikatoren und Daten, entschied man sich für den sogenannten [Coefficient for Human Inequality](http://hdr.undp.org/en/content/what-does-coefficient-human-inequality-measure){:target="_blank"}. Dieser bot eine gute Möglichkeit, die Ungleichheit in einer Bevölkerung im zeitlichen Verlauf zu betrachten. Konkret handelt es sich dabei um eine statistische Kennzahl der Ungleichheit einer Bevölkerung in den Bereichen *Gesundheit*, *Einkommen* und *Bildung*. Zusätzlich wurden für diesen Index Werte über mehrere Jahre angeboten, was wie erwähnt eine zeitliche Betrachtung der Ungleichheit in verschiedenen Ländern ermöglicht.
Demgegenüber wurde eine geeignete Quelle für das wirtschaftliche Wachstum recherchiert. Die Webseite der [World Bank](https://data.worldbank.org/){:target="_blank"} bot hierfür Datensätze zum Wachstum des Bruttoinlandsprodukts pro Kopf (GDP growth per capita) für verschiedene Länder an. Bei der ersten Exploration der Daten wurde der Ansatz jedoch wieder verworfen, da folgende Problemstellung auftrat: Im *Coefficient for Human Inequality* wurde das Wachstum des Pro-Kopf-Einkommens bereits miteinberechnet. Daher wurde im ersten Visualisierungsansatz eine Proportionalität zwischen den beiden Größen im Schaubild erkennbar. Aus diesem Grund wurde für weitere Betrachtungen das **Gross domestic product (GDP) per capita** in absoluten Zahlen genommen, statt des reinen Wachstums. Der Datensatz hierfür konnte erneut auf der Seite des UNDP gefunden werden.



## Hypothesen <a name="hypothesen"/>

Aus den anfänglichen Überlegungen und der Exploration der Datensätze wurden folgende Hypothesen aufgestellt, die in diesem Projekt untersucht werden sollen:
-	"*Bei einer steigenden/wachsenden Wirtschaft in einem Land sollte die Ungleichheit in der Bevölkerung sinken*"
-	"*Umgekehrt sollte die Ungleichheit in der Bevölkerung steigen, wenn die Wirtschaft des Landes sinkt*"


## Daten<a name="daten"/>
### Datenquellen <a name="datenquellen"/>

Im Rahmen des [United Nations Development Programme (UNDP)](http://www.undp.org/){:target="_blank"} veröffentlicht das Human Development Report Office (HDRO) jährliche [Berichte](http://hdr.undp.org/en/){:target="_blank"}, die die menschliche Entwicklung weltweit beschreiben. Diese Daten dienen als Grundlage für politische Diskussionen rund um die menschliche Entwicklung. Das HDRO greift auf unterschiedliche Maßnahmen zurück, um die höchste Qualität der Daten sicherzustellen.  Darunter zählt die regelmäßige Kommunikation mit nationalen und internationalen Statistikämtern. Trotz dieser Zielsetzung weist das HDRO darauf hin, dass einige Probleme mit der Datenqualität bestehen. Diese werden zusammen mit den Daten auf der Webseite veröffentlicht.  
Für die Hypothese standen zwei Dimensionen der [Human Development Data](http://hdr.undp.org/en/data){:target="_blank"} im Fokus: 
- **Inequality**  
- **Income/Composition of resources**  

Für die Beschreibung der Ungleichheit in einem Land wurde der **Coefficient of Human Inequality** herangezogen. Diese künstlich berechnete Kennzahl setzt sich aus den Ungleichheiten in den Bereichen *Gesundheit*, *Bildung* und *Einkommen* zusammen. Als Kennzahl für die wirtschaftliche Lage in einem Land wurde auf das Bruttoinlandsprodukt (BIP) pro Einwohner (engl. **Gross domestic product per capita**) zurückgegriffen.[^fn2] Das BIP ist das wichtigste gesamtwirtschaftliche Produktionsmaß und stellt den Wert aller Güter und Dienstleistungen dar, die in einem Jahr innerhalb der Landesgrenzen einer Volkswirtschaft erwirtschaftet wurde.[^fn3] Die Kaufkraftparität (engl. *purchasing power parity, PPP*) dient dazu, Wechselkursschwankungen zu berücksichtigen. [^fn4] [^fn5]


[^fn2]: [Bruttoinlandsprodukt (BIP) pro Kopf](http://www.bpb.de/wissen/72UZFD,0,0,Bruttoinlandsprodukt_(BIP)_pro_Kopf.html)
[^fn3]: [Bruttoinlandsprodukt (BIP)](http://www.bpb.de/nachschlagen/zahlen-und-fakten/europa/70543/bruttoinlandsprodukt-bip)
[^fn4]: [About Human Development](http://hdr.undp.org/en/humandev)
[^fn5]: [Understanding the data](http://hdr.undp.org/en/statistics/understanding)





### Datenanalyse <a name="datenanalyse"/>

Zu Beginn der Analyse wurden die Daten für *Coefficient of Human Inequality* und *Gross domestic product (GDP) per capita* aus den CSV-Dateien auf Auffälligkeiten exploriert. Erste Auffälligkeit war das ungünstige Format der Daten. Die Daten der einzelnen Länder waren nach Komma als Trennungszeichen separiert. Für die erste Analyse wurde das Format angepasst und eine Trennung nach Spalten vorgenommen. Im neuen Format wurde festgestellt, dass leere Spalten zwischen den Jahren existierten.
Beim Vergleich beider Datensätze für *Coefficient of Human Inequality* und *Gross domestic product (GDP) per capita* ist aufgefallen, dass die Zeiträume abweichen. Für den Datensatz *Gross domestic product (GDP) per capita* lagen Daten für die Jahre zwischen 1990 und 2017 vor, während beim *Coefficient of Human Inequality* nur die Daten zwischen den Jahren 2010 und 2017 vorhanden waren.
Eine weitere Erkenntnis aus der Datenanalyse war die Präsenz einiger leerer Felder. Nicht für alle Jahre und für alle Länder lagen Daten vollständig vor. 


TODO
Nach dem Abgleich dieser Datensätze mit den [ISO-Ländercodes](https://www.iso.org/iso-3166-country-codes.html){:target="_blank"} wurde ebenso eine Differenz bei der Anzahl der Länder festgestellt. 
Für eine erste Darstellung der Daten wurden die Datensätze mittels [Tableau](https://www.tableau.com/de-de){:target="_blank"} visualisiert, um erste inhaltliche Erkenntnisse zu ziehen.

### Datenaufbereitung <a name="datenaufbereitung"/>

Im ersten Schritt der Datenaufbereitung wurden überflüssige Spalten aus beiden Datensätzen entfernt. Dazu gehörten die leeren Spalten sowie die Spalte „HDI Rank (2017)“, welche für die Visualisierung keine Verwendung fand.
Aufgrund der Abweichung der Zeiträume und um eine Gegenüberstellung der Daten zu ermöglichen, wurde ein einheitlicher Zeitraum (2010 bis 2017) festgelegt. Dies hatte zur Folge, dass aus dem Datensatz *Gross domestic product (GDP) per capita* die Jahre 1990, 1995, 2000 und 2005 entfernt wurden.
Für das Problem mit leeren Feldern musste eine Entscheidung getroffen werden. Die zentrale Frage war, ab wann ein Land nicht weiter berücksichtigt werden soll. Entscheidend war wie viele Jahre zur Verfügung stehen. Bei zu wenigen Daten war es nicht mehr möglich, eine zeitliche Entwicklung darzustellen bzw. Erkenntnisse daraus zu ziehen. Aufgrund dessen wurde folgende Regel definiert: Ein Land wird aussortiert, falls keine Jahre oder weniger als vier Jahre auf einem der Datensätze vorliegen.   

###### Aussortierte Länder (aufgrund mangelnder Daten)
---
<div style="color:red">

•	Algeria
•	Bahamas
•	Barbados	
•	China
•	Eritrea
•	Djibouti
•	Fiji
•	Gambia
•	Hong Kong, China (SAR)
•	Iran (Islamic Republic of)
•	Micronesia (Federated States of)
•	Myanmar
•	New Zealand
•	Singapore
•	Solomon Islands
•	South Sudan
•	Sudan
•	Turkmenistan  

</div>
---

<br/>

Zusätzlich wurden bei großen Lücken (= mehr als 2 fehlenden Jahre) die Randwerte entfernt, da bei der Visualisierung durch ein Liniendiagramm die Ergebnisse verfälscht wären.  

<figure>
  <img src="{{ site.urlimg }}/inequality/chart_south_africa_unadjusted.png" />
  <figcaption>Südafrika mit unbereinigten Daten</figcaption>
</figure>
<figure style="text-align:center">
  <img src="{{ site.urlimg }}/inequality/arrow-down.png" width="20" height="4"/>
</figure>
<figure>
  <img src="{{ site.urlimg }}/inequality/chart_south_africa_adjusted.png" />
  <figcaption>Südafrika mit bereinigten Daten</figcaption>
</figure>


<br/>

Der nächste Schritt bestand im Abgleich der Länder zwischen den Datensätzen *Gross domestic product (GDP) per capita* und *Coefficient of Human Inequality*. Schlussendlich wurden mithilfe von [Tableau Prep](https://www.tableau.com/de-de/products/prep){:target="_blank"} Diskrepanzen identifiziert und bereinigt.    

  
###### Betrachtete Länder (nach Abgleich)
---

<div style="color:green">

•	Afghanistan
•	Albania
•	Angola
•	Argentina
•	Armenia
•	Australia
•	Austria
•	Azerbaijan
•	Bangladesh
•	Belarus
•	Belgium
•	Belize
•	Benin
•	Bhutan
•	Bolivia (Plurinational State of)
•	Bosnia and Herzegovina
•	Botswana
•	Brazil
•	Bulgaria
•	Burkina Faso
•	Burundi
•	Cabo Verde
•	Cambodia
•	Cameroon
•	Canada
•	Central African Republic
•	Chad
•	Chile
•	Colombia
•	Comoros
•	Congo (the)
•	Congo (the Democratic Republic of the)
•	Costa Rica
•	Croatia
•	Cyprus
•	Czechia
•	Côte d'Ivoire
•	Denmark
•	Dominican Republic
•	Ecuador
•	Egypt
•	El Salvador
•	Estonia
•	Eswatini
•	Ethiopia
•	Finland
•	France
•	Gabon
•	Georgia
•	Germany
•	Ghana
•	Greece
•	Guatemala
•	Guinea
•	Guinea-Bissau
•	Guyana
•	Haiti
•	Honduras
•	Hungary
•	Iceland
•	India
•	Indonesia
•	Iraq
•	Ireland
•	Israel
•	Italy
•	Jamaica
•	Japan
•	Jordan
•	Kazakhstan
•	Kenya
•	Kiribati
•	Korea (the Republic of)
•	Kyrgyzstan
•	Lao People's Democratic Republic
•	Latvia
•	Lebanon
•	Lesotho
•	Liberia
•	Lithuania
•	Luxembourg
•	Madagascar
•	Malawi
•	Maldives
•	Mali
•	Malta
•	Mauritania
•	Mauritius
•	Mexico
•	Moldova (the Republic of)
•	Mongolia
•	Montenegro
•	Morocco
•	Mozambique
•	Namibia
•	Nepal
•	Netherlands
•	Nicaragua
•	Niger (the)
•	Nigeria
•	Norway
•	Pakistan
•	Palestine, State of
•	Panama
•	Paraguay
•	Peru
•	Philippines (the)
•	Poland
•	Portugal
•	Romania
•	Russian Federation
•	Rwanda
•	Saint Lucia
•	Sao Tome and Principe
•	Senegal
•	Serbia
•	Sierra Leone
•	Slovakia
•	Slovenia
•	South Africa
•	Spain
•	Sri Lanka
•	Suriname
•	Sweden
•	Switzerland
•	Tajikistan
•	Tanzania, United Republic of
•	Thailand
•	Macedonia (the former Yugoslav Republic of)
•	Timor-Leste
•	Togo
•	Trinidad and Tobago
•	Tunisia
•	Turkey
•	Uganda
•	Ukraine
•	United Kingdom of Great Britain and Northern Ireland
•	United States of America
•	Uruguay
•	Uzbekistan
•	Vanuatu
•	Venezuela (Bolivarian Republic of)
•	Viet Nam
•	Yemen
•	Zambia
•	Zimbabwe

</div>

---


## Prototyp <a name="prototyp"/>

*Platzhalter*


## Fazit <a name="fazit"/>

*Platzhalter*

### Erkenntnisse <a name="erkenntnisse"/>
Tatsächlich zeigt sich bei der Mehrheit der Länder weltweit eine positive Entwicklung, was unsere anfängliche Hypothese bestätigt:
  
"*Steigt die Wirtschaft eines Landes, so sinkt die Ungleichheit in der Bevölkerung; bzw. sie bleibt konstant, wenn diese bereits einen niedrigen Wert aufweist.*"      

<figure>
  <img src="{{ site.urlimg }}/inequality/chart_bolivien.png" />
</figure>

Zudem gibt es auch Beispiele, die den umgekehrten Fall der Korrelation aufweisen, z.B. die Zentralafrikanische Republik: Die Wirtschaft sinkt, wodurch die Ungleichheit steigt.  

<figure>
  <img src="{{ site.urlimg }}/inequality/chart_central_africa_republic.png" />
</figure>

Auch zeigen sich in einigen Fällen Ausnahmen, die von der Korrelation abweichen, wie Bulgarien: Trotz wachsender Wirtschaft, steigt die Ungleichheit in der Bevölkerung.  

<figure>
  <img src="{{ site.urlimg }}/inequality/chart_bulgarien.png" />
</figure>


### Ausblick <a name="ausblick"/>

Ausgehend vom erhaltenen **Feedback auf der iExpo** ergaben sich die folgenden möglichen Verbesserungsvorschläge:

- Suchfunktion zur Auswahl von Ländern
- Durchschnittswerte für Kontinente zum Vergleich
- Keine blauen Icons auf blauem Hintergrund
- Höhere Auflösung der Visualisierungen
- Auswahl von max. 2 Ländern
- Start- und Endpunkt der Animation differenziert darstellen
  
<br/>
<br/>

## Credits <a name="credits"/>
  
Das Projekt wurde realisiert durch: 

- Daniel Kogan
- Moritz Mundhenke
- Patrick Lowinski-Loh
- Stefan Sousa
- Tim Schäfer

Grundlagen der Informationsvisualisierung (GDV), Wintersemester 2018/2019 bei Herrn [Prof. Dr. Till Nagel](https://services.informatik.hs-mannheim.de/~nagel/){:target="_blank"}, Hochschule Mannheim

