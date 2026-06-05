# Master Thesis Experiment Prototype and Data Submission

This repository contains the browser-based prototype, cleaned datasets, final analysis notebook, and generated figures for my master thesis experiment at the University of Amsterdam.

The experiment is part of the thesis project:

**Designing Uncertainty-Aware AI Interfaces: Verbal Hedging and Trust Calibration in Text and Synthetic Speech**

The prototype is implemented as a single-page browser application in:

```text
https://mandydamsteegt.github.io/Master_Thesis/
```

The final data analysis reported in the thesis was conducted using:

```text
data/scripts/Data Analyse Defi.ipynb
```

---

## Project purpose

The experiment investigates how people evaluate AI-generated answers and how interface design may influence trust, verification behaviour, and reliance decisions.

The study focuses on two design factors:

### Verbal hedging

Whether the assistant uses uncertainty cues such as:

```text
I think
It seems that
about
roughly
```

### Output modality

Whether answers are presented as:

```text
Text only
Text with synthetic speech
```

Participants complete a sequence of general-knowledge evaluation trials. On each trial, they see a question and an AI-generated answer. Some answers are intentionally correct and some are intentionally incorrect. Participants can accept the answer, reject it, or verify supporting information before making a final decision.

---

## Experimental design

The study uses a **2 × 2 between-subjects design**.

| Condition | Hedging | Modality |
|---|---|---|
| **C1** | No hedge | Text |
| **C2** | Hedge | Text |
| **C3** | No hedge | Speech |
| **C4** | Hedge | Speech |

Participants are assigned to one of these four conditions.

The final sample consisted of **72 participants**, with **18 participants per condition**. Each participant completed **30 main trials**, resulting in **2160 trial-level observations**.

---

## Repository structure

```text
.
├── README.md
│
├── data/
│   ├── rawdata/
│   │   └── data tijdelijk.docx
│   │
│   ├── cleandata/
│   │   ├── ai_hedging_clean_participants.csv
│   │   ├── ai_hedging_clean_trials_long.csv
│   │   ├── ai_hedging_clean_interviews.csv
│   │   ├── ai_hedging_condition_summary.csv
│   │   ├── ai_hedging_block_summary.csv
│   │   └── ai_hedging_data_dictionary.csv
│   │
│   └── scripts/
│       └── Data Analyse Defi.ipynb
│
├── analysis_outputs/
│   └── figures/
│       ├── manipulation_check_uncertainty_certainty.png
│       ├── hedging_effect_verification_correctness.png
│       ├── srq1_verification_by_hedging_and_correctness.png
│       ├── srq2_acceptance_incorrect_answers_by_condition.png
│       ├── srq3_interaction_hedging_modality_accuracy.png
│       ├── srq3_interaction_hedging_modality_verification.png
│       ├── srq4_final_accuracy_across_blocks.png
│       └── srq4_verification_rate_across_blocks.png
│
├── prototype/
│   ├── executable/
│   │   └── index.html
│   │
│   └── src/
│       └── index.html
│
└── misc/
    ├── exclusion_or_data_quality_notes.txt
    └── participant_notes.csv
```

---

## Experiment flow

The participant flow is:

1. **Landing page**
2. **Informed consent**
3. **Audio check for speech conditions**
4. **Instructions**
5. **Practice trials**
6. **Main task with 30 trials across 3 blocks**
7. **Manipulation checks**
8. **Trust questionnaire**
9. **NASA-TLX workload questionnaire**
10. **User Experience Questionnaire**
11. **Post-task questions**
12. **Final reflection questions**
13. **Debrief and data save**

---

## Measures

The prototype logs behavioural and questionnaire data.

### Behavioural measures

Behavioural measures include:

- assigned condition
- item ID
- block number
- trial index
- answer correctness
- displayed answer
- hedge phrase and hedge type
- verification behaviour
- evidence dwell time
- source-opening behaviour
- final accept or reject decision
- decision time
- final decision accuracy

