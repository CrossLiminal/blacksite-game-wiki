# **Character Core Systems**

**System Authority:** Defines the complete blueprint of a Character entity (Player, Companion, or NPC).
**Dependencies:** `Project_Foundations.md`
**Dependents:** `Character_Progression_Systems.md`, `Encounter_Engine.md`, and all systems that interact with characters.
**Version:** 1.0 - Foundational Draft

---

## **Introduction: The Character Blueprint**

This document serves as the complete technical and mechanical blueprint for a Character. It defines the foundational "stat block" of a character (their Meters, Attributes, and Skillsets), the framework for their creation, and the comprehensive, multi-component **Character State Framework** that governs their dynamic, moment-to-moment existence. This document defines what a Character *is*.

---

## **Section 1: Foundational Mechanics (The "Stat Block")**

This section details the core, quantifiable mechanics that form the baseline of any character. These stats serve as the primary input for the universal dice system and represent a character's innate capabilities and resilience.

### **1.1 Core Meters**

Core meters represent a character's resilience pools rather than traditional health. Reaching a value of zero in any meter results in a specific crisis state that incapacitates the character in some way, requiring assistance or recovery, but it does not represent character death.

#### **Meter Calculation**
A character's maximum meter values are calculated at character creation and upon Tier advancement, using the following formula:
**Base Meter Value = Sum of (Attribute × Weight) + Sum of (Skillset Level × Weight)**

#### **Meter Definitions**

##### **Vitality (Physical Resilience)**
*   **Function:** Resistance to physical exhaustion, injury, and bodily harm.
*   **Zero State:** **Physical Incapacitation.** The character is unable to perform strenuous actions and requires rest or medical attention to recover.
*   **Calculation Weights:**
    *   **Attributes:** Physique ×5, Nerve ×2, Intuition ×2, Acumen ×1
    *   **Skillsets:** Jock ×3, Loner ×2, Nerd ×1, Popular ×1, Rebel ×1

##### **Stability (Mental Resilience)**
*   **Function:** Resistance to psychological trauma, horror, and mental breakdown.
*   **Zero State:** **Panic/Irrationality.** The character is unable to make strategic or logical decisions and requires companion guidance or a moment of calm to recover.
*   **Calculation Weights:**
    *   **Attributes:** Acumen ×5, Nerve ×2, Intuition ×2, Physique ×1
    *   **Skillsets:** Nerd ×3, Popular ×2, Jock ×1, Loner ×1, Rebel ×1

##### **Inhibition (Boundary Resilience)**
*   **Function:** Resistance to erotic corruption, sexual coercion, and the erosion of personal boundaries.
*   **Zero State:** **Compulsive Submission.** The character is unable to resist sexually charged scenarios and will automatically acquiesce to erotic corruption.
*   **Calculation Weights:**
    *   **Attributes:** Nerve ×4, Intuition ×3, Physique ×2, Acumen ×1
    *   **Skillsets:** Rebel ×3, Popular ×2, Jock ×1, Nerd ×1, Loner ×1

### **1.2 Attributes**

Attributes are the four core statistics that determine a character's raw potential. They primarily dictate the *quantity* of dice rolled for an action. The human attribute range is 2 to 6, with higher values representing supernatural enhancement.

#### **Attribute Scale**
*   **2 - Deficient:** A noticeable, below-average limitation.
*   **3 - Baseline:** The typical human standard.
*   **4 - Adequate:** Above average; naturally competent.
*   **5 - Superior:** Exceptional human capability.
*   **6 - Peak Human:** The absolute pinnacle of natural human potential.
*   **7+ - Aberrant:** Transcendent, supernatural enhancement.

#### **The Four Attributes**
*   **Physique (PHY):** Represents physical capability, raw strength, endurance, and coordination.
*   **Acumen (ACU):** Represents intellectual capability, reasoning, knowledge, and analysis.
*   **Nerve (NER):** Represents emotional resilience, leadership, stress tolerance, and determination.
*   **Intuition (INT):** Represents instinctive understanding, empathy, situational awareness, and creativity.

### **1.3 Skillsets**

Skillsets represent a character's specialized competencies and training. They primarily dictate the *quality* (the die size, from d4 to d12+) of dice rolled for an action. Characters are considered "Untrained" (d4) in any skillset they have not developed.

#### **Skillset Scale**
*   **d4 (Level 0) - Untrained:** No formal development; raw natural ability only.
*   **d6 (Level 1) - Competent:** Basic proficiency and entry-level capability.
*   **d8 (Level 2) - Skilled:** Developed expertise through experience and practice.
*   **d10 (Level 3) - Expert:** Mastery level; professional or elite human capability.
*   **d12 (Level 4) - Master:** The peak of human achievement in this domain.
*   **d14+ (Level 5+) - Aberrant:** Transcendent ability warped by cosmic influence.

#### **The Five Skillsets**
*   **Jock:** Governs physical prowess, athletic capability, and competitive drive.
*   **Nerd:** Governs academic knowledge, technical analysis, and research capability.
*   **Popular:** Governs social manipulation, group dynamics, and interpersonal influence.
*   **Loner:** Governs self-reliance, survival instincts, and independence.
*   **Rebel:** Governs authority resistance, unconventional thinking, and rule-breaking.

---

## **Section 2: Character Genesis Framework**

This section details the framework for creating all character entities. The system is built on a foundation of archetypes rather than a point-buy system, ensuring characters begin with a thematic and mechanically balanced set of strengths and weaknesses. This framework is used to generate the Player Character at the start of the game and can be used to create any NPC at any experience Tier.

### **2.1 Archetype Creation Rules**

All archetypes are built upon a consistent and balanced mathematical foundation.

#### **Attribute Distribution**
A starting character's attributes are distributed according to a standard formula to ensure a balance of capability and vulnerability:
*   **Formula:** One attribute is set to **4 (Adequate)**, two are set to **3 (Baseline)**, and one is set to **2 (Deficient)**.
*   **Total Points:** This results in a consistent total of 12 attribute points for any newly created Tier 1 character.

#### **Skillset Distribution**
A starting character's skillsets are assigned as follows:
*   **Specialization:** One skillset, chosen to align with the archetype's concept, begins at **d6 (Level 1 - Competent)**.
*   **Foundation:** All other skillsets begin at **d4 (Level 0 - Untrained)**.

#### **Applying Higher Tiers at Genesis**
This framework can be used to generate characters at a higher Tier than 1, which is essential for creating experienced NPCs found deeper in the facility. To do so, create a Tier 1 character using the rules above, and then apply the standard Tier Advancement benefits for each Tier above 1.

*   **Per-Tier Bonus:** For each Tier the character has *above Tier 1*, apply the following benefits:
    *   **+1 Attribute Point** (Player/Designer Choice)
    *   **+2 Skillset Levels** (Player/Designer Choice)
    *   *(Note: The "Keep Dice" bonus is part of the Progression system, not the static character build).*
*   **Attribute Cap:** Attributes increased via this method cannot exceed the **Peak Human (6)** limit. Supernatural enhancement beyond this cap is handled by the Corruption system.

### **2.2 Player Character Archetypes**

The following pre-defined archetypes are available to the player during character creation. They serve as clear examples of the creation rules and provide distinct gameplay experiences. A custom archetype option is also available, provided it adheres to the creation rules.

#### **The Captain (Physique/Jock)**
*   **Concept:** A natural athlete and team leader with protective instincts.
*   **Attributes:** Physique 4, Nerve 3, Intuition 3, Acumen 2
*   **Skillset:** Jock d6

#### **The Farmhand (Physique/Loner)**
*   **Concept:** A self-reliant individual with a practical work ethic forged by a rural background.
*   **Attributes:** Physique 4, Nerve 3, Intuition 3, Acumen 2
*   **Skillset:** Loner d6

#### **The Valedictorian (Acumen/Nerd)**
*   **Concept:** An academic perfectionist who values logic, reason, and the pursuit of knowledge above all.
*   **Attributes:** Acumen 4, Intuition 3, Nerve 3, Physique 2
*   **Skillset:** Nerd d6

#### **The Techie (Acumen/Rebel)**
*   **Concept:** A hacker and tinkerer who excels at unconventional technical solutions and bypassing systems.
*   **Attributes:** Acumen 4, Intuition 3, Nerve 3, Physique 2
*   **Skillset:** Rebel d6

