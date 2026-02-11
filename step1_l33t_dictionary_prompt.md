# Step 1: The Dictionary Phase — 703 L33t-Speak Mapping for Electrical Terms

## Purpose

This prompt instructs Gemini to generate a comprehensive, deterministic mapping
table that converts standard electrical / NFPA 70E terminology into "703 l33t
speak." The dictionary must be **consistent** (same input always produces the
same output) and **complete** enough to drive large-scale document translation
without ad-hoc improvisation.

---

## Prompt

```
You are a linguistics engineer specializing in systematic writing-system
transformations. Your task is to produce a production-grade "703 L33t Speak"
dictionary for the electrical safety domain.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SECTION 1 — CHARACTER SUBSTITUTION ALPHABET
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

First, define the canonical single-character substitution table that all
word-level mappings will be built from. Use the following standard 703 l33t
mapping (one primary substitution per letter):

| Letter | L33t | Notes                                      |
|--------|------|--------------------------------------------|
| A      | 4    |                                            |
| B      | 8    |                                            |
| C      | (    | Parenthesis resembles C                    |
| D      | D    | Kept literal — no clean numeric equivalent |
| E      | 3    |                                            |
| F      | F    | Kept literal                               |
| G      | 6    |                                            |
| H      | #    |                                            |
| I      | 1    |                                            |
| J      | J    | Kept literal                               |
| K      | K    | Kept literal                               |
| L      | 1    | Context-dependent; uses position rules     |
| M      | M    | Kept literal                               |
| N      | N    | Kept literal                               |
| O      | 0    | Zero                                       |
| P      | P    | Kept literal                               |
| Q      | Q    | Kept literal                               |
| R      | R    | Kept literal                               |
| S      | 5    |                                            |
| T      | 7    |                                            |
| U      | U    | Kept literal                               |
| V      | V    | Kept literal                               |
| W      | W    | Kept literal                               |
| X      | X    | Kept literal                               |
| Y      | Y    | Kept literal                               |
| Z      | 2    |                                            |

### Disambiguation Rules

When two letters share the same numeral (I=1 and L=1), apply these rules to
keep the output human-readable:

- **I → 1** takes priority when the letter appears at the START of a word or
  as a standalone word ("I", "In", "Is").
- **L → 1** applies when the letter is in the MIDDLE or END of a word
  ("Electrical" → "31337R1(41").
- If both I and L appear in the same word, both use 1. Readability is preserved
  by the surrounding character context.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SECTION 2 — CORE ELECTRICAL TERM DICTIONARY
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Using the character table above, generate the l33t-speak equivalent for every
term below. Present the results as a three-column table:

| Original Term | L33t Equivalent | Category |

### 2A. Fundamental Electrical Concepts

- Voltage
- Current
- Resistance
- Power
- Energy
- Ampere
- Watt
- Ohm
- Conductor
- Insulator
- Circuit
- Load
- Phase
- Frequency
- Impedance
- Capacitance
- Inductance
- Transformer
- Relay
- Switch
- Breaker
- Fuse
- Wire
- Cable
- Terminal
- Bus
- Panel
- Conduit
- Raceway
- Junction

### 2B. NFPA 70E Safety Terms

- Hazard
- Shock
- Arc Flash
- Arc Blast
- Incident Energy
- Flash Protection
- Boundary
- Limited Approach Boundary
- Restricted Approach Boundary
- Prohibited Approach Boundary
- Energized
- De-energized
- Lockout
- Tagout
- Lockout Tagout
- Grounding
- Bonding
- Ground Fault
- Equipment Grounding Conductor
- Qualified Person
- Unqualified Person
- Electrical Safety
- Safe Work Practices
- Energized Electrical Work Permit
- Risk Assessment
- Job Safety Planning
- Barricade
- Safety Signs
- Warning
- Danger
- Caution

### 2C. Personal Protective Equipment (PPE)

- PPE (keep as abbreviation)
- Arc Rating
- Arc-Rated
- Face Shield
- Hard Hat
- Safety Glasses
- Insulated Gloves
- Rubber Gloves
- Leather Protectors
- Arc Flash Suit
- Balaclava
- Hearing Protection
- Flash Suit Hood
- Voltage-Rated
- Dielectric
- Category 1
- Category 2
- Category 3
- Category 4

### 2D. Procedures & Compliance

- Electrically Safe Work Condition
- Verification
- Absence of Voltage
- Test Instrument
- Multimeter
- Clamp Meter
- Megohmmeter
- Infrared
- Thermography
- Maintenance
- Inspection
- Installation
- Compliance
- Violation
- Standard
- Code
- Regulation
- Authority Having Jurisdiction
- Listed
- Labeled
- Approved
- Certified
- Short Circuit
- Overload
- Overcurrent
- Fault Current
- Available Fault Current
- Clearing Time
- Interrupting Rating

### 2E. Workplace & Equipment

- Switchgear
- Motor Control Center
- Panelboard
- Switchboard
- Disconnect
- Generator
- Uninterruptible Power Supply
- Battery
- Photovoltaic
- Substation
- Overhead Line
- Underground
- Service Entrance
- Meter
- Receptacle
- Outlet
- Luminaire
- Ballast
- Enclosure
- NEMA Rating
- Ingress Protection
- Explosion Proof
- Classified Location
- Hazardous Location

### 2F. Common Verbs & Modifiers

- Energize
- De-energize
- Isolate
- Verify
- Test
- Inspect
- Install
- Remove
- Replace
- Connect
- Disconnect
- Protect
- Expose
- Approach
- Contact
- Measure
- Calculate
- Document
- Train
- Supervise
- Comply
- Rated
- Live
- Dead
- Exposed
- Enclosed
- Guarded
- Accessible
- Nominal
- Maximum
- Minimum

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SECTION 3 — MULTI-WORD TERM & PHRASE RULES
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

For compound terms and phrases, apply these conventions:

1. **Word boundaries**: Preserve spaces between words.
   "Arc Flash" → "4R( F14 5#"  (each word converted independently)

2. **Hyphenated terms**: Keep the hyphen; convert each side.
   "Arc-Rated" → "4R(-R473D"

3. **Abbreviations & Acronyms**: Do NOT convert recognized abbreviations.
   PPE stays PPE. NFPA stays NFPA. NEC stays NEC. OSHA stays OSHA.
   GFCI stays GFCI. AFI stays AFI. UPS stays UPS. MCC stays MCC.
   AHJ stays AHJ. IEEE stays IEEE.

4. **Parenthetical references**: Do NOT convert content inside parentheses
   when it is a code reference: "(Table 130.5(C))" stays unchanged.

5. **Slash-separated terms**: Convert each side of the slash.
   "Lockout/Tagout" → "10(K0U7/74 60U7"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SECTION 4 — PROTECTED TOKENS (INTERFACE WITH STEP 2)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

The dictionary must include a "DO NOT CONVERT" list. These tokens are
protected by the Critical Data Points manifest (see Step 2). When the
translation engine encounters any of the following patterns, it must
skip the l33t conversion and output the original text verbatim:

- **Numerical values with units**: 50V, 100V DC, 1.2 cal/cm², 480V,
  600V, 4160V, 18 inches, 457 mm, 2 seconds, etc.
- **NFPA section references**: Article 100, Section 130.2, Table 130.5(C),
  Table 130.4(D)(a), Annex D, etc.
- **PPE category numbers when used as ratings**: Category 1, Category 2,
  Category 3, Category 4 (the DIGIT is protected; the word "Category"
  can be converted: "(473 60RY 1", "(473 60RY 2", etc.).
- **Anything wrapped in [CDP]...[/CDP] tags**.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SECTION 5 — MACHINE-READABLE OUTPUT FORMAT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

After the human-readable tables, output the entire dictionary as a JSON
object for programmatic consumption by the translation engine:

{
  "dictionary_version": "1.0",
  "l33t_variant": "703",
  "domain": "electrical_safety_nfpa70e",
  "character_map": {
    "A": "4", "B": "8", "C": "(", "D": "D", "E": "3",
    "F": "F", "G": "6", "H": "#", "I": "1", "J": "J",
    "K": "K", "L": "1", "M": "M", "N": "N", "O": "0",
    "P": "P", "Q": "Q", "R": "R", "S": "5", "T": "7",
    "U": "U", "V": "V", "W": "W", "X": "X", "Y": "Y",
    "Z": "2"
  },
  "disambiguation": {
    "I_vs_L": "I→1 at word-start or standalone; L→1 mid/end of word"
  },
  "protected_abbreviations": [
    "PPE", "NFPA", "NEC", "OSHA", "GFCI", "AFCI", "UPS", "MCC",
    "AHJ", "IEEE", "AWG", "NEMA", "IP", "UL", "ANSI", "ASTM",
    "CSA", "HRC", "ARC", "AC", "DC", "LED", "PV", "RPM"
  ],
  "terms": [
    {
      "original": "Voltage",
      "l33t": "V0174 63",
      "category": "fundamental"
    },
    {
      "original": "Current",
      "l33t": "(URR3N7",
      "category": "fundamental"
    },
    {
      "original": "Hazard",
      "l33t": "#424RD",
      "category": "nfpa70e_safety"
    },
    {
      "original": "Grounding",
      "l33t": "6R0UND1N6",
      "category": "nfpa70e_safety"
    }
    // ... all remaining terms follow this structure
  ],
  "conversion_rules": {
    "preserve_spaces": true,
    "preserve_hyphens": true,
    "skip_abbreviations": true,
    "skip_cdp_tokens": true,
    "skip_code_references": true,
    "case_sensitivity": "convert all letters to uppercase before mapping"
  }
}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SECTION 6 — CONSISTENCY REQUIREMENTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

For this dictionary to function in large-scale document translation, it
must satisfy the following properties:

1. **Deterministic**: Running the same input through the mapping must ALWAYS
   produce the same output. No randomized or alternate substitutions.

2. **Idempotent awareness**: Clearly mark which l33t characters collide with
   real digits so the reverse-translation engine can handle them. Provide a
   "collision report" listing every l33t output character that is also a
   digit (0-9), and note which original letter it maps from.

3. **Collision Report Format**:
   | L33t Char | Could Mean (letter) | Could Mean (digit) | Resolution Strategy     |
   |-----------|--------------------|--------------------|------------------------|
   | 0         | O                  | zero               | CDP-tagged = digit      |
   | 1         | I or L             | one                | CDP-tagged = digit      |
   | 2         | Z                  | two                | CDP-tagged = digit      |
   | 3         | E                  | three              | CDP-tagged = digit      |
   | 4         | A                  | four               | CDP-tagged = digit      |
   | 5         | S                  | five               | CDP-tagged = digit      |
   | 6         | G                  | six                | CDP-tagged = digit      |
   | 7         | T                  | seven              | CDP-tagged = digit      |
   | 8         | B                  | eight              | CDP-tagged = digit      |

   The resolution strategy: if a digit appears inside a [CDP] tag, it is a
   real number and must not be reverse-mapped. Outside CDP tags, digits are
   l33t-speak letter substitutions.

4. **Coverage completeness**: After generating all term mappings, provide a
   coverage summary:
   - Total terms mapped
   - Terms by category
   - Any terms where the l33t output is ambiguous or hard to read, with a
     suggested "readability note" for each

5. **Extensibility**: Include a section explaining how a user would add new
   terms to the dictionary by applying the character map, with 3 worked
   examples of terms NOT already in the dictionary.
```

---

## Relationship to Other Steps

| Step | Role | Interaction with This Dictionary |
|------|------|----------------------------------|
| **Step 1** (this file) | Defines the character map and term translations | — |
| **Step 2** (Logic Guardrail) | Identifies protected numerical values (CDPs) | Dictionary skips all CDP-tagged tokens |
| **Step 3+** (Translation) | Applies dictionary to full NFPA 70E content | Consumes the JSON dictionary + CDP manifest |

The dictionary and the CDP manifest work as complementary layers:
- The **dictionary** says *what to convert* and *how*.
- The **CDP manifest** says *what to never convert* and *why*.

Together they ensure the l33t-speak output is stylistically consistent while
remaining technically and legally accurate.