### Questionnaire measures

Questionnaire measures include:

- manipulation checks for perceived uncertainty and certainty
- trust and perceived reliability items
- NASA-TLX workload items
- full 26-item User Experience Questionnaire
- post-task reflection questions

---

## UEQ implementation

The prototype uses the **full 26-item User Experience Questionnaire**.

The original item wording, item order, seven-point semantic differential format, and polarity are preserved. To reduce visual load, the UEQ is presented across two consecutive pages:

- **Page 1:** items 1–13
- **Page 2:** items 14–26

No additional randomisation of UEQ items or polarity is applied.

UEQ item scores are transformed to the standard **-3 to +3 range**, where higher scores indicate a more positive user experience.

The six UEQ scales are:

- **Attractiveness**
- **Perspicuity**
- **Efficiency**
- **Dependability**
- **Stimulation**
- **Novelty**

---

## Running the prototype

The prototype can be run directly from the `index.html` file.

To run locally:

1. Download or clone this repository.
2. Open `https://mandydamsteegt.github.io/Master_Thesis/` in a modern browser.
3. Start the study from the landing page.

Recommended browsers:

- Google Chrome
- Microsoft Edge
- Safari
- Firefox

Speech synthesis availability may differ between browsers and operating systems.

For the speech conditions, audio playback should be enabled and the device volume should be set to a comfortable level.

---

## GitHub Pages

This repository can be hosted with **GitHub Pages**.

If `index.html` is placed in the root of the repository, GitHub Pages will serve the experiment page automatically.

In this repository structure, the executable file is stored at:

```text
prototype/executable/index.html
```

If GitHub Pages is used, the file may need to be copied to the repository root or the GitHub Pages settings should point to the correct folder, depending on the hosting setup.

---

## Admin interface

The prototype includes a hidden researcher interface for managing and inspecting experiment sessions.

The admin interface can be used to:

- start a participant session manually
- select manual or balanced condition assignment
- load locally saved sessions
- import participant JSON files
- export aggregated JSON data
- export trial-level CSV data
- inspect condition-level and item-level summaries

The admin interface is intended only as a lightweight researcher tool for this prototype and should not be treated as secure production authentication.

---

## Data storage

The prototype stores data in two ways.

### Local browser storage

Data is saved to the browser’s local storage as a fallback.

### Backend endpoint

If configured, data is also sent to the backend endpoint defined in the code.

If automatic sending fails, the prototype still saves the session locally.

---

## Data files

The repository includes raw and cleaned data files used for the thesis analysis.

### Raw data

The raw data export is stored in:

```text
data/rawdata/data tijdelijk.docx
```

This file contains the original participant-level data export, including participant metadata, condition assignment, questionnaire responses, post-task responses, qualitative responses, and trial-level logs.

The raw export includes, where applicable:

- participant ID
- source file name
- condition assignment
- condition label
- hedging condition
- modality condition
- informed consent status
- session start and end timestamps
- manipulation-check responses
- trust questionnaire responses
- NASA-TLX workload responses
- User Experience Questionnaire responses
- post-task responses
- qualitative reflection responses
- researcher notes
- number of completed trials
- session status
- practice trial completion status
- break durations
- trial-level logs
- displayed AI answer
- answer correctness
- hedge phrase and hedge type
- verification behaviour
- evidence panel usage
- source-opening behaviour
- final accept/reject decision
- decision time
- final decision accuracy
- voice-related metadata for speech conditions

Where applicable, information not required for reproducing the analysis was removed before long-term storage.

### Cleaned data

The cleaned data files are stored in:

```text
data/cleandata/
```

The cleaned data files are:

```text
ai_hedging_clean_participants.csv
ai_hedging_clean_trials_long.csv
ai_hedging_clean_interviews.csv
ai_hedging_condition_summary.csv
ai_hedging_block_summary.csv
ai_hedging_data_dictionary.csv
```

#### `ai_hedging_clean_participants.csv`