#### **The Performer (Nerve/Jock)**
*   **Concept:** A charismatic and physically expressive individual with a flair for the dramatic.
*   **Attributes:** Nerve 4, Intuition 3, Physique 3, Acumen 2
*   **Skillset:** Jock d6

#### **The Outcast (Nerve/Rebel)**
*   **Concept:** A nonconformist who instinctively challenges authority and established rules.
*   **Attributes:** Nerve 4, Intuition 3, Physique 3, Acumen 2
*   **Skillset:** Rebel d6

#### **The Socialite (Nerve/Popular)**
*   **Concept:** A master of group dynamics and social graces, naturally charismatic and influential.
*   **Attributes:** Nerve 4, Intuition 3, Acumen 3, Physique 2
*   **Skillset:** Popular d6

#### **The Investigator (Intuition/Nerd)**
*   **Concept:** A natural detective with a keen eye for patterns and details others miss.
*   **Attributes:** Intuition 4, Physique 3, Nerve 3, Acumen 2
*   **Skillset:** Nerd d6

#### **The Empath (Intuition/Popular)**
*   **Concept:** An emotionally intelligent counselor, able to read people and act as the heart of a group.
*   **Attributes:** Intuition 4, Physique 3, Nerve 3, Acumen 2
*   **Skillset:** Popular d6

#### **The Survivor (Intuition/Loner)**
*   **Concept:** A self-reliant individual with a powerful danger sense and keen survival instincts.
*   **Attributes:** Intuition 4, Physique 3, Nerve 3, Acumen 2
*   **Skillset:** Loner d6

---

## **Section 3: The Character State Framework (CSF)**

### **3.1: System Overview**

The Character State Framework (CSF) provides the unified, dynamic foundation for all character mechanics. It is the "living soul" of a character, integrating their anatomy, core nature, identity, relationships, and all other transient states into one interconnected system. All game systems—from encounter resolution to narrative generation—reference the CSF to determine available options, scale content, and generate authentic responses for every character.

#### **Universal Application**
The CSF is universal. Every character, including the Player Character and all autonomous Companions, is built upon this same framework. This ensures mechanical consistency and allows for complex, emergent group dynamics to arise naturally from the interaction of individual character states.

#### **Interconnected by Design**
No component within the CSF exists in isolation. A character's physical Anatomy affects their Identity; their Corruption state alters their Relationships; their Agency influences their Arousal. The final components of the framework, **Psychological Integration** and the **Psychology Output Interface**, serve as the engine that processes these interconnected states into the believable, character-driven thoughts and actions that propel the game forward.

---

### **3.2: Anatomy Profile Component**

#### **3.2.1 Design Philosophy**

The Anatomy Profile is the complete, dynamic blueprint of a character's physical body. It is a modular collection of **Anatomical Components**, each a self-contained object with its own properties and states. A character's body is defined simply by the components that exist within their profile. This object-oriented approach provides maximum flexibility, allowing for the representation of standard human forms, corrupted monstrosities, and everything in between. Every property listed exists as a hook for another system to interact with.

#### **3.2.2 The "Corruption Defines the Form" Principle**

To maintain the game's theme of body horror over power fantasy, the core system is deliberately flexible, but the *content* is curated. The system can technically support any number of anatomical features, but a character will only develop them if exposed to a specific, thematically appropriate **Corruption Source** designed to cause that change. This moves the thematic guardrails from rigid code to the content creation process, ensuring that all transformations serve the narrative of horrifying, non-human alteration.

#### **3.2.3 Universal Scaling Standards**

All quantifiable anatomical properties adhere to one of the following universal scales:

*   **Magnitude Scale (1-10+):** For quantifiable physical attributes (e.g., Size, Capacity, Flexibility, Acuity).
*   **Sensitivity Scale (1-5):** For responsiveness to stimuli (e.g., Anatomical Sensitivity, Susceptibility).
*   **Control Scale (1-5):** For conscious mastery over a bodily function (e.g., Muscle Control, Gag Control, Dexterity).

#### **3.2.4 The `Anatomical_Component` Data Structure**

All parts of the body are represented as `Anatomical_Component` objects.

```
Anatomical_Component {
  ID: "groin_penis_01",       // A unique, queryable identifier
  Parent_Component: null,      // ID of the parent component, if any
  Is_Targetable: true,         // Boolean: can this be a direct target of an action?
  Zone: "Groin",               // The high-level body region for broad targeting
  Feature_Type: "Penis",       // The specific anatomical feature
  
  // -- Dynamic State Properties --
  exposure_state: "Covered" | "Partially_Exposed" | "Fully_Exposed",
  
  // This property tracks who and what is currently interacting with the component.
  // The 'agent' is the acting entity.
  // The 'tool' is the item or body part being used.
  in_use_by: null | { 
    agent: Entity_ID, 
    tool: Item_ID | Anatomical_Component_ID 
  },
  
  // -- Descriptive Properties & Modifications --
  properties: { ... },
  modifications: [ ... ]
}
```

#### **3.2.5 Master List of Anatomical Components**

This is the definitive list of components that constitute a character. A character's profile is a dictionary containing a selection of these objects.

##### **Systemic Components (Non-Targetable)**

*   **`build`**
    *   **Description:** A collection of properties defining the character's overall physique and physical capabilities.
    *   **Properties:**
        *   `muscle_tone` (Magnitude): The definition and mass of the character's musculature.
        *   `body_fat` (Magnitude): The percentage and distribution of the character's body fat.
        *   `height` (cm): The character's height.
        *   `flexibility` (Magnitude): The character's physical pliability, affecting positioning in encounters and interaction with the environment.
        *   `derived_build_type` (String): A narrative tag (e.g., "Athletic," "Voluptuous") auto-calculated from the other properties.
*   **`skin`**
    *   **Description:** Defines the properties of the character's skin.
    *   **Properties:**
        *   `texture` (String): The feel of the skin (e.g., "Smooth," "Calloused," "Scaled").
        *   `color` (String): The skin's pigmentation.
        *   `general_sensitivity` (Sensitivity): The baseline tactile responsiveness of the character's entire body, which can act as a multiplier for certain environmental or widespread stimulation effects.
*   **`hair`**
    *   **Description:** A collection of all hair-related properties, key inputs for the Identity component.
    *   **Properties:**
        *   `body_hair_coverage` (String): The amount of body hair (e.g., "None," "Light," "Thick").
        *   `pubic_hair_style` (String): The style of pubic hair (e.g., "Natural," "Trimmed," "Shaved").
        *   `facial_hair_style` (String): The style of facial hair (e.g., "None," "Stubble," "Full_Beard").
        *   `head_hair_color` (String): The color of the hair on the head.
        *   `head_hair_style` (String): The style of the hair on the head.
        *   `head_hair_length` (String): The length of the hair on the head.
*   **`voice`**
    *   **Description:** Defines the character's vocal characteristics, used by the Narrative and Identity systems.
    *   **Properties:**
        *   `pitch` (String): The general pitch of the voice (e.g., "Soprano," "Bass").
        *   `tone` (String): The quality of the voice (e.g., "Clear," "Husky," "Raspy").
        *   `speech_patterns` (List of tags): Narrative flags for dialogue generation (e.g., ["Formal," "Clipped," "Hissing_Sibilance"]).
*   **`chemistry`**
    *   **Description:** Governs biochemical signals and resistances, modeling the "Breeding Theater" of false fertility displays.
    *   **Properties:**
        *   `scent_signature` (String): The character's unique base scent for narrative description.
        *   `pheromone_production` (Magnitude): The broadcast strength of the character's emotional and sexual state.
        *   `pheromone_receptivity` (Sensitivity): The character's susceptibility to biological signals from others.
        *   `chemical_sensitivity` (Sensitivity): The character's resistance to environmental chemicals and drugs.
        *   `heat_cycle_state` (String): The current state of a corruption-induced heat cycle ("None," "Building," "Peak," "Waning").
        *   `heat_cycle_intensity` (Magnitude): The strength of an active heat cycle.
        *   `refractory_rate` (Magnitude): The character's physiological speed of recovery after orgasm. Higher values lead to shorter or nonexistent refractory periods.
