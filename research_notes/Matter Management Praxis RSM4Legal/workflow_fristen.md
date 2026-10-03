# Workflow, Status Models, Automatic Tasks, Deadlines (Fristen) and Emails in Legal Matter Management – Practice and German Deadline Rules (for RSM4Legal)

Research date: 2026-10-03. Method note: direct page fetches to lto.de, help.clio.com, onlinehilfe.advoware.de and 2b1inc.com were blocked by the egress proxy in this environment; findings for those sources are based on search-result extracts (title + snippet) and are marked accordingly. Statute references point to gesetze-im-internet.de (primary source, not fetched; content stated from well-known statutory text).

## 1. How do products model matter lifecycle / status / phases and workflow automation?

### Takeaway
The market pattern is: one configurable, per-matter-type (practice area) list of stages/phases, shown as kanban or a "current phase" field, plus a separate rules engine ("automated workflows") that reacts to stage changes (and other events) by applying task-list templates, generating documents and sending templated emails. German Kanzleisoftware is historically deadline-centric (Fristenkalender, Wiedervorlagen, Verfügungen) rather than stage-centric; newer cloud products (Actaport) move toward stage-driven workflows per Aktentyp.

### Cited Findings
**Clio (Manage/Grow) – the clearest reference model for SMB firms**
- Matter stages are kanban-style boards tracking where each matter sits; stages are connected to practice areas, with one stages board per practice area; up to 25 stages per practice area; board can be filtered (client, attorney) and sorted (alphabetical, last movement date). — [Clio Help: Create and Manage Matter Stages](https://help.clio.com/hc/en-us/articles/15083241879195-Create-and-Manage-Matter-Stages) (search extract)
- Clio Manage "Automated Workflows" (Settings > Automated Workflows) can apply task lists, generate documents, or apply matter templates when there is a new matter or a change in stage; prebuilt recipe "Matter stage changed → Assign task list"; also "Matter stage changed → Generate a document" using document templates with matter data. — [Clio Help: Clio Manage Automated Workflows](https://help.clio.com/hc/en-us/articles/35132279298843-Clio-Manage-Automated-Workflows) (search extract); [AI for Law Firms – Clio automated workflows setup](https://aiforlawfirms.org/how-to-setup-clio-automated-workflows/)
- Clio Grow (intake/CRM) automated workflows: when a lead moves to a stage, automatically send a confirmation email and pre-consultation questionnaire with a chosen email template. — [Clio Help: Clio Grow Automated Workflows](https://help.clio.com/hc/en-us/articles/17770743592219-Clio-Grow-Automated-Workflows) (search extract)
- Consultant commentary positions task lists + matter stages + automated workflows as the three building blocks that "make the work move", and describes gaps filled via Zapier (e.g. "update matter stage and assign next task lists" when review tasks complete). — [2b1 Inc: Clio what's missing part 3](https://2b1inc.com/clio-whats-missing-part-3-of-4-make-the-work-move-task-lists-matter-stages-and-automated-workflows/); [Zapier template](https://zapier.com/automations/legal/legal-operations/matter-management/update-matter-stage-and-assign-next-task-lists)

**Mitratech TeamConnect (enterprise ELM, in-house)**
- Matters carry a "Current Phase" field (e.g., open phase); document folders, tasks and appointments can be added at points in the matter lifecycle. — [TeamConnect Tips and Tricks Jan 2023](https://success.mitratech.com/TeamConnect/TeamConnect_Webinars/January_2023_-_TeamConnect_Tips_and_Tricks/January_2023_-_TeamConnect_Tips_and_Tricks)
- "Workflow Processes" are separate from phases: they provide structure and enforcement for routed approval flows (e.g., invoice posting request staff → manager → director), with one or more users responsible per stage; parts can be automated. — [TeamConnect Enterprise User Guide: Workflow Processes](https://success.mitratech.com/TeamConnect/Enterprise_User_Guide/Workflow_Processes)

**Onit (enterprise ELM)**
- Onit Apptitude is a low-code workflow layer above ELM modules (matter mgmt, eBilling, legal requests, CLM) that "defines behavior: how work moves, who approves it, what triggers next steps"; matter workflows can trigger actions on matter status, risk thresholds or deadlines. — [Swiftwater: What is Onit Apptitude](https://swiftwaterco.com/insights/onit-apptitude/) (third-party consultant, not vendor doc)

**LawVu (in-house)**
- Marketing describes AI triage/assignment, smart intake forms and automated workflows for matters; the concrete documented drag-and-drop workflow builder is for invoice approval (phases, sequential approvers by matter type/amount). — [LawVu Matter Management](https://lawvu.com/workspace/matter-management/); [LawVu invoice approval workflows](https://lawvu.com/product/streamline-your-legal-operations-with-automated-invoice-approval-workflows/)

**Legisway (Wolters Kluwer, in-house, DE market)**
- Covers contracts, entities, compliance, litigation, IP; offers notifications on upcoming deadlines, automatic reminders, automated workflows for task assignment, contract lifecycle incl. renewal/termination. — [Legisway Claims & Litigation (DE)](https://www.wolterskluwer.com/de-de/solutions/legisway/claims-litigation); [Legisway Retail (DE)](https://www.wolterskluwer.com/de-de/solutions/legisway/retail)

**Thomson Reuters Legal One**
- Positioned as matter/case mgmt + time + billing; claims lifecycle tracking of litigation "from initial filing" with deadline adherence; no German-specific workflow detail found. — [Softwarefinder: Legal One](https://softwarefinder.com/legal/legal-one) (aggregator, low reliability)

**German Kanzleisoftware**
- Actaport: Fristen, Termine, Wiedervorlagen and Aufgaben managed centrally in the Akte, linked with documents/notes; templates with placeholders/Textbausteine prefilled from the Akte; API can create/change Aufgaben and Wiedervorlagen. — [Actaport Aktenmanagement](https://www.actaport.de/produkt/aktenmanagement); [Actaport Dokumentenverwaltung](https://www.actaport.de/produkt/dokumentenverwaltung). A search extract claimed "konfigurierbare Workflow-Stages pro Aktentyp; Aufgaben, Fristen und Wiedervorlagen werden automatisch aus dem Workflow abgeleitet" but could not be attributed to a specific vendor page — UNVERIFIED.
- RA-MICRO: module Termine/Fristen calculates and notes Fristen including Vorfristen; holiday settings per Bundesland (federal holidays recognized automatically, Land holidays selectable). — [RA-MICRO Handbuch Termine/Fristen (PDF)](https://wissenspool.ra-micro.de/wp-content/uploads/RM-Handbuch-Termine-Fristen.pdf); [RA-MICRO Hinweis Feiertage Berlin](https://www.ra-micro.de/service/informationen/aktuelle-hinweise/termine-fristen-einstellungen-feiertage-fuer-das-bundesland-berlin.html); [RA-MICRO Onlinehilfe Terminverwaltung](https://onlinehilfen.ra-micro.de/index.php/Terminverwaltung_(Einstellungen))
- Advoware: daily task overview (Wiedervorlagen, Fristen, Aufgaben, Posteingang); automatic Wiedervorlage for each new Akte configurable; Wiedervorlage series; Fristende auto-calculated from Fristbeginn per configured Fristart (days/months/years); setting to roll to next working day or warn when date hits weekend/holiday. — [Advoware: automatische Wiedervorlagen für neue Akten](https://onlinehilfe.advoware.de/Documents/automatischewiedervorlagenf%C3%BCrneueakten1.html); [Advoware: Fristen und Vorfristen eintragen](https://onlinehilfe.advoware.de/Documents/fristenundvorfristeneintragen1.html); [Advoware: Wiedervorlagen – Serien](https://onlinehilfe.advoware.de/Documents/wiedervorlagenserien1.html) (search extracts)
- DATEV Anwalt classic: firm-wide Fristen-/Wiedervorlage-/Terminverwaltung synchronized with Outlook, Postein-/-ausgangsbuch; Verfügungen open a task-capture window prefilled with due date; "erledigt" checkbox in (Teil-)Verfügungen. — [DATEV Anwalt classic](https://www.datev.de/web/de/rechtsberatung/loesungen/mandatsbearbeitung/akte-verwalten/datev-anwalt-classic); [DATEV shop](https://www.datev.de/web/de/shop/produkt-details/anwalt-classic-48611)

### Inferences
- Two architectural families: (a) stage/phase field + event rules (Clio, TeamConnect, Onit, Actaport-newer); (b) deadline/Verfügung-centric with templates (RA-MICRO, Advoware, DATEV). RSM4Legal on Dataverse naturally fits (a) but must embed (b)'s Fristen rigor for German litigation.
- Approval routing (TeamConnect "Workflow Processes", LawVu invoice workflows) is typically modelled separately from the matter lifecycle – keep approvals out of the matter status model.

### Gaps
- No primary documentation found for Litera Foundation/Workflow, HighQ, or Legal One Germany workflow configuration within the tool budget.
- Actaport's exact workflow-stage configuration could not be verified from a vendor page.

## 2. Single leading concept: status vs. phase vs. process stage; per matter type or global?

### Takeaway
Vendors avoid redundancy by having exactly one user-visible lifecycle field per matter (Clio "Matter Stage", TeamConnect "Current Phase") that is scoped per practice area/matter type, plus a small global lifecycle flag (open/pending/closed). Automation hangs off that one field.

### Cited Findings
- Clio: matter stages are per practice area (one board per practice area, max 25 stages each), separate from the global matter status (Open/Pending/Closed – Clio standard field; not separately verified in this session). — [Clio Help: Matter Stages](https://help.clio.com/hc/en-us/articles/15083241879195-Matter-Stages) (search extract)
- TeamConnect uses a "Current Phase" field on the matter, while approval workflows are a separate object. — [TeamConnect Tips Jan 2023](https://success.mitratech.com/TeamConnect/TeamConnect_Webinars/January_2023_-_TeamConnect_Tips_and_Tricks/January_2023_-_TeamConnect_Tips_and_Tricks); [Workflow Processes](https://success.mitratech.com/TeamConnect/Enterprise_User_Guide/Workflow_Processes)

### Inferences
- Recommendation for RSM4Legal: make "Phase" (per matter type, defined in a configuration table e.g. `rsm_matterphase` related to `rsm_mattertype`) the single leading concept; derive Dataverse statecode (Active/Inactive) and a coarse global status reason (Open / On hold / Closed) from it. The Business Process Flow should be a visualization/guidance of that same phase list, not a second source of truth: either one BPF per matter type whose stages map 1:1 to phase records, or (more flexible, avoids BPF sprawl) a custom phase lookup with a PCF/kanban control, and BPF only where guided data capture per stage is needed. Sync direction must be one-way (phase → BPF active stage) to avoid drift.
- Status models per matter type (like Clio practice areas) with an optional shared "template" set to reduce maintenance.

### Gaps
- No vendor documentation found explicitly discussing "status vs. phase" redundancy; recommendation is inferred.

## 3. Task templates: relative due dates, role-based assignment, multiple people, re-entry, transition enforcement

### Takeaway
Relative due dates (offset from trigger/another task) and template task lists applied on stage entry are standard (Clio). Role-based assignment and re-entry/duplicate handling are thinly documented publicly; enforcement of allowed transitions is mostly absent in SMB tools (free drag on kanban) and present in enterprise rule engines.

### Cited Findings
- Clio task lists: series of tasks per case type; relative task deadlines; lists can be duplicated and assigned from inside a matter. Relative due date = due a specific amount of time before/after another task linked to the matter (e.g., Task B "3 days after" Task A completed). — [Clio Help: Task Lists](https://help.clio.com/hc/en-us/articles/9206286672155-Task-Lists); [Clio Help: Manage Tasks](https://help.clio.com/hc/en-us/articles/9204917906971-Manage-Tasks-in-Clio-Manage); [2b1 immigration playbook](https://2b1inc.com/a-field%E2%80%91tested-playbook-for-automated-workflows-in-clio-manage-for-immigration-practices/) (search extracts)
- Clio kanban allows dragging matters between stages (column reorder, filtering); no evidence found of transition rules. — [Clio Help: Matter Stages](https://help.clio.com/hc/en-us/articles/15083241879195-Create-and-Manage-Matter-Stages) (search extract)
- TeamConnect workflow processes: one or more users responsible for activities at each stage, enforced routing. — [TeamConnect Workflow Processes](https://success.mitratech.com/TeamConnect/Enterprise_User_Guide/Workflow_Processes)
- Advoware: automatic Wiedervorlagen per new Akte and auto-rescheduling of expired Wiedervorlagen (delete & re-enter after expiry). — [Advoware: automatische Wiedervorlagen](https://onlinehilfe.advoware.de/Documents/automatischewiedervorlagen.html) (search extract)

### Inferences (recommendations)
- Task template fields: offset (value + unit: calendar days / working days / weeks / months), base (phase-entry date, matter field date e.g. Zustellungsdatum, or completion of predecessor task), roll-forward rule (none / next working day per holiday calendar), assignee rule (matter role e.g. Responsible Lawyer, Assistant, Team/Queue).
- Multiple people per role: offer per template "one task to a team/queue (first to pick)" vs. "one task per person (all must complete)" – Dataverse supports owner = Team natively, so default to a team-owned task for "one of", and fan-out for "all".
- Re-entry/regression: keep idempotency key (matter + template task + phase-entry iteration). Default: do not create duplicates if an open task from the same template exists; on re-entry create a new set only if the previous instance is closed and the template flag "repeat on re-entry" is set. On regression, do not auto-cancel completed tasks; optionally cancel open tasks of later phases (configurable). Never auto-delete Fristen (see section 4 – audit requirement).
- Transitions: configure an allowed-transition matrix per matter type (from-phase → to-phase, optional required fields/role). SMB tools do not enforce this, but Dataverse can (plugin pre-validation) and in-house departments value it for reporting quality.

### Gaps
- Could not verify whether Clio task lists assign by role (e.g., "responsible attorney") vs. named users only, nor how Clio handles a task list re-applied on stage re-entry (search extracts silent; full help pages were not fetchable).

## 4. German deadline calculation and Fristenkontrolle requirements

### Takeaway
Fristberechnung follows §§ 187–193 BGB (via § 222 ZPO for court deadlines); for non-uniform holidays the holiday law of the place where the deadline must be met (court location) governs, not the firm's seat. BGH demands: Fristenkalender, Vorfrist (approx. one week) for Rechtsmittelbegründungsfristen, Streichen only after verified completion, gestufte abendliche Ausgangskontrolle, beA completion only after Eingangsbestätigung, Erledigungsvermerk in the Handakte, and – since BGH 04.03.2026 XII ZB 338/24 – electronic calendars where changed/deleted deadlines remain permanently visible.

### Cited Findings
**Statutory calculation**
- § 187 BGB (event day not counted for event-triggered periods; Abs. 2 day-beginning periods), § 188 BGB (end: weeks/months end on the day with same name/number as event day; if missing in month → last day of month), § 189 (half-month = 15 days), § 191, § 193 BGB (if last day for a declaration/performance is Saturday, Sunday or state-recognized public holiday at the place of declaration/performance → next working day). — [§§ 187–193 BGB, gesetze-im-internet](https://www.gesetze-im-internet.de/bgb/__187.html) (statutory text; not fetched)
- § 222 ZPO: court deadlines calculated per BGB; if end falls on Sunday, general holiday or Saturday → end of next working day; hour periods exclude Sundays/holidays/Saturdays. — [§ 222 ZPO (buzer)](https://www.buzer.de/222_ZPO.htm); [JuraForum § 222 ZPO](https://www.juraforum.de/gesetze/zpo/222-fristberechnung)
- For non-federal holidays the holiday law of the Land where the deadline must be met (court seat) governs; a holiday at the firm's seat is irrelevant if the court sits elsewhere. — [iurado: Feiertage Bundesland maßgeblich §§ 222, 233 ZPO](https://www.iurado.de/?p=urteile&site=iurado&id=2283&page=1&type=2); [IWW AK: Feiertagsfalle Gerichtsort](https://www.iww.de/ak/kanzleiorganisation/fristen-feiertagsfalle-ist-der-feiertag-auch-am-gerichtsort-gesetzlich-anerkannt-f149626)
- § 193 BGB does NOT apply (directly or by analogy) to Kündigungsfristen – BGH 17.02.2005 III ZR 172/04 (protection of the termination recipient); Saturday counts as Werktag in the mietrechtliche Karenzzeit – BGH 27.04.2005 VIII ZR 206/04. — [NJW 2005, 1354 (III ZR 172/04)](https://lorenz.userweb.mwn.de/urteile/iiizr172_04.htm); [urteile.news VIII ZR 206/04](https://urteile.news/BGH_VIII-ZR-20604_Sonnabend-ist-bei-der-Berechnung-der-Karenzzeit-zur-Wahrung-der-Kuendigungsfrist-mitzuzaehlen~N441)

**Vorfrist**
- Lawyer must ensure by general instruction that whenever a Rechtsmittelbegründungsfrist is entered, an adequate Vorfrist is also entered; Vorfrist should generally be about one week; purpose: leave review/processing time for irregularities. Missing Vorfrist = Organisationsverschulden. — [Stollfuß blog 23.10.2025: BGH Vorfrist](https://www.stollfuss.de/blog/BGH-zur-Pflicht-des-Rechtsanwalts-zur-Eintragung-einer-Vorfrist-im-Fristenkalender-2025-10-23); [ZAP: Pflicht zur Eintragung einer Vorfrist](https://www.zap-zeitschrift.de/bgh-pflicht-zur-eintragung-einer-vorfrist-in-den-fristenkalender/); [addlegal: Vorfristen bei Rechtsmittelbegründungsfrist](https://www.addlegal.de/beitraege/bgh-vorfristen-bei-rechtsmittelbegrundungsfrist)

**Delegation, Aktenvorlage, Erledigungsvermerk**
- Noting/monitoring of deadlines may be delegated to carefully selected, trained, reliable staff, but whenever files are presented for a deadline-bound procedural act the lawyer must check the deadline personally; a weekly printout is not sufficient; check may be done via (electronic) Handakte and its Erledigungsvermerk confirming the calendar entry; e-file must not be less secure than paper. — [Deutscher AnwaltSpiegel: Elektronische Fristenkontrolle und Legal Tech](https://www.deutscheranwaltspiegel.de/disputeresolution/legacy/elektronische-fristenkontrolle-und-legal-tech-149993/); [BGH 31.07.2024 XII ZB 573/23 (anwalt24)](https://www.anwalt24.de/urteile/bgh/2024-07-31/xii-zb-573_23); [beck-aktuell: BAG 6 AZR 155/23 follows BGH line (2025)](https://www.beck-aktuell.de/rechtsbranche/anwaltschaft/bag-6azr15523-frist-sorgfaltspflicht-anwaelte-bgh-2025-02-20)

**Streichen nur nach Erledigung, Ausgangskontrolle, beA**
- Gestufte Ausgangskontrolle: evening check by assigned staff against the Fristenkalender whether deadline matters were actually completed/sent; deadlines may only be struck/marked done after verifying in the file that nothing remains to be done. — [Anwaltsblatt: BGH Vorgaben Ausgangskontrolle beA](https://anwaltsblatt.anwaltverein.de/de/anwaeltinnen-anwaelte/anwaltspraxis/bgh-macht-vorgaben-zur-ausgangskontrolle-beim-bea-versand); [Anwaltsblatt: Gestufte Ausgangskontrolle](https://anwaltsblatt.anwaltverein.de/de/themen/recht-gesetz/bgh-gestufte-ausgangskontrolle-fristversaeumnis)
- With beA, deadlines may only be marked done after receipt of the automated Eingangsbestätigung (§ 130a Abs. 5 ZPO); the transmission protocol is not the same as the confirmation. — [Stollfuß 13.03.2024: Ausgangskontrolle beA](https://www.stollfuss.de/blog/BGH-zu-den-Anforderungen-an-die-Ausgangskontrolle-bei-der-Versendung-fristgebundener-Schriftsaetze-ueber-das-beA-2024-03-13); [addlegal: beA-Sorgfaltsanforderungen](https://www.addlegal.de/beitraege/bgh-zu-den-bea-sorgfaltsanforderungen)

**Electronic Fristenkalender**
- BGH 28.02.2019 III ZB 96/18: with an electronic calendar, entries must be checked via printout of entered items or an error log (Kontrollblatt), because input errors are harder to spot than in paper calendars. — [LTO: BGH will einen Ausdruck](https://www.lto.de/recht/juristen/b/bgh-iii-zb-96-18-fristen-elektronischer-kalender-anwalt-organisationsverschulden); [Anwaltsblatt: Kontrolle nur über Papierausdruck](https://anwaltsblatt.anwaltverein.de/de/themen/recht-gesetz/fristenkontrolle-beim-elektronischen-fristenkalender-nur-ueber-papierausdruck); [MIR full text](https://medien-internet-und-recht.de/volltext.php?mir_dok_id=2917). Software vendors' reaction discussed at [legal-tech.de](https://legal-tech.de/diskussion-um-bgh-beschluss-zur-elektronischen-fristenkontrolle-das-ist-die-sichtweise-der-software-anbieter/)
- BGH 04.03.2026 XII ZB 338/24: facts – staff correctly entered appeal and Begründungsfrist with Vorfrist and printed the Kontrollblatt, but later, when only adding the court file number, overwrote all entries; the software did not show the changes. Held: Fristenkalender (also electronic) must keep changed and deleted deadlines permanently recognizable and verifiable; the original entry must not be overwritten; using software that does not show changes = Organisationsverschulden, Wiedereinsetzung denied. — [LTO: Elektronischer Kanzleikalender muss Änderungen anzeigen](https://www.lto.de/recht/juristen/b/bgh-xiizb33824-frist-kalender-elektronisch-versauemt-geaenderte-frist-ueberschrieben); [Haufe: Fristenkalender muss Änderungen erkennen lassen](https://www.haufe.de/recht/kanzleimanagement/bgh-fristenkalender-muss-aenderungen-erkennen-lassen_222_683252.html); [NWB Datenbank](https://datenbank.nwb.de/Dokument/1091625/); [jura.cc](https://www.jura.cc/rechtstipps/elektronischer-fristenkalender-ohne-sichtbare-fristaenderungen-genuegt-nicht/) (all based on search extracts; consistent across sources)
- Advoware publishes an help page "Anforderungen an ein elektronisch geführtes Fristenbuch" (content not retrievable here). — [Advoware Onlinehilfe](https://onlinehilfe.advoware.de/Documents/anforderungenaneinelektronischgef%C3%BChrtesfristenbuch1.html)

**Product implementation**
- RA-MICRO: Vorfrist computed either relative to Fristbeginn ("NACH Beginndatum") or before Fristende ("VOR Fristende"); Land holidays configurable, federal holidays automatic, used in calculation. — [RA-MICRO Handbuch Termine/Fristen](https://wissenspool.ra-micro.de/wp-content/uploads/RM-Handbuch-Termine-Fristen.pdf); [RA-MICRO Onlinehilfe](https://onlinehilfen.ra-micro.de/index.php/Terminverwaltung_(Einstellungen))
- Advoware: Fristarten with configured length; auto Fristende; roll to next working day or warning on weekend/holiday; separate "Fristen und Vorfristen eintragen". — [Advoware: Fristen und Vorfristen eintragen](https://onlinehilfe.advoware.de/Documents/fristenundvorfristeneintragen1.html)
- DATEV: Fristen/Wiedervorlagen with erledigt-flag in Verfügungen; Outlook sync. — [DATEV Anwalt classic](https://www.datev.de/web/de/rechtsberatung/loesungen/mandatsbearbeitung/akte-verwalten/datev-anwalt-classic)

### Inferences (recommendations for RSM4Legal)
- Separate entity "Frist" (not a generic Dataverse task) with: Fristart (catalog: e.g. Berufungsfrist 1 Monat Notfrist, Berufungsbegründung 2 Monate, Einspruch VU 2 Wochen Notfrist), Notfrist flag, Fristbeginn/Zustellungsdatum, computed Fristende, Vorfrist(en) (default 7 days before end for Begründungsfristen, configurable per Fristart), maßgebliches Gericht → Bundesland → holiday calendar, calculation trace, Erledigt-durch/am, Erledigungsart (e.g. "beA Eingangsbestätigung vom …"), Vier-Augen check (entered by / checked by), Kontrollblatt/print or check view.
- Immutable audit: never hard-delete or overwrite Fristen; changes create versions (Dataverse auditing on + custom history table visible in UI, because auditing alone is not readily visible to staff); deletion = status "storniert" with reason, still visible in the calendar (XII ZB 338/24).
- Completion only by authorized roles and only with evidence (link to sent document/beA confirmation) – status-change-triggered automation must NEVER auto-complete or delete a Frist.
- Calculation engine: implement §§ 187/188/193 BGB + § 222 ZPO with holiday table per Bundesland (incl. Augsburg Friedensfest, Fronleichnam regional variants – note some holidays are municipal/partial within a Land; mark as edge case), selectable "Fristende-Verschiebung anwenden" (off for Kündigungsfristen, per III ZR 172/04), and require the user to confirm the computed date (lawyer responsibility – software as aid).
- Daily Fristenliste/Ausgangskontrolle view (all Fristen due today/next days per lawyer, unacknowledged) as Dataverse view/dashboard plus printable report.

### Gaps
- Full text of XII ZB 338/24 not retrieved; exact wording on whether a visible change history inside the software suffices vs. printouts not verified.
- No BRAK official guidance document on electronic Fristenkalender found within budget.
- Holiday data source (e.g. official API) not researched; municipal holidays (Augsburg 8 Aug; Fronleichnam in parts of Saxony/Thuringia) need a court-location-level holiday model – marked uncertain.

## 5. In-house legal (non-litigation) deadlines: Kündigungsfristen, Vertragslaufzeiten, Wiedervorlage

### Takeaway
In-house tools (Legisway, LawVu, TeamConnect, Onit) treat these as contract key dates with reminder notifications and workflows (renewal/termination), not as ZPO-style Fristen; Wiedervorlagen are generic follow-ups.

### Cited Findings
- Legisway: notifications about upcoming deadlines, automatic reminders against missed deadlines, workflows across contract lifecycle incl. renewal and termination. — [Legisway Retail (DE)](https://www.wolterskluwer.com/de-de/solutions/legisway/retail); [Legisway (EN)](https://www.wolterskluwer.com/en/solutions/legisway)
- Onit Apptitude: workflows triggered by matter status, risk thresholds or deadlines. — [Swiftwater: Onit Apptitude](https://swiftwaterco.com/insights/onit-apptitude/)
- Advoware: Wiedervorlage series and automatic Wiedervorlagen. — [Advoware: Wiedervorlagen – Serien](https://onlinehilfe.advoware.de/Documents/wiedervorlagenserien1.html)
- Kündigungsfrist computation: § 193 BGB does not shift the last day for giving notice. — [NJW 2005, 1354](https://lorenz.userweb.mwn.de/urteile/iiizr172_04.htm)

### Inferences
- Model "Key Date" types: Kündigungsfrist (derived = Vertragsende − Kündigungsfrist, no weekend shift, receipt by counterparty), Laufzeitende, automatische Verlängerung, Optionsfrist, Gewährleistungsablauf, Verjährung (end of year rule § 199 BGB), Wiedervorlage. Use multiple reminders (e.g. 90/30/7 days) rather than one Vorfrist; escalation to deputy if unacknowledged.
- Same Frist entity can serve both with a "Fristkategorie" (prozessual / materiell-rechtlich / intern), with stricter controls (Vier-Augen, no delete) mandatory only for prozessual.

### Gaps
- No primary product docs fetched showing exact in-house key-date configuration (LawVu/TeamConnect).

## 6. Automatic emails on status change: drafts vs. automatic send

### Takeaway
SMB products auto-send templated emails mostly in intake/CRM contexts (Clio Grow on lead stage change); for matter work they typically generate documents from templates rather than auto-sending. Automatic sending to clients/opposing parties is rare; internal notifications are routinely automatic.

### Cited Findings
- Clio Grow: on lead stage move, automatically send confirmation email and questionnaire using a selected email template. — [Clio Help: Clio Grow Automated Workflows](https://help.clio.com/hc/en-us/articles/17770743592219-Clio-Grow-Automated-Workflows) (search extract)
- Clio Manage: stage change → generate document from template with matter data (not send). — [Clio Help: Clio Manage Automated Workflows](https://help.clio.com/hc/en-us/articles/35132279298843-Clio-Manage-Automated-Workflows) (search extract)
- External email automation for Clio commonly built via Make/Zapier integrations. — [Make: Clio Manage + Microsoft 365 Email](https://www.make.com/en/integrations/clio-manage/microsoft-email)

### Inferences (recommendation)
- Per email template a "send mode": (1) internal notification – auto send; (2) external (client/counterparty/court) – create Dataverse email activity as draft assigned to the responsible person, to review and send (default); (3) auto-send only for explicitly whitelisted low-risk client updates. Rationale: professional secrecy (§ 43a BRAO, § 203 StGB), wrong-recipient risk, and court communications require beA, not email.
- Status regressions should not re-send emails unless template flag allows; log every generated email on the matter timeline.

### Gaps
- No German Kanzleisoftware documentation found on automated email-on-status features; no BRAK guidance on automated client emails found.
