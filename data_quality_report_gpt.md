### Data Quality Audit of Wind Farm Maintenance Logs
#### Summary of Findings
- **Finding 1**: Extensive duplication between Description and Observations (often verbatim with trailing filler words).
- **Finding 2**: High rate of missing input in the Observations column, missing added value.
- **Finding 3**: Inconsistent error/event code formatting (e.g., FM codes, Q7/Q8 states) and mixed capitalisation/spaces.
- **Finding 4**: Frequent spelling/typing errors, corrupted characters (e.g., “øC”, stray underscores), and inconsistent diacritics.
- **Finding 5**: Mixed language and terminology (Portuguese + English terms; “Blade A”, “pá A”, “Axis 1”) leading to ambiguity.
- **Finding 6**: Lack of quantitative detail (no measured values, units, limits) and missing root cause/outcome context.
- **Finding 7**: Copy-pasted alarm texts without their meaning, clear action taken, resolution, or validation results.
- **Finding 8**: Uncontrolled free-text for components/locations; abbreviations and acronyms used without definition.

#### Common Issues Identified
- **Issue 1 - Redundant entries**: Observations often repeat the Description verbatim and append “para” with the identifier, adding noise and inflating storage without analytical value.

- **Issue 2 – Missing context**: Observations field is frequently empty instead of stating diagnostics, actions, or outcomes.

- **Issue 3 – Inconsistent error code syntax**: Alarm/fault codes (FMxxxx, RT/Q8 events) appear with inconsistent spacing/capitalisation and malformed fragments (e.g., “V,NoRT”, “._”, “____”), impairing parsing and normalisation.

- **Issue 4 – Mixed nomenclature and languages**: Component identifiers and part names fluctuate between Portuguese and English and between formats (“Rotor Blade No. 1”, “pá A”, “Blade A”), undermining entity matching.

- **Issue 5 – Typos and corrupted characters**: Frequent misspellings (“torrre”, “hydraulcia”), malformed characters (e.g., “øC” instead of “°C”), and punctuation artefacts from CSV quoting reduce readability and model accuracy.

- **Issue 6 – Lack of quantitative evidence**: Descriptions reference temperatures, pressures, speeds, or thresholds without numeric values or units; limits reached are stated but not quantified.

- **Issue 7 – Action and outcome not recorded**: Many entries capture the alarm text but omit what was tested/replaced/adjusted and whether the fault was cleared or monitored post-repair.

- **Issue 8 – Acronyms without expansion**: Terms like CMS, MI, LPC, HSS, NDE/DE, TP used without definition/context, hindering future readers and automated classification.

- **Issue 9 – Free-form component/location labels**: Same asset areas recorded with different strings (e.g., “TopBox”, “Top Box”), complicating grouping and KPI calculations.

- **Issue 10 – Inconsistent unit usage and formatting**: Units are sometimes missing or malformed (mbar/°C written as “mbar/ øC”); decimal separators and thousand separators are inconsistent.

#### Actionable Recommendations
- **Recommendation 1 – Enforce a structured free-text template**: In Description, require: (a) Fault/Alarm & code; (b) Component & precise location; (c) Symptom with measurements; (d) Action taken; (e) Result/verification. In Observations, add only new details (diagnostics, photos, follow-up), not a repeat.

- **Recommendation 2 – Separate and validate codes in dedicated fields**: Capture alarm/fault codes (e.g., FM####, Q7/Q8 state) in standardised, validated fields with regex checks; prohibit codes inside free-text unless expanded.

- **Recommendation 3 – Standardise terminology and language**: Provide a controlled vocabulary (picklists) for components, sub-systems, locations, and blade IDs; require a single language for narrative text, with auto-expansion of common acronyms on first use.

- **Recommendation 4 – Mandate quantitative data with units**: When citing thresholds/measurements (temperature, pressure, RPM, voltage), require numeric value + unit (SI) + limit reference; implement unit picklists and auto-formatting (e.g., °C, bar, rpm, V).

- **Recommendation 5 – Block duplication and filler tokens**: Prevent Observations from matching Description; strip trailing filler words via input rules; flag entries that contain only placeholders.

- **Recommendation 6 – Provide spellcheck and character sanitisation**: Enable in-form spellcheck and automatic character normalisation (e.g., “°C” not “øC”), and fix common OCR/CSV artefacts (double quotes, stray underscores).

- **Recommendation 7 – Require action and outcome fields**: Make “Action performed” and “Outcome/Verification” mandatory with options: replaced/adjusted/tested/restarted; include “fault cleared?” yes/no and “post-action reading”.

- **Recommendation 8 – Use controlled picklists and IDs**: Component, sub-assembly, and location must be selected from controlled lists (e.g., Hub > Pitch System > Battery Contactor) with consistent casing (Top Box vs TopBox).

- **Recommendation 9 – Embed quick-reference guidance in the form**: Show short examples for good entries; display tooltips for acronyms (e.g., CMS = Condition Monitoring System) and a one-click “expand acronym” helper.

- **Recommendation 10 – Implement data quality gates**: On save, run validations (no placeholder text, required fields present, units present, code formats correct). Soft-block entries that fail and prompt the technician to correct before submission.