*   **`breeding_signals`**
    *   **Description:** Defines the character's passive, supernatural appeal to reproductively-focused entities.
    *   **Properties:**
        *   `fertility_display` (Magnitude): The character's apparent physical "fitness" for breeding.
        *   `subject_attraction_modifier` (Magnitude): The esoteric "X-factor" that makes a character supernaturally alluring.
        *   `territorial_marking_capacity` (Boolean): A flag indicating if the character can leave persistent pheromonal marks.
        *   `breeding_appeal` (Derived Magnitude): The final, calculated value used by Subjects for targeting.
*   **`senses`**
    *   **Description:** A container for the character's sensory capabilities. The `special_senses` list is the primary hook for supernatural or corrupted perceptual changes, such as **Synesthesia**.
    *   **Properties:**
        *   `vision` ({acuity: Magnitude, tags: List}): Defines sight, including supernatural abilities like "Night_Vision".
        *   `hearing` ({acuity: Magnitude, tags: List}): Defines hearing, including supernatural abilities like "Echolocation".
        *   `scent` ({acuity: Magnitude, tags: List}): Defines smell, including supernatural abilities like "Pheromone_Analysis".
        *   `touch` ({sensitivity: Sensitivity, tags: List}): Defines tactile sense, a key input for arousal and horror.
        *   `special_senses` (List of tags): Defines any transcendent or altered senses. 
            *   **Examples: `["synesthesia_audio_visual", "synesthesia_thermo_erotic"]`**.

##### **Targetable Human Components**

*   **`mouth`**
    *   **Description:** The mouth as a receptive cavity. It is the parent component for the tongue.
    *   **Properties:** `capacity` (Magnitude), `sensitivity` (Sensitivity), `elasticity` (Magnitude), `gag_control` (Control), `saliva_production` (Magnitude), `temperature` (String).
*   **`tongue`**
    *   **Description:** The tongue, a child of the `mouth` component, used for penetrative and manipulative actions.
    *   **Properties:** `length` (Magnitude), `dexterity` (Control), `sensitivity` (Sensitivity), `texture` (String).
*   **`neck`**
    *   **Description:** The neck, a vulnerable area for biting and other horror- or intimacy-focused actions.
    *   **Properties:** `sensitivity` (Sensitivity), `resilience` (Magnitude).
*   **`breasts`** (e.g., `breasts_01`)
    *   **Description:** The mammary glands on the chest. Parent component to nipples.
    *   **Properties:** `size` (Magnitude), `sensitivity` (Sensitivity).
*   **`nipples`** (e.g., `nipples_01`)
    *   **Description:** The nipples, children of a `breasts` component.
    *   **Properties:** `size` (Magnitude), `sensitivity` (Sensitivity), `state` (String, e.g., "Puffy," "Inverted").
*   **`abdomen`**
    *   **Description:** The stomach and abdominal area, a common target for body horror transformations.
    *   **Properties:** `sensitivity` (Sensitivity), `tone` (Magnitude).
*   **`torso_back`**
    *   **Description:** The character's back, a target for horror and intimacy actions.
    *   **Properties:** `sensitivity` (Sensitivity).
*   **`anus`**
    *   **Description:** The anus as a receptive cavity.
    *   **Properties:** `capacity` (Magnitude), `sensitivity` (Sensitivity), `elasticity` (Magnitude), `muscle_control` (Control), `lubrication` (Magnitude).
*   **`hands`**
    *   **Description:** A single component representing both hands, used for manual actions.
    *   **Properties:** `dexterity` (Control), `strength` (Magnitude).
*   **`feet`**
    *   **Description:** A single component representing both feet.
    *   **Properties:** `size` (Magnitude), `sensitivity` (Sensitivity).
*   **`penis`** (e.g., `penis_01`)
    *   **Description:** A primary penetrative organ, which acts as the parent for `testicles` and often a `urethra`. Fills the `genital_penetrative` slot.
    *   **Properties:** `size` (Magnitude), `girth` (Magnitude), `sensitivity` (Sensitivity), `shape` (String, e.g., "Human," "Canine").
*   **`vagina`** (e.g., `vagina_01`)
    *   **Description:** A primary receptive organ which also acts as the parent for a `clitoris` and often a `urethra`. Fills the `genital_receptive` slot.
    *   **Properties:** `capacity` (Magnitude), `sensitivity` (Sensitivity), `elasticity` (Magnitude), `muscle_control` (Control), `lubrication` (Magnitude), `ejaculate_capacity` (Magnitude)
*   **`clitoris`** (e.g., `clitoris_01`)
    *   **Description:** An external erectile organ. Typically a child of a `vagina` component, but can exist standalone. Fills the `genital_penetrative` slot.
    *   **Properties:** `size` (Magnitude), `sensitivity` (Sensitivity).
*   **`urethra`** (e.g., `urethra_01`)
    *   **Description:** A receptive opening, typically a child of a `penis` or `vagina`.
    *   **Properties:** `capacity` (Magnitude), `sensitivity` (Sensitivity).
*   **`testicles`** (e.g., `testicles_01`)
    *   **Description:** The testes, a child component whose presence is dependent on a `penis`.
    *   **Properties:** `size` (Magnitude), `sensitivity` (Sensitivity), `quantity` (Integer), `placement` (String, "External" or "Internal"), `production_capacity` (Magnitude).

#### **3.2.6 Body Modifications System**

Body Modifications are a distinct category of anatomical features that are *applied to* the `modifications` list of existing `Anatomical_Component`s. They range from mundane cosmetics to permanent, supernatural brands and serve as a key vector for character expression, social signaling, and corruption manifestation.

##### **The `Modification` Data Structure**

All modifications, regardless of type, follow a standard data structure, making them easily queryable by other systems.

```
Modification {
  Type: "Piercing",             // The category of modification (e.g., "Tattoo", "Makeup")
  Subtype: "Prince Albert",      // The specific style or name (e.g., "Dragon Scales", "Smoky Eye")
  Location: "Tip",             // A more precise location on the parent component
  Material: "Steel",           // The material, color palette, or ink type
  Is_Supernatural: false,      // Does this mod have magical/corrupting properties?
  Effects: [ ... ]               // A list of any mechanical or narrative tags
}
```

##### **Master List of Modification Types**

*   **Piercings:**
    *   **Description:** Puncturing modifications, typically adorned with jewelry. They are considered minor modifications by the Resonance Field and can heal over time if the jewelry is removed, unless they are supernatural in nature.
    *   **Examples:** `Subtype: "Nipple Ring"`, `Subtype: "Prince Albert"`, `Subtype: "Belly Button Stud"`.
*   **Tattoos:**
    *   **Description:** Inked designs applied to the skin. They are considered major, identity-altering modifications and are made permanent by the Resonance Field, requiring medical intervention for removal.
    *   **Examples:** `Subtype: "Dragon Scales"`, `Subtype: "Tribal Band"`, `Subtype: "Womb Tattoo"`.
*   **Markings:**
    *   **Description:** A category for brands, ritual scars, or supernatural marks left by Subjects. They are permanent and often carry significant supernatural effects, acting as a visible record of a character's history.
    *   **Examples:** `Subtype: "Ritual Scarification"`, `Subtype: "Ownership Brand"`, `Subtype: "Subject-044's Sigil"`.
*   **Cosmetics:**
    *   **Description:** Non-permanent, topical applications like makeup or nail polish. They are easily applied and removed, and do not persist through the Resonance Field's "Equipment Restoration" effect unless they are supernaturally enchanted.
    *   **Examples:** `Subtype: "Smoky Eye Makeup"`, `Subtype: "Black Nail Polish"`, `Subtype: "Gothic Lipstick"`.

##### **Mechanical & Narrative Integration**

Body modifications are not just flavor text; they are queryable objects that have tangible effects:

*   **Social & Psychological Impact:** The `Psychological Integration` component reads a character's modifications. A `Subtype: "Gothic Lipstick"` might add a "Goth" tag to the character's appearance, influencing dialogue. An `Subtype: "Ownership Brand"` can be a source of psychological distress or comfort, affecting the `Identity` and `Relationship` components.
*   **Subject Interaction:** Certain Subjects may have fixations related to specific modifications. A Subject might be drawn to characters with piercings, or be hostile to those bearing the mark of a rival entity.
*   **Equipment Interaction:** Modifications can physically interact with equipment. A `Subtype: "Prince Albert"` piercing could mechanically prevent the removal of a chastity device, creating a complex problem for the player to solve.
*   **Supernatural Effects:** A modification with `Is_Supernatural: true` can grant passive bonuses or penalties. A `Type: "Tattoo"` with `Effects: ["Minor_Pyromancy"]` could grant a small fire-based ability. A `Type: "Marking"` from a Subject might have `Effects: ["Corruption_Vulnerability_Enthrall"]`, making the character more susceptible to that type of corruption.

