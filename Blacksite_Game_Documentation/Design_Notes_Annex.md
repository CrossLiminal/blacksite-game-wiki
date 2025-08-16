# **Design Notes Annex**

**Purpose:** This document is a living reference and companion to the formal design documentation. It contains the detailed context, reasoning, and illustrative examples behind the project's core mechanics and systems. Its purpose is to preserve the "why" behind the design, serving as the primary source material for writing the final, clean documentation.

---

## **Design Note: Universal Player Experience**

### **1. The "Page-Based" Experience**
*   **Finalized Concept:** The entire game, both in and out of encounters, uses a "page-based" narrative interface. The player is presented with a block of descriptive text summarizing events, followed by a set of choices.
*   **Key Mechanics:** This is a UI/UX principle that unifies the `Exploration_Engine` and the `Core_Encounter_Engine`. The `Exploration_Engine`'s "Scene Runner" and the `Encounter_Engine`'s "Player Input Trigger" are two different backend systems that produce the same user-facing result.
*   **Thematic Purpose:** Creates a consistent, immersive, and novel-like experience, focusing the player on narrative and choice rather than complex, real-time mechanics.
*   **Documentation Impact:** This is a foundational principle that should be stated in **`Project_Foundations.md`**.

### **2. The "Consequence of Failure" System**
*   **Problem Solved:** Prevents players from mindlessly spamming a failed skill check with no penalty.
*   **Finalized Concept:** Failure to overcome a challenge always has a cost, chosen from one of three models based on the action's context.
*   **The Three Costs:**
    1.  **Meter Cost:** The attrition model. Failure directly damages a relevant meter (`Vitality`, `Stability`, etc.).
    2.  **Escalation Cost:** The "making noise" model. Failure increases a hidden "Alert" tracker for the area, which can trigger a Hazard or Subject encounter.
    3.  **Lockout Cost:** The "one shot" model. Failure makes the action impossible to attempt again, forcing an alternative solution.
*   **Documentation Impact:** This universal rule system belongs in **`Project_Foundations.md`**.

