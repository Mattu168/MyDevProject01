# Templates, Variables, Email/Signatures, Document Assembly and Clause Libraries in Legal Software (as of Oct 2026)

Research notes for RSM4Legal (Dataverse-based matter management, German market first). Method note: several vendor help centers (support.clio.com, actaport.zendesk.com, onlinehilfen.ra-micro.de, thomsonreuters.com, sharepointnutsandbolts.com) were blocked by the network egress proxy during this research, so findings for those come from search-result snippets of the official pages, not full-page reads. Statements from prior knowledge that could not be verified are explicitly marked "(unverified)".

## 1. Variables / merge fields: how products expose them

### Takeaway
Nearly every product generates the variable catalog from its own data model (matter, client/contact, related parties, custom fields) and gives a picker (side panel / task pane / "view merge fields" list). German Kanzleisoftware (Actaport, RA-MICRO, DATEV Anwalt classic) combines placeholders with reusable Textbausteine that may themselves contain placeholders. Pro-grade assembly tools (Contract Express, HotDocs, Docassemble, Clio Draft) add questionnaires, computed fields and conditional logic. Empty-value handling (delete line, fallback text) is a real, documented concern.

### Cited Findings
**Clio (US market leader, reference for "merge fields")**
- Merge fields are "codes used in place of specific client data" that automatically pull information from a contact or matter into documents; Document Automation produces PDF or Word documents, typical use cases engagement letters and retainer agreements — [Clio: What is Document Automation?](https://support.clio.com/hc/en-us/articles/360005473774-What-is-Document-Automation-)
- Merge fields exist only for Contact and Matter fields plus Custom Fields; additional fields for related contacts appear if related contacts are added to the matter — [Clio: List of Standard Merge Fields](https://support.clio.com/hc/en-us/articles/206803247-Document-Automation-List-of-Standard-Merge-Fields-); [Clio: Related Contact Merge Fields](https://support.clio.com/hc/en-us/articles/5310389465371-Related-Contact-Document-Merge-Fields)
- Catalog is discoverable in Settings > Documents and via "View Merge Fields" when adding a template — [Clio: Document Templates in Clio Manage](https://help.clio.com/hc/en-us/articles/53353783646875-Document-Templates-in-Clio-Manage)
- Custom fields of all types can be used as merge fields provided they are added to the matter; there is a dedicated article on custom contact-type fields — [Clio: Merge fields for contacts in custom fields](https://support.clio.com/hc/en-us/articles/360009691533-Are-Document-Automation-Merge-Fields-Available-for-Contacts-Selected-in-Custom-Fields-)
- Clio has a dedicated article on how empty merge fields populate (i.e., empty-value behavior is a recurring support question) and a separate one on whether task merge fields exist — [Clio: Empty merge fields](https://support.clio.com/hc/en-us/articles/360003738214-How-do-Empty-Merge-Fields-Populate-on-an-Automated-Document-); [Clio: Merge fields for tasks](https://support.clio.com/hc/en-us/articles/360007694693-Are-there-Merge-Fields-for-Tasks-)
- Clio Draft (formerly Lawyaw, acquired by Clio) uses a "Template Builder" with "Cards and Fields" (questionnaire-style grouping of fields) — [Clio Draft: Manage Cards and Fields](https://help.clio.com/hc/en-us/articles/41958729758491-Clio-Draft-Manage-Cards-and-Fields-in-the-Template-Builder)
- Clio Grow has its own document templates (intake/engagement) — [Clio Grow Document Templates](https://help.clio.com/hc/en-us/articles/9290238939163-Document-Templates-in-Clio-Grow)

**Actaport (German cloud Kanzleisoftware)**
- Templates (Vorlagen), placeholders (Platzhalter) and Textbausteine generate prefilled documents directly from the Akte; placeholders are also available inside Microsoft Word — [Actaport Funktionen](https://webproject.actaport.de/de/warum_actaport/funktionen.php); [Actaport Booklet (PDF)](https://we.actaport.de/MEDIEN/NEWSCENTER/PDF/Actaport_Booklet_3pager.pdf)
- Textbausteine with placeholders can be inserted into templates, documents, e-mails and notes — i.e. one shared snippet/variable engine across channels — [Actaport: Platzhalter in Textbausteine einfügen](https://actaport.zendesk.com/hc/de/articles/4407774738322-Platzhalter-in-Textbausteine-einf%C3%BCgen); [Actaport: Textbausteine einfügen](https://actaport.zendesk.com/hc/de/articles/360011604700-Textbausteine-einf%C3%BCgen)
- Per-placeholder option "Zeile löschen" in Kanzleiverwaltung > Vorlagen removes blank lines that result from empty placeholders at generation time — [Actaport: Platzhalter formatieren](https://actaport.zendesk.com/hc/de/articles/360011731960-Platzhalter-formatieren)
- Firm-wide (kanzleiweit) templates and Textbausteine are maintained centrally — [Actaport: Vorlagen und Textbausteine hinterlegen](https://actaport.zendesk.com/hc/de/articles/9137869393052-Vorlagen-und-Textbausteine-hinterlegen)
- Invoice-specific Textbaustein placeholders exist ("Textbaustein 1 (Rechnung)") — [Actaport](https://actaport.zendesk.com/hc/de/articles/4405228386194-Platzhalter-Textbaustein-1-Rechnung)

**RA-MICRO**
- Word integration with "Sternchenaufrufe" (asterisk short calls): Textbausteine are inserted by typing e.g. `*textl12`; different placeholder types are replaced by Akten- or program data on creation/printing — [RA-MICRO Onlinehilfe: Platzhalter + Kurzaufrufe](https://onlinehilfen.ra-micro.de/index.php/Platzhalter_+_Kurzaufrufe); [Überblick Platzhalter](https://onlinehilfen.ra-micro.de/index.php/%C3%9Cberblick_Platzhalter)
- Dedicated "Rubrumplatzhalter/Stammdaten" (party/rubrum data) — [RA-MICRO: Rubrumplatzhalter](https://onlinehilfen.ra-micro.de/index.php/Rubrumplatzhalter/Stammdaten_(Word))
- Textbausteine are recommended/supplied in RTF format; features include rubrum transfer, automatic salutation, closing phrases, letterhead, Serienbrief/mass mailings — [RA-MICRO Seminare: Word/Textbausteine/Briefkopf](https://ra-micro-seminare.de/seminare/word-textbausteine-briefkopf)

**DATEV Anwalt classic**
- Own standard documents can be created and fields inserted via a "Platzhalter" task pane; Textbausteine can be created and integrated into "Assistenten"; supports Serienbriefe/mass mailings and e-mails; multiple letterheads selectable at creation time — [DATEV Hilfe: Überblick Schriftguterstellung](https://apps.datev.de/knowledge/redirects/v1/hilfe/1004227); [DATEV: Anpassung und Erstellung von Anwalt-Vorlagen](https://help-center.apps.datev.de/documents/1000291)
- DATEV publishes a field catalog ("Übersicht der Felder für Anwalt-Vorlagen") — [DATEV Hilfe 1000307](https://help-center.apps.datev.de/documents/1000307)

**Advoware** — No primary documentation found in this session (see Gaps).

**Thomson Reuters Contract Express**
- Authors mark up Word templates with bracket markup; fields in curly braces `{ }` can hold variables (dates, names, amounts), calculations, cross-references and references to text in other templates; conditional text supported; output driven by a questionnaire — [Contract Express Key Concepts](https://www.thomsonreuters.com/en-us/help/contract-express/getting-started/key-concepts); [Wikipedia: ContractExpress](https://en.wikipedia.org/wiki/ContractExpress)

**HotDocs**
- In DOCX templates, HotDocs fields are Word content controls containing a data reference or instruction; they cannot be edited directly in Word (edited via HotDocs Author) — [HotDocs Fields Overview](https://help.hotdocs.com/preview/help/HotDocs_Fields_Overview.htm); [HotDocs Templates Overview](https://help.hotdocs.com/preview/help/HotDocs_Templates_Overview.htm)

**Docassemble (open source)**
- DOCX templates use Jinja2 via python-docx-template: `{{ variable }}`, `{% if %}…{% endif %}`, paragraph-level `{%p if %}` to remove whole paragraphs — [docassemble: Assembling documents](https://docassemble.org/docs/documents.html); [Suffolk LIT Lab: Working with DOCX](https://assemblyline.suffolklitlab.org/docs/authoring/docx/)

**Microsoft SharePoint Premium (Syntex) Content Assembly / "Modern Templates"**
- Upload a Word document, add placeholders in the browser; fields accept manual input (text, hyperlink, image, date) or pull values from a SharePoint list/library or Managed Metadata; tables can be bound to lists (multiple records); optional conditional sections; owners publish the template, users create docs by filling fields — [Plumsail blog](https://plumsail.com/blog/documents-generation-sharepoint-copilot/); [Cloudwell](https://cloudwell.io/sharepoint-premium-content-assembly-how-to-streamline-document-creation/); [Sari Soinoja: contract management with Content Assembly](https://www.sarisoinoja.com/blog/2024-7-31-contract-management-with-sharepoint-premium-content-assembly)

**Dataverse native Word templates (relevant platform baseline)**
- Use Word's XML Mapping Pane to bind content controls to Dataverse fields; plain text content controls are common — [Databear](https://databear.com/generate-word-documents-from-dataverse-no-code/); [Power Platform Girl: native Word templates](https://powerplatformgirl.com/articles/stop-over-engineering-document-generation-in-d365-the-guide-to-native-word-templates)
- Limitations: forgotten field requires re-creating the template from Dynamics and re-mapping; rich text controls cause formatting glitches — [Power Platform Girl](https://powerplatformgirl.com/articles/stop-over-engineering-document-generation-in-d365-the-guide-to-native-word-templates)

### Inferences
- Common pattern: (a) catalog auto-derived from data model incl. related records and custom fields; (b) picker in Word add-in/task pane and in the web editor; (c) snippets (Textbausteine) that contain variables; (d) explicit empty-value rules. RSM4Legal's single `{variable}` engine for email/task/document matches Actaport's model (placeholders shared across documents, e-mails, notes) and is a recognised German-market expectation.
- Recommendation: generate the variable catalog from Dataverse metadata (Matter, Client, Mandant-contacts, Gegner, Gericht, Aktenzeichen, Responsible lawyer, current user, firm/organisation) with dotted paths (`{Matter.Client.Name}`), display labels in German, and support: format specifiers (`{Matter.OpenedOn:dd.MM.yyyy}`, currency), fallback (`{Gegner.Name|"N.N."}`), "remove line if empty", computed fields (Briefanrede/salutation "Sehr geehrte Frau Dr. …", Rubrum, Aktenzeichen-Formatter, date in words), and role-based collections (all Beteiligte). Version the catalog so templates do not break when fields are renamed.
- German specifics (unverified, from domain knowledge): automatic salutation logic (Anrede/Titel/Geschlecht), Rubrum, eigenes/fremdes Aktenzeichen, beA-SAFE-ID, Gerichtsadresse are standard placeholders in RA-MICRO/DATEV/Advoware-type products and should be in the MVP catalog.

### Gaps
- Exact syntax of Clio merge fields (believed to be Word MERGEFIELD «…» style, e.g. «Matter.Client.Name», unverified — help pages blocked).
- Advoware, Litera (Foundation/Contract Companion), SmartDocuments, Bryter, Templafy document variables, Woodpecker, Lawyaw/Clio Draft variable syntax — no primary docs retrieved. From prior knowledge (unverified): Woodpecker and Templafy work as Word add-ins with field panes/data sources; SmartDocuments (used in NL/DE, Wolters Kluwer partner — [SmartDocuments partner page](https://smartdocuments.com/partners/wolters-kluwer/)) uses questionnaires and building blocks; Bryter is a no-code decision/document automation platform.

## 2. Placeholder technique in Word: text tags vs content controls vs fields; split-run problem

### Takeaway
Three camps: text tags (`{{x}}`, `{x}`, `[[x]]`: Docassemble, docxtemplater, Contract Express bracket markup), Word content controls (HotDocs, Dataverse native templates, SharePoint-type tooling) and legacy MERGEFIELD/DOCVARIABLE fields (Serienbrief tradition). Text tags are easiest for authors but suffer from Word splitting a tag across multiple runs; content controls are robust, addressable and lockable but harder to author without an add-in.

### Cited Findings
- Word may split visually continuous text into multiple runs (w:r), so a placeholder may be divided across runs, breaking naive find/replace; advice is to type each placeholder in one go — [Filling a docx template with Python while preserving style](https://blog.xa0.de/post/Filling-a-docx-template-with-Python-while-preserving-style/); [Eric White (Microsoft): Splitting runs in Open XML](https://learn.microsoft.com/en-us/archive/blogs/ericwhite/splitting-runs-in-open-xml-word-processing-document-paragraphs)
- docxtemplater (JS) handles split tags by working on paragraph-level text and re-mapping to runs — [docxtemplater internals deep dive](https://docxtemplater.com/docs/deep-dive-into-docxtemplater-internals/)
- DocxTemplater (C#/.NET) supports placeholders, loops, tables, conditionals, images; content controls can be filled by putting a placeholder in the w:sdt tag; a 2025/26 issue documented formatting loss when a conditional/loop boundary splits a run, fixed via PR — [Amberg/DocxTemplater](https://github.com/Amberg/DocxTemplater); [Issue #146](https://github.com/Amberg/DocxTemplater/issues/146); [PR #149](https://github.com/Amberg/DocxTemplater/pull/149)
- HotDocs moved fields into Word content controls (not directly editable in Word) — [HotDocs Fields Overview](https://help.hotdocs.com/preview/help/HotDocs_Fields_Overview.htm)
- Contract Express uses bracket/curly text markup — [Contract Express Key Concepts](https://www.thomsonreuters.com/en-us/help/contract-express/getting-started/key-concepts)
- Mapped content controls: only map to single childless XML nodes; mapping is lost if children are appended later; native XML Mapping Pane can't edit the customXMLPart; rich text CCs with tables can't be mapped natively — [Microsoft Q&A on binding content controls to custom XML parts](https://learn.microsoft.com/en-us/answers/questions/5420334/is-there-anything-we-need-to-be-aware-of-when-bind?forum=msoffice-all); [Greg Maxey content control tools](https://gregmaxey.com/word_tip_pages/content_control_tools.html)
- Guidance from Word template practitioners: simplest technique that works — REF+bookmark for repetition, document properties for metadata, content controls + XML for complex structured docs — [addbalance: mapped content controls](https://www.addbalance.com/word/MappedControls.htm)

### Inferences
- Recommendation for RSM4Legal: keep the user-facing syntax `{Variable}` and `[[ClauseName]]` as **text tags** for authoring simplicity and parity with email/task templates, BUT (1) normalise runs server-side before replacement (merge adjacent runs with identical rPr, or do paragraph-level text matching as docxtemplater does — use a proven library: docxtemplater (JS, commercial modules), DocxTemplater/OpenXML PowerTools-style (.NET), or Aspose/Syncfusion/Telerik), (2) offer a Word add-in "insert variable / insert clause" picker that writes the tag in one operation (avoids splitting and typos) and optionally wraps it in a content control with tag=`rsm:var:Matter.Client.Name` for robust round-tripping, and (3) provide a template validator that reports unknown variables/clauses and split/malformed tags on upload. Avoid native Dataverse XML-mapping templates as the main engine (re-mapping pain, no clauses, no conditionals).
- `[[Clause]]` replacement must insert formatted content (multiple paragraphs, numbering), so the clause should be stored as a DOCX/OpenXML fragment (or altChunk/AltChunk-free merge) rather than plain text; the paragraph containing the tag should be replaced, inheriting the target list/numbering style (unverified best practice; numbering merging is the hard part).

### Gaps
- No official Microsoft "recommendation" on text tags vs content controls for third-party generation found; Microsoft's own products (Dataverse templates, Syntex) use content controls/placeholders internally (unverified for Syntex internals).

## 3. Clause libraries: storage, versioning, approval, fallbacks, conditions, languages, playbooks, governance

### Takeaway
Clause libraries store pre-approved clauses grouped by clause type with a preferred/standard version plus approved fallback/alternative variants; CLMs (DocuSign CLM, Ironclad, Legisway) connect them to templates (assembly) and to playbooks (review/negotiation). Firm-side tools (Litera Clause Companion, Kleos Simple Clause Manager) are Word add-ins focused on storing and re-using text. Governance (owner, approval, review cycle) is generally described as best practice rather than a hard product feature in the sources found.

### Cited Findings
- Litera Clause Companion: store/retrieve/distribute preferred clauses and firm-approved language inside Word; on saving, it detects deal-specific data (names, dates, addresses, numbers) to anonymise and convert into variables/blanks — [Litera: Introducing Clause Companion](https://www.litera.com/blog/introducing-clause-companion); [Prime Infotech](https://primeinfotech.biz/blog/techthursday/revolutionizing-legal-efficiency-unleash-the-power-of-litera-clause-companion-with-anonymize-for-seamless-lawyer-work-product-reuse/); [Litera Draft product page](https://www.litera.com/products/legal/clause-companion/)
- DocuSign CLM: clause library of standardised, pre-approved clauses; clauses in clause groups have multiple variations, most common = primary; any number of variants/fallback clauses; Conditional Content lets one master template include alternative clauses/paragraphs, e.g. based on selected language — [DocuSign: What is a Clause Library?](https://www.docusign.com/blog/what-is-a-clause-library); [DocuSign Support: Create a custom clause library](https://support.docusign.com/s/document-item?language=en_US&bundleId=pxt1643324456371&topicId=dlc1670948155014.html); [DocuSign Support: Using the Clause Library](https://support.docusign.com/s/document-item?language=en_US&bundleId=sok1600053364751-2-0-0&topicId=smw1600053354293.html&_LANG=enus)
- Ironclad: Clause Library manages clause configurations; Playbooks serve review/negotiation with clause-level guidance and recommended fallback language; preferred/acceptable/fallback tiers; deviations routed to the right reviewer; AI "Jurist" redlining agent uses playbooks and precedents — [Ironclad Clause Library Overview](https://support.ironcladapp.com/hc/en-us/articles/30659446762647-Clause-Library-Overview); [Ironclad: Clause library article](https://ironcladapp.com/journal/contracts/clause-library); [Ironclad AI Playbooks in Workflow Designer](https://support.ironcladapp.com/hc/en-us/articles/24948981301143-Create-Ironclad-AI-Playbooks-in-Workflow-Designer); [Jurist Redlining Agent](https://support.ironcladapp.com/hc/en-us/articles/34188767294359-Use-Jurist-Redlining-Agent-with-Playbooks-and-Precedents); [Ironclad: Indemnity clauses](https://ironcladapp.com/resources/articles/effective-indemnity-clauses)
- Wolters Kluwer Legisway: Clause Library for standard clauses plus Assembly Template to build contracts from preferred clauses; Legisway Advisor (AI review) works inside Word — [LegalTechnologyHub: Legisway](https://www.legaltechnologyhub.com/vendors/legisway-by-wolters-kluwer/); [Legisway Advisor](https://www.wolterskluwer.com/en/solutions/legisway-advisor); [FF News: Legisway enhancements](https://ffnews.com/newsarticle/wolters-kluwer-announces-enhancements-to-ai-workflow-legisway/)
- Kleos (WK, law firm practice management): Office add-in with "Simple Clause Manager" for reusable text blocks and "Template Compiler" to build templates in Word — [Kleos MS Office integration](https://www.wolterskluwer.com/en-gb/solutions/kleos/explore-kleos-features/microsoft-integrations)
- Clause9 documents explicit clause versioning — [Clause9: Clause versioning](https://help.clause9.com/clauses/clause-versioning)
- General clause library best practice: version control, commenting and approval workflows — [Malbek](https://www.malbek.io/blog/contract-clause-library); [SpotDraft guide 2026](https://www.spotdraft.com/blog/contract-clause-library-in-2026); [ContractLogix](https://www.contractlogix.com/contract-management/clause-and-template-library-clm/)
- Comparison of clause library tools for in-house teams (2026) — [Bind Legal](https://bindlegal.com/resources/best-software/clause-library-software-in-house-legal/); Word add-in pattern — [Spellbook](https://spellbook.com/learn/clause-library-word-add-in)

### Inferences
- Recommended RSM4Legal data model: `Clause` (stable key used in `[[Key]]`, clause type/category, owner, practice area, jurisdiction) → `ClauseVersion` (content as DOCX fragment + plain text/HTML for search/AI, language de/en, status Draft → In Review → Approved → Retired, valid-from/to, approver, approval date, change note) → `ClauseVariant` role (Standard / Fallback 1 / Fallback 2 / Not acceptable) to share with CLM and AI playbooks. Generation always picks the latest *Approved* version in the requested language; the generated document records which ClauseVersion IDs were used (audit, later "clause changed — affected documents" report).
- 4-eyes: author ≠ approver enforced (Dataverse business rule/Power Automate approval). Governance typical in larger firms/legal departments: Knowledge Management / Legal Ops team as library administrator, named clause owner per clause (subject-matter partner/senior counsel), periodic review (e.g. annually or on law change) — this is described in best-practice literature (Malbek/SpotDraft above), not verified as hard-wired product features.
- Conditional inclusion: allow `[[Key]]` plus condition syntax (e.g. `[[Haftungsbegrenzung if Matter.Type = "Beratung"]]` or separate `{#if}` blocks) and parameterised clauses (clauses may contain `{variables}` resolved in the same pass). Language variants as separate versions of the same clause key, selected by a document-level language parameter (DocuSign's "Conditional Content by language" is the precedent).
- Reuse the same clause store as the AI playbook source (preferred/fallback positions), as Ironclad does — avoids two diverging libraries between CLM and matter templates.

### Gaps
- Agiloft, ContractPodAi (Leah), Lexion (acquired by DocuSign in 2024, unverified), Juro, Practical Law clause content and Microsoft Copilot (Word "Copilot" drafting from files; no native clause library known, unverified) — not researched in detail due to tool budget/blocked pages.
- No source found on concrete approval workflow screens (4-eyes) in Litera Clause Companion or Kleos.

## 4. Output format, template storage, who maintains templates

### Takeaway
Word (DOCX) remains the working format in legal; PDF is produced for final/sent versions. Templates live either inside the system (Clio, Actaport, DATEV, CLMs) or in SharePoint (Syntex Content Assembly, Templafy-type tools). Maintenance is centralised (Kanzleiverwaltung/admin, KM team) with user-level personal snippets in some tools.

### Cited Findings
- Clio Document Automation outputs Word or PDF — [Clio: What is Document Automation?](https://support.clio.com/hc/en-us/articles/360005473774-What-is-Document-Automation-)
- Actaport: firm-wide templates maintained in Kanzleiverwaltung — [Actaport: Vorlagen und Textbausteine hinterlegen](https://actaport.zendesk.com/hc/de/articles/9137869393052-Vorlagen-und-Textbausteine-hinterlegen)
- DATEV: multiple letterheads (Briefköpfe) configured centrally and chosen per document — [DATEV Schriftguterstellung](https://apps.datev.de/knowledge/redirects/v1/hilfe/1004227)
- SharePoint Content Assembly: template owner/admin publishes modern templates in a library; generated documents stored in SharePoint — [Plumsail](https://plumsail.com/blog/documents-generation-sharepoint-copilot/); [Gravity Union](https://www.gravityunion.com/blog/enhance-content-management-guide-to-sharepoint-premium-part-1)
- Contract Express: templates are authored by specialist authors (markup) — [Contract Express Key Concepts](https://www.thomsonreuters.com/en-us/help/contract-express/getting-started/key-concepts)

### Inferences
- Recommendation: store the template *definition* (metadata: name, type, language, practice area, matter types, required variables, status, version, owner) in Dataverse and the *DOCX file* in SharePoint (Dataverse–SharePoint document integration) or Dataverse file column; generated documents go to the matter's SharePoint folder. Default output DOCX (editable, Word Online), PDF on demand / on send (conversion via Graph `?format=pdf` or a conversion library — unverified choice). Template lifecycle with Draft/Approved like clauses. Roles: Template Admin (KM/Kanzleiverwaltung), Template Author, Users (may only use). Allow personal Textbausteine for users (Actaport/RA-MICRO precedent) but separate them from approved firm templates.

### Gaps
- No quantitative data on Word vs PDF output share.

## 5. Email templates and signatures

### Takeaway
Kanzleisoftware typically offers e-mail templates with the same placeholders/Textbausteine as documents (Actaport, DATEV). Signatures in Microsoft 365 firms are usually managed centrally by dedicated tools (Exclaimer, CodeTwo, Templafy) driven by Entra ID/AD attributes, with conditional disclaimers per office/language; client-side (Outlook add-in) vs server-side (mail routing) are the two technical models.

### Cited Findings
- Actaport Textbausteine with placeholders work in e-mails as well as documents — [Actaport: Platzhalter in Textbausteine](https://actaport.zendesk.com/hc/de/articles/4407774738322-Platzhalter-in-Textbausteine-einf%C3%BCgen); new client communication features — [Actaport update](https://www.actaport.de/update/eine-neue-art-der-mandantenkommunikation)
- DATEV Anwalt classic supports creating e-mails and mass mailings from document creation — [DATEV Schriftguterstellung](https://apps.datev.de/knowledge/redirects/v1/hilfe/1004227)
- Exclaimer: centralised IT-controlled signatures applied as mail routes through Exclaimer (any client/device) for M365, Google, Exchange — [Exclaimer product](https://exclaimer.com/product/email-signature-management/); [Microsoft Marketplace: Exclaimer](https://marketplace.microsoft.com/en-us/product/office/exclaimerltd-1036422.exclaimer?tab=overview)
- CodeTwo: cloud service connected to the M365 tenant, server-side routing; also central management of auto-replies; can disable personal Outlook signatures — [CodeTwo vs Exclaimer](https://www.codetwo.com/codetwo-vs-exclaimer); [CodeTwo M365 signatures](https://www.codetwo.com/email-signatures/)
- Templafy: natively embedded in Outlook (desktop/web/mobile) without mail rerouting; dynamic fields from AD/SCIM; conditional sections per user attribute (e.g., office-specific legal disclaimers); multiple signatures per user (internal/external, new/reply) — [Templafy email signature management](https://www.templafy.com/home/platform/email-signature-management/); [Templafy: Email Signatures HTML best practices](https://support.templafy.com/hc/en-us/articles/360015097757-Email-Signatures-HTML-best-practices); [Templafy: edit and switch signatures](https://support.templafy.com/hc/en-us/articles/360017183117-How-to-edit-and-switch-Email-Signatures)

### Inferences
- Recommendation: RSM4Legal should not compete with signature managers. Provide (a) e-mail templates using the same `{variable}` engine (subject + HTML body + attachments rule, language variants), (b) a per-user signature entity (DE/EN variants, HTML, variables from systemuser/Entra attributes) used only when the system sends mail itself, with a tenant setting "signature handled by external tool (Exclaimer/CodeTwo/Templafy)" to avoid double signatures. Default to **create draft** (Outlook/Dataverse email activity in draft, opened for review) for client-facing mail; auto-send only for low-risk, internal or explicitly configured notifications (e.g., deadline reminders). Server-side signature tools also stamp mails sent from Dataverse/Exchange — test interplay.
- German Pflichtangaben in Geschäfts-E-Mails (§ 37a HGB, § 35a GmbHG, PartGG for Partnerschaften; e.g. register, managing directors) belong in the signature/disclaimer (unverified for specific firm forms — legal check needed).

### Gaps
- No source found describing auto-send vs draft defaults in German Kanzleisoftware; recommendation above is inference.

## 6. Which documents are automated first

### Takeaway
Across guides and vendor examples, the first candidates are high-volume, low-variation documents: engagement letters/Mandatsvereinbarung and retainer agreements, NDAs, standard contracts, demand letters; in German Kanzleisoftware the everyday core is the Anschreiben/Briefvorlage with Rubrum, plus Vollmacht and Kostenrechnung/Kostenfestsetzungsantrag.

### Cited Findings
- Clio cites engagement letters and retainer agreements as typical automation use cases — [Clio: What is Document Automation?](https://support.clio.com/hc/en-us/articles/360005473774-What-is-Document-Automation-)
- Guides name engagement letters, NDAs, standard contracts and demand letters as good early candidates; reported time examples: engagement letter 20 min → 2 min, NDA 30 min → 1 min (vendor marketing, treat with caution) — [Layer3 Labs: Legal document automation 2026](https://www.layer3labs.io/guides/legal-document-automation); [Lawmatics](https://www.lawmatics.com/blog/what-is-legal-document-automation); [Harvey: Law office automation](https://www.harvey.ai/blog/law-office-automation)
- Claim: ABA Legal Technology Survey 2026 — 47% of firms with 10+ attorneys use at least one workflow automation tool beyond PM software (up from 29% in 2023) — reported by [Automation Atlas](https://automationatlas.io/guides/automation-for-legal-2026/); secondary source, not verified against ABA original.
- Actaport has dedicated generation flows for Kostenfestsetzungsantrag and invoice Textbausteine — [Actaport: Kostenfestsetzungsantrag](https://actaport.zendesk.com/hc/de/articles/360017344339-Erstellen-eines-Kostenfestsetzungsantrages)
- RA-MICRO's core Word workflow centres on letters with rubrum transfer, automatic salutation and Briefkopf — [RA-MICRO Seminare](https://ra-micro-seminare.de/seminare/word-textbausteine-briefkopf)

### Inferences
- MVP template set for RSM4Legal (law firm): Anschreiben/Briefvorlage (Briefkopf, Rubrum, Aktenzeichen, Anrede), Mandatsvereinbarung/Vergütungsvereinbarung (note § 3a RVG Textform requirement — unverified detail), Vollmacht (Prozess-/Vollmacht), Datenschutzhinweise/Mandatsbedingungen, Mandatsbestätigung e-mail, Kostennote cover letter. Legal department: NDA (mutual/one-way, DE/EN), Freigabe-/Stellungnahme memo, standard service agreement — NDA is the natural bridge to the existing CLM module and clause library.

### Gaps
- No German-market survey (e.g., LTO, Legal Tech Verzeichnis, Soldan Kanzleimarkt) found on which documents German firms automate first; German specifics above are inference.