#### **3.2.7 Clarification: Sources of Anatomical Change**

A character's Anatomy Profile is altered through two primary pathways, which are mechanically distinct:

1.  **Applied Modifications:** This category includes features like piercings, tattoos, brands, and cosmetics. These are treated as objects *added to* an existing `Anatomical_Component`'s `modifications` list. While they can be the result of a corruption event (e.g., a forced branding), they are mechanically distinct from a fundamental biological change. The full system for these is detailed in **Section 3.2.6: Body Modifications System**.

2.  **Metamorphic Changes:** This category covers the direct, biological rewriting of a character's body. This includes altering the core `properties` of an existing component (e.g., changing `skin.texture` to "Scaled") or adding entirely new, non-human `Anatomical_Component`s to the profile (e.g., adding a `tail_01` object). This process is not handled by the Body Modifications system; it is the direct result of progressing on the `Metamorphosis` corruption track, the full mechanics of which are detailed in the **`Corruption State Component` (Section 3.9)**.

In short: The **Anatomy Profile** is the document that *records the results* of all physical changes, while the **Corruption State** component is the system that *governs the process* of the most profound and permanent of those changes.

#### **3.2.8 Integration with The Resonance Adaptation Field**

The Anatomy Profile is fundamentally governed by the physics of the Resonance Field. This integration provides the in-universe justification for several core mechanics:
*   **Enhanced Malleability:** Allows the body to withstand impossible physical interactions.
*   **Healing & Persistence:** Promotes healing of minor modifications (piercings), but makes major modifications (tattoos, brands) permanent, requiring external intervention to remove.
    *   *Note: The full mechanics for medical intervention are detailed in `Facility_Environment_Systems.md`. The framework for resisting unwanted transformations is detailed in `Character_Progression_Systems.md`.*

---

### **3.3: Character Nature Component**

#### **3.3.1 Design Philosophy**

The Character Nature Component defines the immutable, core personality of a character. It is their innate disposition, their instinctual drives, and their fundamental approach to the world. Unlike other components of the Character State Framework, the Nature does not change over time; it is the permanent "operating system" that informs and guides the character's autonomous behavior.

Its primary mechanical function is to provide the initial **"Behavioral Weighting"** for the `Psychological Integration` component. It's the thumb that flicks the first domino in the AI's decision-making process, ensuring a character's actions are always rooted in their core identity.

*Note: The definitive master lists of all valid options for this component's properties (e.g., Core Drives, Default Responses) are maintained in the **`Character_Core_Systems_Library.md`** document.*

#### **3.3.2 Component Structure**

The `Character Nature` is a collection of simple, descriptive tags, lists, and weights that serve as a clear and concise personality blueprint for the AI.

*   **`archetype_tag` (String):**
    *   **Description:** A single, high-level identifier for the character's core personality.
    *   **Use:** Primarily for the `Narrative_Engine` and designer reference to quickly identify the character's core concept (e.g., "The Scholar," "The Protector").
*   **`core_drives` (List of Strings):**
    *   **Description:** A prioritized list of the character's most fundamental motivations.
    *   **Use:** Provides high-level goals for the AI's long-term behavior and influences the `Thematic Tag` chosen for `IntentPacket`s. The AI will periodically evaluate its actions against these drives.
*   **`default_responses` (Dictionary):**
    *   **Description:** Describes the character's default, instinctual reactions to common social and environmental situations.
    *   **Use:** A direct input for the `Psychology` component when selecting `Reactions` or generating narrative flavor.
        *   `stress_response` (String): How they react to fear and pressure.
        *   `trust_tendency` (Magnitude): Their baseline willingness to trust others.
        *   `group_role` (String): Their default social role in a group.
        *   `conflict_style` (String): How they typically handle interpersonal conflict.
*   **`behavioral_weights` (Dictionary):**
    *   **Description:** A map of broad `Intent` categories to a numerical weight, providing the direct, mechanical bias for action selection.
    *   **Use:** Provides the **baseline Urgency Score** for all potential actions at the start of the AI's decision-making loop.
*   **`corruption_affinity` (Dictionary):**
    *   **Description:** A map of `Corruption_Track` -> `Weight`, defining the character's innate psychological vulnerabilities and resistances.
    *   **Use:** Acts as a passive modifier to corruption gains or resistance checks.

#### **3.3.3 Integration with the Character State Framework**

The `Character Nature` serves as the foundational layer upon which all other state calculations are built. The relationship is simple and powerful:

*   **`Character Nature` is the "Why" (The Baseline):** It provides the constant, unchanging personality biases and priorities.
*   **The rest of the `Character State` is the "What" (The Modifier):** It represents the character's current, transient condition.

During any decision-making process, the `Psychological Integration` component first takes the baseline weights from the `Character Nature`. It then heavily modifies these values based on the character's current state to arrive at the final action. This ensures characters are both consistent in personality and realistically reactive to their circumstances.

---

### **3.4: Identity Alignment Component**

#### **3.4.1 Design Philosophy**

The Identity Alignment Component is a nuanced system that models a character's sense of self. It is designed to create meaningful, authentic gameplay and narrative revolving around gender identity and expression, particularly under the duress of cosmic horror. It operates on a core principle of separating a character's immutable **Core Identity** from their transient **Gender Expression**. The dissonance between these two states creates quantifiable psychological stress (**Dysphoria**) or affirmation (**Euphoria**), which directly impacts decision-making and narrative flavor.

The system is designed with player agency and respect at its core. A character's fundamental identity is protected by clear **Warning Systems**, ensuring that any permanent change is the result of a deliberate, long-term process, not a sudden "gotcha" moment.

#### **3.4.2 Component Structure**

*   **`core_identity` (Object):**
    *   **Description:** Defines the character's fundamental, internal sense of self. For the player, this is chosen; for companions, it is part of their `Character Nature`.
    *   **Properties:**
        *   `gender_identity` (String): The character's core gender (e.g., "Male," "Female," "Non-Binary").
        *   `identity_confidence` (Magnitude): How secure the character feels in their identity.
*   **`gender_expression` (Object):**
    *   **Description:** Defines the character's current outward presentation to the world. This is the part of their identity that can be altered by clothing, corruption, and anatomical changes.
    *   **Properties:**
        *   `current_presentation` (String): A tag describing their overall presentation (e.g., "Masculine," "Feminine," "Androgynous").
        *   `pronouns` (String): The pronouns the character is currently using/being referred to with.
*   **`presentation_comfort` (Magnitude):**
    *   **Description:** A calculated value representing the character's psychological comfort with their current `gender_expression`. It is the delta between their `core_identity` and their presentation.
    *   **Use:** This is the primary mechanical output of the component. High comfort provides stability and confidence. Low comfort generates psychological stress (Dysphoria) and motivates actions to correct the dissonance.
*   **`identity_stability` (Magnitude):**
    *   **Description:** A "health bar" for the character's sense of self. It decreases slowly when a character endures prolonged periods of high dysphoria.
    *   **Use:** Acts as a modifier for resisting psychological corruption. At critical levels, it triggers narrative "warning signs" of impending identity crisis. Permanent identity change can only occur if this value reaches zero.

#### **3.4.3 Warning System**

To preserve player agency, the system provides clear, graduated warnings as `identity_stability` decreases:
*   **Level 5-4 (Stable/Questioning):** No significant negative effects.
*   **Level 3 (Uncertain):** The character's internal monologue may show signs of self-doubt. They may begin to show a slight, unsettling adaptation to a forced presentation.
*   **Level 2 (Unstable):** The `Psychology` component may begin to offer new, experimental choices that conflict with the character's `core_identity`. Resistance to identity-altering corruption is significantly penalized.
*   **Level 1 (Critical):** The character's thoughts may begin to actively diverge from their established identity. The player is given clear narrative cues that their character's sense of self is on the verge of collapse, presenting a final opportunity to intervene.
*   **Level 0 (Dissolution):** The point of no return. Without intervention, the `core_identity` is permanently rewritten to align with the long-term forced expression.

#### **3.4.4 Integration with the Character State Framework**

The Identity Alignment component is a powerful modulator of a character's psychology and actions.

