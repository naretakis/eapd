## Writing Principles

The CMS Advanced Planning Document (APD) modernization project is a prototype. The primary user of this product are subject matter experts with acute understanding of the APD submission process, content (and specifically, help text) in this application is designed to direct these users.

There are sections within the application (e.g. standards & conditions) that are extracted directly from the APD template from CMS.

## Voice & Tone

**Help the user understand** <br />
Our audience are analysts familiar with APDs, so we use direct language that helps the user understand what's expected throughout each section.

**Detail whenever possible** <br />
Use examples where appropriate. Don't be afraid to avoid brevity when necessary to explain what's required.

**Avoid familiarity, be direct** <br />
In translating a templated print experience into an application, it is not necessary to make language overtly personal, as our users do not expect this. Instead, opt for direct language that assumes a level of subject matter expertise with APDs.

**Write instructional help text** <br />
Ensure the instructions & help text guide advises the user on what we need in each section.

## Content management

### What is and is not in YAML

Copy that is likely to need routine editing and updating as we learn from users is managed in YAML. This includes all sentence- and paragraph-type text, including section intros, instructions, and help text.

Things like buttons and form field labels are generally not managed in YAML. These are tied closely to rendering and changes to them are likely to go hand in hand with other design changes. YAML abstracts the content from the visual design. When the content is as intimately related to strong visual style elements like buttons and forms, it is a better practice to make content changes by pairing with a visual designer or engineer to consider the entire presentation.

### How content is pulled from YAML

YAML elements are called by the site in an order dictated elsewhere in the code. If you write a set of instructions with order heading-detail-short in a YAML file, the code might still call for it in order heading-short-detail, or it might not pull the detail at all. Changing the order or what’s included requires engineering work, though it is generally a light lift.

## Style guidelines
In the status quo, APD language can be confusing and difficult to decipher. The goal then, is to develop content that is clear, direct, and errs on the side of explaining what to do in each section rather than assuming the end user already knows. While the users understand APDs and the underlying subject matter, they may not understand how to complete the APD using this interface.

Always remember that this app is very information-dense. Nobody is going to get full information from a quick read. **For edge cases, opt for a style that aids in scanning rather than one that provides all possible detail.** People will write, discuss, and calculate for that.

### Acronyms and abbreviations

* Spell out abbreviations on the first mention. See our [[Glossary of Acronyms]].
* APD, CMS, and HITECH are exceptions to that. They never need to be spelled out within the form itself. Consider spelling them out on other pages, using your judgment about whether there is sufficient context otherwise.
* If an abbreviation is used only once or twice on a page, or if what is abbreviated is very short, avoid using it.

### Capitalization

