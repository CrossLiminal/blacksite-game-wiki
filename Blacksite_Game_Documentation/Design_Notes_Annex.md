# **Design Notes Annex**

**Purpose:** This document is a living reference and companion to the `Development_Roadmap`. It contains the core concepts, design philosophies, and initial brainstorming for systems that are still in development. It serves as the primary source material for writing the final, clean documentation for each pending task.

---

### **Notes for `Exploration_Engine.md`**

**1. The "Ambient Psychology" System**
*   **Problem Solved:** Makes the exploration phase feel alive and prevents companions from being silent props.
*   **Core Concept:** During exploration, the `Exploration_Engine` will perform lightweight queries of all present characters' `Psychology Systems` to generate ambient thoughts and incidental dialogue. The `Narrative_Engine` then weaves these dynamic outputs into the static room descriptions.

**2. The Hierarchical Choice System**
*   **Problem Solved:** Prevents UI clutter for complex, multi-part actions (e.g., using a specific item on a specific target's body part).
*   **Core Concept:** The UI will use a "drill-down" or expanding menu system. The player starts with a high-level "verb" (e.g., `[Use Item...]`) and then makes a series of contextual choices to specify the target, tool, and method.

**3. The "Off-Screen Resolution" System**
*   **Problem Solved:** Gives mechanical weight and narrative consequence to the party being split up.
*   **Core Concept:** When a companion is exploring independently, they can trigger their own encounters. These are resolved via a lightweight, abstracted "Simulated Encounter" by the `Core_Engine`. Outcomes are logged and reported to the player, and can create "Intervention" opportunities.

---

### **Notes for `Subject_Core_Systems.md`**

**5. The "One Subject at a Time" Rule**
*   **Problem Solved:** Dramatically simplifies encounter balance and reinforces the power of Subjects.
*   **Core Concept:** Encounters can only ever have one active Subject at a time. The lore explanation is that their `Corruption Bleed` auras are fundamentally incompatible and would cause catastrophic reality distortion if overlapped. This does not forbid encounters with 1 Subject + multiple Hazards.

**6. The "Disruption" & "Insight" Systems**
*   **Problem Solved:** Provides players with a non-appeasement "win" condition against meter-less Subjects, turning them into unique puzzles.
*   **Core Concept:** "Disruption" is the act of attacking a Subject's manifestation or psychological weakness. "Insights" are the in-game knowledge required to unlock Disruption actions, which can be discovered via Research, Observation, or Experimentation.

**7. The "Two-Vector" Corruption System**
*   **Problem Solved:** How do Subjects corrupt characters both passively and actively?
*   **Core Concept:** Subjects apply corruption through two distinct vectors:
    1.  **`Corruption Bleed`:** A passive, proximity-based aura that slowly applies a generalized, thematic corruption to all characters in the area.
    2.  **`Direct Application`:** A specific, targeted corrupting action used during an encounter that applies a large, focused package of corruption.

**8. The "Fixation Matrix" as `Nature` Equivalent**
*   **Problem Solved:** How to model the alien, goal-oriented psychology of a Subject.
*   **Core Concept:** A Subject's `Psychology` is not driven by a complex, human-like `Nature`. Instead, it is driven by a **`Fixation Matrix`**—a simple, obsessive list of goals and priorities (e.g., `[Enforce_Territory]`, `[Test_Prey_Resilience]`, `[Apply_Botanical_Corruption]`). This is their immutable "operating system."

**9. Intersubject Dynamics**
*   **Problem Solved:** How do Subjects interact with each other when the player isn't around?
*   **Core Concept:** Subjects have predefined relationships with one another (Rivalries, Synergies, Indifference). These dynamics can affect the state of the facility. A player might find a room wrecked because two rival Subjects had a territorial dispute, or find a Hazard that has been augmented by the influence of a nearby Subject.

---

### **Notes for `Hazard_Systems.md`**

**10. The Modular Hazard System**
*   **Problem Solved:** Creates a lightweight system for simpler threats (traps, Processed Personnel) without the overhead of a full psychology system.
*   **Core Concept:** A Hazard is built from a library of modular components (Core Profile, Trigger, Behavior, Effect). The **"Psychology Shim"** is a lightweight translator that allows a Hazard's static, pre-defined profile to be formatted into a valid `PsychologyOutput` that the `Encounter_Engine` can understand.

---

### **Notes for `Character_Progression_Systems.md`**

**11. The "Clothing as Defensive Bonus" System**
*   **Problem Solved:** Creates a simple, flexible system for handling clothing in intimate/hostile encounters.
*   **Core Concept:** Instead of complex "access layers," clothing items provide a flat **`Defensive_Bonus`** to a character's opposed roll when an enemy attempts an action that requires changing a zone's `exposure_state`. A single roll determines both the success of the exposure and the primary action.

**12. The "Player Agency vs. Transformation" Framework**
*   **Problem Solved:** How to give the player meaningful agency to resist unwanted physical transformations (`Metamorphosis`) without negating the horror of corruption.
*   **Core Concept:** Resisting a `Corruption Vector` is a choice with a cost. It may require spending a rare resource, or inflicting a large amount of `Stability` damage as the character's mind fights their body. Conversely, *accepting* the transformation might prevent the `Stability` damage, creating a tempting choice between preserving the body or the mind.

---

### **Notes for `Facility_Environment_Systems.md`**

**13. Facility Medical Services Integration**
*   **Problem Solved:** How does the player reverse unwanted physical changes, and how does the facility turn this into a system of control?
*   **Core Concept:** The medical bay is a "body shop," not a hospital. Physical transformations can be reversed, but always at a significant cost (rare resources, favors, completing dangerous tasks). Crucially, the psychological and corrupting effects are permanent. This creates a dependency loop where the player is tempted to accept "useful" corruptions, believing they can just "fix it later," drawing them deeper into the facility's control.

---

### **Notes for `Story_Framework.md`**

**14. The `Live_Documentation_System`**
*   **Problem Solved:** How to deliver lore and create a sense of a living, uncaring system observing the player.
*   **Core Concept:** As the player performs actions and their state changes, the game generates in-universe "documentation" about them in real-time. After a particularly traumatic encounter, a "Clinical Observation Report" might appear in the player's log. After a character develops a new corruption, a new, redacted "Specimen Profile" might be created for them, written from the cold, detached perspective of The Other or The Architect.

---

### **Notes for `Character_Core_Systems.md`**

**15. The "Affinity-Weighted Expression" Model for Branching Corruption**
*   **Problem Solved:** How to model branching corruption tracks (like `Dominion`) in a way that is psychologically authentic, works for autonomous companions, and allows for non-binary states (e.g., being both a Voyeur and an Exhibitionist). Replaces the old, rigid "binary flip" idea.
*   **Core Concept:** A character's progress on a branching track is measured with a single **`Corruption Threshold`** (representing their knowledge/potential in that domain). Their expression of that knowledge is determined by separate, dynamic **`Affinity Scores`** for each branch (e.g., `Dominant Affinity` vs. `Submissive Affinity`).
    *   `Character Nature` provides the starting affinities.
    *   In-game experiences (positive/negative reinforcement) modify these scores over time.
    *   The `Psychology System` uses the affinity scores as a primary weight to determine which type of action to take.
    *   A "heel-face turn" is now an organic, psychologically-driven process where a character's affinity for an opposing expression grows through experience, rather than a simple binary switch.

---

### **Reference Notes for Completed Systems**
*(Core philosophies of complex, recently designed systems, preserved here for high-level reference.)*

**16. The "Slot & Hijack" Principle for Anatomy** (Ref: `Character_Core_Systems.md`)
*   **Concept:** To maintain a body horror theme, character anatomy has defined "slots" for major features. Corruption can add to empty slots, but a "Hijack" transformation will consume and replace an existing body part, representing a horrifying violation of the human template.

**17. The "Creeping Transformation" & `Corruption Vector`** (Ref: `Character_Core_Systems.md`)
*   **Concept:** Corruption is not instantaneous. It applies a persistent **`Corruption Vector`** (an "instruction packet") to a character. This vector then applies its thematic change in small, terrifying increments at set intervals, allowing a desperate window for the player to try and intervene.

**18. The `Eroticism Profile` & "Conditioning" Model** (Ref: `Character_Core_Systems.md`)
*   **Concept:** A character's sexual tastes are modeled in the **`Eroticism Profile`**. This profile is dynamic, with `Affinity Score`s for various acts developing organically through positive/negative experiences, or being forcibly rewritten by `Deviance` corruption.

**19. The "Hybrid Priority" Model for Psychology** (Ref: `Character_Core_Systems.md`)
*   **Concept:** The AI resolves conflicting desires using a two-level system. **Hard Overrides** (from absolute physical states like `Agency 0`) filter out impossible actions, while a **Weighted Combination** of all other psychological drivers determines the final, highest-urgency choice from the remaining options.

---

### **Additions for `Design_Notes_Annex.md`**

**20. The `Knowledge_Base` System for Collective Party Knowledge**
*   **Problem Solved:** How to store and access permanent, party-wide tactical and narrative information (like `Insights` and discovered lore) without incorrectly placing it in a single character's state.
*   **Core Concept:** A new, global `Knowledge_Base` system will serve as the central repository for all information the party has collectively learned. This system is diegetically represented by the "Dossiers" tab in the Facility Tablet UI. Actions that require specific knowledge (like a Disruption) will have their prerequisites query this central database rather than an individual character's state. This ensures that knowledge gained by one character is available to all, streamlining gameplay.

**21. The Analyst as "Network Ghost"**
*   **Problem Solved:** How to diegetically represent The Analyst's unique nature as a non-corporeal companion and justify their character arc.
*   **Core Concept:** The Analyst is not bound to a single device but exists as a "network ghost" within a secure legacy sub-network of the facility. They can observe events and communicate contextually through any nearby terminal, speaker, or PDA. This role as an ever-present but intangible observer directly fuels their core character crisis of competence vs. embodiment. Their efforts to manage the `Knowledge_Base` are a reflection of their desperate attempt to be useful and understand a physical world they cannot touch, perfectly teeing up their "Identity Through Embodiment" arc.

**22. "Consequence Packages" for Modular Action Resolution**
*   **Problem Solved:** How to create reusable, complex outcomes for actions without hardcoding them for every single action.
*   **Core Concept:** The `Encounter_Engine_Library` will contain a new section for "Consequence Packages." An action's outcome (e.g., `Standard_Disruption_Failure`) will point to a `Package_ID` instead of listing individual effects. This package contains a collection of effects (deal damage, apply status effect, trigger reaction, etc.). This allows for rapid creation and balancing of action outcomes and is used for Disruption failures, "Messy Disruption" ties, and potentially complex standard attacks.

---