*   **Psychological Integration:**
    *   **Choice & Urgency:** `presentation_comfort` is a major factor in calculating Urgency Scores. A dysphoric character will have a high urgency to remove restricting clothing or correct their presentation. A euphoric character may gain urgency for social or confident actions.
    *   **Narrative Flavor:** The component directly informs the `Emotional Tone` and `Internal Monologue Hint` of the `PsychologyOutput`, ensuring the character's internal state is always reflected in the narrative.
*   **Corruption:** A low `identity_stability` score creates a severe vulnerability to the `Efface` (Identity Erosion) and `Enthrall` (Mental Conditioning) corruption tracks.
*   **Anatomy:** Changes to the `Anatomy Profile` (voice pitch, hair growth, metamorphic changes) are a primary input for calculating `presentation_comfort`.
*   **Relationships:** Companions can provide identity validation and support, which can help stabilize or restore `identity_stability` and improve `presentation_comfort`.

--

### **3.5: Relationship State Component**

#### **3.5.1 Design Philosophy**

The Relationship State Component is the universal system for tracking a character's social and emotional connections. It is built on the principle of simplicity, using a single, unified scale to model all relationships, from alliances and rivalries with other characters to fear and fascination with Subjects. This component is not just for narrative flavor; it is a core mechanical driver for companion autonomy, psychological comfort, and the complex power dynamics of equipment control.

A key feature of this system is companion autonomy. Companions will form and develop their own relationships with each other based on shared experiences, creating a living, emergent social ecosystem that the player can influence but not directly control.

#### **3.5.2 Universal Relationship Scale**

All relationships are tracked on a numerical scale from 0 to 11. The narrative meaning of a value on this scale changes depending on the context of the relationship.

##### **Relationship Categories & Terminology**

*   **Character ↔ Character:**
    *   **RESENTFUL (0-2):** Active dislike, blame, and tension.
    *   **NEUTRAL (3-5):** Cautious cooperation and professional distance.
    *   **COOPERATIVE (6-8):** Mutual support and developing trust.
    *   **LOYAL (9-11):** Deep emotional investment and unconditional support.
*   **Character → Subject:**
    *   **TERRIFIED (0-2):** Overwhelming fear and avoidance.
    *   **WARY (3-5):** Cautious respect and defensive interaction.
    *   **CONFIDENT (6-8):** Comfortable interaction and assertive behavior.
    *   **FASCINATED (9-11):** A powerful draw to the Subject, seeking interaction and creating a vulnerability to corruption.
*   **Subject → Character (Inverted Scale):**
    *   **VENGEFUL (0-2):** Active, obsessive pursuit of the character.
    *   **AGGRESSIVE (3-5):** General hostility and territorial enforcement.
    *   **ANNOYED (6-8):** Mild irritation and opportunistic harassment.
    *   **PASSIVE (9-11):** Indifference and minimal interaction.
*   **Character ↔ Facility NPC:**
    *   **SUSPICIOUS (0-2):** Distrust and assumption of hidden agendas.
    *   **PROFESSIONAL (3-5):** Formal, transactional cooperation.
    *   **TRUSTING (6-8):** Personal rapport and willing assistance.
    *   **SUPPORTIVE (9-11):** Active advocacy and personal investment.

#### **3.5.3 Equipment Control Integration**

A critical function of the Relationship State is to govern the complex psychological dynamics of equipment control (e.g., restraints, chastity devices).

##### **Control Comfort: The Logic of Accommodation**
This mechanic models a character's psychological adaptation to being controlled. It is a direct mechanical expression of the "Logic of Accommodation," creating the horror of finding comfort in subjugation over time.

*   **`control_comfort` (Scale 0-5):** A value that tracks a character's psychological acceptance of a specific control scenario. It begins at a low value and progresses over time at a rate determined by the quality of the relationship with the controller.
    *   **0: Active Resistance:** Constant psychological distress and escape-seeking behavior.
    *   **1: Reluctant Tolerance:** Frequent complaints and resistance.
    *   **2: Neutral Acceptance:** Treating the control as a practical necessity.
    *   **3: Comfortable Compliance:** Finding the control reassuring or beneficial.
    *   **4: Seeking Control:** Feeling unsettled or anxious without the controller's management.
    *   **5: Psychological Dependency:** Actively seeking more restrictive control.

*Note: The specific rules governing keyholding and consent status are detailed in the Equipment Framework within `Character_Progression_Systems.md`. The precise numerical values for comfort progression rates are maintained in `Character_Core_Systems_Library.md`.*

#### **3.5.4 Integration with Psychology**

The Relationship State is a primary input for the `Psychological Integration` component, shaping a character's internal world and driving their autonomous actions. The `Psychology` component uses this data to weigh behaviors, filter and frame choices, and generate emergent social dynamics between companions, as detailed in **Section 3.10**.

---

### **3.6: Agency Profile Component**

#### **3.6.1 Design Philosophy**

The Agency Profile Component is the systematic representation of a character's freedom to act. It tracks a character's capability restrictions across six distinct categories, creating meaningful tactical constraints and driving narrative opportunities. The core philosophy of this component is that a loss of agency is a problem to be solved, not a punishment. Even a character with zero agency in a category remains an active participant in the story, creating gameplay centered on dependency, assistance, and the psychological horror of helplessness.

#### **3.6.2 The Agency Rating System**

A character's agency in each category is measured on a simple, clear scale. The base value for all categories is 3 and is dynamically reduced by external factors like equipment, status effects, or corruption.

*   **Agency 3 (Full):** Unrestricted capability. All related actions are available without penalty.
*   **Agency 2 (Minor Restriction):** A slight impairment. A small dice penalty is applied to relevant actions, and some advanced options may be unavailable.
*   **Agency 1 (Major Restriction):** A severe impairment. A significant dice penalty is applied to relevant actions, and most related options are unavailable.
*   **Agency 0 (Incapacitated):** Complete inability to act in this category. This is a **narrative trigger**, removing all related independent actions and instead creating unique "Request Assistance" or "Struggle" options that involve other characters.

#### **3.6.3 The Six Categories of Agency**

*   **`Mobility`:** Governs physical movement. Low mobility restricts positioning options and the ability to perform actions requiring locomotion, like fleeing or giving chase.
*   **`Speech`:** Governs verbal communication. Low speech agency restricts or muffles dialogue, penalizing social actions and preventing the use of spoken commands or abilities.
*   **`Manual`:** Governs the use of hands. Low manual agency restricts the ability to manipulate objects, use equipment, or perform fine motor tasks.
*   **`Vision`:** Governs sight. Low vision agency obscures information, penalizes actions reliant on sight (like observation or aiming), and can make navigation difficult.
*   **`Hearing`:** Governs auditory perception. Low hearing agency can cause a character to miss crucial audio cues and penalizes actions that rely on listening.
*   **`Decision`:** Governs autonomous choice. This is a special category affected by psychological factors like extreme arousal, mental domination, or compulsive corruption. Low decision agency can remove a character's ability to refuse certain actions or can heavily bias them toward specific, often self-destructive, choices.

#### **3.6.4 Integration with Psychology and Engines**

The Agency Profile is a critical, real-time input for a character's AI and the game's core engines.

*   **Engine Integration:** The `Encounter_Engine` and `Exploration_Engine` constantly read a character's Agency Profile to filter the list of available actions and apply appropriate mechanical penalties. An action that is impossible due to an agency restriction will simply not be presented as an option.
*   **Psychological Impact:** A character's agency state is a powerful driver for the `Psychological Integration` component.
    *   **Urgency:** A character with low agency will have a dramatically increased `Urgency Score` for any action that could restore that agency (e.g., escaping restraints, seeking help).
    *   **Emotional State:** Low agency is a direct trigger for desperate or fearful emotional states, influencing the narrative tone and a character's internal monologue.
    *   **Arousal & Helplessness:** For characters with a corresponding `Nature`, a state of low agency can be interpreted as a source of `Arousal Pressure`, creating a complex psychological feedback loop.

---

### **3.7: Arousal State Component**

#### **3.7.1 Design Philosophy**

The Arousal State Component systematically models a character's psychological arousal, serving as a core driver for both tactical decision-making and the emergence of explicit content. It is built on the crucial separation of a character's transient, in-the-moment arousal from their innate physical sensitivity, allowing for complex and psychologically authentic character states. This component is universal, with every character's arousal state being a dynamic and queryable part of the game world.