* Use title case for headers. This is especially imperative for [section titles](#Sections) and [subsection titles](#Subsections), which are headings at the `h1` and `h2` levels and also serve as the primary navigation of the app, but it should be observed universally unless further research says otherwise. Title case is easier to _scan_. This also applies to [field](#Fields) subgroup labels and table names/headers.
* Use sentence case for button labels and individual field labels. These govern refined information and interactions and specificity is important. Sentence case is easier to _read_.
* Unless starting a sentence or heading, do not capitalize “the” before a proper noun (for example: `the Centers for Medicare and Medicaid Services`).
* Use title case for legal citations (for example: `Access to Records, Reporting and Agency Attestations` and `42 CFR Part 495.350`).
* Outside of headers, Do not capitalize people’s official titles unless they precede a specific name (for example: `Medicaid director`).

### Numbers

* Use numerals instead of spelling out numbers. Avoid putting a number at the beginning of a sentence or headline.
* The numbers in this app are large; avoid extra digits. Where possible, round dollar amounts to the nearest whole dollar. For summary information, `k` and `M` are useful abbreviations that protect visual simplicity.
* Use the `%` sign instead of spelling out _percent_.
* Represent shares of discreet things, such as FTEs, as decimals (for example, 1.5 FTEs). Represent shares of wholes as percentages (for example, 75%). Do not use fractions.

### Punctuation and text styling

* Use the oxford comma.
* Add a single space after each period.
* Avoid using ampersands.
* When referring to buttons or sections, use _emphasis_ rather than “quotation marks”. Use quotation marks only when quoting something.
* Use the correct style of quotation marks and apostrophes (`‘’` and `“”` rather than`''` and `""`.

## Content elements
_This section is very much a work in progress._

Content that follows prescribed patterns consistently can help make the experience of using the eAPD as intuitive as possible. Users can find what they need more quickly, and can trust that what the eAPD asks them to do is what the HITECH program needs from them.

### Pages

The eAPD has a few pages. The bulk of content is in the **builder**, the form that someone completes to create an APD. For each APD, there is a unique instance of the form that can be saved with its own content. There is not a unique URL for each APD - the print/export view is located at ...eapd.cms.gov/print for the current APD that is open. 

The **homepage** or **dashboard** lists all of the state’s APDs. Each state has one homepage.

Those are the two pages with content relevant to the creation and submission of the APD. Additional pages are content about the app itself (such as an account management page, a privacy disclaimer, etc.).

### Sections
**Section title:** Section titles also serve as the primary navigation in the left-hand sidebar. Use title case. They must be less than 35 characters long; in the sidebar, longer titles would truncate and be hard to distinguish from one another. Other than `Certify and Submit` they should not be active verbs.

**Section description:** Current APD practices are not consistent across states, so for many users the section titles will require clarification. The description provides this clarity. (For example: What is `Program Summary` summarizing? What are `Program Activities?`) All sections should have a description. Lead with an imperative verb. (For example, `Provide` or `Describe`, not `Activities are`.)

If there is information a user needs be aware of while drafting an APD that is not addressed directly within a subsection, note it in the description. Descriptions should be short and direct, no more than 50 words. Avoid technical details about the information to be submitted or reviewed within the subsections.

### Subsections
**Structure and usage:** All sections have at least one subsection. Each subsection is composed specifically for its purpose. To keep the interaction patterns consistent, the most active content (for example: fields to complete, tables to review, and buttons to click) should always be within a subsection. (There is one exception, see [Activities](#activities)).

**Subsection title:** Subsection titles also serve as the secondary navigation in the left-hand sidebar. Use title case. These must be less than 60 characters long. Longer subsection titles may truncate in the sidebar. They should not use active verbs.

### Activities

In the user-facing hierarchy, each activity is at the same level as a subsection under the section _Program Activities_. However, in the YAML, the components of an activity, rather than the activity as a whole, are equivalent to subsections. When a user adds a new activity, an identical set of those components is created together as that activity.

### Instructions

**Usage:** Most fields are preceded by instructions that explain how to complete them, in an element we have called an `instruction`. It several sub-elements: `header`, `short`, `detail`, and helpText`.

**heading:** Instruction headings render much like headers, though they are semantically distinct. Use for non-sentence instructional copy, such as titles for individual components of subsections. Use sentence case. For example: Business Results.

**short:** Short instructions render as strong text. Use for short and to the point imperative sentences telling the user what to do with the following fields. For example: Describe how this activity will support the Modularity condition.

- Follow the guidelines in the CMS Design System, which includes limiting the use of the word "please" in instructions and relying on simple, plain language text. 

**detail:** Detail instructions are longer and more specific than short instructions. Example: Write a high level description to describe funding used to support this activity. (Review Letter 10‐016 for examples of grants for inclusion.)

**helpText:** helpText is information that is useful to someone who is filling out the form but does not tell them directly what to do or how.  Help text should always appear on the screen with the section it refers to, or at the field level when it's giving instructions about a specific field. It renders with different visual presentation from the text around it to call attention to it. For example: CMS recommends that states connect with regional CMS HITECH contacts prior to developing HIE funding request. HIE funding requests are complex. Early consultation with CMS facilitates a more efficient approval process. 

**Common usage in the eAPD system for consistency:**
- We have two phrases in the export view to indicate that information was not provided. 
  - "X not specified." This is used for fields with numbers, dates, and other formatted answers. (e.g Dates not specified). 
  - "No response was provided." Include details if possible or necessary (e.g. No response was provided for how this activity will support the Medicaid standards and conditions. Or a variation No outcomes(s) and corresponding metrics were provided.)

### Fields

**Field group:**

**Field subgroup:** Some subsections contain lists that are built from field groups. Those field groups are arranged tabularly. Each row is a subgroup. The left column of each subgroup is a label for that subgroup, written in title case. Keep the label to a few words, just enough to distinguish from the other subgroups. Arrange subgroups logically, so that similar data is grouped together.

- _Example 1:_ descriptive information like titles and names appear together, and cost breakdowns appear together; fields are arranged as verbal and then numerical.
- _Example 2:_ whole contract information appears together, and information about specific years appears together; fields are arranged as general and then specific.

**Field label:** Most fields will have labels. (Field subgroup labels sometimes appear without individual field labels. Otherwise, there should always be a field label.) The label should be exactly what the field _is_, a label rather than an instruction. (For example: a field where the user should state someone’s role should be labeled `Role`, instead of `Describe this person’s role`.) This is true for all field types except toggles.

**Toggle label:** Toggles in the eAPD are all `Yes`/`No` toggles. Therefore, it must be clear what the user is affirming or negating. If the toggle has its own label, it should be a sentence, ending in sentence-ending punctuation rather than a colon. If possible, it should be a question. (For example: `Is this person an hourly resource?` is preferable to `This person is an hourly resource.`)

For the Federal Citations and Justifications subsection, there is no toggle label. The subsection instructions should provide the required clarity.

### Tables

### Buttons
**Actions:**

**Navigation:**

**Toggles:**

## Terminology

### Terms particular to the APD

**Activity:** The activity is the basic unit of work that the APD is built on. Each one is a discreet, narrowly-scoped body of work, supported with HITECH funding, that supports a state’s larger program.

**APD:** The Advanced Planning Document is the application for CMS funding to support state programs. It includes details about the work to be supported. CMS uses APDs for a number of different programs. Current work on the eAPD app supports the HITECH APD. Occasionally the app will refer to “the previous APD” which is one that the state has submitted before that covers HITECH-supported work on the same state program.

**eAPD:** This is the name of the app for working purposes. It helps to distinguish the technological work from the document that results. Within the app itself, every effort should be made to refer only to the APD or an APD to help normalize the app as the primary tool for creating, managing, and processing APDs rather than as an add-on.

**Fiscal years:** To reduce confusion about how to report financial information, specify Federal Fiscal Year or FFY — as opposed to fiscal year or FY — when relevant. Some states fiscal years (occasionally noted as SFY) are different from the FFY.

**Program:** The program is the totality of the state’s health IT modernization work, including HITECH work supported under a given APD. The activities described in an APD should all be in support of the state’s program.

### Commonly used definitions and Glossary

* [Glossary of Acronyms](https://github.com/18F/cms-hitech-apd/wiki/Glossary-of-Acronyms)
* **Advanced Planning Document (APD)**
* **Centers for Medicare and Medicaid Services (CMS)**
* **Electronic Health Record (EHR)**
* **Health Information Exchange (HIE)**
* **Health Information Technology for Economic and Clinical Health Act (HITECH)**
