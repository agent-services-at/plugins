---
license: Copyright (c) 2026 Niederschick OG & Tobias Zucali. All rights reserved. Use restricted to customers with a valid agreement with Niederschick OG.
build: v1.4.0
---

# Einrichtung des Plugins

Sie benötigen den **Zugangscode** aus Ihrer E-Mail und einen Tarif, der Plugins unterstützt. Den Code geben Sie nur auf der Anmeldeseite ein, nie im Chat.

## Claude

Claude verwendet im Browser (claude.ai) und in der [Claude-Desktop-App](https://claude.com/de/download) eine gemeinsame Oberfläche für kurze Chats und umfangreiche Arbeitsaufträge. Alle Einstellungen liegen auf der Seite [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours).

### Installation

1. **Marketplace hinzufügen.** Der Marketplace ist die Bezugsquelle des Plugins; über ihn kommen auch Aktualisierungen.

   * [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours) öffnen.
   * Oben rechts **+ Hinzufügen** > **Marketplace hinzufügen** > **Aus einem Repository hinzufügen** wählen.
   * Im Feld **URL** `agent-services-at/plugins` eingeben und **Synchronisieren** wählen.

   Klappt nicht? → [Marketplace oder Plugin-Installation fehlgeschlagen](#marketplace-oder-plugin-installation-fehlgeschlagen)

2. **Plugin hinzufügen.**

   * Claude bietet nach dem Synchronisieren das Plugin **EmpCo-UWG Monitor** an: **Hinzufügen** wählen.
   * Erscheint es nicht, im Reiter **Entdecken** nach „EmpCo“ suchen.
   * Claude öffnet danach die Seite des Plugins.

   Klappt nicht? → [Claude: Plugin nicht auffindbar](#claude-plugin-nicht-auffindbar)

3. **Mit dem Zugangscode verbinden.** Erst diese Anmeldung schaltet die Prüfregeln frei.

   * Auf der Seite des Plugins den Reiter **Konnektoren** öffnen und beim Konnektor `empco-uwg-monitor` **Verbinden** wählen.
   * Die Dialoge zum benutzerdefinierten Konnektor mit den Voreinstellungen bestätigen und erneut **Verbinden** wählen.
   * Auf der Anmeldeseite [https://claims.agent-services.at](https://claims.agent-services.at) den **Zugangscode** eingeben und bestätigen. Die Aktivierung kann einen Moment dauern.
   * Erledigt, sobald beim Konnektor **Verbunden** steht.
   * Empfohlen: den Konnektor anklicken und unter **Tool-Berechtigungen** bei „Verarbeitungsschritt abrufen“ **Immer erlauben** wählen. Dann fragt Claude nicht bei jeder Prüfung nach.

   Klappt nicht? → [Verbindung fehlt oder Sitzung abgelaufen](#verbindung-fehlt-oder-sitzung-abgelaufen)

4. **Erste Prüfung starten.**

   * Oben auf der Seite des Plugins **Ausprobieren** wählen oder eine Unterhaltung beginnen.
   * Diesen einfachen Auftrag eingeben:

     ```text
     /report-claim-risks Prüfe: „Nur heute 30 % günstiger."
     ```

   * Fragt Claude um Erlaubnis für „Verarbeitungsschritt abrufen“, **Immer erlauben** wählen. Bei einer Website fragt Claude außerdem, ob es Seiten abrufen darf: **Alles für diese Website erlauben** oder **Einmal erlauben** wählen.
   * **Fertig**, wenn der Monitor die riskanten Aussagen mit Risikostufe und Formulierungsvorschlag auflistet.

   [**Weitere Beispiele ansehen**](https://claims.agent-services.at/verwendung#text-dokument-oder-website-prufen)

   Klappt nicht? → [Befehl im Chat nicht verfügbar](#befehl-im-chat-nicht-verfugbar)

Der vollständige Ablauf ist in Claude im Browser und in der Desktop-App getestet. In Claude Code erscheinen Skill und Konnektor ebenfalls; eine vollständige Prüfung ist dort nicht getestet.

### Aktualisieren

Aktualisierungen übernimmt Claude selbst (**Automatisch synchronisieren** ist voreingestellt). Für eine sofortige Aktualisierung:

1. [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours) öffnen, **+ Hinzufügen** > **Marketplaces verwalten** wählen.
2. Beim Marketplace `agent-services` im Menü (drei Punkte) **Nach Updates suchen** wählen.
3. Eine Unterhaltung beginnen. Die laufende Version nennt die Diagnose (`/diagnose-monitor-plugin`); weicht sie von der Version auf der Plugin-Seite ab, kurz warten und eine weitere Unterhaltung beginnen.

Meldungen bei der Aktualisierung erklärt [Aktualisierung in Claude: Meldungen](#aktualisierung-in-claude-meldungen).

### Verbindung neu anmelden

Wenn der Monitor meldet, dass die Verbindung zum Regelserver fehlt, oder der Konnektor nicht **Verbunden** anzeigt:

1. [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours) öffnen und das Plugin `EmpCo-UWG Monitor` öffnen.
2. Auf dem Reiter **Konnektoren** des Plugins (nicht dem allgemeinen Reiter „Konnektoren“ der Anpassungen-Seite) beim Eintrag `empco-uwg-monitor` erneut **Verbinden** wählen.
3. Auf der Anmeldeseite [https://claims.agent-services.at](https://claims.agent-services.at) den Zugangscode erneut eingeben und bestätigen. Die Aktivierung kann einen Moment dauern.
4. Sobald **Verbunden** steht, eine Unterhaltung beginnen und die Anfrage erneut stellen.

## ChatGPT

Das Plugin läuft in der **ChatGPT-Desktop-App** im Modus **Work**. Im Browser (chatgpt.com) und im Standard-Chat steht die Verbindung des Plugins nicht zur Verfügung.

### Installation

1. **Desktop-App installieren und Plugins einschalten.**

   * [ChatGPT für Desktop herunterladen](https://chatgpt.com/download), installieren und anmelden.
   * **Einstellungen > Allgemein** öffnen und **Plugins** einschalten.

   Klappt nicht? → [ChatGPT: Plugins-Schalter fehlt](#chatgpt-plugins-schalter-fehlt)

2. **Marketplace hinzufügen.** Der Marketplace ist die Bezugsquelle des Plugins; über ihn kommen auch Aktualisierungen.

   * **Einstellungen > Plugins** öffnen.
   * Oben rechts **Hinzufügen > Marketplace hinzufügen** wählen, `agent-services-at/plugins` eingeben und bestätigen.
   * Erledigt, sobald im Reiter **Marketplace** der Eintrag `agent-services` erscheint.

   Klappt nicht? → [macOS: Marketplace-Fehler in ChatGPT](#macos-marketplace-fehler-in-chatgpt)

3. **Plugin hinzufügen und mit dem Zugangscode verbinden.**

   * **Anpassen > Plugins** öffnen, Reiter **Persönlich**.
   * Unter dem Namen des Marketplaces beim Plugin `EmpCo-UWG Monitor` auf **+** klicken.
   * ChatGPT leitet zur Anmeldung weiter: den **Zugangscode** eingeben und bestätigen.

   Klappt nicht? → [ChatGPT: Plugins-Schalter fehlt](#chatgpt-plugins-schalter-fehlt) oder [Verbindung fehlt oder Sitzung abgelaufen](#verbindung-fehlt-oder-sitzung-abgelaufen)

4. **Erste Prüfung starten.**

   * In der Desktop-App den Modus **Work** wählen und einen Chat öffnen.
   * Diesen einfachen Auftrag eingeben:

     ```text
     /report-claim-risks Prüfe: „Nur heute 30 % günstiger."
     ```

   * **Fertig**, wenn der Monitor die riskanten Aussagen mit Risikostufe und Formulierungsvorschlag auflistet.

   [**Weitere Beispiele ansehen**](https://claims.agent-services.at/verwendung#text-dokument-oder-website-prufen)

   Klappt nicht? → [Befehl im Chat nicht verfügbar](#befehl-im-chat-nicht-verfugbar)

### Aktualisieren

1. **Einstellungen > Plugins** öffnen, Reiter **Marketplace**.
2. Beim Marketplace `agent-services` auf **Upgrade** klicken.
3. Einen Chat im Modus **Work** öffnen.

### Verbindung neu anmelden

Wenn der Monitor meldet, dass die Verbindung zum Regelserver fehlt:

1. **Einstellungen > Plugins** öffnen, Reiter **MCPs**.
2. Unter „From plugins“ beim Eintrag `empco-uwg-monitor` auf **Authenticate** klicken.
3. Im geöffneten Browserfenster den Zugangscode eingeben und bestätigen.
4. Danach einen Chat öffnen und die Anfrage erneut stellen.

## Wenn es nicht funktioniert

Die meisten Probleme lösen die Schritte unten. Hilft keiner davon, führen Sie die [Diagnose](#diagnose-bericht-an-den-support) aus und senden ihren Bericht an den [Support](https://claims.agent-services.at/support). **Wenn Sie das Plugin nicht ausführen können**, kopieren Sie den [Diagnosetext](https://claims.agent-services.at/docs/diagnose#text-zum-einfugen) und senden ihn im betroffenen Chat als Nachricht; die Anwendung erstellt damit denselben Bericht. Die Oberflächen von Claude und ChatGPT ändern sich laufend; weicht eine Bezeichnung ab, hilft meist die sinngemäß passende Schaltfläche.

### Installation

#### ChatGPT: Plugins-Schalter fehlt

**Symptom:** Der Bereich **Plugins** fehlt in den Einstellungen, der Schalter lässt sich nicht einschalten, oder das Plugin erscheint nicht unter **Anpassen > Plugins**.

1. Prüfen, dass die **Desktop-App** verwendet wird; im Browser (chatgpt.com) steht die Verbindung des Plugins nicht zur Verfügung. [ChatGPT für Desktop herunterladen](https://chatgpt.com/download).
2. Die Desktop-App auf die neueste Version aktualisieren.
3. Unter **Einstellungen > Allgemein** den Schalter **Plugins** einschalten.
4. Fehlt der Bereich auch danach, erlaubt Ihr Tarif oder Ihre Organisation keine Plugins. Die Freigabe erteilt der Anbieter beziehungsweise die Administration Ihrer Organisation.

#### macOS: Marketplace-Fehler in ChatGPT

**Symptom:** Beim Hinzufügen des Marketplaces in der macOS-App erscheint ein Fehler oder nichts passiert.

1. Die macOS-App benötigt für das Hinzufügen eines Marketplaces die **Xcode Command Line Tools**. Installationsanleitung von Apple: [Installing the Command Line Tools](https://developer.apple.com/documentation/xcode/installing-the-command-line-tools/).
2. Die ChatGPT-Desktop-App danach neu starten und den Marketplace erneut hinzufügen.
3. Alternativ das Plugin ohne Marketplace installieren: [Plugin-Installation per Zip-Datei](#plugin-installation-per-zip-datei).

#### Claude: Plugin nicht auffindbar

**Symptom:** Nach dem Synchronisieren bietet Claude das Plugin nicht an.

1. Im Reiter **Entdecken** nach „EmpCo“ suchen.
2. Prüfen, dass der Marketplace `agent-services` unter **+ Hinzufügen** > **Marketplaces verwalten** steht, und dort **Nach Updates suchen** wählen.
3. Fehlt der Marketplace, ihn mit der Schreibweise `agent-services-at/plugins` erneut hinzufügen (Schritt 1 der [Installation in Claude](#installation-claude)).

#### Marketplace oder Plugin-Installation fehlgeschlagen

**Symptom:** Der Marketplace lässt sich nicht hinzufügen oder das Plugin nicht installieren.

1. Die Schreibweise `agent-services-at/plugins` prüfen.
2. Die Anwendung auf die neueste Version aktualisieren.
3. Als Rückfall die Zip-Datei verwenden: [Plugin-Installation per Zip-Datei](#plugin-installation-per-zip-datei). Bei einem Fehler zur Zip-Struktur die Datei erneut vom Server laden, statt sie zu bearbeiten.

#### Befehle doppelt oder verwechselt

**Symptom:** Befehle des Plugins erscheinen doppelt oder werden verwechselt.

In Claude ist vermutlich zusätzlich eine per Zip-Datei installierte Fassung mit demselben Namen vorhanden. Diese Fassung unter [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours) über **Entfernen** löschen und das Plugin nur über den Marketplace verwenden.

#### Plugin-Installation per Zip-Datei

Ist der Marketplace nicht erreichbar, lässt sich dasselbe Paket als Zip-Datei installieren. Aktualisierungen kommen auf diesem Weg nicht automatisch; Sie installieren sie von Hand.

1. **Datei herunterladen.**

   * [`empco-uwg-monitor-plugin.zip`](https://claims.agent-services.at/downloads/empco-uwg-monitor-plugin.zip) herunterladen und nicht entpacken.
   * Liegt danach keine `.zip`-Datei im Ordner **Downloads**, hat der Browser sie selbst entpackt und gelöscht (zum Beispiel Safari): Stattdessen [`empco-uwg-monitor-plugin.zip.plugin`](https://claims.agent-services.at/downloads/empco-uwg-monitor-plugin.zip.plugin) herunterladen und in `empco-uwg-monitor-plugin.zip` umbenennen.

2. **Hochladen.**

   - **Claude:**
     * [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours) öffnen.
     * Oben rechts **+ Hinzufügen** > **Plugin hochladen** wählen.
     * Die Zip-Datei auswählen.
     * Den Konnektor wie in [Schritt 3 der Installation in Claude](#installation-claude) verbinden.
     * **Ausprobieren** wählen.
   - **ChatGPT:**
     * In der Desktop-App oder im Browser (chatgpt.com) **Plugins** > **Hinzufügen** > **Plugin hochladen** wählen.
     * Die Zip-Datei auswählen.
     * Die Anmeldung wie in [Schritt 3 der Installation in ChatGPT](#installation-chatgpt) abschließen.

**Neue Fassung installieren:**

- **Claude:** Ein per Zip-Datei installiertes Plugin lässt sich nicht zuverlässig überschreiben. Das Plugin zuerst unter [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours) über **Entfernen** löschen und die heruntergeladene Zip-Datei hochladen. Erscheint die installierte Fassung nicht sofort, kann sie verzögert sein; nach einer Stunde erneut prüfen.
- **ChatGPT:** Ein hochgeladenes Plugin lässt sich in ChatGPT weder über die Oberfläche aktualisieren noch löschen; das ist nur mit einem Skript möglich. Für ChatGPT ist deshalb der Marketplace der empfohlene Weg.

### Verbindung und Anmeldung

#### Verbindung fehlt oder Sitzung abgelaufen

**Symptom:** Der Monitor meldet, dass die Verbindung zum Regelserver fehlt, der Konnektor zeigt nicht **Verbunden**, oder die Anmeldung ist abgelaufen.

Die Verbindung aktualisieren: [in Claude](#verbindung-neu-anmelden-claude) oder [in ChatGPT](#verbindung-neu-anmelden-chatgpt) (dort über **Authenticate**). Danach eine Unterhaltung beginnen.

#### Zugangscode gesperrt oder abgelaufen

**Symptom:** Die Anmeldeseite meldet, dass der Zugangscode gesperrt oder abgelaufen ist.

Eine erneute Anmeldung mit demselben Code hilft nicht. Die [Diagnose](#diagnose-bericht-an-den-support) ausführen, den Support kontaktieren, ihren Bericht beifügen und die angezeigte Meldung nennen.

#### Anmeldung nicht abschließbar

**Symptom:** Die Anmeldung lässt sich nicht abschließen, oder der Monitor meldet auch nach der Anmeldung, dass die Verbindung fehlt.

Die [Diagnose](#diagnose-bericht-an-den-support) ausführen. Den Support kontaktieren und ihren Bericht beifügen. Der Monitor nennt dazu die im Plugin hinterlegte Supportadresse.

### Prüfung und Aktualisierung

#### Befehl im Chat nicht verfügbar

**Symptom:** Nach der Installation erscheint `/report-claim-risks` im Chat nicht, oder der Monitor reagiert nicht auf den Befehl.

1. Den empfohlenen Modus verwenden: in Claude eine Unterhaltung beginnen, in ChatGPT den Modus **Work** der Desktop-App.
2. Eine Sitzung beziehungsweise einen Chat öffnen.
3. Prüfen, dass das Plugin installiert ist und beim Konnektor **Verbunden** steht ([Claude](#installation-claude), [ChatGPT](#installation-chatgpt)).
4. Hilft das nicht, können Sie das Plugin nicht ausführen. Den [Diagnosetext](https://claims.agent-services.at/docs/diagnose#text-zum-einfugen) kopieren, im selben Chat als Nachricht senden und den Bericht an den [Support](https://claims.agent-services.at/support) schicken.

#### Aktualisierung in Claude: Meldungen

- Der Hinweis „Ausführbare Dateien oder Einstellungen können von der Version abweichen, die du vor dieser Synchronisierung verwendet hast“ erscheint bei jeder neuen Version und ist keine Fehlermeldung.
- Der Marketplace gehört zum Claude-Konto: Wurde er auf claude.ai hinzugefügt, fehlt er in der Desktop-App unter **Marketplaces verwalten** möglicherweise, und **Nach Updates suchen** meldet dort „Konnte nicht nach Updates suchen“. Dann die Aktualisierung auf claude.ai im Browser auslösen.

#### Diagnose-Bericht an den Support

Die Diagnose prüft Verbindung, Versionen und Umgebung und erstellt daraus einen Bericht. Er enthält nur technische Angaben, nie geprüfte Texte oder Ergebnisse. Legen Sie ihn jeder Supportanfrage bei.

1. Im Chat dieses Schema eingeben (weitere Hinweise: [Den passenden Skill starten](https://claims.agent-services.at/verwendung#den-passenden-skill-starten)):

   ```text
   /diagnose-monitor-plugin [optional: version | technik | voll]
   ```

   **Wenn Sie das Plugin nicht ausführen können**, weil der Befehl fehlt oder das Plugin nicht reagiert: den [Diagnosetext](https://claims.agent-services.at/docs/diagnose#text-zum-einfugen) kopieren und im selben Chat als Nachricht senden. Die Anwendung erstellt dann denselben Bericht.

2. Die eckige Klammer weglassen oder einen Zusatz anhängen:
   - `version`: nur Versionen und einfache Fähigkeitschecks,
   - `technik`: ergänzt technische Details zu einem vorhandenen Prüflauf,
   - `voll`: zusätzlich Werkzeugliste und lokale Umgebungsangaben.
   Enthält das Gespräch bereits eine Prüfung, wertet der Aufruf ohne Zusatz deren Ablauf mit aus.
3. Den Bericht (der Kasten mit dem Text) kopieren und an den Support senden.

## Unterstützte Anwendungen

Das Plugin folgt der offenen [Agent Plugins Spezifikation](https://agent-plugins.org/) und läuft in jeder Anwendung, die sie unterstützt. **Getestet und empfohlen** ist es mit:

| Anwendung           | Empfohlener Modus | Hinweis                                                                              |
| ------------------- | ----------------- | ------------------------------------------------------------------------------------ |
| [Claude](#claude)   | Claude            | Browser (claude.ai) und Desktop-App; Claude Code ist nicht vollständig getestet      |
| [ChatGPT](#chatgpt) | Work              | nur Desktop-App; im Browser (chatgpt.com) steht die Verbindung des Plugins nicht zur Verfügung |

Welche Tarife Plugins unterstützen, legt der jeweilige Anbieter fest; empfohlen wird ein Tarif mit ausreichender Kapazität. Andere Anwendungen sind nicht getestet; die Nutzung erfolgt auf eigene Verantwortung.

## Einrichtung für Organisationen ohne Einzelanmeldung

*Für die IT-Administration. Einzelpersonen melden sich wie oben beschrieben an.*

Organisationen können das Plugin mit einem **Organisationstoken** für alle Arbeitsplätze anbinden. Dann ist keine Anmeldung der einzelnen Personen nötig. Der Weg hängt von der Anwendung ab:

- **Claude Code:** Das Plugin liest den Token aus der Umgebungsvariable `EMPCO_MONITOR_TOKEN` und sendet ihn bei jeder Verbindung zum Server. Ohne Variable meldet sich jede Person wie oben beschrieben einzeln an.
- **Codex:** Das Plugin selbst darf in den Verbindungs-Headern keine Variablen tragen (so legt es die Agent-Plugins-Spezifikation fest). Die IT ergänzt deshalb in der Codex-Konfiguration einen Eintrag für den Server des Plugins, der den Token aus einer Umgebungsvariable liest.
- **Claude (Browser und Desktop-App) und ChatGPT:** für diesen Weg nicht geprüft; dort meldet sich jede Person wie oben beschrieben einzeln an.

**Einrichten**

1. Den Organisationstoken beim Support anfordern: [https://claims.agent-services.at/support](https://claims.agent-services.at/support).
2. Die Umgebungsvariable `EMPCO_MONITOR_TOKEN` mit dem Token als Benutzer- oder Systemvariable auf den Arbeitsplätzen setzen, etwa über die Geräteverwaltung (Jamf, Intune, Gruppenrichtlinie) unter macOS, Windows oder Linux.
3. Nur für Codex: In der Konfigurationsdatei `config.toml` von Codex diesen Eintrag ergänzen. Er trägt denselben Namen wie das Plugin, und Codex führt ihn mit dem Server des Plugins zusammen:

   ```toml
   [mcp_servers.empco-uwg-monitor]
   url = "https://claims.agent-services.at/v1/mcp"
   env_http_headers = { "X-Empco-Token" = "EMPCO_MONITOR_TOKEN" }
   ```

4. Die Anwendung nach dem Setzen vollständig beenden und wieder öffnen, damit sie die Variable liest.
5. Das Plugin wie oben installieren. Beim Verbinden des Konnektors ist keine Anmeldung nötig. Zur Prüfung `/diagnose-monitor-plugin` starten: Die Diagnose zeigt die Verbindung zum Regelserver.

Fragt der Konnektor trotz gesetzter Variable nach einer Anmeldung, ist die Variable in der Anwendung nicht angekommen: Anwendung vollständig beenden und wieder öffnen und den Namen der Variable prüfen; bei Codex zusätzlich den Eintrag in `config.toml`. Sonst den Support kontaktieren.

**Rotation und Rückruf:** Bei Verlust oder Wechsel stellt der Support einen Ersatz-Token aus und sperrt den abgelösten Token. Danach die Variable auf allen Arbeitsplätzen ersetzen und die Anwendung vollständig beenden und wieder öffnen.

**Vertraulichkeit:** Der Token gilt für die ganze Organisation. Nicht in Chats, Tickets oder Repositories ablegen und einen Verlust sofort melden. Die Variable ist für Programme auf dem Arbeitsplatz lesbar, auch für Werkzeuge, die die Anwendung dem Assistenten bereitstellt, etwa eine Shell; ein präparierter Text in einem geprüften Dokument könnte versuchen, sie auszugeben. Der Support stellt dann einen neuen Token aus.

**Geprüfter Stand (7. Oktober 2026):** Mit Claude Code 2.1.272 verbindet sich das Plugin mit gesetzter Variable ohne Anmeldung und fragt ohne Variable nach der Anmeldung. Mit der Codex-CLI 0.156.1 funktioniert der Weg mit dem Eintrag in `config.toml`; das Plugin allein sendet den Header dort nicht. Claude (Browser und Desktop-App) und die ChatGPT-Desktop-App sind für diesen Weg nicht geprüft.

## Technischer Hintergrund

Das Plugin ist ein einziges Paket für Claude, ChatGPT und Codex. Es enthält die Verbindung zum EmpCo-UWG Wissensdatenbank-Server (Model Context Protocol, MCP), über die der Monitor die Prüfregeln abruft, und die Skills, die festlegen, wann und wie er sie abruft. Ohne angemeldete Verbindung steht das Werkzeug `fetch_claims_monitor_step` nicht zur Verfügung und keine Prüfung ist möglich.

- **Öffentliche Dokumentation der Schnittstelle:** [https://claims.agent-services.at/docs/mcp](https://claims.agent-services.at/docs/mcp)
- **Stand dieser Anleitung:** 3. Oktober 2026, geprüft mit Claude (Browser und Desktop-App) und der ChatGPT-Desktop-App.