### **3. The Hierarchical Choice System**
*   **Problem Solved:** Prevents UI clutter when performing complex, multi-part actions (e.g., using a specific item on a specific target's body part).
*   **Finalized Concept:** The UI will use a "drill-down" or expanding menu system. The player starts with a high-level "verb" (e.g., `[Initiate Intimacy...]`) and then makes a series of contextual choices to specify the target, tool, and method, which assembles the final `IntentPacket`.
*   **Key Mechanics:** Introduces "smart buttons" like `[Continue]` and `[Change Pace]` to streamline repeated actions within an encounter.
*   **Documentation Impact:** This is a core part of the **`Exploration_Engine.md`** as it defines the primary UI interaction model.

---

## **Design Note: Core Character & Entity Concepts**

### **4. The Resonance Adaptation Field**
*   **Finalized Concept:** The Resonance is a primordial Subject intertwined with the facility's reactor, creating a passive reality-warping field. The "Protective Injection Protocol" attunes subjects to this field.
*   **Key Mechanics:**
    1.  **Enhanced Physical Malleability:** Explains character survival of physically impossible encounters.
    2.  **Equipment Restoration ("Resonance Repair"):** Passively repairs damaged/torn clothing after an encounter, removing logistical tedium.
    3.  **Superficial Healing:** Allows minor modifications like piercings to heal naturally.
    4.  **Limits of Protection:** Major modifications (tattoos, brands) persist and require medical services for reversal. Psychological corruption is permanent.
*   **Thematic Purpose:** Reinforces the horror that the facility is "maintaining" its test subjects. Provides lore for Processed Personnel (attunement failure).
*   **Documentation Impact:** The core definition belongs in **`Project_Foundations.md`**. Its effects are detailed in **`Character_Core_Systems.md`** (`Anatomy`) and **`Character_Progression_Systems.md`** (`Equipment`).

### **5. The "One Subject at a Time" Rule**
*   **Finalized Concept:** Encounters can only ever have one active Subject at a time.
*   **Thematic Purpose:** Reinforces Subjects as sovereign, overwhelming forces of nature. The lore explanation is that their `Corruption Bleed` auras are fundamentally incompatible and would cause catastrophic reality distortion if overlapped.
*   **Key Mechanics:** Dramatically simplifies encounter balance. Allows for the "Hand-Off" encounter type, where fleeing one Subject leads you into another's territory, creating a new encounter. Does not forbid encounters with 1 Subject + multiple Hazards/Personnel.
*   **Documentation Impact:** This is a constitutional rule that belongs in **`Subject_Core_Systems.md`**.

### **6. The "Disruption" & "Insight" Systems**
*   **Problem Solved:** Provides players with a non-appeasement "win" condition against meter-less Subjects.
*   **Finalized Concept:** "Disruption" is the act of attacking a Subject's manifestation, psychology, or systemic weakness. "Insights" are the in-game knowledge required to unlock Disruption actions.
*   **The Three Pathways to Insight:**
    1.  **Research:** Finding Subject documentation during exploration.
    2.  **Observation:** Using an in-encounter action to analyze the Subject.
    3.  **Experimentation:** Using environmental objects or items in creative ways.
*   **Thematic Purpose:** Turns each Subject into a unique puzzle to be solved, rewarding all playstyles.
*   **Documentation Impact:** This core mechanic belongs in **`Subject_Core_Systems.md`**.

### **7. The Modular Hazard System**
*   **Problem Solved:** Creates a lightweight system for handling simpler threats (traps, Processed Personnel) without the overhead of a full psychology system.
*   **Finalized Concept:** A Hazard is built from a library of modular components (Core Profile, Trigger, Behavior, Interaction, Effect).
*   **Key Mechanics:** The "Psychology Shim" translates a Hazard's static profile into a valid `PsychologyOutput`, allowing it to interface seamlessly with the `Encounter_Engine`.
*   **Documentation Impact:** This entire system is the core of **`Hazard_Systems.md`**.

---

## **Design Note: Progression & Exploration**

### **8. The "Ambient Psychology" System**
*   **Problem Solved:** Makes the exploration phase feel alive and prevents companions from being silent props.
*   **Finalized Concept:** During exploration, the `Exploration_Engine` will perform a lightweight query of all present characters' `Psychology Systems` to generate ambient thoughts and incidental dialogue.
*   **Key Mechanics:** The `Narrative_Engine` weaves these dynamic psychological outputs into the static room descriptions, creating a unique narrative experience for each visit based on the party's current state.
*   **Documentation Impact:** This is a core feature of the **`Exploration_Engine.md`**.

### **9. The "Off-Screen Resolution" System**
*   **Problem Solved:** Gives mechanical weight to the party being split up.
*   **Finalized Concept:** When a companion is exploring independently, they can trigger their own encounters. These are resolved via a lightweight, abstracted "Simulated Encounter" by the `Core_Encounter_Engine`.
*   **Key Mechanics:** The outcome is logged and reported to the player by The Analyst. This can lead to the player needing to "Intervene" in a nearby encounter.
*   **Documentation Impact:** This system belongs in **`Character_Progression_Systems.md`**, as it's a core part of companion autonomy and progression.

### **10. The "Clothing as Defensive Bonus" System**
*   **Problem Solved:** Creates a simple, flexible system for handling clothing in intimate/hostile encounters that is superior to rigid "access layers."
*   **Finalized Concept:** Clothing items provide a flat **`Defensive_Bonus`** to a character's opposed roll when an enemy attempts an action that requires changing a zone's `exposure_state`.
*   **Key Mechanics:** A single opposed roll determines both the success of the exposure attempt and the primary action. `exposure_state` (`Covered`, `Exposed`) is tracked on the character's `Anatomy Profile`.
*   **Documentation Impact:** The rules for this belong in **`Character_Progression_Systems.md`** (Equipment Framework), with the `exposure_state` property being defined in **`Character_Core_Systems.md`** (Anatomy Profile).