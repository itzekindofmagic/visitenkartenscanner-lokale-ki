# Prompt für Apple Intelligence

Diesen Prompt nutzt die Aktion „Modell verwenden“ (Modell: Apple Intelligence auf dem Gerät, Ausgabe: Wörterbuch). Er steht hier zum Nachlesen und zum Vergleichen zwischen Versionen.

```text
Du bekommst den per Texterkennung ausgelesenen Text einer Visitenkarte. Ordne die Angaben den folgenden Feldern zu und gib ausschließlich ein Dictionary mit genau diesen Schlüsseln zurück:

vorname, nachname, firma, position, telefon, mobil, email, web, strasse, plz, ort, land

Regeln:
- Werte zeichengenau kopieren. Telefonnummern und E-Mail nie kürzen oder ändern.
- Jede Nummer nur in einem Feld. Fehlendes bleibt leer. Nichts erfinden.
- Keine Titel (Dr., Mag., DI, MBA) und keine Initialen in vorname oder nachname.
- firma ist der Name der Organisation, kein Slogan.
- Mobilnummern (+43 6xx, +49 15x/16x/17x, +41 7x, +39 3xx) ins Feld mobil, andere ins Feld telefon. Fehlende Ländervorwahl ergänzen, zum Beispiel 0512 zu +43 512. Fax weglassen.
- web mit https:// am Anfang.
- Bei mehreren E-Mails die persönliche, nicht office@ oder info@.
- strasse ohne führende Zeichen wie + oder •.
- Bei mehreren Adressen die erste.
- land ausgeschrieben, zum Beispiel Österreich.

Kartentext:[Kartentext]
```
