# Aktennummer/Aktenzeichen und System-/Admin-Einstellungen in Kanzlei- und Matter-Management-Software (Stand Okt. 2026)

> Methodischer Hinweis: Direkte Seitenabrufe (WebFetch) auf onlinehilfe.advoware.de, onlinehilfen.ra-micro.de, actaport.zendesk.com und clio.com wurden vom Netzwerk-Proxy blockiert. Die Belege stammen deshalb aus den Suchergebnis-Auszügen dieser Hersteller-Hilfeseiten (URLs angegeben). Die Auszüge sind konsistent und herstellernah, wurden aber nicht im Volltext gegengelesen. Bei Abweichungen gilt: vor der Umsetzung im Volltext prüfen.

## 1. Formate der Aktennummer (DE vs. international)

### Takeaway
In Deutschland ist das klassische Format **„laufende Nummer/Jahrgang"** (z. B. `537/12`, `120/20`) mit jährlichem Neustart der Zählung. RA-MICRO, Advoware, Actaport und DATEV setzen alle darauf, teilweise mit konfigurierbaren Zusatzbausteinen (Referat, Sachbearbeiter, Standort). International überwiegen **Client-Matter-Nummern** (`Mandantennummer-Matter-Nr.`) oder fortlaufende firmenweite Nummern mit konfigurierbarer Vorlage (Clio). Enterprise-Systeme wie Elite 3E oder TeamConnect erlauben freie alphanumerische IDs bzw. Muster-Bausteine.

