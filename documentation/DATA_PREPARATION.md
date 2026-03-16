# Datenaufbereitung

## Ziel

Diese Datei dokumentiert die Schritte, mit denen der ursprüngliche LimeSurvey-Datensatz für die Analyse vorbereitet wurde.

Die Datenaufbereitung dient dazu,

- Ausschlusskriterien anzuwenden,
- zentrale Variablen lesbarer zu benennen,
- Antwortformate zu vereinheitlichen,
- und strukturierte Analyse-Datensätze für die Hypothesentests H1 bis H4 zu erzeugen.

## 1. Ausgangsdatensatz

Der Rohdatensatz stammt aus einem Export der Online-Umfrage in LimeSurvey. Er enthält:

- demografische Angaben
- Antworten im Author Recognition Test (ART)
- Einzelbewertungen zu den Textausschnitten
- Vergleichsfragen zu den Textpaaren
- Einschätzungsfragen zu zusätzlichen Textausschnitten
- optionale offene Antworten

## 2. Ausschlusskriterien

Vor der Analyse wurden Fälle entfernt, die die vorab festgelegten Mindestanforderungen an die Bearbeitungszeit nicht erfüllen.

### 2.1 Gesamtausschluss nach Bearbeitungszeit

Die Variable  
`interviewtime. Gesamtzeit`  
enthält die gesamte Bearbeitungsdauer in Sekunden.

Alle Fälle mit einer Bearbeitungszeit von unter **900 Sekunden** wurden ausgeschlossen.

### 2.2 Ausschluss nach Gruppenzeiten der Textbewertungsblöcke

Zusätzlich wurden die folgenden Gruppenzeiten geprüft:

- `groupTime308. Gruppenzeit: Textausschnitte Fragen`
- `groupTime309. Gruppenzeit: Textausschnitte Fragen`
- `groupTime310. Gruppenzeit: Textausschnitte Fragen`
- `groupTime304. Gruppenzeit: Textausschnitte Fragen`

Unterschritt eine Person in mindestens einer dieser Variablen den Wert von **90 Sekunden**, wurde der Fall ausgeschlossen.

### 2.3 Ergebnis der Bereinigung

Nach Anwendung der Ausschlusskriterien verblieben **138 gültige Fälle** im Datensatz.

## 3. Gruppenzuordnung

Die Teilnehmenden wurden randomisiert einer von zwei Experimentalgruppen zugeteilt:

- **Gruppe A** = ohne Autorschaftsinformation
- **Gruppe B** = mit Autorschaftsinformation

Die Gruppenzugehörigkeit war im Rohdatensatz in der Spalte

`gleichung. {if(is_empty(gleichung), rand(1,2), gleichung)}`

kodiert als:

- `1` = Gruppe A
- `2` = Gruppe B

Für die Analyse wurde daraus eine lesbare Gruppenvariable mit den Ausprägungen `A` und `B` gebildet.

## 4. Umbenennung zentraler Variablen

Mehrere zentrale Metadaten und demografische Variablen wurden umbenannt, um die Arbeit mit dem Datensatz zu erleichtern.

Beispiele:

- `id. Antwort ID` → `participant_id`
- `interviewtime. Gesamtzeit` → `interview_time_sec`
- `Q001. Wie alt sind Sie?` → `age`
- `Q002. Was ist Ihr Geschlecht?` → `gender`
- `Q005. Was studieren Sie aktuell oder was ist Ihr Beruf?` → `study_or_job_raw`

## 5. Umwandlung der Antwortformate

Viele geschlossene Antworten lagen im Rohdatensatz als Text mit vorangestellter Zahl vor, z. B.:

`1 – stimme überhaupt nicht zu`

Für die statistische Analyse wurde aus solchen Antworten die führende Zahl extrahiert und als numerischer Wert gespeichert.

## 6. Strukturierung der Einzelbewertungen

Die Bewertungsfragen der Einzeltexte wurden in ein Long-Format überführt.  
Dabei wurden unter anderem folgende Informationen gespeichert:

- `participant_id`
- `group`
- `pair_id`
- `text_pos`
- `text_type`
- `item_no`
- `response_num`

## 7. Strukturierung der Vergleichsfragen

Die Vergleichsfragen wurden ebenfalls in ein Long-Format überführt.  
Dabei wurden unter anderem gespeichert:

- `participant_id`
- `group`
- `pair_id`
- `question_no`
- `response_num`
- `preference_target`

## 8. Strukturierung der Einschätzungsfragen

Die Einschätzungsfragen zu zusätzlichen Textausschnitten wurden ebenfalls in ein Long-Format überführt.

Dabei wurden unter anderem gespeichert:

- `participant_id`
- `group`
- `text_id`
- `true_type`
- `predicted_type`
- `correct`

## 9. Offene Antworten

Offene Antworten wurden in separaten Dateien gesammelt, um sie von den geschlossenen Daten zu trennen.

Dabei wurden unter anderem unterschieden:

- offene Antworten zu Item 9 der Einzeltexte
- offene Antworten zu Vergleichsfrage 2
- optionale Kommentare zu den Einschätzungsfragen

Diese Daten werden aus Datenschutzgründen nur nach gesonderter Prüfung veröffentlicht.

## 10. Ergebnisdateien der Datenaufbereitung

### `master_clean_renamed.xlsx`
Bereinigter Hauptdatensatz im Wide-Format.

### `ratings_long.xlsx`
Long-Format der Einzelbewertungen.

### `compare_long.xlsx`
Long-Format der Vergleichsfragen.

### `estimation_long.xlsx`
Long-Format der Einschätzungsfragen.

### `open_item9_long.xlsx`
Offene Antworten zu Item 9.

### `open_compare2_long.xlsx`
Offene Antworten zu Vergleichsfrage 2.