Participant-level cleaned dataset. Each row represents one participant.

This file includes participant-level information such as:

- participant ID
- condition
- condition label
- hedging condition
- modality condition
- manipulation-check responses
- trust questionnaire responses
- NASA-TLX workload responses
- UEQ responses
- post-task responses
- participant-level summary measures

#### `ai_hedging_clean_trials_long.csv`

Trial-level long-format cleaned dataset. Each row represents one participant-trial observation.

This is the main dataset for the behavioural analyses.

This file includes trial-level variables such as:

- participant ID
- condition
- condition label
- hedging condition
- modality condition
- item ID
- block
- trial index
- answer correctness
- displayed AI answer
- hedge phrase
- hedge type
- verification behaviour
- evidence panel usage
- source-opening behaviour
- final decision
- decision time
- final accuracy
- question text

#### `ai_hedging_clean_interviews.csv`

Cleaned qualitative reflection dataset. This file contains the open-text responses used to support the interpretation of the behavioural findings.

The qualitative responses cover topics such as:

- what strategy participants used when deciding to accept, reject, or verify
- whether hedging phrases were noticed
- whether modality influenced interpretation
- whether behaviour changed across blocks

#### `ai_hedging_condition_summary.csv`

Condition-level summary file with descriptive statistics by experimental condition.

#### `ai_hedging_block_summary.csv`

Block-level summary file with descriptive statistics across the three repeated interaction blocks.

This file was used to inspect behavioural adaptation over time, including changes in verification rate, final accuracy, and decision time across blocks.

#### `ai_hedging_data_dictionary.csv`

Data dictionary explaining the variable names, labels, and coding conventions used in the cleaned datasets.

This file should be consulted before reproducing the analysis.

---

## Main coding conventions

### Condition coding

| Code | Condition |
|---|---|
| **C1** | No hedge + Text |
| **C2** | Hedge + Text |
| **C3** | No hedge + Speech |
| **C4** | Hedge + Speech |

### Hedging coding

| Value | Meaning |
|---|---|
| **0** | No hedge |
| **1** | Hedge |

### Modality coding

| Value | Meaning |
|---|---|
| **0** | Text |
| **1** | Speech |

### Answer correctness coding

| Value | Meaning |
|---|---|
| **0** | Incorrect AI answer |
| **1** | Correct AI answer |

### Verification behaviour coding

| Value | Meaning |
|---|---|
| **0** | Participant did not verify |
| **1** | Participant verified/opened the evidence panel |

### Final accuracy coding

| Value | Meaning |
|---|---|
| **0** | Participant’s final answer was incorrect |
| **1** | Participant’s final answer was correct |

### Block coding

| Value | Meaning |
|---|---|
| **1** | Block 1 |
| **2** | Block 2 |
| **3** | Block 3 |

---

## Final analysis notebook

The final analysis was conducted in:

```text
data/scripts/Data Analyse Defi.ipynb
```

This notebook loads the cleaned datasets, performs the final descriptive and inferential analyses, and generates the figures used in the thesis.

The notebook performs the final analysis steps, including:

1. Loading the cleaned datasets.
2. Checking the sample size and condition balance.
3. Summarising participant counts per condition.
4. Calculating manipulation-check summaries.
5. Calculating verification rates by hedging and answer correctness.
6. Calculating verification rates by condition.
7. Calculating acceptance of incorrect answers by condition.
8. Calculating final accuracy by condition and modality.
9. Calculating interaction patterns between hedging and modality.
10. Calculating verification and final accuracy patterns across blocks.
11. Generating the final figures used in the thesis.

To reproduce the analysis, run `Data Analyse Defi.ipynb` from top to bottom.

The notebook assumes that the cleaned CSV files are available in:

```text
data/cleandata/
```

---

## Figures

The figures generated from the final analysis notebook are stored in:

```text
analysis_outputs/figures/
```

Included figures:

```text
manipulation_check_uncertainty_certainty.png
hedging_effect_verification_correctness.png
srq1_verification_by_hedging_and_correctness.png
srq2_acceptance_incorrect_answers_by_condition.png
srq3_interaction_hedging_modality_accuracy.png
srq3_interaction_hedging_modality_verification.png
srq4_final_accuracy_across_blocks.png
srq4_verification_rate_across_blocks.png
```

### Figure descriptions

#### `manipulation_check_uncertainty_certainty.png`

Shows perceived uncertainty and perceived certainty by hedging condition.

#### `hedging_effect_verification_correctness.png`

Shows the change in verification rate between the hedge and no-hedge conditions for correct and incorrect answers.

#### `srq1_verification_by_hedging_and_correctness.png`

Shows verification rates by hedging condition and answer correctness.

#### `srq2_acceptance_incorrect_answers_by_condition.png`

Shows the acceptance rate for incorrect AI answers across the four experimental conditions.

#### `srq3_interaction_hedging_modality_accuracy.png`

Shows the interaction between hedging and modality on final accuracy.

#### `srq3_interaction_hedging_modality_verification.png`

Shows the interaction between hedging and modality on verification rate.

#### `srq4_final_accuracy_across_blocks.png`

Shows final accuracy across the three interaction blocks by experimental condition.

#### `srq4_verification_rate_across_blocks.png`

Shows verification rate across the three interaction blocks by experimental condition.

---

## Reproducibility route

To reproduce the final reported analysis:

1. Open the cleaned data folder:

```text
data/cleandata/
```

2. Review the data dictionary:

```text
data/cleandata/ai_hedging_data_dictionary.csv
```

3. Open the final analysis notebook:

```text
data/scripts/Data Analyse Defi.ipynb
```

4. Run the notebook from top to bottom.

5. Compare the generated outputs with the figures in:

```text
analysis_outputs/figures/
```

To inspect the original raw export:

```text
data/rawdata/data tijdelijk.docx
```

To re-run or inspect the prototype:

```text
prototype/executable/index.html
```

---

## Data quality and exclusions

See:

```text
misc/exclusion_or_data_quality_notes.txt
```

Suggested content if no participants were excluded:

```text
No participants were excluded from the final dataset. The final sample consisted of 72 participants, with 18 participants per condition. Each participant completed 30 main trials, resulting in 2160 trial-level observations.

The final analysis reported in the thesis was conducted using `Data Analyse Defi.ipynb`. The figures in `analysis_outputs/figures/` were generated from this final analysis notebook.
```

---

## Participant notes

See:

```text
misc/participant_notes.csv
```

Suggested content if no notable participant-level issues were recorded:

```csv
participant_id,notes
ALL,No notable participant-level issues or irregularities were recorded during data collection.
```

---

## Important notes before running the prototype

Before using the prototype for real data collection, the following should be tested:

- all four experimental conditions
- speech playback
- audio check and secret word validation
- condition assignment
- data saving to the backend
- local JSON and CSV export
- source links in the verification panel
- complete participant flow from start to finish

---

## Limitations

This is a research prototype, not a production system.

Known limitations include:

- browser speech synthesis voices may differ between devices
- audio quality depends on participant hardware and browser settings
- local storage can be cleared by the browser or user
- the prototype cannot prevent participants from using external search tools
- speech playback may behave differently across browsers and operating systems
- online participation limits control over participants’ environment
- the evidence panel is a controlled research mechanism and does not represent a full real-world search process

---

## Privacy

The prototype is designed for anonymous academic data collection.

It does **not** ask for:

- participant name
- email address
- phone number
- direct personal identifiers

Data is stored with anonymous participant/session identifiers and is intended to be analysed at group level.

---

## Final note

The definitive analysis route for this thesis submission is:

```text
data/cleandata/
→ data/scripts/Data Analyse Defi.ipynb
→ analysis_outputs/figures/
```

Only `Data Analyse Defi.ipynb` and the figures listed in this README should be treated as the final analysis used for the thesis.