### Cited Findings
**Deutschland**
- RA-MICRO: Format „Aktennummer/2-stelliger Jahrgang" (z. B. 537/12). Höchste Nummer pro Jahr: 99999/JJ. Eingabeerleichterungen wie „2.10", „2,10" oder „210" sind möglich. — [RA-MICRO Handbuch Akten (PDF)](https://wissenspool.ra-micro.de/wp-content/uploads/RM-Handbuch-Akten.pdf); [RA-MICRO Online-Hilfe: Akte anlegen](https://onlinehilfen.ra-micro.de/index.php/Akte_anlegen)
- Advoware: Das Aktenzeichen wird „nach einem Baukastensystem" zusammengesetzt. Mögliche Bausteine sind Referat, Sachbearbeiter, Aktennummer (auch mit führenden Nullen), Jahrgang (2- oder 4-stellig), Konto (Honorarkonto), freie Felder 1–4 sowie Datenpool- und Standortkürzel. Als Trenner stehen `.`, `-`, `/`, `#` und das Leerzeichen zur Wahl. — [Advoware Online-Hilfe: Aktenzeichen – Grundeinstellung](https://onlinehilfe.advoware.de/Documents/aktenzeichengrundeinstellung.html)
- Advoware: Referate werden mit Kürzel und Langbezeichnung gepflegt. Die Kürzel können ins Aktenzeichen einfließen. — [Advoware: Referate – Grundeinstellung](https://onlinehilfe.advoware.de/Documents/referategrundeinstellung.html)
- Actaport: Die Aktennummer vergibt das System im Format Nr./JJ (Beispiel: 700/22). Zusätzlich gibt es ein „Alternatives Aktenzeichen" mit frei wählbarer Syntax. — [Actaport: Aktennummer anpassen](https://actaport.zendesk.com/hc/de/articles/4432839720348-Aktennummer-anpassen); [Actaport: Akte anlegen](https://actaport.zendesk.com/hc/de/articles/360011235759-Akte-anlegen)
- Actaport trennt das eigene Aktenzeichen vom gerichtlichen und vom gegnerischen Aktenzeichen. Diese werden am jeweiligen Beteiligten (Gericht, Gegenanwalt) erfasst, nicht an der Akte. — [Actaport: Gerichtliches und gegnerisches Aktenzeichen](https://actaport.zendesk.com/hc/de/articles/4407870131090-Gerichtliches-und-gegnerisches-Aktenzeichen)
- DATEV Anwalt classic: Die Aktennummer wird automatisch vergeben. Einstellbar sind eine jahresbezogene Vergabe, eine fortlaufende Vergabe über den Jahreswechsel hinweg und eine Vergabe für mehrere Standorte (u. a. Neustart mit 000001 nach dem Jahreswechsel). — [DATEV Hilfe-Center 1005537: Nummernvergabe für die Aktenanlage einrichten](https://apps.datev.de/help-center/documents/1005537)
- Allgemeine Konvention in Deutschland: Die Nummern laufen jahresweise und tragen das zweistellige Jahr, getrennt durch Schrägstrich („120/20"). Gerichte und Behörden verwenden eigene Aktenzeichen-Systematiken. — [Wikipedia: Aktenzeichen (Deutschland)](https://de.wikipedia.org/wiki/Aktenzeichen_(Deutschland))
- Kleos/AnNoText (Wolters Kluwer): In den öffentlichen Unterlagen ist kein Nummernformat dokumentiert. Belegt ist nur, dass beim beA-Versand das „AZ1" des Beteiligten als Aktenzeichen vorgeschlagen wird und dass die Administration erzwingen kann, eingehende Nachrichten einer Aktennummer zuzuordnen. — [Wolters Kluwer AnNoText Änderungshistorie 2026](https://assets.contenthub.wolterskluwer.com/api/public/content/3228543-aenderungshistorie-annotext-2026-5acb7df102?v=3a8f89b4)

**International**
- Clio Manage: Standardvorlage `[matter number]-[client summary name]`, die Matter-Nummern beginnen bei 00001. Administratoren konfigurieren das Schema unter Settings > Firm Preferences > Matter Numbering mit Presets und Feldbausteinen: Client Number, Client First/Last/Summary Name, Matter Description sowie Matter Number in drei Varianten (Firm-wide, Per Client, Per Year). — [Clio Help: Matter Numbering Scheme](https://help.clio.com/hc/en-us/articles/9286019831707-Matter-Numbering-Scheme)
- Clio bietet den Modus „Manual for Each Matter", der die Automatik abschaltet, sowie einen Override pro Matter. — [Clio: Manual for each matter](https://support.clio.com/hc/en-us/articles/360002463953-KCS-How-to-Set-Matter-Numbering-to-Manual-for-Each-Matter); [Clio: Override a Matter Number](https://support.clio.com/hc/en-us/articles/115002434654-KCS-How-to-Override-a-Matter-Number)
- Elite 3E (Thomson Reuters): Die Matter-Nummer kommt automatisch über „Next Matter Number". Berechtigte Nutzer dürfen sie überschreiben (bis 64 alphanumerische Zeichen). Daneben gibt es eine „Alternate Number" für Fremdsysteme und eine eigene Client-Matter-ID für das LEDES-eBilling. — [Elite 3E Matter Form and Field Definitions](http://treonlinehelp.elite.com/robohelp/robo/server/3E/projects/3E%20Billing%20Master%20Files%20Guide/matter_fd.htm)
- Mitratech TeamConnect: Datensätze lassen sich per Muster automatisch benennen. Bausteine sind z. B. Anlagedatum, Default-Kategorie oder Name der Hauptpartei. Konfiguriert wird das in der Object Definition „Matter". — [TeamConnect Glossary](https://help.teamconnect.com/TC40/UserHelp/administrator-10-1.html)
- LawVu (Inhouse): Die Matter-ID hat das Präfix „LV" plus Nummern, z. B. „LV0536-0099". — [LawVu API Docs: Fields](https://api-docs.lawvu.com/docs/guides/fields)
- LeanLaw: Die Matter-IDs zählen pro Mandant ab 1 (Client-Matter-Logik). — [LeanLaw: Automating Client and Matter IDs](https://support.myleanlaw.co/en/articles/1962793-automating-client-and-matter-ids)
- Lexzur dokumentiert eine konfigurierbare Matter-ID für Inhouse-Rechtsabteilungen. Das bestätigt die Konfigurierbarkeit als Marktstandard, Details nicht geprüft. — [Lexzur: How to Configure Matter IDs](https://documentation.lexzur.com/spaces/LEX/pages/142971193/How+to+Configure+Matter+IDs)

### Inferences
- Der Marktstandard ist ein **konfigurierbares Muster aus Bausteinen** (Präfix/Kürzel + Zähler mit Breite + Jahr + Trenner), kein fest verdrahtetes Format. Advoware und Clio zeigen das am deutlichsten.
- Für deutsche Kanzleien ist `lfd. Nr./JJ` die Erwartung „out of the box". Für internationale Kanzleien und Konzernrechtsabteilungen passen `Client-Matter` bzw. `Präfix-JJJJ-NNNNN` besser.
- Ein zusätzliches **alternatives/externes Aktenzeichen** (Actaport, Elite 3E „Alternate Number", eBilling-ID) ist üblich. Fremde Aktenzeichen (Gericht, Gegner, Kanzlei des Mandanten) gehören an den Beteiligten bzw. die Rolle, nicht ins Primärfeld.

### Gaps
- Für Thomson Reuters Legal One, Aderant Expert, Onit, Legisway und Kleos/AnNoText fand ich keine öffentlich dokumentierten Standardformate. Legisway-Dokumentation ist nicht frei zugänglich.
- Das Standardformat der RA-MICRO-Mandantennummer und deren Verknüpfung mit der Aktennummer ist nicht belegt.

## 2. Zeitpunkt der Nummernvergabe (Intake vs. Aktenanlage) und Vorläufignummern

### Takeaway
Deutsche Kanzleisoftware vergibt die Nummer bei **Aktenanlage**, automatisch und standardmäßig als nächste freie Nummer. Optional lässt sie sich manuell bzw. „am Ende der Aktenanlage" vergeben. Berufsrechtlich muss die Kollisionsprüfung **vor Mandatsannahme** liegen. Enterprise-Systeme (Elite 3E, Aderant) bilden deshalb einen Intake-Workflow ab, in dem die Akte erst nach bestandener Konfliktprüfung „geöffnet" wird.

### Cited Findings
- RA-MICRO: Standard ist die automatische Vergabe, die zur nächsten freien Nummer hochzählt. Wahlweise kann manuell vergeben werden, und zwar am Ende der Aktenanlage. — [RA-MICRO Online-Hilfe: Akte anlegen](https://onlinehilfen.ra-micro.de/index.php/Akte_anlegen); Praxisdiskussion: [FoReNo: Akten-Nr. bei Aktenanlage selbst bestimmen](https://www.foreno.de/viewtopic.php?t=8086)
- Advoware: Das Aktenzeichen „wird vom Programm vergeben und kann nicht geändert werden", damit jede Nummer nur einmal vorkommt. — [Advoware: Aktenzeichen – Grundeinstellung](https://onlinehilfe.advoware.de/Documents/aktenzeichengrundeinstellung.html)
- Advoware kann leere Aktennummern vorab erzeugen (Hilfsprogramme > Systemprogramme > Aktennummern anlegen), z. B. für Unterakten ohne fortlaufende Nummer. Nummern sind dort also vom Akteninhalt entkoppelt reservierbar. — [Advoware: Unterakten ohne fortlaufende Aktennummer](https://onlinehilfe.advoware.de/Documents/unteraktenohnefortlaufendeaktennummer.html)
- Elite 3E: Eine Intake-Fachkraft erfasst das Intake-Formular. 3E prüft Finanzdaten (offene Posten, WIP) und eskaliert ggf. an den CFO. Erst nach der Konfliktprüfung wird die Akte eröffnet, und fehlen Mandatsdokumente, geht sie auf „hold". (Quelle ist ein Praktiker-Beitrag, kein Hersteller.) — [LinkedIn, S. McCarthy: Making Sense of Elite 3E](https://www.linkedin.com/pulse/making-sense-elite-3e-scott-mccarthy-mba)
- Aderant Expert Sierra automatisiert Client Intake, Konfliktprüfung und File Opening als Workflow. — [Aderant Expert Sierra](https://www.aderant.com/solutions-expert-sierra/); [Aderant Case Study Ulmer & Berne](https://www.aderant.com/client-stories/ulmer-berne-case-study/)
- Berufsrecht: Nach § 43a Abs. 4 BRAO i. V. m. § 3 BORA dürfen keine widerstreitenden Interessen vertreten werden. Die Kollisionsprüfung soll vor Mandatsannahme stattfinden, und Kanzleisoftware wird dafür elektronisch genutzt. Stellt sich ein Konflikt später heraus, sind die Mandanten unverzüglich zu informieren und die Mandate zu beenden (§ 3 Abs. 2 BORA). — [MKG: Interessenkollision in der Kanzlei](https://mkg-online.de/2024/06/26/interessenkollision-in-der-anwaltlichen-praxis/); [Anwaltsblatt: Interessenkollision 3.0](https://anwaltsblatt.anwaltverein.de/de/themen/recht-gesetz/interessenkollision-grosse-brao-reform)
- Dataverse-Autonumber: Der Wert wird beim Anlegen des Datensatzes vorab gezogen. Abgebrochene Anlagen erzeugen Lücken, die nicht aufgefüllt werden. — [Microsoft Learn: Autonumber columns](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/autonumber-fields)

### Inferences
- Wird die Nummer schon beim Intake gezogen, entstehen Lücken durch abgelehnte Anfragen (Konflikt, Ablehnung). Außerdem tauchen Nummern für Nicht-Mandate auf. Bewährt ist daher die Trennung zwischen **Anfrage-/Intake-ID** (technisch, z. B. `ANF-2026-000123`) und **finaler Aktennummer**, die erst beim Statuswechsel „Eröffnet" nach Konfliktfreigabe vergeben wird.
- Die Option „manuell/Nummer erst am Ende" (RA-MICRO) und die Vorab-Reservierung (Advoware) zeigen: Ein Override mit Rechten und Eindeutigkeitsprüfung ist Praxisstandard.

### Gaps
- Für die deutschen Produkte fand ich keine Herstellerdokumentation zu expliziten „Vorläufigen Aktennummern" bzw. Intake-Nummern. Unklar bleibt, ob etwa RA-MICRO oder Advoware die Kollisionsprüfung vor der Nummernvergabe erzwingen. Im Volltext prüfen.

## 3. Lückenlosigkeit, Jahresreset, Zähler pro Bereich/Standort

### Takeaway
Für **Aktennummern** von Rechtsanwälten fand ich **keine** gesetzliche oder berufsrechtliche Pflicht zur Lückenlosigkeit. § 50 BRAO verlangt nur eine geordnete, zutreffende Handakte mit 6 Jahren Aufbewahrung. Lückenlos bzw. streng fortlaufend sind nur **notarielle Verzeichnisse** (NotAktVV). Für **Rechnungen** gilt: einmalig und fortlaufend, Lücken sind aber zulässig, wenn sie nachvollziehbar sind. Ein Jahresreset der Aktennummer ist in Deutschland Standard. Getrennte Nummernkreise pro Standort oder für Notariat sind konfigurierbar.

### Cited Findings
- § 50 BRAO: Handakten müssen „ein geordnetes und zutreffendes Bild über die Bearbeitung" der Aufträge geben. Aufbewahrung 6 Jahre ab Ende des Kalenderjahres der Mandatsbeendigung. Eine Pflicht zur fortlaufenden Aktennummer enthält die Vorschrift nicht. — [§ 50 BRAO, gesetze-im-internet.de](https://www.gesetze-im-internet.de/brao/__50.html); [dejure § 50 BRAO](https://dejure.org/gesetze/BRAO/50.html)
- (Hinweis: Die Handakte ist in **§ 50 BRAO** geregelt, nicht in „§ 50 BORA". Die BORA enthält keine Nummerierungsvorgabe; ein Aktenregister als Pflicht fand ich nicht.) — [§ 50 BRAO](https://www.gesetze-im-internet.de/brao/__50.html)
- NotAktVV (Kontrast): Das Urkundenverzeichnis wird je Kalenderjahr mit fortlaufenden Nummern geführt. Versehentlich nicht eingetragene Vorgänge kommen unter die nächste Nummer. Auch die Massenummer im Verwahrungsverzeichnis besteht aus Jahr und fortlaufender Nummer. — [NotAktVV Abschnitt 2 (buzer)](https://www.buzer.de/gesetz/14179/b37165.htm); [NotAktVV (gesetze-im-internet)](https://www.gesetze-im-internet.de/notaktvv/BJNR224610020.html); [BNotK: UVZ-Nummernformat](https://onlinehilfe.bnotk.de/einrichtungen/elektronisches-urkundenarchiv/urkundenverzeichnis-uvz/uvz-nummernformat-festlegen-oder-aendern.html)
- Rechnungen (§ 14 Abs. 4 Nr. 4 UStG): Die Nummer muss einmalig und fortlaufend sein, Lücken sind nach BFH bzw. Literatur zulässig. Lücken sollten dokumentiert werden (Storno, manuelle Rechnungen). — [NWB Experten-Blog: Keine Pflicht zur lückenlosen Rechnungsnummer](https://www.nwb-experten-blog.de/keine-pflicht-zur-vergabe-lueckenlos-fortlaufender-rechnungsnummern/); [Betriebs-Berater: Urteil zu EÜR](https://betriebs-berater.ruw.de/steuerrecht/urteile/Keine-Pflicht-zur-Vergabe-lueckenlos-fortlaufender-Rechnungsnummern-bei-Einnahme-ueberschuss-Rechnung-34849)
- Advoware-Empfehlung: Das System beginnt jedes Jahr automatisch mit Nummer 1. Wer jahresunabhängig fortzählen will, nutzt den Jahreswechsel-Assistenten („Aktennummer ändern"). Mit der Option „Aktennummer darf editiert werden" ist ein manueller Eingriff möglich. — [Advoware: Unterakten ohne fortlaufende Aktennummer / Jahreswechsel](https://onlinehilfe.advoware.de/Documents/unteraktenohnefortlaufendeaktennummer.html); [Advoblog Hülskötter: Jahreswechsel](https://advoblog.huelskoetter.info/advoware-darauf-sollten-sie-beim-jahreswechsel-achten/)
- Advoware Aktenablage: Es gibt getrennte Nummernkreise für Anwalts- und Notarakten (abschaltbar über „kein separater Nummernkreis für Notarakten") und optional getrennte Ablagenummern je Standort. Die nächste Nummer ist frei setzbar, z. B. Jahr + „00001" für bis zu 99.999 Akten pro Jahr. — [Advoware: Aktenablage – Grundeinstellung](https://onlinehilfe.advoware.de/Documents/aktenablagegrundeinstellung.html)
- DATEV: jahresbezogener Reset, fortlaufende Zählung über Jahre oder Mehrstandort-Vergabe als Einstellung. — [DATEV 1005537](https://apps.datev.de/help-center/documents/1005537)
- RA-MICRO: Die Zählung erfolgt pro Jahrgang (Obergrenze 99999/JJ). Laufende Nummern werden zentral unter „Einstellungen Laufende Nummern" gepflegt. — [RA-MICRO: Einstellungen Laufende Nummern](https://onlinehilfen.ra-micro.de/index.php/Einstellungen_Laufende_Nummern)
- Actaport: Die Aktennummer für das laufende oder kommende Jahr ist in den Einstellungen setzbar, z. B. Sprung auf 700/22. Bestehende Akten bleiben unverändert. Ein Sprung in der Nummernfolge ist also ausdrücklich vorgesehen. — [Actaport: Aktennummer anpassen](https://actaport.zendesk.com/hc/de/articles/4432839720348-Aktennummer-anpassen)
- Clio: Zähleroptionen firmenweit, pro Mandant oder pro Jahr. — [Clio Help: Matter Numbering Scheme](https://help.clio.com/hc/en-us/articles/9286019831707-Matter-Numbering-Scheme)
- GoBD verlangt Nachvollziehbarkeit und Unveränderbarkeit buchungsrelevanter Daten, nicht Lückenlosigkeit der Belegnummern. — [kostenlose-erechnung.de Ratgeber](https://kostenlose-erechnung.de/ratgeber/rechnungsnummer-system-pflichten/) (Sekundärquelle, mittlere Verlässlichkeit)

### Inferences
- **Eindeutigkeit und Unveränderbarkeit** sind die harten Anforderungen. Lückenlosigkeit ist bei Aktennummern Komfort bzw. Kanzleiwunsch, keine Rechtspflicht. Dass mehrere Hersteller Sprünge ausdrücklich erlauben (Actaport, Advoware), stützt das.
- Strenge Lückenlosigkeit wäre nur nötig, wenn RSM4Legal Notariatsverzeichnisse oder Rechnungsnummern selbst führt. Rechnungsnummern liegen typischerweise in der Buchhaltung bzw. im ERP; dort reicht „einmalig + fortlaufend + Lücken dokumentiert".
- Zählerdimensionen, die der Markt anbietet: global, pro Jahr, pro Standort, pro Bereich (Anwalt/Notar), pro Mandant.

### Gaps
- Kammerverlautbarungen (BRAK/RAK) zu einem Aktenregister oder einer Nummerierungspflicht fand ich nicht. Das ist zwar nur ein fehlender Beleg und kein Gegenbeweis, deckt sich aber mit dem Normtext von § 50 BRAO.
- Ob GwG-Aufzeichnungspflichten (§ 8 GwG) eine Referenznummer erfordern, habe ich nicht recherchiert.

## 4. Mandant-Akte-Hierarchie (Kanzlei vs. Rechtsabteilung)

### Takeaway
In Kanzleien ist **Mandant → Akte** universell. International ist es oft in der Nummer selbst kodiert (Client-Matter, Clio „Per Client", LeanLaw, Elite 3E Client-Feld). In Deutschland ist die Aktennummer meist mandantenunabhängig (`lfd./JJ`), der Mandant hängt als Beteiligter bzw. Rolle an der Akte. In Rechtsabteilungen ersetzt die **Geschäftseinheit/Abteilung** den Mandanten (LawVu Departments). Die Nummer ist dort meist ein Systempräfix plus Zähler.

### Cited Findings
- Clio: Bausteine „Client Number" und „Matter Number (Per Client)" für Client-Matter-Nummern. Ändern lässt sich die Client-Nummer, die in die Matter-Nummer einfließt. — [Clio: Matter Numbering Scheme](https://help.clio.com/hc/en-us/articles/9286019831707-Matter-Numbering-Scheme); [Clio: Change the Client Number used in Matter Numbering](https://support.clio.com/hc/en-us/articles/115004772533-Can-I-Change-the-Client-Number-That-s-Used-in-Matter-Numbering-)
- Elite 3E: Jedes Matter ist einem Client zugeordnet. Für das eBilling existiert eine separate Client-Matter-ID (LEDES `CLIENT_MATTER_ID`). — [Elite 3E Matter Field Definitions](http://treonlinehelp.elite.com/robohelp/robo/server/3E/projects/3E%20Billing%20Master%20Files%20Guide/matter_fd.htm)
- LeanLaw: Die Matter-ID startet pro Mandant bei 1. — [LeanLaw](https://support.myleanlaw.co/en/articles/1962793-automating-client-and-matter-ids)
- LawVu (Inhouse): Rechtsabteilungen werden über „Departments" strukturiert, die Matter-ID ist systemgeneriert („LV…"). — [LawVu: Manage departments](https://help.lawvu.com/en/articles/3297498-how-to-manage-your-departments-in-lawvu); [LawVu API Fields](https://api-docs.lawvu.com/docs/guides/fields)
- Advoware: Optional fließt ein Honorarkonto ins Aktenzeichen ein, ansonsten bleibt das Aktenzeichen mandantenunabhängig. — [Advoware: Aktenzeichen – Grundeinstellung](https://onlinehilfe.advoware.de/Documents/aktenzeichengrundeinstellung.html)

### Inferences
- In der Nummer kodierte Hierarchien sind fragil: Bei Mandantenwechsel, Fusion oder Umhängen „lügt" die Nummer. Besser ist die Hierarchie als **Beziehung** (Lookup) im Datenmodell. Der Client-Code darf optional als Anzeige-Baustein in die Nummer, wird aber bei Anlage eingefroren.
- Für Rechtsabteilungen bietet sich ein Baustein „Geschäftsbereich/Gesellschaft" anstelle des Mandanten an.

### Gaps
- Die Default-Konventionen für Inhouse-Nummern in TeamConnect, Onit und Legisway sind öffentlich nicht dokumentiert.

## 5. Admin-/Systemeinstellungen: Struktur, technisch vs. fachlich, Auditierung

### Takeaway
Die Produkte zeigen Einstellungen in Ebenen: **Kanzlei-/Firmenebene** (Clio Firm Preferences; Advoware „Grundeinstellungen" je Modul; RA-MICRO „Einstellungen Laufende Nummern"), **Bereichs-/Referatsebene** (Advoware Referate, Standorte) und **Objekt-/Typebene** (TeamConnect Object Definitions/Categories, Actaport Einstellungen > Akte für Zusatzfelder). Das Nummernschema darf typischerweise nur der Administrator ändern. Bei einer Schemaänderung fragt Clio ausdrücklich, ob Bestandsakten umbenannt werden sollen. Ein Audit von Konfigurationsänderungen ist bei Enterprise-Systemen dokumentiert (TeamConnect Audit-Logger), bei deutschen KMU-Produkten öffentlich kaum.

### Cited Findings
- Clio: Nur Administratoren dürfen das Nummernschema ändern. Beim Ändern gibt es die Option „Update all existing matters to reflect new numbering scheme". — [Clio: Creating and Updating the Matter Numbering Scheme](https://support.clio.com/hc/en-us/articles/203336530-Customizing-and-Updating-the-Matter-Number)
- Advoware: modulweise „Grundeinstellung"-Seiten (Aktenzeichen, Aktenablage, Aktensuche, Referate, Standardwerte für Listen). Für Änderungsprotokolle gibt es eine automatisierte Löschung bei Aktenablage. Advoware führt also Änderungsprotokolle auf Aktenebene. — [Advoware: Aktenablage – automatisierte Löschung von Änderungsprotokollen](https://onlinehilfe.advoware.de/Documents/aktenablageautomatisiertel%C3%B6schungvon%C3%A4nderungsprotokollen.html); [Advoware: Aktensuche – Grundeinstellung](https://onlinehilfe.advoware.de/Documents/aktensuchegrundeinstellung.html)
- Actaport: Menü > Einstellungen > Akte für individuelle Zusatzinformationen (Custom Fields) zu Akten. — [Actaport: Individuelle Zusatzinformationen](https://actaport.zendesk.com/hc/de/articles/360017678440-Individuelle-Zusatzinformationen-f%C3%BCr-Akten-hinterlegen)
- Kleos/AnNoText: Einstellungen über das Zahnrad bzw. die Administration, z. B. Pflicht zur Aktenzuordnung eingehender beA-Nachrichten. — [AnNoText Änderungshistorie 2026](https://assets.contenthub.wolterskluwer.com/api/public/content/3228543-aenderungshistorie-annotext-2026-5acb7df102?v=3a8f89b4)
- TeamConnect: trennt Admin-Bereich (System Settings, Logging, Accounts) und Designer bzw. Object Definitions (fachliche Konfiguration: Kategorien, Custom Fields, Wizards, Rules). Ein Audit-Logger protokolliert u. a. Änderungen an Log-Leveln mit Wer/Alt/Neu/Zeit. — [TeamConnect: Working with Admin Settings](https://success.mitratech.com/TeamConnect/Enterprise_Administrator_Help/System_Administration/01_Working_with_Admin_Settings); [TeamConnect: Appenders](https://success.mitratech.com/TeamConnect/TeamConnect_Setup_and_Development/Enterprise_Customization_Help/Working_with_System_Settings/06_Appenders); [TeamConnect Designer UI](https://success.mitratech.com/TeamConnect/TeamConnect_Setup_and_Development/Enterprise_Customization_Help/Introduction_to_Customization/03_TeamConnect_Designer_User_Interface)
- TeamConnect: Object Definitions umfassen Name, Kategorien, Custom Fields, Suchansichten, Wizard-Inhalte und Regeln je Objekttyp (Matter-Typ-Konfiguration). — [TeamConnect Glossary](https://help.teamconnect.com/TC40/UserHelp/administrator-10-1.html)
- Dataverse-Autonumber: Format-Tokens `{SEQNUM:n}`, `{RANDSTRING:n}`, `{DATETIMEUTC:fmt}`. Seed ist setzbar (Standard 1000). Ein Reset pro Jahr oder ein Zähler pro Dimension ist nativ nicht vorgesehen; den Seed per API/Flow zurückzusetzen ist ein Workaround. — [Microsoft Learn: Create autonumber columns](https://learn.microsoft.com/en-us/power-apps/developer/data-platform/create-auto-number-attributes); [CRM Crate: Reset seed via Power Automate](https://www.crmcrate.com/power-automate/how-to-change-or-reset-auto-number-seed-value-using-power-automate/)

### Inferences
- Bewährtes Muster: (a) **technische Einstellungen** (Integrationen, Logging, Schnittstellen, Feature-Flags), die nur der Systemadministrator oder die IT pflegt, getrennt von (b) **fachlichen Einstellungen** (Nummernschemata, Rechtsgebiete/Referate, Aktentypen, Fristen-Defaults, Pflichtfelder), die ein fachlicher Admin bzw. Kanzleimanager pflegt. Die Trennung entspricht TeamConnect Admin vs. Designer.
- Nummernschemata sollten **versioniert und auditiert** sein (Wer/Wann/Alt/Neu). Eine Schemaänderung darf Bestandsnummern nicht stillschweigend ändern. Der Clio-Dialog belegt, dass dieser Punkt in der Praxis relevant ist.
- Dataverse-Bordmittel: Das Audit für Konfigurationstabellen ist aktivierbar. Native Autonumber reicht für Intake-IDs. Für die finale Aktennummer mit Jahresreset, Bereichszähler und Musterbausteinen braucht es eine eigene Zählertabelle mit transaktionaler Vergabe (Plugin, synchron, Pre-/Post-Operation in derselben Transaktion). Das ist ein Architekturschluss, keine Herstellerempfehlung.

### Gaps
- Für RA-MICRO, Advoware, DATEV und Actaport fand ich keine öffentliche Doku, ob Änderungen an Grundeinstellungen selbst (z. B. am Nummernschema) revisionssicher protokolliert werden.

---

## Empfehlungen für RSM4Legal (je offene Frage)

1. **Format:** Konfigurierbares Muster aus Bausteinen: `{Präfix/Bereichskürzel}`, `{Zähler:n}`, `{JJ|JJJJ}`, `{Mandanten-/Einheitencode}`, Trennzeichen. Das deutsche Kanzlei-Default ist `{NNN}/{JJ}` (z. B. `123/26`), das Inhouse/international-Default `{PRÄFIX}-{JJJJ}-{NNNNN}` (z. B. `LEG-2026-00012`). Client-Matter (`10023-0004`) gibt es als Preset. Das Muster wird pro Kanzlei/Mandant (Tenant) gesetzt, optional pro Rechtsgebiet bzw. Aktentyp überschreibbar.
2. **Zeitpunkt:** Zwei Nummern. Bei Erfassung bekommt die Anfrage eine technische Intake-ID (Dataverse-Autonumber genügt, Lücken egal). Die finale Aktennummer wird erst beim Statuswechsel „Eröffnet" nach Konfliktfreigabe vergeben (§ 43a Abs. 4 BRAO / § 3 BORA). Ein manueller Override (z. B. Migration, Altakten) ist nur mit Recht und Eindeutigkeitsprüfung erlaubt.
3. **Lückenlosigkeit:** Keine Rechtspflicht für Aktennummern. Garantiert werden **Eindeutigkeit und Unveränderbarkeit nach Vergabe**, vergeben wird „best effort gapless": Weil die Nummer erst bei Eröffnung transaktional gezogen wird, entstehen praktisch keine Lücken. Vergebene Nummern werden nie wiederverwendet, auch nicht nach Storno oder Löschung, sondern bleiben als „storniert" stehen. Rechnungsnummern bleiben im ERP bzw. der Buchhaltung (§ 14 UStG).
4. **Reset/Zähler:** Zählerdimensionen konfigurierbar: global, pro Jahr (Default in Deutschland), pro Standort, pro Bereich/Präfix, pro Mandant. Umgesetzt wird das als Zählertabelle (Schlüssel = Dimensionen + Jahr) mit sperrender, transaktionaler Vergabe, nicht über die native Autonumber.
5. **Hierarchie:** Mandant (bzw. Geschäftseinheit/Gesellschaft für Rechtsabteilungen) als Pflicht-Lookup an der Akte. Ein Code in der Nummer ist nur optional und wird bei Vergabe eingefroren. Fremde Aktenzeichen (Gericht, Gegner, Mandanten-Referenz, eBilling-ID) liegen als eigene Felder an der Beteiligtenrolle bzw. Akte.
6. **Einstellungen:** Drei Ebenen (Kanzlei/Tenant → Bereich/Rechtsgebiet/Standort → Aktentyp) mit Vererbung. Technische und fachliche Einstellungen liegen in getrennten Bereichen mit getrennten Rollen (Sysadmin vs. fachlicher Admin). Das Dataverse-Audit ist auf allen Konfigurationstabellen aktiv. Änderungen am Nummernschema wirken nur auf neue Akten und werden mit Gültig-ab versioniert. Eine Massenumbenennung von Bestandsakten bleibt ein bewusster, protokollierter Sondervorgang.
