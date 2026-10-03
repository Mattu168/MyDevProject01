# Matter-Level Access Control, Phase-Dependent Access, Role Assignment and Ethical Walls in Legal Matter Management / DMS (RSM4Legal context, as of Oct 2026)

> Method note: Research was done via web search on 2026-10-03. Direct page fetches to vendor docs (intapp.com, docs.imanage.com, pages.netdocuments.com, learn.microsoft.com) were **blocked by the egress proxy**, so findings rely on search-result snippets of those primary pages. URLs point at the primary pages the snippets came from. Where a claim is my inference or comes from general product knowledge and not a snippet, it is marked **[inference]** or **[unverified]**.

## 1. How leading products handle matter teams, inclusionary/exclusionary walls, need-to-know, default access, lateral hires, time-limited access and revocation on closure

### Takeaway
The market has two layers. (a) A **policy/wall engine** (Intapp Walls, iManage Security Policy Manager, NetDocuments Workspace Security Manager) sets *inclusionary* (need-to-know: only the listed people) and *exclusionary* (deny these people) policies centrally, keeps them in sync with matter teams and HR/time data, and pushes them to downstream systems. (b) **Matter/DMS systems** (iManage Work, NetDocuments, Clio, TeamConnect, LawVu, HighQ, Legisway) apply simpler per-matter ACLs: public vs private/restricted, named users and groups, and a block/deny function. Time-limited access and access requests with approval are standard in the wall engines. Automatic tightening on matter closure is usually handled by **archive/read-only flags and policy expiry**, not by a full phase-by-phase permission model.

