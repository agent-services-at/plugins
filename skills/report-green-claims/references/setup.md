---
license: Copyright (c) 2026 Niederschick OG & Tobias Zucali. All rights reserved. Use restricted to customers with a valid agreement with Niederschick OG.
build: v1.0.0
---

# Einrichtung des Plugins

Der EmpCo-UWG Monitor wird als **Plugin** „EmpCo-UWG Monitor" installiert. Es ist ein einziges Paket und enthält beides, was nötig ist:

1. die Verbindung zum EmpCo-UWG Wissensdatenbank-Server, über die die Prüfregeln abgerufen werden, und
2. den **Skill**, der festlegt, wie und wann die Regeln abgerufen werden.

Ohne angemeldete Verbindung steht das Tool `fetch_claims_monitor_step` nicht zur Verfügung und keine Prüfung ist möglich.

**Voraussetzung:** ein gekaufter Zugangscode (Lizenz). Er wird bei der Anmeldung der Verbindung eingegeben, nicht im Chat.

## Unterstützte Anwendungen

Das Plugin folgt der offenen [Agent Plugins Spezifikation](https://agent-plugins.org/) und besteht aus einem Skill und einer MCP-Verbindung (Model Context Protocol). Es läuft in jeder Anwendung, die diese Spezifikation unterstützt; die Zahl der Anwendungen wächst. **Getestet und empfohlen** ist es mit:

- **Claude** (claude.ai im Browser und Claude-Desktop-App): empfohlen ist der Modus Cowork; Chat und Code sind nicht vollständig getestet.
- **ChatGPT** (Desktop-App, alle Tarife): empfohlen ist der Modus Work; im Browser (chatgpt.com) steht die Verbindung des Plugins nicht zur Verfügung.

Empfohlen wird ein Tarif der Anwendung (Einzelplatz oder Organisation) mit ausreichender Kapazität; welche Tarife Plugins unterstützen, regelt der jeweilige Anbieter und ändert sich laufend. Andere Anwendungen sind nicht getestet; die Nutzung erfolgt auf eigene Verantwortung. [Verwendung in Claude](#verwendung-in-claude) und [Verwendung in ChatGPT](#verwendung-in-chatgpt) nennen den jeweils getesteten Stand.

## Claude

Claude läuft im Browser (claude.ai) und in der Claude-Desktop-App und hat drei Modi: Chat, Cowork und Code.

### Installation in Claude

Das Plugin wird über einen **Marketplace** installiert, ein öffentliches GitHub-Repository mit dem Plugin: `tobias-zucali/EmpCo-UWG-Monitor-Plugin`. Er ist der empfohlene Weg, weil sich das Plugin darüber aktualisieren und entfernen lässt. Ein bereits über Zip-Upload installiertes Plugin mit demselben Namen zuerst entfernen (**Customize > Plugins > Yours**), damit Befehle nicht mit der alten Installation verwechselt werden.

In der Desktop-App und auf claude.ai (deutsche Oberfläche):

1. **Anpassungen > Plugins > Hinzufügen > Marketplace hinzufügen** wählen, dann **Aus einem Repository hinzufügen**. Im Feld **URL** `tobias-zucali/EmpCo-UWG-Monitor-Plugin` eingeben, **Automatisch synchronisieren** eingeschaltet lassen und **Synchronisieren** wählen. Der Warnhinweis zu Plugins aus Marktplätzen gilt für jeden fremden Marketplace; das Plugin dieses Marketplaces stammt vom Anbieter des Monitors.
2. Den Reiter **Entdecken** öffnen, nach dem Plugin suchen (z. B. „EmpCo“) und beim Plugin **Hinzufügen** wählen. Claude öffnet danach die Seite des Plugins.
3. Dort zum Reiter **Konnektoren** wechseln und den Connector `empco-uwg-monitor` verbinden: Claude leitet zur Anmeldung weiter, dort den Zugangscode eingeben und bestätigen. Erst danach steht `fetch_claims_monitor_step` zur Verfügung – die Installation allein reicht nicht.
4. Oben auf der Seite des Plugins **In Cowork ausprobieren** wählen und einen Prüfauftrag stellen.

Ist der Marketplace nicht erreichbar, lässt sich dasselbe Paket als Zip-Datei installieren: [`empco-uwg-monitor-plugin.zip`](https://claims.agent-services.at/downloads/empco-uwg-monitor-plugin.zip) herunterladen und unter **Customize > Plugins > Add > Upload plugin** (deutsche Oberfläche: **Anpassungen > Plugins > Hinzufügen > Plugin hochladen**) auswählen. Danach den Connector wie in Schritt 3 verbinden und **In Cowork ausprobieren** wählen.

### Verwendung in Claude

**Empfohlen wird Cowork**; dort ist der gesamte Ablauf bis zur Prüfung getestet. Andere Modi können das Plugin unter Umständen ebenfalls nutzen, sind aber nicht vollständig getestet; die Nutzung erfolgt auf eigene Verantwortung. Derzeit sind im Chat Skill und (nach der Anmeldung) Connector sichtbar, ein vollständiger Prüfauftrag ist dort nicht getestet. Die Anbieter erweitern die Unterstützung des Plugin-Formats laufend, die Lage in einzelnen Modi kann sich deshalb schnell ändern.

Eine neue Cowork-Sitzung starten und einen Prüfauftrag stellen, z. B. „Prüfe: „Unsere Verpackung ist 100 % umweltfreundlich."" Fragt Claude dabei um Erlaubnis, den Connector zu kontaktieren, **„Immer erlauben"** wählen – sonst erscheint die Abfrage bei jedem einzelnen Regelabruf erneut.

### Aktualisieren in Claude

Mit eingeschaltetem **Automatisch synchronisieren** übernimmt Claude neue Versionen aus dem Marketplace selbst. Für sofortige Aktualisierung unter **Anpassungen > Plugins > Hinzufügen > Marketplaces verwalten** beim Marketplace `tobias-zucali/EmpCo-UWG-Monitor-Plugin` über das Menü (drei Punkte) **Nach Updates suchen** wählen. Der Marketplace gehört zum Claude-Konto: Wurde er auf claude.ai hinzugefügt, fehlt er in der Desktop-App unter **Marketplaces verwalten** möglicherweise, und **Nach Updates suchen** meldet dort „Konnte nicht nach Updates suchen“; dann die Aktualisierung auf claude.ai im Browser auslösen. Der Hinweis „Ausführbare Dateien oder Einstellungen können von der Version abweichen, die du vor dieser Synchronisierung verwendet hast“ erscheint bei jeder neuen Version und ist keine Fehlermeldung. Die Plugin-Version auf der Seite des Plugins zeigt den zuletzt synchronisierten Stand; die tatsächlich laufende Version nennt die Diagnose (`/diagnose-monitor-plugin`). Weicht sie von der Seite des Plugins ab, die Aktualisierung abwarten und eine neue Cowork-Sitzung starten; der Connector bleibt in der Regel verbunden, andernfalls wie unter „Verbindung neu anmelden“ erneut verbinden.

Ein per Zip-Upload installiertes Plugin lässt sich nicht zuverlässig überschreiben: Es zuerst unter **Customize > Plugins**, Reiter **Yours** (deutsche Oberfläche: **Anpassungen > Plugins > Deine**) über **Entfernen** löschen, dann die neue Zip-Datei hochladen. Erscheint die neue Fassung nicht sofort, kann sie verzögert sein; nach einer Stunde erneut prüfen.

### Verbindung in Claude neu anmelden

Wenn `fetch_claims_monitor_step` fehlt: **Customize > Plugins**, Reiter **Yours** (deutsche Oberfläche: **Anpassungen > Plugins > Deine**) → das installierte Plugin `EmpCo-UWG Monitor` öffnen → dort auf dem plugin-eigenen Reiter **Connectors** (nicht der allgemeine „Connectors"-Menüpunkt in der Customize-Navigation) beim Eintrag `empco-uwg-monitor` erneut verbinden und den Hinweisen im geöffneten Browserfenster folgen. Nach erfolgreicher Anmeldung eine neue Cowork-Sitzung starten und die Anfrage erneut stellen.

## ChatGPT

ChatGPT läuft als Desktop-App und im Browser (chatgpt.com, Web-App) und hat drei Modi: Chat, Work und Codex.

### Installation in ChatGPT

Das Plugin gilt für die ChatGPT-Desktop-App, in allen Tarifen einschließlich Free. Es wird über den **Marketplace** `tobias-zucali/EmpCo-UWG-Monitor-Plugin` installiert (empfohlen; darüber lässt sich das Plugin aktualisieren und entfernen).

**Voraussetzung in der Desktop-App:** Unter **Einstellungen > Allgemein** muss **Plugins** („Allow ChatGPT to use installed plugins") eingeschaltet sein. Dieser Schalter erlaubt ChatGPT, installierte Plugins zu verwenden.

1. In der Desktop-App **Einstellungen > Plugins** öffnen (englische Oberfläche: **Settings > Plugins**), oben rechts **Hinzufügen > Marketplace hinzufügen** wählen (**Add > Add a marketplace**) und `tobias-zucali/EmpCo-UWG-Monitor-Plugin` eingeben. Der Marketplace erscheint danach im Reiter **Marketplace**.
2. Zu **Anpassen > Plugins** (**Customize > Plugins**) wechseln und den Reiter **Persönlich** (**Personal**) öffnen. Unter dem Namen des Marketplaces steht das Plugin `EmpCo-UWG Monitor`; auf **+** klicken. ChatGPT leitet zur Anmeldung weiter: dort den Zugangscode eingeben und bestätigen.

Ist der Marketplace nicht erreichbar, lässt sich dasselbe Paket als Zip-Datei hochladen: [`empco-uwg-monitor-plugin.zip`](https://claims.agent-services.at/downloads/empco-uwg-monitor-plugin.zip) herunterladen und in der Desktop-App oder im Browser (chatgpt.com) unter **Plugins** → **Hinzufügen** → **Plugin hochladen** auswählen; danach Schritt 2 (Anmeldung). Ein hochgeladenes Plugin lässt sich in ChatGPT weder aktualisieren noch löschen.

### Aktualisieren in ChatGPT

In der Desktop-App unter **Einstellungen > Plugins**, Reiter **Marketplace**, beim Marketplace `tobias-zucali/EmpCo-UWG-Monitor-Plugin` auf **Upgrade** klicken. Danach einen neuen Chat im Modus **Work** starten.

### Verwendung in ChatGPT

In der Desktop-App den Modus **Work** wählen (empfohlen; im Standard-Chat und in der Web-App sind Skill und Verbindung des Plugins derzeit nicht verfügbar, beides kann sich mit der Unterstützung durch ChatGPT ändern), neuen Chat starten und einen Prüfauftrag stellen, z. B. „Prüfe: „Unsere Verpackung ist 100 % umweltfreundlich."" Im Browser steht die Verbindung des Plugins derzeit nicht zur Verfügung – dort ist keine Prüfung möglich.

### Verbindung in ChatGPT neu anmelden

Wenn `fetch_claims_monitor_step` fehlt: **Einstellungen** → **Plugins** → Reiter **MCPs** → unter „From plugins" beim Eintrag `empco-uwg-monitor` auf **Authenticate** klicken und den Hinweisen im geöffneten Browserfenster folgen. Nach erfolgreicher Anmeldung einen neuen Chat starten und die Anfrage erneut stellen.

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

Angaben für eine Supportanfrage und die Kontaktadresse stehen auf der [Support-Seite](https://claims.agent-services.at/support). Jeder Supportanfrage liegt der Bericht der Diagnose bei; er entsteht mit dem [direkten Aufruf des Diagnose-Skills](#skill-direkt-aufrufen).

- **Die Verbindung fehlt oder die Sitzung ist nicht mehr gültig:** Einmal in der jeweiligen Anwendung neu anmelden ([Claude](#verbindung-in-claude-neu-anmelden), [ChatGPT](#verbindung-in-chatgpt-neu-anmelden)) (in ChatGPT auf **Authenticate**). Ein abgelaufenes OAuth-Token kann dabei erneuert werden; danach einen neuen Chat starten.
- **Die Anmeldeseite meldet, dass der Zugangscode gesperrt oder abgelaufen ist:** Eine erneute Anmeldung mit demselben Code stellt den Zugriff nicht wieder her. Die Diagnose ausführen. Den Support kontaktieren, deren Bericht beifügen und die angezeigte Meldung nennen.
- **Anmeldung kann nicht abgeschlossen werden oder `fetch_claims_monitor_step` fehlt weiterhin:** Die Diagnose ausführen. Den Support kontaktieren und deren Bericht beifügen. Der Assistent nennt die im Plugin mitgelieferte Supportadresse.
- **Marketplace lässt sich nicht hinzufügen oder Plugin nicht installieren:** Schreibweise `tobias-zucali/EmpCo-UWG-Monitor-Plugin` prüfen und die Anwendung aktualisieren. Als Rückfall die Zip-Datei hochladen ([Claude](#installation-in-claude), [ChatGPT](#installation-in-chatgpt)); bei einem Fehler zur Zip-Struktur die Datei erneut vom Server laden statt manuell zu bearbeiten. Die manuelle Einrichtung nur der MCP-Verbindung ist kein Ersatz, weil dabei der Skill des Plugins fehlt.
- **Bericht für den Support (jeder Anfrage beifügen):** Der Diagnose-Skill des Plugins erzeugt einen belegten Bericht mit ausschließlich technischen Angaben zu Umgebung, Verbindung und Versionen; Prüftexte und Analyseergebnisse gehören nie dazu. Der direkte Aufruf steht unter [Skill direkt aufrufen](#skill-direkt-aufrufen) (in Claude `/diagnose-monitor-plugin`); dieser Aufruf startet ohne Rückfrage. Der Zusatz `version` liefert nur Versionen und einfache Fähigkeitschecks, `technik` ergänzt technische Details zu einem vorhandenen Prüflauf, `voll` zusätzlich Werkzeugliste und lokale Umgebungsangaben. Enthält das Gespräch bereits eine Prüfung, wertet der Aufruf ohne Zusatz deren Ablauf mit aus. Den Bericht (der Kasten mit dem Text) kopieren und senden. Wo Skills nicht verfügbar sind, steht derselbe Text auf der Seite [Diagnose zum Einfügen](https://claims.agent-services.at/docs/diagnose) bereit.
- **Öffentliche Dokumentation der Schnittstelle:** [https://claims.agent-services.at/docs/mcp](https://claims.agent-services.at/docs/mcp)
