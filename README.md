```markdown
# ScrapTrap – AI-Bot-Policy & Payment Enforcement Modul

[ 🇩🇪 Deutsch](#deutsch) | [ 🇬🇧 English](#english)

---

## <a name="deutsch"></a>🇩🇪 Deutsch

# ScrapTrap – AI-Bot-Policy & Payment Enforcement Modul

## Übersicht & Problemstellung

Hochwertige, redaktionell erstellte Inhalte von Privatseiten, Sammlerportalen, Fachdatenbanken und Onlineshops werden systematisch und ungefragt von automatisierten KI-Crawlern abgegriffen.

Herkömmliche Schutzmechanismen – allen voran die `robots.txt` – stellen lediglich eine höfliche Bitte dar. Kommerzielle KI-Betreiber (wie Anthropics Claude-Bot, Perplexity, GPTBot und andere) ignorieren diese passiven Vorgaben häufig ohne jede technische oder rechtliche Konsequenz, erzeugen immense Serverlast und eignen sich fremdes geistiges Eigentum an.

**Das ScrapTrap AI-Bot-Policy & Payment Enforcement Modul beendet diese schutzlose Haltung.** Es gibt Rechteinhabern und Seitenbetreibern die volle Datensouveränität zurück, indem es Zugriffsregeln, rechtliche Bedingungen und technische Sperren auf Layer-7-Ebene durchsetzt – bevor Inhalte oder Ressourcen ausgeliefert werden.

---

## Technische Architektur & Grundprinzipien

* **100% Serverseitig & Unabhängig:** Läuft vollständig auf der eigenen Infrastruktur ohne Cloud-Abhängigkeiten. Vollständig DSGVO-konform (keine Cookies, keine Sessions, kein User-Tracking, keine Consent-Banner-Pflicht).

* **Deterministischer Abgleich:** Gleicht eingehende Requests mit einer gepflegten Signatur- und Verhaltensdatenbank bekannter KI-Bots und Trainings-Crawler ab (AmazonBot, GPTBot, Claude-Bots, Google-Extended, PerplexityBot, CommonCrawl, ByteSpider, Cohere, Diffbot, Meta-Crawler etc.).

* **SearchBot-Schutz:** Nachweislich authentische, legitime Suchmaschinen-Crawler (Googlebot, Bingbot etc.) werden vom KI-Modul gezielt ausgenommen, um jegliche Gefahr von SEO-Rankingverlusten auszuschließen.

* **Verbindungskonsistenz-Doublecheck:** Integriert eine doppelte Verbindungsprüfung (`Meth. (doublecheck)`), die gerichtsfest protokolliert, dass der Bot die Zugangsbeschränkungen und Zahlungsbedingungen tatsächlich zur Kenntnis genommen hat.

* **Robots.txt-Ersterkennung:** Prüft beim Erststart eine vorhandene `robots.txt` auf entsprechende Disallow-Einträge (um das Argument eines stillschweigenden Zugeständnisses zu entkräften) und bietet bei Bedarf die automatische Erstellung an.

---

## Funktionsbereiche & Betriebsmodi

### Feature 1: Payment Enforcement & Automatische Abrechnung (Mode: Pay)

Wird ein KI-Crawler identifiziert, stoppt ScrapTrap die reguläre Content-Auslieferung und antwortet mit einem rechtlich fundierten Payload:

* **HTTP-Statuscode:** `402 Payment Required`
* **Klarformulierter HTML-Hinweis:** Erläutert das Verbot von unlizenziertem KI-Training und Scraping.
* **Maschinenlesbare Header:** Übermittelt die genauen Nutzungsbedingungen inklusive Aufwandsentschädigungen für unerlaubte Zugriffe trotz Unterlassungsaufforderung.
* **Urheber- & Verantwortlichkeitszuordnung:** Enthält Betreiberangaben, Verweise auf ScrapTrap / Fledisoft sowie optional den Namen des Betreibers zur Sicherung späterer Ansprüche.
* **Automatische Sperre:** Sperrt die zugreifende Bot-IP automatisch für 24 Stunden pro Verstoß.
* **Juristischer Hintergrund:** Stützt sich auf § 44b UrhG (TDM-Opt-Out im deutschen Recht), europäische Urheberrechtsrichtlinien sowie den US-amerikanischen CFAA-Framework.

### Feature 2: Gesteuerte JSON-LD-Ausgabe & GEO-Kontrolle (Mode: Pay & JSON)

Anstatt auf unstandardisierte Vorschläge wie `llms.txt` oder dubiose KI-Indexierungsdienste zu setzen – die Daten oft ohne Gegenleistung weiterverkaufen –, behalten Seitenbetreiber mit ScrapTrap die volle Kontrolle über die an KI-Modelle übermittelten Daten:

* **JSON-LD-Haupteintrag (Mode: Pay&JSON [Main]):** Ein zentraler, im Adminbereich definierter struktureller Datensatz. Wird zusammen mit dem 402-Hinweis ausgegeben und teilt dem Bot maschinenlesbar mit, welche Informationen für das Training genutzt werden dürfen.
* **Differenzierte Unter-Einträge (Mode: Pay&JSON [SubT]):** Kontextbezogene JSON-LD-Inhalte, die an spezifische Kategorien oder Aufrufe gekoppelt sind (z. B. spezielle Produktvorteile oder Rubriken).
* **Optional:** Generiert auf Wunsch bei Speicherung des Standard-JSONs automatisch eine lokale `llms.txt` im Hauptverzeichnis für abwärtskompatible Abfragen.

### Feature 3: Freigabe von Altruistic Content (Mode: Altruistic)

Ermöglicht die gezielte, ungesperrte Freigabe einzelner, gesellschaftlich oder wissenschaftlich relevanter Inhalte (z. B. Erste-Hilfe-Anleitungen, Open-Source-Dokumentationen, Forschungsergebnisse oder politische Aufklärung) für ausgewählte KI-Bots, während der Rest der Website geschützt bleibt.

* **Query-String (QS) Routing:** Wird sofort vor dem CMS-Bootstrap oder Datenbankabfragen für maximale Performance ausgewertet.
* **Gezieltes Whitelisting:** Konfiguration über Parameter-Strings (IDs, Verzeichnisse, Pretty Links) über 10 dedizierte Felder für ausgewählte KI-Bots. Nicht ausgewählte Scraper bleiben weiterhin blockiert.

---

## Modulare Integration & Ökosystem

* **Standalone oder Komplettschutz:** Funktioniert als einzelnes Modul oder nahtlos integriert in die ScrapTrap Security Suite.
* **Kombination mit Download-Saver:** Schützt statische Dateien (PDFs, Medien, Kataloge) nach denselben Regeln (Auslieferung von 402 Payment Notices, JSON-LD oder Altruistic Release).
* **Kombination mit GoodBot & Mini-WAF:** Kann ideal mit dem ScrapTrap GoodBot-Modul und der integrierten Query-String-Mini-WAF kombiniert werden, um SEO-Crawl-Raten zu überwachen und schädliche Parameter-Payloads abzufangen.

---

## Log-Beispiele



```log
Eintrag 60590: 🔒🤖🧠 GESPERRT - Grund: AI-Crawler / KI-Bot; Gesperrt durch Schutzmodul: @ScrapTrap AI-Blocker (Mode: Pay)
Referer: Direktaufruf
IP: 216.73.217.145
Host: 216.73.217.145
UserAgent: Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Claude-SearchBot/1.0; +searchbot@anthropic.com)
Zeit: 19:09:42 - Reaktionszeit ST-Aufruf→Log: 251.267 ms - Modulstart→Log: 3.45 ms
Conn.: keep-alive - Meth. (doublecheck) GET

