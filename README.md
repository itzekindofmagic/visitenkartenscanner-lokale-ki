# Visitenkartenscanner für iPhone

Ein Kurzbefehl für Apple Kurzbefehle: Visitenkarte fotografieren, Felder automatisch erkennen, Kontakt als vCard anlegen. Texterkennung und KI-Auswertung laufen **auf dem iPhone**. Die Kartendaten gehen dafür an keinen Cloud-Dienst.

> Screenshot folgt (`screenshots/`), mit einer erfundenen Musterkarte.

## Was er macht

1. Kamera öffnet sich, du fotografierst die Karte.
2. iOS erkennt den Text auf dem Foto (auf dem Gerät).
3. **Apple Intelligence auf dem Gerät** ordnet den Text in 12 Felder: Vorname, Nachname, Firma, Position, Telefon, Mobil, E-Mail, Web, Straße, PLZ, Ort, Land.
4. Duplikat-Prüfung: Gibt es die E-Mail schon in deinen Kontakten, fragt der Kurzbefehl nach.
5. LinkedIn-Suche nach Name und Firma öffnet sich. Profil-URL kopieren, zurück zum Kurzbefehl, URL bestätigen.
6. Eine vCard entsteht, mit dem Scan-Datum als Notiz.
7. Vorschau: Du prüfst die Daten und legst den Kontakt selbst an.

Die Regeln für die Feldzuordnung (Titel weglassen, Mobilnummern erkennen, Ländervorwahl ergänzen usw.) stehen im Prompt: [docs/prompt.md](docs/prompt.md).

## Datenfluss

| Schritt | Wo die Daten verarbeitet werden |
|---|---|
| Foto und Texterkennung | Auf dem iPhone |
| Feldzuordnung mit KI | Apple Intelligence auf dem Gerät (fest eingestellt) |
| Duplikat-Prüfung | Deine lokalen Kontakte |
| **LinkedIn-Suche** | **Vorname, Nachname und Firma gehen als Suchbegriff an LinkedIn (Microsoft, USA)** |
| vCard und Vorschau | Auf dem iPhone |

Der LinkedIn-Schritt ist der einzige, bei dem Daten das Gerät verlassen. Wer das vermeiden will, löscht im Kurzbefehl die Aktionen von „Text“ (Name und Firma) bis „Variable festlegen“ (LinkedIn) und entfernt die Zeile `URL;TYPE=LinkedIn` aus der vCard.

Hinweis: Visitenkarten enthalten personenbezogene Daten. Für den Umgang mit gescannten Kontakten gelten die üblichen Datenschutzregeln, wie bei jeder anderen Kontaktverwaltung.

## Voraussetzungen

* iPhone mit **Apple Intelligence** (nach aktuellem Stand ab iPhone 15 Pro)
* iOS-Version mit der Aktion „Modell verwenden“ in Kurzbefehle (iOS 26 oder neuer)
* Apple Intelligence aktiviert, Sprache Deutsch eingestellt
* Zugriff auf Kamera und Kontakte für Kurzbefehle

Getestet auf: iPhone 17. Rückmeldungen zu anderen Geräten sind willkommen.

## Installation

**Variante A: iCloud-Link (empfohlen)**
Auf dem iPhone öffnen und „Kurzbefehl hinzufügen“ tippen:
https://www.icloud.com/shortcuts/261aa35f59e4454e9436df126c4b71d4

**Variante B: Datei**
[`Visitenkartenscanner.shortcut`](Visitenkartenscanner.shortcut) auf das iPhone laden und öffnen. Die Datei ist von Apple signiert. Die Signatur gilt bis Dezember 2027. Danach kommt hier eine neu signierte Version.

Tipp: Den Kurzbefehl auf den Home-Bildschirm legen oder der Aktionstaste zuweisen.

## Bekannte Grenzen

* Erkennt der Kurzbefehl keinen Text, endet er mit einem Hinweis. Für einen neuen Versuch einfach neu starten.
* Die Duplikat-Prüfung läuft nur über die E-Mail. Karten ohne E-Mail werden nicht geprüft.
* Das KI-Modell kann Felder falsch zuordnen. Deshalb immer die Vorschau prüfen.
* Wird beim LinkedIn-Schritt nichts kopiert, schlägt das Feld den bisherigen Inhalt der Zwischenablage vor. Vor dem Bestätigen prüfen oder leeren.
* Ein Semikolon auf der Karte kann die vCard-Felder verschieben (selten).

## Aufbau des Repos

```
Visitenkartenscanner.shortcut   signierte Kurzbefehl-Datei
docs/prompt.md                  Prompt für Apple Intelligence
screenshots/                    Bilder für dieses README
CHANGELOG.md                    Versionen
```

## Lizenz

MIT, siehe [LICENSE](LICENSE).

Erstellt von itzekindofmagic.com
