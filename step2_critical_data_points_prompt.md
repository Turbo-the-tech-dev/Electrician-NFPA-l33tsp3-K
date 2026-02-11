# Step 2: The Logic Guardrail — Critical Data Points Extraction Prompt

## Purpose

This prompt instructs Gemini to extract every numerical safety limit from NFPA 70E
and tag each one as a **protected token** so that downstream l33t-speak stylistic
transformation cannot alter any value that carries legal or technical significance.

---

## Prompt

```
You are an electrical-safety data analyst. Your task has two phases:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PHASE 1 — EXTRACT CRITICAL DATA POINTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Scan the full text of NFPA 70E (Standard for Electrical Safety in the Workplace)
and extract every instance of a numerical safety limit. A "Critical Data Point"
is any number, value, threshold, or measurement that, if altered, could change
the technical meaning, legal requirement, or safety outcome of the standard.

For each Critical Data Point, record the following fields:

| Field              | Description                                                  |
|--------------------|--------------------------------------------------------------|
| cdp_id             | Sequential identifier (CDP-001, CDP-002, …)                 |
| value              | The exact numerical value with its unit (e.g., "50V")        |
| unit_type          | Category of unit (voltage, current, energy, distance, time)  |
| nfpa_section       | Section or table reference (e.g., "Table 130.5(C)")          |
| context            | One-sentence description of what the limit governs            |
| risk_if_altered    | What could go wrong if this number is changed                |
| protection_class   | One of: ABSOLUTE, THRESHOLD, RANGE_BOUND (defined below)     |

### Protection Classes

- **ABSOLUTE**: The value must never be modified in any form. Changing even one
  digit could create a life-safety hazard. Examples: voltage thresholds, incident
  energy boundaries, approach distances.

- **THRESHOLD**: The value defines a boundary between two safety categories or
  action levels. Altering it could reclassify a hazard incorrectly. Examples:
  arc-flash PPE category cutoffs, fault-current limits.

- **RANGE_BOUND**: The value is one endpoint of an acceptable range. Moving the
  endpoint widens or narrows the safe operating window. Examples: clearing times,
  working distances.

### Categories to Cover (non-exhaustive)

Extract Critical Data Points from at least the following domains:

1. **Voltage thresholds**
   - Shock hazard voltage threshold (50V AC / 100V DC and similar)
   - Nominal voltage ranges defining hazard categories

2. **Incident energy and arc-flash values**
   - 1.2 cal/cm² (arc-flash PPE boundary)
   - PPE category incident energy breakpoints (4, 8, 25, 40 cal/cm²)
   - Arc-flash boundary distances

3. **Approach boundaries**
   - Limited Approach Boundary distances
   - Restricted Approach Boundary distances
   - Prohibited Approach Boundary distances
   (as specified in Table 130.4(D)(a) and Table 130.4(D)(b))

4. **Fault-current and clearing-time values**
   - Available fault-current thresholds
   - Maximum clearing times for circuit-protective devices
   - Upstream overcurrent device ratings

5. **PPE arc ratings**
   - Minimum arc rating for each PPE category (cal/cm²)
   - HRC/ARC category numeric boundaries

6. **Working distances**
   - Standard working distances used in incident energy calculations
   - 18 inches (457 mm) and similar reference distances

7. **Time-based limits**
   - 2-second rule for arc-flash calculations
   - Equipment maintenance intervals tied to safety
   - De-energization verification wait times

8. **Miscellaneous numerical limits**
   - Insulation resistance test voltages
   - Ground-fault protection thresholds
   - Leakage-current limits
   - Equipment labeling requirements that include numeric values

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PHASE 2 — BUILD THE PROTECTION MANIFEST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Using the extracted data, produce a machine-readable protection manifest in JSON
format. This manifest will be consumed by a downstream l33t-speak transformation
engine. Its purpose is to guarantee that protected values pass through the
stylistic conversion UNCHANGED.

### Manifest Schema

{
  "manifest_version": "1.0",
  "standard": "NFPA 70E",
  "edition": "<edition year>",
  "generated_by": "Gemini — Critical Data Points Extraction",
  "protection_rules": {
    "description": "Rules the l33t-speak engine MUST obey",
    "rules": [
      {
        "rule_id": "R-001",
        "rule": "NEVER substitute digits within a Critical Data Point. The characters 0-9 are FROZEN inside any token tagged [CDP]. L33t-speak substitutions such as 3→E, 1→L, 0→O, 5→S, 7→T are PROHIBITED within CDP tokens."
      },
      {
        "rule_id": "R-002",
        "rule": "NEVER alter unit symbols or abbreviations attached to a Critical Data Point. V, kV, A, kA, cal/cm², mm, in., ft, AWG, kcmil, Hz, ms, s, and °C/°F must remain in their standard engineering form."
      },
      {
        "rule_id": "R-003",
        "rule": "NEVER split a number from its unit. '50V' must stay as '50V', not '50 V' or '5 0V'. '1.2 cal/cm²' must remain exactly '1.2 cal/cm²'."
      },
      {
        "rule_id": "R-004",
        "rule": "NEVER alter decimal points, negative signs, slash marks, or superscripts that are part of a numerical expression. '1.2', '-30°C', 'cal/cm²' must remain intact."
      },
      {
        "rule_id": "R-005",
        "rule": "NEVER change NFPA section references, table numbers, or article numbers. 'Table 130.5(C)', 'Article 100', 'Section 130.4(D)(a)' are protected references."
      },
      {
        "rule_id": "R-006",
        "rule": "Wrap every Critical Data Point in a [CDP]...[/CDP] token pair before passing text to the l33t-speak engine. The engine must treat everything inside these tags as immutable."
      },
      {
        "rule_id": "R-007",
        "rule": "After l33t-speak transformation, run a VERIFICATION PASS that compares every [CDP] token in the output against the protection manifest. Any mismatch must be flagged and reverted to the original value."
      }
    ]
  },
  "critical_data_points": [
    {
      "cdp_id": "CDP-001",
      "value": "50V",
      "unit_type": "voltage",
      "nfpa_section": "Article 100 / 130.2",
      "context": "AC voltage threshold above which a shock hazard exists",
      "risk_if_altered": "A higher number could falsely classify live parts as safe; a lower number could trigger unnecessary shutdowns",
      "protection_class": "ABSOLUTE",
      "protected_token": "[CDP]50V[/CDP]"
    }
    // ... all remaining CDPs follow this structure
  ]
}

### Output Requirements

1. Return the COMPLETE manifest as valid JSON.
2. Every Critical Data Point must have a unique cdp_id.
3. Include ALL numerical safety limits you can identify — err on the side of
   inclusion. If a number appears in a safety context, protect it.
4. After the JSON, provide a SUMMARY TABLE in markdown listing:
   - Total CDPs extracted
   - Count by protection_class (ABSOLUTE / THRESHOLD / RANGE_BOUND)
   - Count by unit_type
5. Flag any value where the same number appears in multiple contexts with
   different meanings (e.g., "2" as both a PPE category and a time in seconds).
```

---

## How This Prompt Functions as a Logic Guardrail

| Concern                         | How the prompt addresses it                              |
|---------------------------------|----------------------------------------------------------|
| Digits corrupted by l33t-speak  | Rule R-001 freezes all digits inside CDP tokens          |
| Units garbled (V → \/}          | Rule R-002 locks engineering unit symbols                |
| Numbers separated from units    | Rule R-003 keeps value+unit as atomic tokens             |
| Decimal / sign corruption       | Rule R-004 protects mathematical notation                |
| Section references mangled      | Rule R-005 shields regulatory cross-references           |
| Missed protection               | Rule R-006 requires explicit tagging before conversion   |
| Post-conversion drift           | Rule R-007 mandates a verification pass against manifest |

This two-phase approach ensures that the l33t-speak transformation layer
receives an explicit, machine-readable list of every value it must not touch,
rather than relying on pattern-matching heuristics that could miss edge cases.