Eintrag 60591: 🔒🤖🧠 GESPERRT - Grund: AI-Crawler / KI-Bot; Gesperrt durch Schutzmodul: @ScrapTrap AI-Blocker (Mode: Pay&JSON [Main])
Referer: Direktaufruf
IP: 216.73.217.145
...
Conn.: keep-alive - Meth. (doublecheck) GET

Eintrag 60592: 🔒🤖🧠 GESPERRT - Grund: AI-Crawler / KI-Bot; Gesperrt durch Schutzmodul: @ScrapTrap AI-Blocker (Mode: Pay&JSON [SubT: "Produktvorteile"])
...

Eintrag 60593: 🔒🤖🧠 GESPERRT - Grund: AI-Crawler / KI-Bot; Gesperrt durch Schutzmodul: @ScrapTrap AI-Blocker (Mode: Altruistic ["Stichprobenrechner"])
...
```

---

## ⚠️ Rechtlicher Hinweis

Die Durchsetzung rechtlicher Ansprüche hängt von der jeweiligen Rechtslage ab. ScrapTrap bietet die technische Grundlage und eine präzise, nachweisbare Zugriffsdokumentation als Basis für die rechtliche Verfolgung.

**Originaldokumentation unter:** [https://www.scraptrap.de/scraptrap_ai_ki_bot_policy.php](https://www.scraptrap.de/scraptrap_ai_ki_bot_policy.php)

---
*Besonderes Augenmerk: Keine Cloud-Abhängigkeiten, keine Cookies & Sessions, keine JS-Frameworks*



---

## <a name="english"></a>🇬🇧 English

# ScrapTrap – AI-Bot-Policy & Payment Enforcement Module

## Overview & Problem Statement

High-quality, editorially created content from private websites, collector portals, specialized databases, and online shops is systematically scraped without consent by automated AI crawlers.

Traditional protection mechanisms—first and foremost `robots.txt`—represent merely a polite request. Commercial AI operators (such as Anthropic’s Claude-Bot, Perplexity, GPTBot, and others) frequently ignore these passive guidelines without any technical or legal consequences, creating immense server loads and appropriating foreign intellectual property.

**The ScrapTrap AI-Bot-Policy & Payment Enforcement Module puts an end to this defenseless stance.** It restores full data sovereignty to rights holders and website operators by enforcing access rules, legal terms, and technical blocks at Layer 7—before any content or assets are delivered[cite: 3].

---

## Technical Architecture & Core Principles

* **100% Server-Side & Independent:** Runs entirely on your own infrastructure without cloud dependencies[cite: 3]. Fully GDPR-compliant (no cookies, no sessions, no user tracking, no consent banner required)[cite: 3].

* **Deterministic Matching:** Cross-checks incoming requests against a maintained signature and behavior database of known AI bots and training crawlers (AmazonBot, GPTBot, Claude-Bots, Google-Extended, PerplexityBot, CommonCrawl, ByteSpider, Cohere, Diffbot, Meta crawlers, etc.)[cite: 3].

* **SearchBot Protection:** Verifiably authentic, legitimate search engine crawlers (Googlebot, Bingbot, etc.) are explicitly excluded by the AI module to prevent any risk of SEO ranking loss[cite: 3].

* **Connection Consistency Double-Check:** Integrates a double connection verification (`Meth. (doublecheck)`), which legally and forensically logs that the bot has actually taken note of access restrictions and payment terms[cite: 3].

* **Robots.txt Initial Check:** Inspects an existing `robots.txt` upon initial launch for corresponding disallow directives (to counter the argument of implicit consent) and offers automated creation if required[cite: 3].

---

## Operating Modes & Functional Features

### Feature 1: Payment Enforcement & Automated Billing (Mode: Pay)

When an AI crawler is identified, ScrapTrap halts regular content delivery and responds with a legally grounded payload[cite: 3]:

* **HTTP Status Code:** `402 Payment Required`[cite: 3]
* **Clear HTML Notice:** Explains the explicit prohibition of unlicensed AI training and scraping[cite: 3].
* **Machine-Readable Headers:** Transmits precise terms of use, including compensation fees for unauthorized access despite cease-and-desist conditions[cite: 3].
* **Attribution & Accountability:** Includes operator details, references to ScrapTrap / Fledisoft, and optionally the operator's name to secure future legal claims[cite: 3].
* **Automated Block:** Automatically blocks the accessing bot IP for 24 hours per violation[cite: 3].
* **Legal Framework:** Grounded in § 44b UrhG (TDM Opt-Out under German Copyright Law), European Copyright Directives, and the US CFAA Framework[cite: 3].

### Feature 2: Controlled JSON-LD Output & GEO Management (Mode: Pay & JSON)

Instead of relying on unstandardized proposals like `llms.txt` or dubious AI indexing services—which often resell data without compensation—website operators retain full control over the data fed into AI models via ScrapTrap[cite: 3]:

* **Main JSON-LD Entry (Mode: Pay&JSON [Main]):** A centralized structural dataset defined in the admin panel[cite: 3]. Issued alongside the 402 notice, informing the bot in a machine-readable format which specific information is permitted for model training[cite: 3].
* **Differentiated Sub-Entries (Mode: Pay&JSON [SubT]):** Context-aware JSON-LD content linked to specific categories or calls (e.g., unique product advantages or sections)[cite: 3].
* **Optional:** Automatically generates a local `llms.txt` in the root directory upon saving the default JSON for backward-compatible queries[cite: 3].

### Feature 3: Altruistic Content Release (Mode: Altruistic)

Enables selective, unblocked access to specific, socially or scientifically relevant content (e.g., first-aid guides, open-source documentation, research findings, or political educational material) for chosen AI bots, while keeping the rest of the website fully protected[cite: 3].

* **Query-String (QS) Routing:** Evaluated immediately prior to CMS bootstrap or database queries to ensure maximum performance[cite: 3].
* **Targeted Whitelisting:** Configurable via parameter strings (IDs, directories, pretty links) across 10 dedicated fields for selected AI bots[cite: 3]. Non-selected scrapers remain strictly blocked[cite: 3].

---

## Modular Integration & Ecosystem

* **Standalone or Full Protection:** Functions as an independent module or seamlessly integrates into the broader ScrapTrap Security Suite[cite: 3].
* **Download-Saver Integration:** Protects static files (PDFs, media files, catalogs) following the same rulesets (delivering 402 Payment Notices, JSON-LD, or Altruistic Releases)[cite: 3].
* **GoodBot & Mini-WAF Combination:** Ideally pairs with the ScrapTrap GoodBot module and the integrated Query-String Mini-WAF to monitor SEO crawl rates and block malicious parameter payloads[cite: 3].

---

## Log Examples

```log
Eintrag 60590: 🔒🤖🧠 BLOCKED - Reason: AI-Crawler / AI-Bot; Blocked by module: @ScrapTrap AI-Blocker (Mode: Pay)
Referer: Direct Access
IP: 216.73.217.145
Host: 216.73.217.145
UserAgent: Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Claude-SearchBot/1.0; +searchbot@anthropic.com)
Time: 19:09:42 - Response time ST-Call→Log: 251.267 ms - Module Start→Log: 3.45 ms
Conn.: keep-alive - Meth. (doublecheck) GET

