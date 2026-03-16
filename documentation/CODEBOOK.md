# Codebook

## Ziel

Dieses Codebook dokumentiert die Struktur der Datensätze. Es soll nachvollziehbar machen, welche Dateien welche Informationen enthalten, wie zentrale Variablen kodiert sind und welche Datensätze für die Reproduktion der Hypothesen H1 bis H4 verwendet werden.

Das Codebook bezieht sich auf die **bereinigten und aufbereiteten Analyse-Datensätze**, nicht auf den vollständigen ursprünglichen LimeSurvey-Rohdatensatz.

## Überblick über die bereitgestellten Datensätze

### `master_clean_renamed.xlsx`
Bereinigter Hauptdatensatz im Wide-Format.  
Eine Zeile entspricht einer Person. Die Datei enthält zentrale Metadaten, demografische Variablen, Gruppenzugehörigkeit und die ursprünglichen Antwortspalten in bereinigter Form.

### `ratings_long.xlsx`
Long-Format der Einzelbewertungen.  
Eine Zeile entspricht einer Person × einem Textausschnitt × einem Item.  
Diese Datei ist die zentrale Grundlage für die Qualitätsanalysen sowie für H1 und H2.

### `compare_long.xlsx`
Long-Format der Vergleichsfragen.  
Eine Zeile entspricht einer Person × einem Textpaar × einer Vergleichsfrage.  
Diese Datei dient vor allem explorativen Analysen der direkten Vergleichsurteile.

### `estimation_long.xlsx`
Long-Format der Einschätzungsfragen zu zusätzlichen Textausschnitten.  
Eine Zeile entspricht einer Person × einem gezeigten Zusatztext.  
Diese Datei ist die zentrale Grundlage für H3 und H4.

### `open_item9_long.xlsx`
Long-Format der offenen Antworten zu Item 9 der Einzeltexte.  
Diese Datei enthält optionale offene Antworten und wird aus Datenschutzgründen nur nach gesonderter Prüfung bereitgestellt.

### `open_compare2_long.xlsx`
Long-Format der offenen Antworten zu Vergleichsfrage 2.  
Auch diese Datei enthält Freitext und wird nur nach gesonderter Prüfung öffentlich gemacht.

---

## 1. Zentrale Metadaten im bereinigten Hauptdatensatz

Im bereinigten Hauptdatensatz wurden mehrere zentrale Variablen umbenannt.

### Identifikation und Gruppenzuordnung

- `participant_id`  
  Eindeutige ID der Person im Datensatz.

- `group_code`  
  Ursprüngliche numerische Gruppenzuordnung.  
  `1 = Gruppe A`, `2 = Gruppe B`

- `group`  
  Lesbare Gruppenzuordnung.  
  `A = ohne Autorschaftsinformation`  
  `B = mit Autorschaftsinformation`

### Zeitvariablen

- `interview_time_sec`  
  Gesamte Bearbeitungszeit in Sekunden.

### Demografische Variablen

- `age`  
  Alter der teilnehmenden Person.

- `gender`  
  Geschlecht.

- `native_language`  
  Muttersprache.

- `native_language_other`  
  Freitextangabe bei „Sonstiges“ zur Muttersprache.

- `education`  
  Höchster Schulabschluss.

- `education_other`  
  Freitextangabe bei „Sonstiges“ zum Schulabschluss.

- `study_or_job_raw`  
  Freitextangabe zu Studienfach oder Beruf.

- `reading_frequency_raw`  
  Selbsteinschätzung der Lesehäufigkeit literarischer Texte.

---

## 2. ART-Variablen

Der Author Recognition Test (ART) dient als Maß für die Print Exposure.

Im bereitgestellten Datensatz wurden daraus folgende zusammenfassende Variablen gebildet:

- `ART_correct`  
  Anzahl korrekt beantworteter ART-Items.

- `ART_total_answered`  
  Anzahl beantworteter ART-Items.

- `ART_rate`  
  Anteil korrekt beantworteter ART-Items.

Die ursprünglichen ART-Spalten beginnen mit `ART` und enthalten Antworten auf reale und fiktive Autor*innennamen.

---

## 3. Datei `ratings_long.xlsx`

Diese Datei enthält die Einzelbewertungen der Textausschnitte im Long-Format.

### Eine Zeile enthält:

- `participant_id`
- `group`
- `column_name`
- `pair_id`
- `text_pos`
- `text_type`
- `item_no`
- `raw_response`
- `response_num`
- `response_text`

### Bedeutung der zentralen Variablen

- `pair_id`  
  ID des Textpaars (`1` bis `4`)

- `text_pos`  
  Position des Textes innerhalb des Textpaars (`1` oder `2`)

- `text_type`  
  Tatsächlicher Texttyp:  
  `human` oder `ai`

- `item_no`  
  Nummer des Items

- `response_num`  
  Numerisch kodierte Antwort auf einer 1–7-Skala

- `response_text`  
  Freitextantwort bei offenen Fragen