#### **3.7.2 The Arousal Scales**

The component operates on two distinct but related scales: a character's innate disposition (`Base Horniness`) and their fluctuating, moment-to-moment level of arousal (`Current Arousal`).

##### **`Base Horniness` (-3 to +3)**
This is a semi-permanent stat representing a character's innate, baseline relationship with sexuality. It is their psychological "center of gravity."

*   **-3 (Sex-Repulsed):** The character's baseline is active disgust and revulsion towards sexuality.
*   **-2 (Asexual-leaning):** The character lacks innate sexual drive and is generally disinterested.
*   **-1 (Subdued):** The character has a low but present libido.
*   **0 (Average):** The character has a typical, situational libido.
*   **+1 (Responsive):** The character has a higher-than-average libido and is easily aroused.
*   **+2 (Hypersexual):** The character is in a near-constant state of high arousal.
*   **+3 (Nympho/Incu-Succu-leaning):** The character's sexuality is a voracious, defining, almost predatory part of their identity.

##### **`Current Arousal` (-10 to +10)**
This is the dynamic, calculated value representing the character's psycho-sexual state at any given moment. It is the sum of their `Base Horniness` and all active `Arousal Pressure` sources, and is divided into five Tiers with distinct mechanical effects.

*   **-6 to -10 (Repulsed):** An active state of disgust. If the character is unable to escape a sexually charged environment, they begin to take **passive `Stability` damage** over time.
*   **-1 to -5 (Averse):** A state of active disinterest and discomfort. The `Psychology` component generates `Urgency` to avoid or end sexual situations.
*   **0 (Neutral):** A clear, unbiased mental state. No passive effects.
*   **+1 to +5 (Aroused):** A state of sexual interest. The `Psychology` component begins to increase the `Urgency` of relief-seeking actions.
*   **+6 to +10 (Compulsive):** A state of overwhelming arousal. The `Psychology` component heavily prioritizes erotic actions, and the character begins to take **passive `Inhibition` damage** over time if they cannot find release.

#### **3.7.3 Arousal Pressure & Relief**

`Arousal Pressure` is the mechanic that causes `Current Arousal` to fluctuate. It is a temporary value derived from a list of active sources, which can be positive (arousing) or negative (repulsing).

*   **Pressure Sources:** These are numerous and varied, falling into broad categories like Physical (denial, heat cycles), Psychological (power dynamics, dysphoria/euphoria), and Environmental (Subject auras).
*   **Relief Mechanisms:** A character can reduce their `Current Arousal` through various means, such as sexual release (orgasm), removing the source of pressure (e.g., taking off restrictive equipment), or leaving a high-pressure environment.

*Note: The definitive master list of all valid `Arousal Pressure Sources` and their default numerical values is maintained in `Character_Core_Systems_Library.md`.*

#### **3.7.4 Integration with Psychology**

The `Current Arousal` Tier is a primary input for the `Psychological Integration` component, shaping a character's internal state and driving their autonomous actions. The component uses the Arousal Tier to weigh the urgency of actions, filter the list of psychologically available choices, and modify the emotional tone of the narrative. At Compulsive or Repulsed Tiers, it can also directly impact a character's `Decision Agency`.

---

### **3.8: Climax State Component**

#### **3.8.1 Design Philosophy**

The Climax State Component is a universal system that manages the build-up to, execution of, and consequences following an orgasm. It is not merely a narrative event but a significant mechanical **state change** that has profound effects on a character's psychology, agency, and vulnerability. The system is designed to function seamlessly across both dynamic `Encounters` and the `Exploration` phase, turning the act of sexual release into a meaningful mechanic with both potential benefits and significant risks.

#### **3.8.2 The Climax Framework**

The process of reaching climax is modeled in three phases: the build-up, the event itself, and the aftermath.

##### **Phase 1: `Climax Proximity` (The Build-up)**
A character's progression towards orgasm is tracked by a universal meter.

*   **`climax_proximity` (Magnitude 0-100):** This meter represents a character's current level of sexual stimulation. It can be increased by any system in the game:
    *   **In Encounters:** Actions tagged as "Stimulating" will add points to the meter.
    *   **In Exploration:** Passive stimulation from equipment (e.g., vibrators) or environmental effects interacting with high `Anatomy` sensitivity can add points with each exploration action taken.
*   **Threshold Trigger:** Reaching **100** on this meter initiates a "Climax Event."

##### **Phase 2: The Climax Event (The Release)**
When `climax_proximity` reaches its threshold, a Climax Event is triggered. This is a brief, interruptive event that immediately alters the character's state.

*   **`climax_type` (String):** Every climax is assigned a type based on its context, which determines its psychological and mechanical effects. Examples include:
    *   **`Pleasure`:** A positive, sought-after orgasm.
    *   **`Stress_Relief`:** A desperate release of overwhelming tension.
    *   **`Submissive`:** An orgasm resulting from yielding to a dominant force.
    *   **`Forced`:** An orgasm triggered against the character's will, causing psychological distress.
*   **Immediate Mechanical Effects:**
    *   `climax_proximity` resets to **0**.
    *   `Current Arousal` is significantly reduced.
    *   All **`Agency Profile`** scores are temporarily reduced to 1 or 0 for a short duration, creating a critical **vulnerability window**.
    *   **Meter Effects:** The event can have positive or negative effects on meters (e.g., a `Pleasure` climax may restore a small amount of `Stability`, while a `Forced` climax will deal `Stability` damage).

##### **Phase 3: The Aftermath (Consequences & Cooldown)**
Following the event, the character enters a temporary post-climax state, primarily managed by the application of a **`Refractory Period` Status Effect**.

*   **`Refractory Period` (Status Effect):**
    *   **Dynamic Duration:** The duration of this effect is not fixed. It is dynamically calculated based on the character's **`refractory_rate`** from their `Anatomy Profile`, allowing for a wide spectrum of recovery times from hours to mere moments.
    *   **Core Effects:** This status effect temporarily locks the `climax_proximity` meter, applies negative `Arousal Pressure`, and can reduce the `Sensitivity` of relevant anatomical components.
*   **`Post-Climax State` (Status Effect):** In addition to the refractory period, a separate status effect is applied based on the `climax_type`, granting psychological bonuses or penalties (e.g., "Post-Climax Clarity," "Submissive Afterglow").

#### **3.8.3 Exploration & Vulnerability**

A climax occurring during the `Exploration` phase is a high-risk gamble. After the Climax Event resolves, the `Exploration_Engine` performs a **Vulnerability Check**. A failed check can immediately trigger a Subject ambush or another negative event, forcing the player into a new `Encounter` while they are still in a severely disadvantaged state from their post-climax agency drain.

#### **3.8.4 The Component Structure**

While the surrounding systems handle the event logic, the `Climax State` component on the character itself is simple, tracking the core variables:

*   **`climax_proximity`:** The current 0-100 value.
*   **`climax_cooldown_active`:** A boolean flag.
*   **`climax_history`:** A log of recent climaxes, including their `type` and `partner`, which is used by the `Psychological Integration` component to identify patterns of conditioning and trauma.

---

### **3.9: Eroticism Profile Component**

#### **3.9.1 Design Philosophy**

The Eroticism Profile Component is the systematic model of a character's "erotic landscape." It tracks their innate preferences, developed tastes, and aversions towards specific sexual acts and concepts. It is not a simple "fetish list" but a dynamic profile of a character's relationship with desire itself.

This system is built to distinguish between a character's innate disposition (seeded by `Character Nature`), their organic development through consensual or positive experiences, and their unnatural alteration via `Corruption`. It provides the core data for generating believable, preference-driven sexual behavior and complex psychological arcs.

#### **3.9.2 The `Eroticism Profile` Structure**

The component's core is a dictionary that maps specific content flags (representing erotic concepts) to a numerical score.

*   **`Affinity Score` (-10 to +10):** This score quantifies a character's feeling towards a specific erotic act.
    *   **Positive Score:** Represents a preference or fetish. The character is actively drawn to this concept.
    *   **Negative Score:** Represents an aversion or squick. The character is actively repulsed by this concept.
    *   **Zero:** Represents neutrality or inexperience.

#### **3.9.3 Profile in Action: Examples**

To illustrate how the profile functions, consider the following examples. A character's profile is a dictionary of `Content_Flag: Affinity_Score` pairs.