### Cited Findings
**Intapp Walls (the main ethical-wall engine for law firms)**
- Creates and manages both **exclusionary and inclusionary walls** that isolate records and matters from inappropriate access — [Intapp blog: Integrated onboarding & conflicts](https://www.intapp.com/blog/integrated-onboarding-conflicts/) (search snippet)
- Enforces lateral-hire screens, matter-level confidentiality, waiver-driven restrictions and MNPI controls. Enforcement is consistent and logged for audit "across every system the firm runs" — [Intapp blog: Walls for AI / Harvey](https://www.intapp.com/blog/intapp-walls-harvey-integration/) (snippet)
- "Self-maintaining walls add and remove people based on **time or document activity**, and matter teams can request and approve access within policy, without a compliance ticket for every change" — [Intapp Walls product page](https://www.intapp.com/walls/) / [Self-maintaining access management](https://www.intapp.com/walls/self-maintaining-access-management/) (snippet)
- "Automatically updating permissions in real time as personnel roles or **engagement statuses change**. When policies change, Intapp Walls detects the change and automatically updates team and user access rights" — [Intapp self-maintaining access management](https://www.intapp.com/walls/self-maintaining-access-management/) (snippet). This is the closest vendor statement to **status-driven access**.
- When walls change, Intapp Workspaces enforces the change and automatically removes people from (MS) Teams who no longer have permission — [Intapp blog: secure collaboration with Workspaces, Walls and Microsoft Teams](https://www.intapp.com/blog/secure-collaboration-intapp-microsoft-3/) (snippet)
- Recommended practice: a **multi-layered framework** of client-level rules that stay active when *temporary matter-based restrictions expire* (e.g. when an M&A matter ends) — [Intapp: Manage and enforce ethical policies](https://www.intapp.com/legal/ethical-walls-compliance/) (snippet). So matter-level walls are often **time-bound**, while a client-level baseline remains.
- Uses "engagement context" (matter metadata) to enforce need-to-know against humans and AI agents (Copilot, LLMs) — [Intapp Walls](https://www.intapp.com/walls/) (snippet). A 2025/26 integration with Harvey enforces walls in an AI tool — [Harvey blog](https://www.harvey.ai/blog/harvey-intapp-ethical-walls)
- The Walls API exposes **matter team membership with roles** (load team, add user with role) — [DEV Community: Matter Team Membership via Intapp Walls API](https://dev.to/seanmdrew/working-with-matter-team-membership-using-the-intapp-walls-api-2nop)
- On-prem Walls has reached end of life and customers are moving to the cloud — [Bressler risk blog / Epiq](https://bresslerriskblog.com/epiq-updates-resources-intapp-on-prem-eol-cloud-migration-client-walls-case-study-client-video-spotlightsponsor-spotlight/); [Intapp blog AI governance migration](https://www.intapp.com/blog/ai-governance-migration/) (snippet titles; EOL details not verified)

**iManage Security Policy Manager (SPM) + iManage Work**
- SPM is the governance layer on top of iManage Work and applies ethical-wall policies automatically, with audit — [iManage SPM product page](https://imanage.com/imanage-products/security-governance/security-policy-manager/)
- **Time-limited access** is supported: "Your access to some assets may be time-limited ... the Access Period column" lists the limit, and assets expiring within 7 days get a warning icon — [SPM user help: Viewing assets and their access periods](https://docs.imanage.com/cloud/spm-user-help/en-US/Viewing_assets_and_their_access_periods.html) (snippet)
- **Access request workflow**: approvers can choose "Access Period is Time Limited". Renewal can be set in hours, days or unlimited. Requests can also be configured as **auto-granted and time-limited, with no approval** — [SPM: Updating Security Policy](https://docs.imanage.com/cloud/spm-admin-help/en-US/Updating_Security_Policy.html); [Managing Matter Access Requests](https://docs.imanage.com/cloud/spm-admin-help/en-US/Managing_Matter_Access_Requests.html) (snippets)
- For restricted matters there are "six possibilities for requesting, approving or providing access". Client/matter admins and **local matter administrators** can change access-request settings and notification templates at matter level — [SPM: Updating Security Policy (2)](https://docs.imanage.com/cloud/spm-admin-help/en-US/Updating_Security_Policy2.html) (snippet)
- iManage Work has two layers: **role-based security** (capabilities) plus **object-based ACLs** (Full / Read-Write / Read Only / No Access) on workspaces and documents — [iManage Work: Managing security](https://docs.imanage.com/work-web-help/10.5.0/en-US/Managing_security.html); [Control Center: Privileges, Roles, and Groups](https://docs.imanage.com/cloud/cc-help/en-US/Privileges,_Roles,_and_Groups.html) (snippets). This is structurally the same as Dataverse security roles plus record access.
- Archiving a workspace keeps it searchable, with controls that prevent further editing. The "archive flag is only a designation". On restore, prior security is reapplied — [Litera support: Working with the Workspace Tab](https://support.litera.com/article/Working-with-the-Workspace-Tab-552525) (snippet; this is a Litera/iManage-integration context and may refer to a specific tool such as Litera's archiving/CAM, **uncertain**)

**NetDocuments**
- Ethical walls with granular access at user, document or workspace level on a need-to-know basis. **Workspace Security Manager (WSM)** manages matter/workspace confidentiality and ethical walls at scale — [NetDocuments WSM brochure](https://pages.netdocuments.com/rs/549-CKV-717/images/usa-sml-wsm-product-brochure.pdf); [NetDocuments security & governance](https://www.netdocuments.com/solutions/security-data-governance/) (snippets)
- Matter-centric workspaces with client-matter numbering. Metadata includes matter type, practice area, responsible attorney and **status** — [comparethecloud 2026 comparison](https://www.comparethecloud.net/articles/imanage-vs-netdocuments-vs-sharepoint-document-management-uk-law-firm) (secondary source)
- [unverified] Detailed WSM rules for closure or lateral hires could not be read (the PDF was blocked).

**Clio Manage (SMB practice management)**
- Matters are **visible to all firm users by default**. When creating or editing a matter, the user can pick "Everyone" or "Specific users or groups". Choosing specific users/groups makes it exclusive to them (inclusionary) — [Clio Help: Matter Permissions and Rates](https://help.clio.com/hc/en-us/articles/9286062516123-Matter-Permissions-and-Rates)
- Admins can **block specific users** from a matter, one at a time or in bulk, "to easily restrict users from accessing matters where there may be conflicts of interest" (exclusionary) — same source
- [unverified] No evidence found of status-driven access changes in Clio.

**Mitratech TeamConnect (corporate legal ELM)**
- A matter is **public or private**. The Security tab assigns users/groups to private matters with Read/Update/Delete/Permission rights. Normal users see private records only with record-level grants. "Super users" see all records they have group rights for — [Mitratech Success Center: Users](https://success.mitratech.com/TeamConnect/Enterprise_Administrator_Help/Account_Administration/Users); [Object Definition Security](https://success.mitratech.com/TeamConnect/Enterprise_User_Guide/Records/Object_Definition_Security)
- Rights are given to **groups, not individual users**, by record type, category and custom field. **Embedded** records inherit access. **Related** records do not inherit by default; inheritance is set per object definition — [Groups](https://success.mitratech.com/TeamConnect/Enterprise_Administrator_Help/Account_Administration/03_Groups); [Object Definition Security](https://success.mitratech.com/TeamConnect/Enterprise_User_Guide/Records/Object_Definition_Security)
- TeamConnect has a rules engine (validation, approval, custom-action rule types) — [Rule Types](https://success.mitratech.com/TeamConnect/TeamConnect_Setup_and_Development/Enterprise_Customization_Help/Using_Rules/02_Rule_Types). [inference] Phase-based access changes would be built with these rules, not as standard behaviour.

**LawVu (in-house)**
- Separate visibility levels and "privacy walls" per matter. A matter can be restricted so others see no sensitive details. Individual conversations can be private. Files/folders have their own access levels — [LawVu Help: User management](https://help.lawvu.com/en/articles/2969806-user-management-in-lawvu); [File access in LawVu](https://help.lawvu.com/en/articles/9881655-file-access-in-lawvu)
- **Matter Owner** has full control (tasks, invites, permissions). **Matter Managers** are a second role. **LawVu Teams** give visibility over matters without membership — [Matter Owners and Matter Managers](https://help.lawvu.com/en/articles/2883448-what-are-matter-owners-and-matter-managers); [LawVu Teams](https://help.lawvu.com/en/articles/4509592-lawvu-teams)
- External law firms collaborate on matters inside LawVu — [Law Firms Article 2](https://help.lawvu.com/en/articles/5102295-law-firms-article-2-engage-with-clients-on-matters-in-lawvu)

**Thomson Reuters HighQ (collaboration / extranet)**
- An archived site is invisible to all users, **but archiving "does not remove users from the site or change user permissions"** — [HighQ Knowledge: Archive a site](https://knowledge.highq.com/help/site-content-and-user-administration/archive-a-site) (snippet)
- TR itself names this a governance gap: after matters close, sites stay active with external users still having access. Firms found **thousands of external accounts** with no login for more than a year. Sites can be restricted to internal users, which suspends externals — [TR blog: HighQ governance with Syncly](https://legal.thomsonreuters.com/blog/your-highq-environment-is-growing-your-governance-model-isnt/) (snippet)
- [unverified] Legal One details were not found in this session.

**Onit, Legisway, Litera**
- Onit: role-based permissions, SSO/MFA, audit trails. Outside-counsel management sits in one hub — [Onit platform](https://www.onit.com/platform/) (marketing; no detail on matter-level ACLs found)
- LexisNexis CounselLink+ (comparable ELM): configurable workflows for **matter creation, assignment and closure** with approval chains, plus secure outside-counsel access to matter details — [CounselLink+ matter management](https://www.lexisnexis.com/en-us/products/counsellink/matter-management.page) (snippet)
- Legisway: role-based user types (Administrator, Editor/Manager, Viewer/Reader, Requestor) and user rights to "segment the information" — [Legisway User Types](https://www.wolterskluwer.com/en/solutions/legisway/user-types); [Legisway data privacy](https://www.wolterskluwer.com/en/solutions/legisway/data-privacy). No matter-level wall engine was found.
- Litera: no specific ethical-wall product found in this session (Litera's footprint is drafting/time/experience tools and iManage-adjacent workspace tooling) **[unverified]**.

### Inferences
- The RSM4Legal design (capability roles + owner teams by practice area x region + Access Team per matter + deny-overlay plugin) matches the market pattern: capability roles, a baseline by organisational unit, a per-matter team, and a central wall policy. It resembles iManage Work + SPM and Intapp Walls + DMS.
- **Inclusionary ("need-to-know") walls** in the market mean "only matter team plus explicitly approved", which is the same as confidentiality level "restricted" with the Access Team as the sole grant path. **Exclusionary walls** mean "everyone per default except X", which is the deny overlay.
- Common standard features RSM4Legal should copy: (1) time-limited grants with expiry warnings, (2) access-request with approval by the matter owner/responsible lawyer, (3) a client-level baseline that survives when matter restrictions expire, (4) audit log of every grant/revoke, (5) periodic recertification of external users.

### Gaps
- Exact Intapp Walls configuration options for "on matter close" (e.g. auto-convert inclusionary wall to archived or keep forever) could not be verified. The vendor pages were blocked.
- NetDocuments WSM and Thomson Reuters Legal One feature details were not retrievable.
- No numbers found on how common inclusionary vs exclusionary walls are (ILTA surveys would be the source; not found).

## 2. Is phase- or status-dependent access common?

### Takeaway
**Partly.** Status-driven changes are common at two points: **matter closure/archive** (read-only, hidden, or removal of externals) and **engagement status changes** propagated by the wall engine (Intapp "self-maintaining"). **Fine-grained phase-by-phase access** (e.g. add an approver in the "settlement" phase and remove them on leaving it) is **not standard out of the box** in the products reviewed. It is built with workflow/rules engines or done as time-limited grants. Closure cleanup is a known weak spot (HighQ).

### Cited Findings
- Intapp updates access when "engagement statuses change" and can add/remove people based on time or document activity — [Intapp self-maintaining access](https://www.intapp.com/walls/self-maintaining-access-management/) (snippet)
- Temporary matter restrictions expire (e.g. at the end of an M&A deal), and client-level rules remain as a redundant layer — [Intapp ethical policies](https://www.intapp.com/legal/ethical-walls-compliance/) (snippet)
- iManage: archived workspaces stay searchable but cannot be edited, which amounts to **read-only on closure** — [Litera support](https://support.litera.com/article/Working-with-the-Workspace-Tab-552525) (snippet; context uncertain)
- iManage SPM: time-limited and auto-granted temporary access is the vendor's model for temporary needs — [SPM Updating Security Policy](https://docs.imanage.com/cloud/spm-admin-help/en-US/Updating_Security_Policy.html) (snippet)
- HighQ archiving does **not** change permissions, and external users stay on closed-matter sites. TR recommends governance tooling — [HighQ Archive a site](https://knowledge.highq.com/help/site-content-and-user-administration/archive-a-site); [TR blog](https://legal.thomsonreuters.com/blog/your-highq-environment-is-growing-your-governance-model-isnt/)
- HighQ: external access can be limited by time, role or files/folders — [HighQ review (secondary)](https://thelegalpractice.com/tools/highq-review-legal-practice-management-software/)
- ELM workflows typically cover matter creation, assignment and **closure** with approval chains — [CounselLink+](https://www.lexisnexis.com/en-us/products/counsellink/matter-management.page)
- Dataverse community pattern: temporary user access through access teams, removed by automation — [d365hub: Managing temporary user access with access teams](https://d365hub.com/Posts/Details/e10fc3ad-1f2e-48be-9ded-3e4de1a20990/managing-temporary-user-access-in-dataverse-with-access-teams)

### Inferences (recommendations for RSM4Legal)
- **Do automate status changes at a few clear points, not at every phase:**
  1. **Matter closed / archived:** switch the matter and its child records to read-only for the team (Dataverse: deactivate records, or swap Access Team template rights from Write to Read through a plugin/flow that re-grants). Remove external and temporary members. Keep responsible lawyer + records management. Keep the ethical wall deny active **indefinitely** (a wall must outlive the matter, because the confidential information stays).
  2. **Engagement of external counsel / experts ends:** revoke their access automatically (end date on the membership row).
  3. **Approval-type participation** (e.g. "approver lead" in settlement): model this as **time-limited or task-scoped access** (grant when the approval task is created, revoke on completion or expiry). Do not model it as a phase-bound permanent team role. This matches the iManage SPM "time-limited / auto-granted" pattern and the Intapp "self-maintaining" pattern.
- **Avoid automatic removal of core team members on phase change.** Lawyers often need earlier-phase material later. Revoking access mid-matter creates support tickets and risks people working around the system. The market pattern is to **add** at phase entry and **tighten** at closure.
- Implement phase changes as **data-driven rules** (table "Matter Phase Access Rule": phase, role, grant/revoke, rights, duration) run by a plugin on status change. Do not hard-code them. Log every automatic grant/revoke in an audit table (Dataverse auditing of team membership + a custom log).
- Run **recertification** (e.g. quarterly) of externals and long-lived temporary grants, given the HighQ experience.

### Gaps
- No survey data (ILTA/Legal IT) found on how many firms run phase-dependent access.
- No vendor documentation found that names a "settlement-phase approver" type mechanism. That example is RSM4Legal-specific.

## 3. Role assignment on matters (responsible attorney, matter team roles) used for workflow routing

### Takeaway
Typical and expected. Products use matter roles (Responsible/Originating attorney, Matter Owner/Manager, team members with roles) both for **access** and for **routing** of tasks, approvals, notifications and access requests. In the wall engines, **matter team roles drive who approves access requests**.

### Cited Findings
- LawVu: Matter Owner has full control (tasks, invites, permissions), with Matter Managers as a second level — [LawVu: Matter Owners and Matter Managers](https://help.lawvu.com/en/articles/2883448-what-are-matter-owners-and-matter-managers)
- Intapp: matter teams request and approve access within policy without compliance tickets. The API adds users to matter teams **with roles** — [Intapp Walls](https://www.intapp.com/walls/); [DEV: Intapp Walls API](https://dev.to/seanmdrew/working-with-matter-team-membership-using-the-intapp-walls-api-2nop)
- iManage SPM: access requests route to matter-level approvers (local matter admins) with notification templates — [SPM Updating Security Policy (2)](https://docs.imanage.com/cloud/spm-admin-help/en-US/Updating_Security_Policy2.html); [Requesting access to a Matter](https://docs.imanage.com/cloud/spm-user-help/en-US/Requesting_access_to_a_Matter.html)
- NetDocuments carries a "responsible attorney" metadata field on matters — [comparethecloud](https://www.comparethecloud.net/articles/imanage-vs-netdocuments-vs-sharepoint-document-management-uk-law-firm)
- CounselLink+: approval chains for budgets, staffing and invoices plus matter assignment workflows — [CounselLink+](https://www.lexisnexis.com/en-us/products/counsellink/matter-management.page)
- TeamConnect: approval rule types in its rules engine — [Rule Types](https://success.mitratech.com/TeamConnect/TeamConnect_Setup_and_Development/Enterprise_Customization_Help/Using_Rules/02_Rule_Types)

### Inferences
- RSM4Legal should keep a **Matter Team Member** table (matter, user/contact, role, valid from/to, source: manual/rule/request) as the **single source of truth**. A plugin syncs it into the Dataverse Access Team. Workflows (Power Automate / approvals) resolve approvers by role from this table. Do not resolve them from Access Team membership, which carries no role.
- Recommended roles: Responsible Partner, Responsible Associate/Lead, Team Member, Assistant/Paralegal, Approver (temporary), External Counsel (time-boxed), Records/Compliance (read).
- Using roles for both routing and access makes **role changes security-relevant**. Audit them.

### Gaps
- No statistics found on how common role-based routing is. It is evident from product designs, not from surveys.

## 4. Professional rules context (Germany, plus UK/US references)

### Takeaway
German law (since the BRAO reform of 1 Aug 2022) explicitly allows an ethical wall as a condition for lifting a firm-wide **Tätigkeitsverbot** in certain cases (e.g. "Sozietätswechsler"). It needs **client consent in text form + organisational measures**: different persons, **no mutual access to paper and electronic files (incl. beA)**, and a communication ban. §43e BRAO requires need-to-know limits for service providers. The UK SRA and ABA Rule 1.10 set similar or stricter "effective measures / timely screen" standards. Technical walls must therefore be **demonstrable, audit-logged and set up in time**.

### Cited Findings
- §43a Abs. 2 BRAO (Verschwiegenheit) is the base duty. §43e BRAO allows giving service providers access to confidential facts "to the extent necessary for the service" — [dejure.org §43e BRAO](https://dejure.org/gesetze/BRAO/43e.html); [lxgesetze §43e](https://lxgesetze.de/brao/43e)
- §43e requirements: contract in **text form**, confidentiality duty with notice of criminal liability under §203 StGB, knowledge limited to what the contract needs (**need-to-know**), subcontractors bound the same way — [legal-tech-verzeichnis: §43e](https://legal-tech-verzeichnis.de/fachartikel/digitales-vertragsmanagement-in-kanzleien-was-paragraph-43e-brao-verlangt/); [law-flow checklist](https://www.law-flow.de/blog/geheimhaltungsvereinbarung-43e-brao) (secondary)
- §3 BORA (new version after the 2022 reform): the extension of a Tätigkeitsverbot to the firm does not apply if affected clients consented after full information **in text form** and appropriate measures protect confidentiality. Measures: matters handled **exclusively by different persons**, **mutual access to paper files and electronic data, incl. beA, excluded**, and the handling persons barred from communicating with each other — [§3 BORA (lxgesetze)](https://lxgesetze.de/bora/3); [Anwaltsblatt: Interessenkollision im Vorher-Nachher-Check](https://anwaltsblatt.anwaltverein.de/de/anwaeltinnen-anwaelte/berufsrecht/interessenkollision-im-vorher-nachher-check); [BRAK proposal §3 BORA](https://www.brak.de/fileadmin/01_ueber_die_brak/7-sv/Antr%C3%A4ge_der_Aussch%C3%BCsse_2._Sitzung/Antrag_AS_2-Anderung__3-BORA.pdf); [Haufe: BRAO-Reform Tätigkeitsverbote](https://www.haufe.de/recht/kanzleimanagement/brao-reform-ab-182022/brao-reform-interessenkollision-und-taetigkeitsverbote_222_571774.html)
- The statutory basis is §43a Abs. 4 BRAO (new), which extends conflicts to the firm with exceptions, including the "Sozietätswechsler" case — [Anwaltsblatt: Neues zum Sozietätswechsler](https://anwaltsblatt.anwaltverein.de/de/themen/schwerpunkt/interessenkollision-core-value); [Anwaltsblatt FAQ BRAO-Reform](https://anwaltsblatt.anwaltverein.de/de/themen/recht-gesetz/faq-brao-reform-interessenkollision) (exact paragraph sub-numbering **not verified** in this session)
- UK SRA Code 6.5: do not act where you hold material confidential information of an adverse (former) client "unless **effective measures** have been taken which result in there being **no real risk of disclosure**". The bar is "quite high". Examples: systems that identify issues, separate teams at all levels incl. support staff, **separate servers so information cannot be cross-accessed**, encryption/passwords, staff awareness of who works on what — [SRA guidance: Confidentiality of client information](https://www.sra.org.uk/solicitors/guidance/confidentiality-client-information/)
- ABA Model Rule 1.10(a)(2): a lateral's former-client conflict is not imputed if the lawyer is **timely screened**, gets **no part of the fee**, and the former client gets **written notice** describing the screening procedures, with a compliance statement and an agreement to answer inquiries. A screen should be set up when the disqualifying event occurs (hire or case intake). The firm must be able to **prove** the screen — [ABA Model Rule 1.10 (Ethics 2000)](https://www.americanbar.org/groups/professional_responsibility/policy/ethics_2000_commission/e2k_rule110rem/); [Texas Bar: Screening lateral hires](https://www.texasbar.com/AM/Template.cfm?Section=articles&ContentID=69965&Template=%2FCM%2FHTMLDisplay.cfm)
- GDPR: [inference, standard knowledge] Art. 5(1)(c) data minimisation, Art. 25 privacy by design/default and Art. 32 security support need-to-know defaults and access logging. No specific source was fetched in this session.

### Inferences
- Requirements for RSM4Legal derived from §3 BORA / SRA / ABA:
  - The wall must cover **all data stores**: Dataverse matter records, documents (SharePoint/DMS), email/beA, Teams, and **search/AI (Copilot)**. A deny in Dataverse alone does not meet "kein wechselseitiger Zugriff auf elektronische Daten". Intapp's AI enforcement shows the market direction.
  - **Timeliness:** the wall has to be active *before* the lateral starts or the conflicting matter opens. Integrate wall creation into conflict check / intake and onboarding.
  - **Evidence:** keep a wall register (parties, reason, consent in text form, date set, acknowledgments), plus audit logs of access attempts and changes, for client queries or proceedings.
  - The **wall must not expire on matter closure.** Confidential information persists. That is why Intapp layers client-level rules.
  - §43e BRAO: give support/IT/vendor access only as needed. Admin/system roles in Dataverse bypass record-level security, so privileged access needs process controls (named admins, logging, §43e contracts with Microsoft/partners).

### Gaps
- No German court ruling on the technical adequacy of electronic walls found in this session.
- The exact current text of §43a Abs. 4 BRAO was not retrieved.

## 5. Dataverse-specific: access teams vs record sharing (POA), scalability and Microsoft guidance

### Takeaway
Microsoft's guidance: **ownership/business-unit and owner-team access scales best**. Sharing (incl. access teams, which work through sharing) writes **PrincipalObjectAccess (POA)** rows and costs performance in proportion to shared volume. Access teams are the recommended pattern for **per-record collaboration with varying people**. They are lighter than owner teams (no security roles, no ownership) but still create POA entries. **Dataverse has no native "deny"**, so ethical walls need a design that *withholds grants*, not one that overrides them.

### Cited Findings
- "Retrieval times to records using the ownership model grow independent of the amount of data ... with the sharing model retrieval times grow in direct proportion to the amount of data shared with the user". Sharing "performs less efficiently and can be harder to troubleshoot than role-based access" — [Microsoft Learn: Ownership-based security in Dataverse](https://learn.microsoft.com/en-us/power-platform/admin/wp-security-cds) (snippet)
- POA stores sharing between principals and records incl. cascaded/inherited shares. It is checked when a user lacks ownership/role privilege on a record — [Microsoft Learn: Manage PrincipalObjectAccess storage](https://learn.microsoft.com/en-us/power-platform/admin/manage-principalobjectaccess-storage) (snippet via search)
- Adding a user to an access team creates POA rows. Large access-team use increases POA and can degrade performance. Unused access teams should be cleaned up — [crmsoftwareblog: Design and scalability of access teams](https://www.crmsoftwareblog.com/2014/03/design-and-scalability-considerations-when-using-access-teams-in-dynamics-crm-2013/) (older, community); [Medium: reviewing POA](https://fordosa90.medium.com/admin-diaries-reviewing-the-poa-table-with-power-bi-6db7248a5aa9)
- "Sharing with a team is more efficient than sharing separately with each user" — [temmyraharjo: Dataverse share record access](https://temmyraharjo.wordpress.com/2022/03/12/dataverse-share-record-access/) (community)
- System-managed access teams: created per record from an **access team template** that defines rights. Other rows cannot be shared with that team. Max **4 access team templates per table** (per search snippet) — [Microsoft Learn: Use access and owner team templates](https://learn.microsoft.com/en-us/power-platform/admin/about-team-templates); [Create a team template](https://learn.microsoft.com/en-us/power-platform/admin/create-team-template-add-entity-form) (snippets; the "4 per entity" figure should be re-verified)
- Access team templates can be solution-aware since 2023 wave 1 — [Microsoft Learn release plan](https://learn.microsoft.com/en-us/power-platform/release-plan/2023wave1/data-platform/access-team-templates-be-added-solution)
- Access teams don't own records and hold no security roles. Members get rights through the template and still need privileges via their own security roles — [Microsoft Learn (on-prem dev guide): Use access teams and owner teams](https://learn.microsoft.com/en-us/dynamics365/customerengagement/on-premises/developer/use-access-teams-owner-teams-collaborate-share-information?view=op-9-1) (snippet + **[training knowledge]**)

### Inferences (recommendations)
- **Keep the layering:** security role = what (capability, at most BU depth), owner team per practice area x region = default breadth for "normal" confidentiality, Access Team per matter = individual need-to-know additions. For "restricted/highly confidential" matters, own the record by a **restricted owner team** or a dedicated BU so no BU-wide role sees it, and grant only through the Access Team. This is the Dataverse version of an *inclusionary wall*.
- **Ethical wall "deny overlay":** Dataverse cannot deny access a role or BU grant already gives. A plugin can (a) block a walled user from being added to the access team / shares, (b) validate on retrieve (RetrieveMultiple/Retrieve plugins are possible but expensive and do not cover all channels, e.g. some exports/TDS/search **[inference]**), and (c) ensure walled matters are never in a scope the user can reach by role (owner team/BU placement). **Recommendation:** enforce the wall mainly by *placement and withholding grants* (a and c), use (b) only as a defensive layer, and audit.
- **Child records:** use cascade sharing (relationship behaviour "cascade share/unshare") or the newer per-table "inherited" access carefully. Cascades multiply POA rows. Prefer child records owned by the same team as the matter. **[inference]**
- **Phase-dependent access in Dataverse:** implement as membership changes in the Matter Team Member table → plugin AddUserToRecordTeam / RemoveUserFromRecordTeam. Use a second access team template (e.g. "Matter – Read Only") for read-only participants and closed matters, which avoids rewriting share masks. Run a scheduled flow for **expiry dates** (time-limited grants).
- On **matter closure**, remove temporary/external members, move remaining members to the read-only template (or deactivate records), and keep the wall register active. This keeps POA small over time, which is good for scale.
- Monitor POA size (Power Platform admin center capacity / POA reports). Clean up orphan access teams.

### Gaps
- Microsoft Learn pages could not be fetched. Exact current wording and limits (templates per table, POA thresholds) need re-checking on learn.microsoft.com.
- No official Microsoft numeric threshold for "too many" POA rows was found. Community guidance only.
- Whether Copilot/Dataverse search fully respects record-level sharing in every channel was not verified in this session.
