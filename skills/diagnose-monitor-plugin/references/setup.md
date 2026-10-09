---
license: Copyright (c) 2026 Niederschick OG & Tobias Zucali. All rights reserved. Use restricted to customers with a valid agreement with Niederschick OG.
build: v1.3.0
---

# Einrichtung des Plugins

Der EmpCo-UWG Monitor wird als **Plugin** „EmpCo-UWG Monitor" installiert. Es ist ein einziges Paket und enthält beides, was nötig ist:

1. die Verbindung zum EmpCo-UWG Wissensdatenbank-Server, über die die Prüfregeln abgerufen werden, und
2. den **Skill**, der festlegt, wie und wann die Regeln abgerufen werden.

Ohne angemeldete Verbindung steht das Tool `fetch_claims_monitor_step` nicht zur Verfügung und keine Prüfung ist möglich.

**Vorab bereithalten:**

- den **Zugangscode** (Lizenz), den Sie per E-Mail erhalten haben; er wird bei der Anmeldung der Verbindung eingegeben, nicht im Chat,
- die **Desktop-App** von Claude oder ChatGPT (Download-Links stehen in der jeweiligen Installation).

## Unterstützte Anwendungen

Das Plugin folgt der offenen [Agent Plugins Spezifikation](https://agent-plugins.org/) und besteht aus einem Skill und einer MCP-Verbindung (Model Context Protocol). Es läuft in jeder Anwendung, die diese Spezifikation unterstützt; die Zahl der Anwendungen wächst. **Getestet und empfohlen** ist es mit:

| Anwendung | Empfohlener Modus | Hinweis |
| --- | --- | --- |
| [Claude](#claude) | Cowork | Browser (claude.ai) und Desktop-App; Chat und Code sind nicht vollständig getestet |
| [ChatGPT](#chatgpt) | Work | nur Desktop-App; im Browser (chatgpt.com) steht die Verbindung des Plugins nicht zur Verfügung |

Empfohlen wird ein Tarif der Anwendung (Einzelplatz oder Organisation) mit ausreichender Kapazität; welche Tarife Plugins unterstützen, regelt der jeweilige Anbieter und ändert sich laufend. Andere Anwendungen sind nicht getestet; die Nutzung erfolgt auf eigene Verantwortung. Die Oberflächen der Anwendungen ändern sich laufend; weichen Bezeichnungen oder Schritte ab, helfen die Hinweise unter [Wenn es nicht funktioniert](#wenn-es-nicht-funktioniert).

## Claude

### Installation

Das Plugin wird über einen **Marketplace** installiert, ein öffentliches GitHub-Repository mit dem Plugin: `agent-services-at/plugins`. Der Marketplace heißt `agent-services`, das Plugin darin `empco-uwg-monitor`. Darüber lässt sich das Plugin später aktualisieren und entfernen.

Alle Schritte laufen auf der Seite [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours); sie ist in der Desktop-App und im Browser (claude.ai) dieselbe. Die Claude-Desktop-App ist nicht nötig; für die tägliche Arbeit wird sie empfohlen ([Claude für Desktop herunterladen](https://claude.com/de/download)).

1. **Marketplace hinzufügen.**

   * [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours) öffnen.
   * Oben rechts **+ Hinzufügen** wählen.
   * **Marketplace hinzufügen** wählen.
   * **Aus einem Repository hinzufügen** wählen.
   * Im Feld **URL** `agent-services-at/plugins` eingeben.
   * **Synchronisieren** wählen.

   Klappt nicht? → [Marketplace oder Plugin-Installation fehlgeschlagen](#marketplace-oder-plugin-installation-fehlgeschlagen)

2. **Plugin hinzufügen.**

   * Nach dem Synchronisieren bietet Claude das Plugin **EmpCo-UWG Monitor** an: **Hinzufügen** wählen.
   * Erscheint es nicht, den Reiter **Entdecken** öffnen und nach „EmpCo“ suchen.
   * Nach dem Hinzufügen öffnet Claude die Seite des Plugins.

   Klappt nicht? → [Claude: Plugin nicht auffindbar](#claude-plugin-nicht-auffindbar)

3. **Konnektor verbinden.** Die Installation allein genügt nicht; erst die Anmeldung schaltet die Prüfregeln frei.

   * Auf der Seite des Plugins den Reiter **Konnektoren** öffnen.
   * Beim Konnektor `empco-uwg-monitor` **Verbinden** wählen.
   * Die Dialoge zum benutzerdefinierten Konnektor bestätigen; die Voreinstellungen passen.
   * Erneut **Verbinden** wählen. Claude öffnet im Browser die Anmeldeseite auf [https://claims.agent-services.at](https://claims.agent-services.at).
   * Den **Zugangscode** aus der E-Mail eingeben und bestätigen. Die Aktivierung kann einen Moment dauern.
   * Prüfen, dass beim Konnektor **Verbunden** steht.
   * (Optional) Den Konnektor `empco-uwg-monitor` anklicken und unter **Tool-Berechtigungen** bei „Verarbeitungsschritt abrufen“ **Immer erlauben** wählen.

   Klappt nicht? → [Verbindung fehlt oder Sitzung abgelaufen](#verbindung-fehlt-oder-sitzung-abgelaufen)

4. **In Cowork ausprobieren.** Oben auf der Seite des Plugins **In Cowork ausprobieren** wählen und einen Prüfauftrag stellen; Beispiele und Ablauf stehen unter [Erste Prüfung](#erste-prufung).

### Verwendung

**Empfohlen wird Cowork**; dort ist der gesamte Ablauf bis zur Prüfung getestet. Andere Modi können das Plugin unter Umständen ebenfalls nutzen, sind aber nicht vollständig getestet; die Nutzung erfolgt auf eigene Verantwortung. Im Chat sind Skill und (nach der Anmeldung) Konnektor sichtbar, ein vollständiger Prüfauftrag ist dort nicht getestet. Die Anbieter erweitern die Unterstützung des Plugin-Formats laufend, die Lage in einzelnen Modi kann sich deshalb schnell ändern.

1. Eine neue Cowork-Sitzung starten.
2. Einen Prüfauftrag stellen, zum Beispiel: `Prüfe diesen Text auf Greenwashing-Risiken: Unsere Verpackung ist 100 % umweltfreundlich.`
3. Fragt Claude um Erlaubnis für „Verarbeitungsschritt abrufen“, **Immer erlauben** wählen (siehe Installation, Schritt 3).
4. Soll eine Website geprüft werden, fragt Claude außerdem, ob es Seiten dieser Website abrufen darf: **Alles für diese Website erlauben** oder **Einmal erlauben** wählen, sonst kann die Seite nicht geprüft werden.

Weitere Beispiele und den Ablauf einer Prüfung zeigt [Erste Prüfung](#erste-prufung).

### Aktualisieren

Das Plugin wird über den Marketplace aktualisiert; **Automatisch synchronisieren** ist voreingestellt und übernimmt neue Versionen selbst. Für eine sofortige Aktualisierung:

1. [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours) öffnen, **+ Hinzufügen** > **Marketplaces verwalten** wählen.
2. Beim Marketplace `agent-services` im Menü (drei Punkte) **Nach Updates suchen** wählen.
3. Die laufende Version nennt die Diagnose (`/diagnose-monitor-plugin`); die Plugin-Version auf der Seite des Plugins zeigt den zuletzt synchronisierten Stand. Weichen beide ab, die Aktualisierung abwarten und eine neue Cowork-Sitzung starten.

Der Konnektor bleibt in der Regel verbunden; andernfalls [neu anmelden](#verbindung-neu-anmelden-claude). Meldungen und Abweichungen bei der Aktualisierung: [Aktualisierung in Claude: Meldungen](#aktualisierung-in-claude-meldungen).

### Verbindung neu anmelden

Wenn `fetch_claims_monitor_step` fehlt oder der Konnektor nicht **Verbunden** anzeigt:

1. [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours) öffnen.
2. Das Plugin `EmpCo-UWG Monitor` öffnen.
3. Auf dem Reiter **Konnektoren** des Plugins (nicht dem allgemeinen Reiter „Konnektoren“ der Anpassungen-Seite) beim Eintrag `empco-uwg-monitor` erneut **Verbinden** wählen.
4. Auf der Anmeldeseite [https://claims.agent-services.at](https://claims.agent-services.at) den Zugangscode erneut eingeben und bestätigen. Die Aktivierung kann einen Moment dauern.
5. Sobald **Verbunden** steht, eine neue Cowork-Sitzung starten und die Anfrage erneut stellen.

## ChatGPT

### Installation

Das Plugin gilt für die ChatGPT-Desktop-App und wird über den **Marketplace** `agent-services-at/plugins` installiert (empfohlen; darüber lässt sich das Plugin aktualisieren und entfernen). Im Browser (chatgpt.com) steht die Verbindung des Plugins nicht zur Verfügung.

1. **ChatGPT-Desktop-App installieren und Plugins einschalten.**

   * [ChatGPT für Desktop herunterladen](https://chatgpt.com/download), installieren und anmelden.
   * In der Desktop-App **Einstellungen > Allgemein** öffnen.
   * **Plugins** einschalten. Dieser Schalter erlaubt ChatGPT, installierte Plugins zu verwenden.

   Klappt nicht? → [ChatGPT: Plugins-Schalter fehlt](#chatgpt-plugins-schalter-fehlt)

2. **Marketplace hinzufügen.**

   * **Einstellungen > Plugins** öffnen.
   * Oben rechts **Hinzufügen > Marketplace hinzufügen** wählen.
   * `agent-services-at/plugins` eingeben und bestätigen.
   * Prüfen, dass der Marketplace als `agent-services` im Reiter **Marketplace** erscheint.

   Klappt nicht? → [macOS: Marketplace-Fehler in ChatGPT](#macos-marketplace-fehler-in-chatgpt)

3. **Plugin hinzufügen.**

   * **Anpassen > Plugins** öffnen.
   * Den Reiter **Persönlich** öffnen.
   * Unter dem Namen des Marketplaces steht das Plugin `EmpCo-UWG Monitor`; auf **+** klicken.
   * ChatGPT leitet zur Anmeldung weiter: den **Zugangscode** aus der E-Mail eingeben und bestätigen.

   Klappt nicht? → [ChatGPT: Plugins-Schalter fehlt](#chatgpt-plugins-schalter-fehlt) oder [Verbindung fehlt oder Sitzung abgelaufen](#verbindung-fehlt-oder-sitzung-abgelaufen)

### Verwendung

1. In der Desktop-App den Modus **Work** wählen (empfohlen; im Standard-Chat sind Skill und Verbindung des Plugins nicht verfügbar, das kann sich mit der Unterstützung durch ChatGPT ändern).
2. Einen neuen Chat starten.
3. Einen Prüfauftrag stellen, zum Beispiel: `Prüfe diesen Text auf Greenwashing-Risiken: Unsere Verpackung ist 100 % umweltfreundlich.`

Weitere Beispiele und den Ablauf einer Prüfung zeigt [Erste Prüfung](#erste-prufung).

### Aktualisieren

1. In der Desktop-App **Einstellungen > Plugins** öffnen, Reiter **Marketplace**.
2. Beim Marketplace `agent-services` auf **Upgrade** klicken.
3. Einen neuen Chat im Modus **Work** starten.

### Verbindung neu anmelden

Wenn `fetch_claims_monitor_step` fehlt:

1. **Einstellungen > Plugins** öffnen, Reiter **MCPs**.
2. Unter „From plugins" beim Eintrag `empco-uwg-monitor` auf **Authenticate** klicken.
3. Den Hinweisen im geöffneten Browserfenster folgen.
4. Nach erfolgreicher Anmeldung einen neuen Chat starten und die Anfrage erneut stellen.

## Einrichtung für Organisationen ohne Einzelanmeldung

*Nur für die IT-Administration; Einzelpersonen melden sich wie oben beschrieben an.*

Organisationen können das Plugin mit einem **Organisationstoken** für alle Arbeitsplätze anbinden. Dann ist keine Anmeldung der einzelnen Personen nötig. Der Weg hängt von der Anwendung ab:

- **Claude Code:** Das Plugin liest den Token aus der Umgebungsvariable `EMPCO_MONITOR_TOKEN` und sendet ihn bei jeder Verbindung zum Server. Ohne Variable meldet sich jede Person wie oben beschrieben einzeln an.
- **Codex:** Das Plugin selbst darf in den Verbindungs-Headern keine Variablen tragen (so legt es die Agent-Plugins-Spezifikation fest). Die IT ergänzt deshalb in der Codex-Konfiguration einen Eintrag für den Server des Plugins, der den Token aus einer Umgebungsvariable liest.
- **Claude (Browser, Desktop-App, Cowork) und ChatGPT:** für diesen Weg nicht geprüft; dort meldet sich jede Person wie oben beschrieben einzeln an.

**Einrichten**

1. Den Organisationstoken beim Support anfordern: [https://claims.agent-services.at/support](https://claims.agent-services.at/support).
2. Die Umgebungsvariable `EMPCO_MONITOR_TOKEN` mit dem Token als Benutzer- oder Systemvariable auf den Arbeitsplätzen setzen, etwa über die Geräteverwaltung (Jamf, Intune, Gruppenrichtlinie) unter macOS, Windows oder Linux.
3. Nur für Codex: In der Konfigurationsdatei `config.toml` von Codex diesen Eintrag ergänzen. Er trägt denselben Namen wie das Plugin, und Codex führt ihn mit dem Server des Plugins zusammen:

   ```toml
   [mcp_servers.empco-uwg-monitor]
   url = "https://claims.agent-services.at/v1/mcp"
   env_http_headers = { "X-Empco-Token" = "EMPCO_MONITOR_TOKEN" }
   ```

4. Die Anwendung nach dem Setzen vollständig beenden und neu starten, damit sie die Variable liest.
5. Das Plugin wie oben installieren. Beim Verbinden des Konnektors ist keine Anmeldung nötig. Zur Prüfung `/diagnose-monitor-plugin` starten: Die Diagnose zeigt die Verbindung zum Regelserver.

Fragt der Konnektor trotz gesetzter Variable nach einer Anmeldung, ist die Variable in der Anwendung nicht angekommen: Anwendung neu starten und den Namen der Variable prüfen; bei Codex zusätzlich den Eintrag in `config.toml`. Sonst den Support kontaktieren.

**Rotation und Rückruf:** Bei Verlust oder Wechsel stellt der Support einen neuen Token aus und sperrt den alten. Danach die Variable auf allen Arbeitsplätzen ersetzen und die Anwendung neu starten.

**Vertraulichkeit:** Der Token gilt für die ganze Organisation. Nicht in Chats, Tickets oder Repositories ablegen und einen Verlust sofort melden. Die Variable ist für Programme auf dem Arbeitsplatz lesbar, auch für Werkzeuge, die die Anwendung dem Assistenten bereitstellt, etwa eine Shell; ein präparierter Text in einem geprüften Dokument könnte versuchen, sie auszugeben. Der Support stellt dann einen neuen Token aus.

**Geprüfter Stand (7. Oktober 2026):** Mit Claude Code 2.1.272 verbindet sich das Plugin mit gesetzter Variable ohne Anmeldung und fragt ohne Variable nach der Anmeldung. Mit der Codex-CLI 0.156.1 funktioniert der Weg mit dem Eintrag in `config.toml`; das Plugin allein sendet den Header dort nicht. Claude (Browser, Desktop-App, Cowork) und die ChatGPT-Desktop-App sind für diesen Weg nicht geprüft.

## Erste Prüfung

Nach Installation und Anmeldung genügt ein gewöhnlicher Auftrag im Chat, den Aufruf des Plugins übernimmt die Anwendung. Beispiele für Prüfaufträge:

- „Prüfe diesen Werbetext auf Greenwashing-Risiken: Unsere Verpackung ist klimaneutral und 100 % umweltfreundlich.“
- „Prüfe diese drei Aussagen aus unserem Newsletter: [Text einfügen]“
- „Prüfe die Startseite von https://beispiel.at auf Umweltaussagen.“

So kann ein Gespräch verlaufen (gekürzt; der Wortlaut der Antwort variiert):

```text
Du:      Prüfe diesen Werbetext: „Unsere Verpackung ist klimaneutral und
         100 % umweltfreundlich.“

Monitor: [Die Anwendung fragt um Erlaubnis, den Regelserver zu kontaktieren.
         „Immer erlauben“ wählen.]

         Gesamt-Treffer: 2

         1. „klimaneutral“ – Risiko: 🔴 Hoch
            Rechtsgrundlage: EmpCo-Richtlinie Art. 1, UWG-Anhang
            Prüfhinweis: Absolute Klimaaussage ohne Methode, Datenbasis
            und unabhängige Verifikation.
            Formulierungsvorschlag: Konkreten Bezug nennen, z. B. „Die
            Emissionen der Produktion wurden um 60 % reduziert (Quelle: …).“

         2. „100 % umweltfreundlich“ – Risiko: 🔴 Hoch
            Prüfhinweis: Generische Umweltaussage ohne klaren Bezugspunkt.
            …

         Hinweis: automatisierte Ersteinschätzung, keine Rechtsberatung.

Du:      Formuliere die Verpackungsaussage so um, dass sie belegbar ist.
         Wir verwenden 80 % Recyclingkarton (Zertifikat vorhanden).
```

Bei einer Website ohne genannte Unterseite beginnt der Monitor mit der Startseite und nennt weitere Seiten als Vorschlag zur Vertiefung. Die Ergebnisse sind eine Ersteinschätzung und ersetzen keine rechtliche Beratung.

### Skill direkt aufrufen

Meist genügt der Auftrag im Chat; die Anwendung wählt den Skill selbst. Ein Skill lässt sich auch gezielt starten: Der Name des Skills mit vorangestelltem `/` und dahinter der Auftrag. Das funktioniert in Claude, ChatGPT und Codex gleich.¹

```text
/report-green-claims Prüfe: „Unsere Verpackung ist klimaneutral.“
```

Das Plugin bringt zwei Skills mit:

| Skill | Zweck |
| --- | --- |
| `report-green-claims` | Prüfung von Texten und Websites |
| `diagnose-monitor-plugin` | Bericht für den Support bei Problemen |

Ein direkter Aufruf startet den Skill ohne Rückfrage. Die Diagnose erzeugt einen Bericht für den Support ([Wenn es nicht funktioniert](#wenn-es-nicht-funktioniert)).

¹ Je nach Client kann der Aufruf abweichen: Manche Anwendungen bieten nach `/`, `@` oder `$` eine Auswahlliste der Skills an oder verlangen den Plugin-Namen vor dem Skill (`/empco-uwg-monitor:report-green-claims`).

## Wenn es nicht funktioniert

Angaben für eine Supportanfrage und die Kontaktadresse stehen auf der [Support-Seite](https://claims.agent-services.at/support). Jeder Supportanfrage liegt der [Bericht der Diagnose](#diagnose-bericht-an-den-support) bei.

### Installation

#### ChatGPT: Plugins-Schalter fehlt

**Symptom:** Der Bereich **Plugins** fehlt in den Einstellungen, der Schalter lässt sich nicht einschalten, oder das Plugin erscheint nicht unter **Anpassen > Plugins**.

1. Prüfen, dass die **Desktop-App** verwendet wird; im Browser (chatgpt.com) steht die Verbindung des Plugins nicht zur Verfügung. [ChatGPT für Desktop herunterladen](https://chatgpt.com/download).
2. Die Desktop-App auf die neueste Version aktualisieren.
3. Unter **Einstellungen > Allgemein** den Schalter **Plugins** einschalten.
4. Fehlt der Bereich auch danach, gewährt der Tarif oder die Organisation Plugins möglicherweise nicht; die Freigabe regelt der Anbieter beziehungsweise die Administration der Organisation.

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
3. Als Rückfall die Zip-Datei verwenden: [Plugin-Installation per Zip-Datei](#plugin-installation-per-zip-datei). Bei einem Fehler zur Zip-Struktur die Datei erneut vom Server laden statt manuell zu bearbeiten.

#### Befehle doppelt oder verwechselt

**Symptom:** Befehle des Plugins erscheinen doppelt oder werden verwechselt.

In Claude ist vermutlich zusätzlich eine per Zip-Datei installierte Fassung mit demselben Namen vorhanden. Sie unter [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours), über **Entfernen** löschen und das Plugin nur über den Marketplace verwenden.

#### Plugin-Installation per Zip-Datei

Ist der Marketplace nicht erreichbar, lässt sich dasselbe Paket als Zip-Datei installieren. Auf diesem Weg werden Aktualisierungen nicht automatisch eingespielt; neue Versionen müssen von Hand installiert werden.

1. **Datei herunterladen.**

   * [`empco-uwg-monitor-plugin.zip`](https://claims.agent-services.at/downloads/empco-uwg-monitor-plugin.zip) herunterladen und nicht entpacken.
   * Liegt danach keine `.zip`-Datei im Ordner **Downloads**, hat der Browser sie selbst entpackt und gelöscht (zum Beispiel Safari): Stattdessen [`empco-uwg-monitor-plugin.zip.plugin`](https://claims.agent-services.at/downloads/empco-uwg-monitor-plugin.zip.plugin) herunterladen und in `empco-uwg-monitor-plugin.zip` umbenennen.

2. **Hochladen.**

   - **Claude:**
     * [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours) öffnen.
     * Oben rechts **+ Hinzufügen** > **Plugin hochladen** wählen.
     * Die Zip-Datei auswählen.
     * Den Konnektor wie in [Schritt 3 der Installation in Claude](#installation-claude) verbinden.
     * **In Cowork ausprobieren** wählen.
   - **ChatGPT:**
     * In der Desktop-App oder im Browser (chatgpt.com) **Plugins** > **Hinzufügen** > **Plugin hochladen** wählen.
     * Die Zip-Datei auswählen.
     * Die Anmeldung wie in [Schritt 3 der Installation in ChatGPT](#installation-chatgpt) abschließen.

**Neue Fassung installieren:**

- **Claude:** Ein per Zip-Datei installiertes Plugin lässt sich nicht zuverlässig überschreiben. Das Plugin zuerst unter [Anpassungen > Plugins > Meine](https://claude.ai/customize/plugins/yours), über **Entfernen** löschen und die neue Zip-Datei hochladen. Erscheint die neue Fassung nicht sofort, kann sie verzögert sein; nach einer Stunde erneut prüfen.
- **ChatGPT:** Ein hochgeladenes Plugin lässt sich in ChatGPT weder über die Oberfläche aktualisieren noch löschen; das ist nur mit einem Skript möglich. Für ChatGPT ist deshalb der Marketplace der empfohlene Weg.

### Verbindung und Anmeldung

#### Verbindung fehlt oder Sitzung abgelaufen

**Symptom:** `fetch_claims_monitor_step` fehlt, der Konnektor zeigt nicht **Verbunden**, oder die Sitzung ist ungültig.

Einmal in der jeweiligen Anwendung neu anmelden: [Claude](#verbindung-neu-anmelden-claude), [ChatGPT](#verbindung-neu-anmelden-chatgpt) (dort auf **Authenticate**). Ein abgelaufenes OAuth-Token kann dabei erneuert werden; danach einen neuen Chat beziehungsweise eine neue Cowork-Sitzung starten.

#### Zugangscode gesperrt oder abgelaufen

**Symptom:** Die Anmeldeseite meldet, dass der Zugangscode gesperrt oder abgelaufen ist.

Eine erneute Anmeldung mit demselben Code stellt den Zugriff nicht wieder her. Die Diagnose ausführen, den Support kontaktieren, deren Bericht beifügen und die angezeigte Meldung nennen.

#### Anmeldung nicht abschließbar

**Symptom:** Die Anmeldung lässt sich nicht abschließen, oder `fetch_claims_monitor_step` fehlt auch nach der Anmeldung.

Die Diagnose ausführen. Den Support kontaktieren und deren Bericht beifügen. Der Assistent nennt die im Plugin mitgelieferte Supportadresse.

### Prüfung und Aktualisierung

#### Aktualisierung in Claude: Meldungen

- Der Hinweis „Ausführbare Dateien oder Einstellungen können von der Version abweichen, die du vor dieser Synchronisierung verwendet hast“ erscheint bei jeder neuen Version und ist keine Fehlermeldung.
- Der Marketplace gehört zum Claude-Konto: Wurde er auf claude.ai hinzugefügt, fehlt er in der Desktop-App unter **Marketplaces verwalten** möglicherweise, und **Nach Updates suchen** meldet dort „Konnte nicht nach Updates suchen“. Dann die Aktualisierung auf claude.ai im Browser auslösen.

#### Diagnose-Bericht an den Support

Der Diagnose-Skill des Plugins erzeugt einen belegten Bericht mit ausschließlich technischen Angaben zu Umgebung, Verbindung und Versionen; Prüftexte und Analyseergebnisse gehören nie dazu. Jeder Supportanfrage beifügen.

1. Den Skill `/diagnose-monitor-plugin` aufrufen (Hinweise zum Aufruf: [Skill direkt aufrufen](#skill-direkt-aufrufen)); der direkte Aufruf startet ohne Rückfrage.
2. Optional einen Zusatz angeben:
   - `version`: nur Versionen und einfache Fähigkeitschecks,
   - `technik`: ergänzt technische Details zu einem vorhandenen Prüflauf,
   - `voll`: zusätzlich Werkzeugliste und lokale Umgebungsangaben.
   Enthält das Gespräch bereits eine Prüfung, wertet der Aufruf ohne Zusatz deren Ablauf mit aus.
3. Den Bericht (der Kasten mit dem Text) kopieren und an den Support senden.

Wo Skills nicht verfügbar sind, steht derselbe Text auf der Seite [Diagnose zum Einfügen](https://claims.agent-services.at/docs/diagnose) bereit.

### Weitere Informationen

- **Öffentliche Dokumentation der Schnittstelle:** [https://claims.agent-services.at/docs/mcp](https://claims.agent-services.at/docs/mcp)
- **Stand dieser Anleitung:** 3. Oktober 2026, geprüft mit Claude (Browser und Desktop-App) und der ChatGPT-Desktop-App.
