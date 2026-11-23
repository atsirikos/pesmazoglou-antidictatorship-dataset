# Ioannis (Yangos) Pesmazoglou Anti-Dictatorship Discourse Metadata (A6S8Y3)

## Dataset Overview
This dataset contains structured archival metadata for 29 folders from Archive 6 (Ioannis Pesmazoglou Archive), Series 8 (Anti-dictatorship Activity), Subseries 3 (Speeches, Statements, and Interviews) held at the Historical Archive of the Bank of Greece (IATE). Each row represents one archival folder as catalogued in the published finding aid.

## Motivation
Ioannis Pesmazoglou was a prominent Greek economist, Deputy Governor of the Bank of Greece, and leading intellectual opponent of the Greek military junta (1967 to 1974). This dataset operationalises his archival finding aid to support quantitative humanities research on:
* How his public opposition balanced domestic economic critique, European integration (EEC), and higher education policy.
* The ratio between his authored public statements and the supporting economic, legal, and press dossiers (`πηγές`) he compiled to substantiate them.

## Selection Criteria
* **Included:** All 29 folders in Series 8, Subseries 3 (`A6S8Y3F01` to `A6S8Y3F29`), selected because this subseries directly captures Pesmazoglou's public discourse during the dictatorship.
* **Excluded:** Other subseries in Series 8 (Subseries 1 on EMEP/EKIN organisational records and Subseries 2 on exile and arrest reactions), as well as dictatorship-era folders located in Series 3 (EEC) and Series 5 (University of Athens).
* **Representativeness and Gaps:** The dataset represents catalogued folder-level descriptions rather than individual documents. Material weeded during archival processing (such as duplicate typescripts) and uncatalogued items are absent.

## Data Collection Process
The metadata was manually transcribed and structured in November 2026 from pages 50 to 53 of the publicly available PDF finding aid (`Arxeio_Pesmazoglou.pdf`, printed 15 July 2022) published by the Bank of Greece Historical Archive.

## Cleaning and Preprocessing
* Normalised printed extreme years so `start_year` is always earlier than or equal to `end_year` (correcting the reversed print order in folder `A6S8Y3F05` on page 50 of the PDF, where `1969` appeared before `1960`).
* Translated prose descriptions (`Περιγραφή`) into controlled English vocabularies for `document_genres` and `primary_topics`.
* Classified each folder with a boolean flag (`is_source_dossier`) distinguishing folders composed primarily of third-party background sources (`πηγές`) from folders containing Pesmazoglou's own authored drafts, speeches, or interviews.

## Repository Structure and Codebook

    .
    ├── .gitignore
    ├── README.md
    ├── check_dataset.ipynb
    ├── data.csv
    └── requirements.txt

### Codebook for `data.csv`

| Column name | Meaning | Type | Allowed values / format | Missing values |
| :--- | :--- | :--- | :--- | :--- |
| `id` | Unique archival folder identifier | string | `A6S8Y3F01` to `A6S8Y3F29` | Not allowed |
| `source` | Public URL of the Bank of Greece finding aid | string | Valid URL | Not allowed |
| `licence` | Copyright status and terms of the source | string | Free text stating source terms | Not allowed |
| `folder_title_el` | Original Greek folder title from the finding aid | string | Free text in Greek | Not allowed |
| `start_year` | Earliest documented year in the folder | integer | `YYYY` (ISO 8601) | Empty cell |
| `end_year` | Latest documented year in the folder | integer | `YYYY` (ISO 8601) | Empty cell |
| `is_source_dossier` | Whether the folder holds primarily background sources | boolean | `True` or `False` | Not allowed |
| `document_genres` | Controlled English list of document types in the folder | string | Semicolon separated lowercase tags | Empty cell |
| `primary_topics` | Controlled English list of subject themes in the folder | string | Semicolon separated lowercase tags | Empty cell |

## Uses and Limitations
* **Appropriate Uses:** Exploratory archival analysis, temporal mapping of opposition themes, and genre distribution studies of anti-dictatorship intellectual activity.
* **Limitations:** These records are secondary archival surrogates written by archivists, not primary historical texts. They cannot be used for close textual analysis, sentiment analysis, or exact document counts inside each folder. Date ranges reflect the extreme dates of items inside the folder (for example, `A6S8Y3F26` starts in 1932 due to older legislation included as background).

## Ethical and Legal Aspects
* **Copyright and Source Licence:** The underlying finding aid is published by the Bank of Greece and governed by its Terms of Use (`All rights reserved`; accurate reproduction with attribution is permitted, while commercial sale or modification of original files is prohibited without written consent). No primary archival scans or copyrighted texts are uploaded to this repository.
* **Personal Information:** Folder descriptions reference historical public figures (such as Ioannis Pesmazoglou, Nikolaos Makarezos, Georgios-Alexandros Mangakis, and Günter Grass) in their public political or intellectual capacities. No sensitive private personal data of living individuals is included.

## Licence and Citation
The structured metadata schema, controlled-vocabulary annotations in `data.csv`, and validation code in `check_dataset.ipynb` are shared under a **CC BY 4.0** licence. The underlying archival descriptions remain the intellectual property of the Historical Archive of the Bank of Greece.

**Suggested citation:**
Tsirikos, A. (2026). *Ioannis (Yangos) Pesmazoglou Anti-Dictatorship Discourse Metadata (A6S8Y3)* [Dataset]. Derived from Bank of Greece Historical Archive, Archive 6, Series 8, Subseries 3.