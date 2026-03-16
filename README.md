# Es war einmal… ein Algorithmus
## Materialien zur Masterarbeit

Dieses Repository enthält ergänzende Materialien zur Masterarbeit  
**„Es war einmal… ein Algorithmus: Eine vergleichende Rezeptionsstudie zu KI-generierten und menschlich verfassten Märchentextausschnitten über Meerjungfrauen“**.

Die Arbeit untersucht, wie Leser*innen KI-generierte und menschlich verfasste Märchentextausschnitte bewerten und inwiefern diese Bewertung durch Wissen über die Autorschaft beeinflusst wird. Das Repository dient der Transparenz und Nachvollziehbarkeit der empirischen Auswertung. Es enthält den vollständigen Fragebogen, den Auswertungscode und Dokumentationen zur Datenstruktur und Datenaufbereitung.

## Ziel des Repositories

Das Repository soll nachvollziehbar machen,

- wie der zugrundeliegende LimeSurvey-Datensatz aufgebaut ist,
- welche Bereinigungsschritte vor der Analyse vorgenommen wurden,
- wie die Variablen kodiert und umstrukturiert wurden,
- und wie die Daten zur Überprüfung der Hypothesen H1 bis H4 verwendet wurden.

Da der vollständige Fragebogen für den gedruckten Anhang der Arbeit zu umfangreich ist, wird er hier zusätzlich bereitgestellt.

## Inhalt des Repositories

- vollständige Darstellungsfassung des Fragebogens
- Textausschnitte für computergestützte Analyse
- Jupyter-Notebook zur Datenbereinigung 
- Jupyter-Notebooks zur Auswertung
- Jupyter-Notebooks zur computergestützten Analyse
- Dokumentation der Variablenstruktur
- Dokumentation der Datenaufbereitung

## Repository-Struktur

questionnaire/ – Vollständige Darstellungsfassung des Fragebogens (Fragebogen), Textausschnitte (im Ordner stylo_texts und alle Textausschnitte (xlsx-Datei))  
documentation/ – Codebook, Datenaufbereitung, Reproduzierbarkeit  
notebooks/ – Jupyter-Notebook zur Datenaufbereitung, Datenanalyse, computergestützten Analyse

## Fragebogen

Der vollständige Fragebogen der Studie befindet sich im Ordner `questionnaire/`.  
Er dokumentiert die in LimeSurvey umgesetzte Erhebungsfassung in lesbarer Form.

## Daten und Datenschutz

Der ursprüngliche Rohdatensatz stammt aus einer anonymisierten LimeSurvey-Erhebung.  
Aus Datenschutzgründen wird in diesem Repository kein Datensatz bereitgestellt. Das Datenaufbereitungs-Notebook dokumentiert die Verarbeitung des ursprünglichen LimeSurvey-Exports.

## Hypothesen

**H1**  
Der Unterschied in der wahrgenommenen literarischen Qualität zwischen menschlich verfassten Märchentextausschnitten und entsprechenden KI-generierten Textausschnitten ist in der Bedingung mit Autorschaftsinformation signifikant größer als in der Bedingung ohne Autorschaftsinformation.

**H2**  
In der Informationsbedingung (Gruppe B) erhalten als menschlich gekennzeichnete Textausschnitte höhere durchschnittliche Qualitätsbewertungen als als KI-generiert gekennzeichnete Texte.

**H3**  
Die Gesamt-Erkennungsrate, also der Anteil korrekt klassifizierter zusätzlicher Textausschnitte, liegt signifikant über dem Zufallsniveau von 50 %.

**H4**  
Die Erkennungsleistung für die Unterscheidung KI-generierter und menschlich verfasster Texte ist in der Informationsbedingung höher als in der Bedingung ohne Autorschaftsinformation.

## Wichtige Dateien (in diesem Repository nicht enthalten, wurde zur Bewertung an Dozent*innen weitergegeben)

### `data/processed/master_clean_renamed.xlsx`
Bereinigter Hauptdatensatz im Wide-Format mit umbenannten zentralen Variablen.

### `data/processed/ratings_long.xlsx`
Long-Format der Einzelbewertungen. Grundlage für Qualitätsmaße, Bewertungsdimensionen und die Hypothesen H1 und H2.

### `data/processed/compare_long.xlsx`
Long-Format der Vergleichsfragen pro Textpaar. Grundlage für explorative Analysen der direkten Präferenz- und Ähnlichkeitsurteile.

### `data/processed/estimation_long.xlsx`
Long-Format der Einschätzungsfragen zu zusätzlichen Textausschnitten. Grundlage für H3 und H4.

## Zentrale reproduzierbare Ergebnisse

Die mit den bereitgestellten Datensätzen und dem Notebook reproduzierbaren Kernergebnisse umfassen unter anderem:

- finale Stichprobe: **N = 138**
- höhere durchschnittliche Bewertung von KI-Texten in Gruppe A
- höhere durchschnittliche Bewertung menschlicher Texte in Gruppe B
- signifikante Unterstützung von H1 und H2
- Gesamt-Accuracy von ca. **63,2 %**
- signifikant höhere Erkennungsleistung in Gruppe B als in Gruppe A

## Notebook

Die zentrale Analyse ist im Notebook  
`notebooks/reproduce_main_results.ipynb`  
dokumentiert.

## Hinweise zur Nachnutzung

Für die Reproduktion der Analyse empfiehlt es sich folgende Reihenfolge:
1. `REPRODUCIBILITY.md` lesen  
2. `documentation/CODEBOOK.md` lesen  
3. `documentation/DATA_PREPARATION.md` lesen  

