# Master Thesis Experiment Prototype

This repository contains the browser-based prototype for my master thesis experiment at the University of Amsterdam.

The experiment is part of the thesis project:

**Designing Uncertainty-Aware AI Interfaces: Verbal Hedging and Trust Calibration in Text and Synthetic Speech**

The prototype is implemented as a single-page application in `index.html`.

## Project purpose

The experiment investigates how people evaluate AI-generated answers and how interface design may influence trust, verification behaviour, and reliance decisions.

The study specifically focuses on two design factors:

1. **Verbal hedging**  
   Whether the assistant uses uncertainty cues such as “I think”, “It seems that”, “about”, or “roughly”.

2. **Output modality**  
   Whether answers are presented as text only or as text with synthetic speech.

Participants complete a sequence of general knowledge evaluation trials. On each trial, they see a question and an AI-generated answer. Some answers are intentionally correct and some are intentionally incorrect. Participants can accept the answer, reject it, or verify supporting information before making a final decision.

## Experimental design

The study uses a **2 × 2 between-subjects design**.

| Condition | Hedging | Modality |
|---|---:|---:|
| C1 | No hedge | Text |
| C2 | Hedge | Text |
| C3 | No hedge | Speech |
| C4 | Hedge | Speech |

Participants are assigned to one of these four conditions.

## Experiment flow

The participant flow is:

1. Landing page
2. Informed consent
3. Audio check for speech conditions
4. Instructions
5. Practice trials
6. Main task with 30 trials across 3 blocks
7. Manipulation checks
8. Trust questionnaire
9. NASA-TLX workload questionnaire
10. User Experience Questionnaire
11. Post-task questions
12. Final reflection questions
13. Debrief and data save

## Measures

The prototype logs behavioural and questionnaire data.

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

Questionnaire measures include:

- manipulation checks for perceived uncertainty and certainty
- trust and perceived reliability items
- NASA-TLX workload items
- full 26-item User Experience Questionnaire
- post-task reflection questions

## UEQ implementation

The prototype uses the full 26-item User Experience Questionnaire.

The original item wording, item order, seven-point semantic differential format, and polarity are preserved. To reduce visual load, the UEQ is presented across two consecutive pages:

- page 1: items 1–13
- page 2: items 14–26

No additional randomisation of UEQ items or polarity is applied.

UEQ item scores are transformed to the standard `-3` to `+3` range, where higher scores indicate a more positive user experience.

The six UEQ scales are:

- Attractiveness
- Perspicuity
- Efficiency
- Dependability
- Stimulation
- Novelty

## Running the prototype

The prototype can be run directly from the `index.html` file.

To run locally:

1. Download or clone this repository.
2. Open `index.html` in a modern browser.
3. Start the study from the landing page.

Recommended browsers:

- Google Chrome
- Microsoft Edge
- Safari

Speech synthesis availability may differ between browsers and operating systems.

## GitHub Pages

This repository can be hosted with GitHub Pages.

If `index.html` is placed in the root of the repository, GitHub Pages will serve the experiment page automatically.

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

## Data storage

The prototype stores data in two ways:

1. **Local browser storage**  
   Data is saved to the browser’s local storage as a fallback.

2. **Backend endpoint**  
   If configured, data is also sent to the backend endpoint defined in the code.

If automatic sending fails, the prototype still saves the session locally.

## Privacy

The prototype is designed for anonymous academic data collection.

It does not ask for:

- participant name
- email address
- phone number
- direct personal identifiers

Data is stored with anonymous participant/session identifiers and is intended to be analysed at group level.

## Important notes

Before using the prototype for real data collection, the following should be tested:

- all four experimental conditions
- speech playback
- audio check and secret word validation
- condition assignment
- data saving to the backend
- local JSON and CSV export
- source links in the verification panel
- complete participant flow from start to finish

## Limitations

This is a research prototype, not a production system.

Known limitations include:

- browser speech synthesis voices may differ between devices
- audio quality depends on participant hardware and browser settings
- local storage can be cleared by the browser or user
- the prototype cannot prevent participants from using external search tools
