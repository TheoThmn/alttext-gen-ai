# Mistral Alt-Text Generator – Benutzerdokumentation

Dieses Tool erzeugt kurze, objektive Bildbeschreibungen (“Alt-Texte”) für ganze Bildordner mit Hilfe der Mistral-API. Die resultierenden Beschreibungen werden in einer frei wählbaren Textdatei gespeichert.


## Systemvoraussetzungen

| Komponente   | Mindestanforderung                                                                            |
| ------------ | --------------------------------------------------------------------------------------------- |
| **Browser**  | Aktueller Chromium-Browser (Chrome, Edge, Brave ≥ v86) mit aktivierter File-System-Access-API |
| **Aufruf**   | Über `https://` **oder** `http://localhost` (lokaler Web-Server erforderlich)                 |
| **Internet** | HTTPS-Zugriff auf `api.mistral.ai`                                                            |



## Erste Schritte

1. **Bilderordner wählen**
   Klicke **Ordner wählen** und erteile Lesezugriff.

2. **Ausgabedatei anlegen**
   Mit **Datei wählen / anlegen** eine neue (oder bestehende) `.txt`-Datei bestimmen.

3. **Prompt anpassen (optional)**
   Vorgabeprompt kann editiert werden.

4. **Mistral-API-Key & Timeout hinterlegen**
   Klick auf ⚙️→ **Einstellungen**

   * Key einfügen (Link zum Mistral-Portal vorhanden).
   * Timeout (Millisekunden) festlegen (Standard: 1500 ms).
   * **Key speichern** anhaken, wenn er dauerhaft im `localStorage` bleiben soll; sonst wird er nur sitzungsweise (`sessionStorage`) gehalten. Bitte nicht auf gemeinsam genutzten Geräten verwenden 

6. **Start** drücken

   * Log zeigt den Ablauf.
   * Nach Ende wird die Ausgabedatei beschrieben und ein Erfolgseintrag protokolliert.

## Dateiverarbeitung

1. **Filter** – nur `.jpg`, `.jpeg`, `.png`, `.webp`
2. **Sortierung** – alphabetisch / numerisch
3. **API-Aufruf** für jedes Bild
4. **Response** → `<Dateiname>: <Caption>`
5. **Timeout** – Pause zwischen Aufrufen (Standard 1500 ms)
6. **Speichern** – gesamte Liste wird ein Mal nach Abschluss geschrieben


## Fehler- & Sicherheits­hinweise

| Meldung                               | Bedeutung / Abhilfe                                                                                                              |
| ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| *„401 (ungültiger/abgelaufener Key)“* | API-Key prüfen / erneuern                                                                                                        |
| *Dateipicker erscheint nicht*         | Seite nicht über HTTPS/localhost geladen **oder** Browser ohne FS-API                                                            |
| *❌ Schreiben fehlgeschlagen*          | Schreibrechte verweigert – Datei erneut wählen & „Änderungen zulassen“                                                           |
| **Datenschutz**                       | Key wird nur client-seitig gespeichert; Speicherung optional. Keine Daten werden an andere Server gesendet als `api.mistral.ai`. |

---

## Tipps & Tricks

* **Batch-Größe optimieren**
  Bei API-Limits ggf. Timeout erhöhen (> 1500 ms).
* **Prompt-Varianten testen**
  Verschiedene Anweisungen führen zu unterschiedlichem Stil – z. B. „ohne Artikel“, „max. 120 Zeichen“.
* **Mehrsprachig**
  Prompt einfach in gewünschter Sprache formulieren, Beschreibung folgt automatisch.