### Zuordnung von `text_pos` zu `text_type`

Die Reihenfolge der Texttypen ist nicht in allen Textpaaren gleich:

- Textpaar 1 und 4:  
  `text_pos 1 = human`, `text_pos 2 = ai`

- Textpaar 2 und 3:  
  `text_pos 1 = ai`, `text_pos 2 = human`

### Itemstruktur

Die Einzelitems 1–8 sind geschlossene Bewertungsfragen.  
Item 9 ist eine offene Frage.  
Item 10 und gegebenenfalls Item 11 sind textspezifische Zusatzitems.

### Zuordnung der zentralen Einzelitems

- Items 1, 2, 4, 5 → Appetenzurteil
- Items 3, 6 → Leistungsurteil
- Item 7 → Akzeptanzurteil
- Item 8 → Bedeutungszuschreibung

### Verwendung in der Analyse

`ratings_long.xlsx` ist die wichtigste Grundlage für:

- Bildung des Gesamtindex literarischer Qualität
- Bildung der Bewertungsdimensionen
- Berechnung von Human- und AI-Mittelwerten pro Person
- Berechnung von `DeltaQuality`
- Hypothesentest H1
- Hypothesentest H2

---

## 4. Datei `compare_long.xlsx`

Diese Datei enthält die Vergleichsfragen zu den Textpaaren im Long-Format.

### Eine Zeile enthält:

- `participant_id`
- `group`
- `column_name`
- `pair_id`
- `question_no`
- `raw_response`
- `response_num`
- `response_text`
- `preference_target`

### Bedeutung der zentralen Variablen

- `question_no`  
  Nummer der Vergleichsfrage innerhalb eines Textpaars

- `response_num`  
  Numerisch kodierte Antwort bei geschlossenen Vergleichsfragen

- `response_text`  
  Freitextantwort bei offenen Vergleichsfragen

- `preference_target`  
  Rekodierte Präferenzrichtung bei geschlossenen Präferenzfragen:
  - `human`
  - `ai`
  - `neutral`

### Struktur der Vergleichsfragen

- Vergleichsfrage 1 → Präferenz
- Vergleichsfrage 2 → offene Begründung
- Vergleichsfrage 3 → stilistische Ähnlichkeit
- Vergleichsfrage 4 → Präferenz
- Vergleichsfrage 5 → Präferenz

### Verwendung in der Analyse

`compare_long.xlsx` dient vor allem für:

- explorative Analysen der direkten Textpräferenz
- Analysen stilistischer Ähnlichkeit
- Auswertung der offenen Begründungen
- Vergleich mit `DeltaQuality`

---

## 5. Datei `estimation_long.xlsx`

Diese Datei enthält die Einschätzungsfragen zu zusätzlichen Textausschnitten im Long-Format.

### Eine Zeile enthält:

- `participant_id`
- `group`
- `column_name`
- `text_id`
- `true_type`
- `raw_response`
- `predicted_type`
- `correct`
- `comment` (optional)

### Bedeutung der zentralen Variablen

- `text_id`  
  ID des gezeigten Zusatztextes

- `true_type`  
  Tatsächlicher Texttyp:
  - `human`
  - `ai`

- `predicted_type`  
  Einschätzung der teilnehmenden Person:
  - `human`
  - `ai`

- `correct`  
  Kodiert, ob die Einschätzung korrekt war:
  - `1 = korrekt`
  - `0 = falsch`

- `comment`  
  Optionale Freitextbegründung der Einschätzung

### Verwendung in der Analyse

`estimation_long.xlsx` ist die zentrale Grundlage für:

- Gesamt-Accuracy
- Accuracy nach Texttyp
- Accuracy nach Gruppe
- Accuracy auf Personenebene
- Hypothesentest H3
- Hypothesentest H4

---

## 6. Bereits gebildete Analysevariablen

Ein Teil der zentralen Analysevariablen wird im Notebook aus den Long-Dateien gebildet, z. B.:

- `QualityIndex`
- `DeltaQuality`
- `Appetenz`
- `Leistung`
- `Akzeptanz`
- `Bedeutung`
- `Accuracy`

Diese Variablen sind nicht zwingend in jeder bereitgestellten Datei schon enthalten, werden aber im Notebook reproduzierbar berechnet.

---

## 7. Zuordnung zu den Hypothesen

### H1
Vergleich des Unterschieds zwischen Human- und AI-Bewertungen in Gruppe A vs. Gruppe B.  
Datengrundlage: `ratings_long.xlsx`

### H2
Vergleich der Human- und AI-Bewertungen innerhalb von Gruppe B.  
Datengrundlage: `ratings_long.xlsx`

### H3
Prüfung, ob die Gesamt-Erkennungsrate über dem Zufallsniveau von 50 % liegt.  
Datengrundlage: `estimation_long.xlsx`

### H4
Vergleich der individuellen Erkennungsleistung zwischen Gruppe A und Gruppe B.  
Datengrundlage: `estimation_long.xlsx`

---