##### **Example Profile: "The Scholar" (Early Game)**
```
Eroticism_Profile {
  "bondage_equipment": -4,  // Innate aversion to restraint (from Nature)
  "worship_scenarios": 2,   // Innate interest due to religious Nature
  "public_exposure": -5,    // Innate aversion due to modest Nature
  "watersports": 0,         // Neutral/Inexperienced
  "anal_penetration": 0,    // Neutral/Inexperienced
}
```

##### **Example 1: Organic Development (Positive Reinforcement)**
*   **Scenario:** The Player and The Scholar have a high `COOPERATIVE` relationship. In a private, consensual encounter, the Player performs an act of worship on The Scholar, leading to a `Pleasure` type climax for The Scholar.
*   **Mechanic:** The `Psychological Integration` component processes this positive outcome.
*   **Result:** The Scholar's `Affinity Score` for `"worship_scenarios"` might increase from `2` to `4`. The experience was affirming. The AI for The Scholar will now have a significantly higher `Urgency` to seek out or accept worship in the future.

##### **Example 2: Organic Development (Negative Reinforcement)**
*   **Scenario:** The Protector, who has a negative `Affinity Score` for `anal_penetration`, is overpowered by a Subject and anally penetrated, resulting in a `Forced` climax and `Stability` damage.
*   **Mechanic:** The `Psychology` component processes this traumatic event.
*   **Result:** The Protector's `Affinity Score` for `"anal_penetration"` plummets further into the negative. The trauma reinforces their aversion, making them even more resistant to similar situations in the future.

##### **Example 3: Unnatural Alteration (Corruption)**
*   **Scenario:** The Manipulator has a low `Affinity Score` for `submission`. They repeatedly fail to resist the influence of a Subject that corrupts them along the `Dominion (Submission)` track.
*   **Mechanic:** Upon crossing a `Dominion (Submission)` threshold, the `Corruption State` component directly modifies the `Eroticism Profile`.
*   **Result:** The Manipulator's `Affinity Score` for `submission` is forcibly increased by a large amount. Their `Psychology` now has to reconcile their `Nature` (which despises submission) with their new, supernaturally-imposed *desire* for it. This creates a powerful internal conflict and is a core driver of the horror.

#### **3.9.4 Development of Erotic Tastes**

A character's `Affinity Score` for any given act is dynamic and shaped by three primary forces:

1.  **Innate Disposition:** The `Character Nature` component provides the **initial, starting `Affinity Score`s** for the profile, defining the character's tastes at the moment of their creation.
2.  **Organic Development (Experience):** Scores are updated by the `Psychological Integration` component based on the outcome of experiences. A positive event (e.g., a `Pleasure` type climax, a positive relationship gain) will increase the affinity for the acts involved. A traumatic or negative event will decrease it. This represents natural development through positive and negative reinforcement.
3.  **Unnatural Alteration (Corruption):** The `Corruption State` component, particularly the `Deviance` track, can directly and forcibly modify `Affinity Score`s, representing the supernatural rewriting of a character's desires, often in direct opposition to their `Nature`.

#### **3.9.5 Integration with Psychology**

The `Eroticism Profile` is a primary input for the `Psychological Integration` component, serving as a powerful driver for a character's autonomous sexual choices.

*   **Driving Urgency:** The `Affinity Score` for a potential action is a major modifier when the `Psychology` component calculates its `Urgency Score`. A character will have a high intrinsic urgency to perform actions that align with their high-affinity kinks and a strong drive to avoid those that trigger their aversions.
*   **Informing AI Behavior:** This system is the core mechanic that allows companion AI to exhibit authentic, preference-driven sexual behavior. It enables them to proactively seek out acts they enjoy, react positively or negatively to offers from others, and develop unique erotic personalities over time.

---

### **3.10: Corruption State Component**

#### **3.10.1 Design Philosophy**

The Corruption State Component is the primary system for permanent, long-term character transformation. It is the mechanical manifestation of the constitutional principle "Consequences Stay Consequences." Corruption is not a temporary debuff to be cured, but a fundamental and irreversible alteration of a character's physical, psychological, and moral being. It represents the character's systematic accommodation to the cosmic horror of the facility, a process that grants terrible new power at the cost of the self.

#### **3.10.2 The Mechanics of Transformation: `Corruption Vectors`**

Corruption is a multi-stage process driven by **`Corruption Vector`** objects. A Vector is a persistent "instruction packet" that contains the blueprint for a slow, creeping, permanent change.

1.  **Application:** A corruption source applies a `Corruption Status Effect`, which in turn attaches one or more `Corruption Vector`s to this component.
2.  **The Vector:** The Vector itself is a lightweight pointer. It contains the **`Track`** it affects (e.g., `Metamorphosis`), a **`Theme`** that defines the nature of the change (e.g., `Hyena`), and the number of **`Intervals`** the transformation will take.
3.  **The Creeping Change:** At specific intervals (e.g., when resting), the system processes the Vector. It looks up the Vector's `Theme` in the **`Corruption Theme Library`** and finds the list of potential changes for the character's current **`Corruption Threshold`**. It then applies one of these changes to the relevant CSF component.
4.  **The Threshold as Limiter:** The character's `Corruption Threshold` is the gatekeeper. A character with a low threshold can only undergo minor thematic changes, while a character with a high threshold has unlocked the potential for extreme and horrifying transformations.

#### **3.10.3 `Corruption Vector` in Action: An Example**

*   **The Vector Attached:** A character has a `Corruption Vector` with `{ Track: "Metamorphosis", Theme: "Hyena", Intervals: 5 }`.
*   **The Character's State:** Their `Metamorphosis Threshold` is currently at `Level 2`.
*   **The Interval:** The character rests. The system processes the vector.
*   **The Library Lookup:** The system opens the `Corruption Theme Library` and looks up the `Hyena` theme. It finds the data block for `Metamorphosis Threshold 2`, which contains a list of possible minor changes, including an instruction to change the `teeth_shape` property of the `mouth` component to `"Sharpened"`.
*   **The Push:** The system applies this change from the library to the character's `Anatomy Profile`. The vector's interval counter is incremented.
*   **The Result:** The character wakes up with subtly, but undeniably, sharper teeth. This process repeats, pulling new instructions from the library at each interval, until the vector is complete.

#### **3.10.4 Threshold-Based Progression**

A character's accommodation to corruption is measured in Thresholds, which are gained by accumulating corruption points.

*   **Corruption Points & Thresholds:** Each of the seven tracks has a Threshold level (from 0 to 10+). Crossing a threshold is a significant event that represents a new level of permanent integration.
*   **Threshold Effects:** Each threshold unlocks new passive perks (often double-edged), increases the intensity limit for transformations, and may be a prerequisite for a Subject's most powerful corrupting abilities.
*   **Story Gating:** Higher thresholds are explicitly gated by the character's `Tier`, ensuring a character's corruption is always narratively consistent with their experience.

#### **3.10.5 The Seven Corruption Tracks**

Each track targets different aspects of the Character State Framework.

*   **`Dominion` (Power Dynamics):** Rewrites a character's place in the power hierarchy. Its vectors primarily target and alter the `behavioral_weights` in the **`Character Nature`** component, creating an innate drive towards Dominance or Submission.
*   **`Metamorphosis` (Physical Transformation):** The biological rewriting of the body. Its vectors directly add or "hijack" **`Anatomical_Component`s** in the `Anatomy Profile`, causing horrifying physical changes.
*   **`Enthrall` (Mental Conditioning):** A "user-level" attack that adds new rules and compulsions to a character's thought process. Its vectors target the **`Psychological Integration`** component, creating internal conflict as the character's `Nature` fights against alien conditioning.
*   **`Deviance` (Moral Boundary Erosion):** The systematic rewriting of desire. Its vectors target and forcibly alter the `Affinity Score`s within the **`Eroticism Profile`**, supernaturally changing what a character finds pleasurable.
*   **`Exposure` (Privacy Erosion):** The destruction of personal boundaries. Similar to `Deviance`, its vectors primarily target the **`Eroticism Profile`**, conditioning a character towards voyeurism or exhibitionism.
*   **`Communion` (Ritualistic Bonding):** The creation of unnatural affection. Its vectors target the **`Relationship State`**, slowly and forcibly increasing a character's relationship score towards a specific entity, creating a Stockholm-syndrome-like bond.
*   **`Efface` (Identity Erosion):** A "root-level" attack that rewrites the character's core being. Its vectors are unique in that they initiate a contested roll to directly and permanently alter the properties of the **`Character Nature`** component itself. This is the horror of being replaced without even realizing it.