Eintrag 60591: 🔒🤖🧠 BLOCKED - Reason: AI-Crawler / AI-Bot; Blocked by module: @ScrapTrap AI-Blocker (Mode: Pay&JSON [Main])
Referer: Direct Access
IP: 216.73.217.145
...
Conn.: keep-alive - Meth. (doublecheck) GET

Eintrag 60592: 🔒🤖🧠 BLOCKED - Reason: AI-Crawler / AI-Bot; Blocked by module: @ScrapTrap AI-Blocker (Mode: Pay&JSON [SubT: "Product Advantages"])
...

Eintrag 60593: 🔒🤖🧠 BLOCKED - Reason: AI-Crawler / AI-Bot; Blocked by module: @ScrapTrap AI-Blocker (Mode: Altruistic ["Sample Calculator"])
…

---

## ⚠️ Legal Notice

The enforcement of legal claims depends on the applicable jurisdiction[cite: 3]. ScrapTrap provides the technical foundation and precise, verifiable access documentation required to substantiate legal proceedings.

**Original Documentation:** [https://www.scraptrap.de/scraptrap_ai_ki_bot_policy.php](https://www.scraptrap.de/scraptrap_ai_ki_bot_policy.php)

---
*Key focus: Zero cloud dependencies, zero cookies & sessions, zero JS frameworks*