#### **3.10.6 Resistance and Reversal**

While the psychological and spiritual changes of corruption are permanent, the player is not entirely without recourse to manage its physical manifestations.
*   **Resistance:** A character's ability to fight off the application of a `Corruption Vector` or mitigate its effects is a core part of the gameplay loop.
*   **Reversal:** Some purely physical changes (specifically those from `Metamorphosis`) can be reversed, always at a cost.

*Note: The full framework for resisting unwanted transformations is detailed in `Character_Progression_Systems.md`. The mechanics for medical reversal services are detailed in `Facility_Environment_Systems.md`.*

---

### **3.11: Psychological Integration Component**

#### **3.11.1 Design Philosophy: The Decision Engine**

The Psychological Integration Component is the "central processing unit" of a character's mind. It is a sophisticated calculation engine whose purpose is to consume the entirety of the character's current state and process it through the lens of their immutable `Nature` to produce authentic, believable, and character-driven psychological outputs. This component is the engine of autonomy, generating the internal monologue, filtering choices, and driving the complex decision-making of companions.

#### **3.11.2 The Decision-Making Process**

The component follows a clear, multi-step process to determine a character's highest-urgency intent.

1.  **Filter by Physical Reality:** First, the component checks for any absolute physical limitations imposed by the character's state. It filters the master list of all possible actions down to only those that are physically achievable.
2.  **Gather Psychological Drivers:** It then gathers all relevant psychological inputs from the character's `Nature` and their current `Character State`.
3.  **Apply Weighted Priorities:** It calculates a final `Urgency Score` for each physically possible action by applying a weighted combination of all competing psychological drivers.
4.  **Select & Output:** The action with the highest final `Urgency Score` is selected and packaged into a formal `PsychologyOutput` packet for the game's engines.

#### **3.11.3 The State Priority Hierarchy: A Hybrid Model**

To resolve conflicts between a character's physical limitations and their psychological desires, the component uses a two-level priority system.

##### **Level 1: Physical Reality (Hard Overrides)**
These states represent absolute, physical impossibilities. They act as a **hard filter** on the list of available actions before any psychological calculation takes place.
*   **`Agency 0` (Incapacitated):** Overrides all conflicting desires. If `Speech Agency` is 0, no "Speak" actions are possible, period.
*   **`Meter Crisis` (e.g., `Vitality 0`):** Overrides conflicting desires. A character who is physically incapacitated cannot perform strenuous actions, regardless of their psychological urgency to do so.

##### **Level 2: Psychological Priority (Weighted Combination)**
Once the list of actions is filtered by physical reality, the component calculates the `Urgency Score` for the remaining options. This is a **weighted system** where different psychological states apply multipliers to a baseline urgency derived from `Character Nature`. This allows for complex and sometimes contradictory motivations to compete. In this layer, a powerful driver (like `Compulsive Arousal`) can temporarily outweigh a weaker one (like a `NEUTRAL Relationship`).

#### **3.11.4 Psychological Drivers (Inputs for the Weighted System)**

The following components and states serve as the primary inputs for the psychological weighting process:

*   **`Meter States` (The 4-Stage Psychology):** A character's position on the Peak/Moderate/Low/Crisis scale for each meter (`Vitality`, `Stability`, `Inhibition`) is a powerful psychological driver, creating biases towards confidence, caution, or desperation.
*   **`Character State` Components:** Every other component of the CSF acts as a modifier:
    *   **`Anatomy`:** Provides physical capabilities that inform choice.
    *   **`Identity`:** `Presentation Comfort` creates powerful urges for affirmation or correction.
    *   **`Relationships`:** A character's feelings toward a target heavily influence social and supportive actions.
    *   **`Agency` (Non-Crisis):** Low agency creates a strong drive to restore freedom.
    *   **`Arousal`:** The `Current Arousal` Tier is a dominant multiplier for erotic or avoidant behaviors.
    *   **`Climax`:** Post-climax status effects provide potent, short-term psychological directives.
    *   **`Eroticism Profile`:** `Affinity Score`s provide a direct bonus or penalty to the urgency of related erotic actions.
    *   **`Corruption`:** Provides powerful, permanent new urgencies that compete with the character's original `Nature`.

#### **3.11.5 The Final Output: Generating Psychological Authenticity**

The final result of the integration process is not just a single chosen action, but a rich set of data that ensures a character's behavior is authentic and believable across all game systems.

*   **Choice Filtering & Framing:** The component's first output is the final, filtered list of psychologically possible actions. It also provides contextual reframing for the *description* of these actions, ensuring the text reflects the character's internal state (e.g., "Submit to their demands" might be reframed as "Find safety in their authority" for a character high in `Dominion(Submission)`).
*   **Narrative Flavor:** The component is responsible for generating the `Emotional Tone` (e.g., "Desperate," "Confident," "Resigned") and the `Internal Monologue Hint` that are attached to the final `PsychologyOutput`. These are direct, high-level instructions for the `Narrative_Engine`.
*   **Emergent Social Dynamics:** This is where the complex interplay of relationships is resolved. When a companion's AI makes a decision, this component is what weighs their `Relationship` with the player against their `Relationship` with other companions, their personal `Corruption`, and their `Nature`, leading to unscripted alliances, betrayals, and other complex social behaviors.

#### **3.11.6 Output Application: Emergent Social Dynamics**

The true power of the `Psychological Integration` component is realized when multiple autonomous characters interact. The system does not rely on scripted social scenes; instead, it generates complex and emergent social dynamics by having each character process their own state and relationships independently.

This is best illustrated by how the component handles conflicting relationships:

*   **Example: "Competing Loyalties"**
    *   **Scenario:** The Player proposes an action that puts The Scholar at risk. The Protector's `Psychology` component must decide whether to support the Player's plan.
    *   **The Calculation:** The component weighs several conflicting drivers:
        *   Its `Relationship` with the Player (e.g., `COOPERATIVE: 7`).
        *   Its `Relationship` with The Scholar (e.g., `LOYAL: 10`).
        *   Its `Character Nature` (`core_drive: "Ensure_Ally_Safety"`).
        *   The perceived risk of the action.
    *   **The Result:** In this case, the `Urgency Score` for an "Oppose Player's Plan" or "Propose Safer Alternative" action would almost certainly be higher than the urgency to comply, driven by the higher relationship score and the core nature. This creates a moment of dynamic, unscripted conflict between the Player and The Protector, born entirely from the AI processing its own priorities.

*   **Example: "United Opposition"**
    *   **Scenario:** The Manipulator, who is `RESENTFUL` towards both The Scholar and The Protector, attempts to take the last medkit.
    *   **The Calculation:** Both The Scholar's and The Protector's `Psychology` components independently calculate the urgency of a "Block Manipulator" action. Because their `Relationship` with The Manipulator is low and the action conflicts with group survival goals, this urgency will be very high for both of them.
    *   **The Result:** The system generates a scenario where two characters spontaneously form a temporary alliance to oppose a third, without any specific script telling them to do so.

This capacity for emergent, multi-character social calculation is the ultimate output of the `Psychological Integration` component, creating a truly dynamic and unpredictable narrative.

---

### **3.12: Character Psychology Output Interface**

#### **3.12.1 Design Philosophy: The Universal Contract**

This component defines the formal, standardized data structure that the `Psychological Integration` component assembles as its final output. This "packet" is the universal language that a Character's mind uses to communicate its desires and state to the rest of the game's systems, primarily the `Core_Encounter_Engine` and the `Narrative_Engine`. Its strict, consistent structure is what allows for the project's modularity, ensuring that any entity's psychology can seamlessly interface with the core engines.

#### **3.12.2 The `PsychologyOutput` Packet Structure**

**[TODO: The final, detailed specification for this data structure is pending the design of the `Scene Requirement Data Structure` ("Intent Packet") in the `Narrative_Engine.md`. This section will be completed as part of the Engine design phase to ensure perfect integration.]**

This structure will contain, at a minimum:
*   The chosen highest-urgency **`IntentPacket`**.
*   The final calculated **`Urgency Score`**.
*   The **`Emotional Tone`** and **`Internal Monologue Hint`** for the `Narrative_Engine`.
*   The character's **`Continue Encounter`** flag.