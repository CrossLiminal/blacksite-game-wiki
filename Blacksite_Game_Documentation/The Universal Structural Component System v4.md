# **The Universal Structural Component System**

**System Authority:** Defines the universal framework for the physical and systemic composition of all entities.
**Dependencies:** `Project_Foundations.md`
**Dependents:** `Entity_Core_Systems.md`, `Character_Core_Systems.md`, `Subject_Core_Systems.md`, `Hazard_Systems.md`, `Core_Encounter_Engine.md`.
**Version:** 4.0 - Final Unified Architecture

---

## **1. System Overview & Design Philosophy**

The Universal Structural Component System provides a single, unified framework for defining the physical, quasi-physical, and systemic nature of any entity in the game, from human Characters to alien Subjects and corporeal Hazards.

The core philosophy is built on three key principles:

1.  **Unified Architecture:** There is only **one** fundamental component type, the `Structural_Component`. Its function is determined entirely by the data it contains. This massively simplifies the `Core_Encounter_Engine`'s logic.
2.  **Composition over Categorization:** An entity is **composed** of a collection of `Structural_Component`s and **Systemic Profiles**. A component's role—be it interactive or primarily descriptive—is an emergent property of its data. This provides infinite flexibility for character transformation and alien design.
3.  **Function over Form:** The system prioritizes defining what a component *does* (`Capabilities`) and what *can be done to it* (`Receptivities`) over rigid anatomical labels, allowing for a vast range of interactions to be resolved through a minimal, elegant ruleset.

An entity's complete physical and systemic description—be it a Character's **`Anatomy Profile`** or a Subject's **`Manifestation Profile`**—is an implementation of the systems defined herein.

---

## **2. The `Structural_Component`**

The `Structural_Component` is the universal building block for all physical and quasi-physical parts of an entity. A component that primarily serves a narrative purpose will have minimal or empty `capabilities`, while a component used for direct interaction will have a full suite. Corruption can add capabilities to any component, transforming a descriptive part into an interactive one.

#### **Core Fields:**

*   **`ID`:** A unique, queryable identifier (e.g., `"mouth_01"`, `"hair_head_01"`).
*   **`Zone`:** A tag indicating the broad region where the component is located (e.g., `"Oral"`, `"Chest"`, `"Appendages"`). Used for high-level targeting and resolving area effects.
*   **`Feature_Type`:** A simple "noun" tag for quick AI categorization (e.g., `"Orifice"`, `"Appendage"`, `"Hair"`).
*   **`properties`:** A dictionary for the component's semi-permanent, defining characteristics.
*   **`capabilities`:** A list of tags defining the actions this component can **perform**.
*   **`receptivities`:** A list of tags defining the actions that can be **done to this component**.
*   **`modifications`:** A list where applied modifications like tattoos or piercings are stored.
*   **`states`:** A dictionary for the component's volatile, temporary conditions (`exposure_state`, `condition`, `in_use_by`).

#### **The `states` Dictionary in Detail**

This dictionary tracks the component's current, moment-to-moment condition during gameplay.

*   **`exposure_state`:**
    *   **Purpose:** Defines the component's current level of coverage by clothing or environmental factors.
    *   **Values:** A string from a fixed list: `"Covered"`, `"Partially_Exposed"`, or `"Fully_Exposed"`.

*   **`condition`:**
    *   **Purpose:** Defines the component's current physical status.
    *   **Values:** A string from a fixed list, such as `"Normal"`, `"Sore"`, `"Damaged"`, `"Numb"`, `"Sensitized"`.

*   **`in_use_by`:**
    *   **Purpose:** Tracks if the component is currently occupied in a direct, physical interaction. This is the primary mechanic for determining if a body part is "busy."
    *   **Default Value:** `null`.
    *   **Active Value:** When a component is in use, this field becomes an **object** with the following, precise structure:
        *   **`agent` (Entity ID):** The unique identifier of the entity *performing the action* on this component.
        *   **`tool` (Component ID):** The unique identifier of the `Structural_Component` being *used* by the agent (e.g., the ID of the agent's hand, penis, or tentacle).

    *   **Example of `in_use_by` in action:**
        *   If the Player is performing a handjob on a Companion:
            *   On the **Companion's `penis_01` component**, the `in_use_by` state would be: `{ agent: "Player_ID", tool: "player_hand_01" }`.
            *   On the **Player's `hand_01` component**, the `in_use_by` state would be: `{ agent: "Player_ID", tool: "companion_penis_01" }`.

### **The Action Framework: Capability & Receptivity**

For an action to be valid, the acting component must possess the required **Capability**, and the target component must possess the corresponding **Receptivity**. The same tag has a different meaning depending on which list it's in.

| Tag | As a Capability (in the `capabilities` list) | As a Receptivity (in the `receptivities` list) |
| :--- | :--- | :--- |
| **`PENETRATION`** | Defines a component that can be used to penetrate. | Defines a component that can receive penetration. |
| **`MANIPULATION`** | Defines a component that can be used to touch, hold, grope, or restrain. | Defines a component that can be touched, held, groped, or restrained. |
| **`FRICTION`** | Defines a component that can be used to rub against a surface for stimulation. | Defines a component that can be rubbed against for stimulation. |
| **`ENCLOSURE`** | Defines a component that can be used to surround, squeeze, or constrict. | Defines a component that can be surrounded, squeezed, or constricted. |
| **`IMPACT`** | Defines a component that can be used to strike a surface. | Defines a component that can be struck. |

*Designer's Note: The master lists for all tags (`Zone`s, `Feature_Type`s, `Capabilities`, and `Receptivities`) will be maintained in `Core_Data_Library.md`.*

---

## **3. The Systemic Profiles**

These are top-level components that model an entity's internal, background systems. They have their own unique, well-defined structures.

### **3.1 `Frame` Systemic Profile**
*   **Purpose:** Defines the core mechanical stats of the entity's entire physical frame.
*   **Structure:**
    *   `height` (in cm)
    *   `muscle_tone` (Magnitude)
    *   `body_fat` (Magnitude)
    *   `flexibility` (Magnitude)
    *   `derived_build_type` (A tag for AI assessment, e.g., "Athletic")
    *   `derived_mass` (in kg)

### **3.2 `Senses` Systemic Profile**
*   **Purpose:** Models the entity's ability to perceive the world, defined by a baseline effectiveness (`acuity`) and any special capabilities (`tags`).
*   **Structure:**
    *   **`vision`:** `{ "acuity": Magnitude, "tags": [...] }` (e.g., `["Night_Vision"]`)
    *   **`hearing`:** `{ "acuity": Magnitude, "tags": [...] }`
    *   **`scent`:** `{ "acuity": Magnitude, "tags": [...] }` (e.g., `["Pheromone_Analysis"]`)
    *   **`touch`:** `{ "sensitivity": Sensitivity, "pain_threshold": Sensitivity }`
    *   **`taste`:** `{ "acuity": Magnitude }`
    *   **`special`:** `{ "tags": [...] }` (e.g., `["Synesthesia_Audio_Visual"]`)

### **3.3 `Chemistry` Systemic Profile**

*   **Purpose:** To model the entity's complete biochemical state, including baseline scents, dynamic pheromonal broadcasts, and cyclical reproductive states. This is the single source of truth for all scent- and pheromone-based mechanics.
*   **Structure:** A collection of nested objects, each modeling a specific subsystem.

    *   **`base_scent_profile`:** Defines the entity's constant, passive scent for narrative description.
        *   **`primary_note` (String):** The most dominant or recognizable scent note (e.g., "Ozone," "Lilac," "Musk").
        *   **`secondary_note` (String):** A subtle undertone that adds complexity (e.g., "Petrichor," "Cinnamon," "Brine").
        *   **`intensity` (Magnitude):** How powerfully the base scent projects into the immediate area.

    *   **`pheromone_system`:** Models the entity's active, mechanically-relevant chemical signals. This is the primary system read by the engine's Proximity Effects phase.
        *   **`production_potency` (Magnitude):** The entity's baseline, innate strength for all pheromonal broadcasts.
        *   **`receptivity` (Sensitivity):** How strongly the entity is affected by the pheromones of others. This acts as a resistance or vulnerability modifier.
        *   **`current_broadcast` (Object):** The specific signal the entity is actively emitting right now.
            *   **`type` (String):** The nature of the signal being broadcast (e.g., "Arousal," "Fear," "Aggression," "Territorial," or "None").
            *   **`intensity` (Magnitude):** The final, calculated strength of the current broadcast (e.g., `production_potency` + bonus from a `Heat Cycle`).

    *   **`reproductive_system`:** Models all signals and states related to fertility and breeding.
        *   **`cycle_type` (String):** The nature of the entity's reproductive cycle (e.g., "Heat," "Rut," "Spawning," "Pollination").
        *   **`cycle_state` (String):** The current phase of the cycle ("None," "Building," "Peak," "Waning").
        *   **`cycle_intensity` (Magnitude):** The strength of the cycle's **internal** psychological and physical effects on the entity itself.
        *   **`fertility_display` (Magnitude):** How "visibly" fertile the entity appears (e.g., swollen features, glowing markings). This is a passive, visual signal.
        *   **`allure_modifier` (Magnitude):** The entity's esoteric, non-pheromonal "X-factor" for supernatural attraction.
        *   **`can_mark_territory` (Boolean):** A flag indicating if the entity has the ability to leave persistent scent marks in the environment.

    *   **`systemic_rates`:** Defines core biochemical rates of change.
        *   **`refractory_rate` (Magnitude):** Governs the speed of physiological and psychological recovery after climax.
        *   **`chemical_resistance` (Magnitude):** Governs resistance to non-pheromonal chemical agents like drugs or poisons.

    *   **`derived_breeding_appeal` (Magnitude):** This is a calculated, top-level value that represents the entity's total reproductive "signal strength" at any given moment. It is the sum of their `fertility_display`, `allure_modifier`, and any bonuses from their `pheromone_broadcast` and `cycle_state`. This is the single value queried by an observer's `Psychology System` (Character or Subject) to assess desirability and reproductive readiness.

---

## **4. Component Blueprints & Structural Templates**

To streamline entity creation, the system uses two concepts defined in the data libraries:

*   **Component Blueprints:** The master definition for each type of `Structural_Component` (e.g., `mouth`, `hand`, `hair`). The blueprint lists all the possible `properties` the component can have, its default `Zone`, `Capabilities`, etc.
*   **Structural Templates:** A pre-defined assembly of Component Blueprints that represents a common body plan (e.g., `Template_Humanoid`). A designer can start with a template and then customize it.

---

## **5. Size Mismatch & Accommodation Mechanics**

The **Resonance Adaptation Field** allows characters to survive physically impossible interactions, but not without consequence. When an `Interactive_Component` with a `size` property attempts to interact with a component with a `capacity` property, the engine calculates the **Size Differential** (`capacity - size`). A negative differential triggers the following graduated consequences.

*   **Extreme Mismatch (Differential ≤ -5):** Major `Vitality` damage + **"Severe Trauma"** status effect.
*   **Severe Mismatch (Differential -4 to -3):** Moderate `Vitality` damage + **"Stretched"** status effect.
*   **Moderate Mismatch (Differential -2 to -1):** Minor `Vitality` damage + **"Sore"** status effect.

#### **The "Accommodation Trauma" Status Effect**
This is a special, multi-stage status effect applied by a Severe Mismatch, representing the body's horrifying adaptation process. At its final stage, "Adapted," all penalties fade, and the component's baseline `capacity` property is **permanently increased by 1**, representing a corruption of the body's natural limits.

---

### **Appendix A: Example Component Blueprints (Humanoid Template)**

This appendix provides a set of example blueprints for the `Structural_Component`s and `Systemic_Profile`s that constitute a baseline human entity. These are assembled into the `Template_Humanoid` used for character creation.

---
#### **Systemic Profiles (Examples)**

**`Frame` Profile Example:**
*   **Properties:**
    *   `height`: 175
    *   `muscle_tone`: 5
    *   `body_fat`: 5
    *   `flexibility`: 5
    *   `derived_build_type`: "Average"
    *   `derived_mass`: 75

**`Senses` Profile Example:**
*   **Properties:**
    *   `vision`: `{ "acuity": 5, "tags": [] }`
    *   `hearing`: `{ "acuity": 5, "tags": [] }`
    *   `scent`: `{ "acuity": 3, "tags": [] }`
    *   `touch`: `{ "sensitivity": 3, "pain_threshold": 3 }`
    *   `taste`: `{ "acuity": 3 }`
    *   `special`: `{ "tags": [] }`

**`Chemistry` Profile Example:**
*   **Properties:**
    *   `base_scent_profile`: `{ "primary_note": "Human_Musk", "secondary_note": "Clean_Sweat", "intensity": 3 }`
    *   `pheromone_system`: `{ "production_potency": 3, "receptivity": 3, "current_broadcast": { "type": "None", "intensity": 0 } }`
    *   `reproductive_system`: `{ "cycle_type": "None", "cycle_state": "None", "cycle_intensity": 0, "fertility_display": 3, "allure_modifier": 3, "can_mark_territory": false }`
    *   `systemic_rates`: `{ "refractory_rate": 3, "chemical_resistance": 3 }`
    *   `derived_breeding_appeal`: 6

---
#### **Structural Components (Examples)**

**Component Blueprint: `mouth`**
*   **Default Zone:** "Oral"
*   **Default Feature Type:** "Orifice_Oral"
*   **Default Capabilities:** `[MANIPULATION, ENCLOSURE, FRICTION]`
*   **Default Receptivities:** `[PENETRATION, MANIPULATION, FRICTION]`
*   **Default Properties:**
    *   `capacity`: 4
    *   `throat_sensitivity`: 3
    *   `oral_elasticity`: 3
    *   `gag_reflex`: 3
    *   `saliva_production`: 3
    *   `tongue_length`: 3
    *   `tongue_dexterity`: 3

**Component Blueprint: `hands`**
*   **Default Zone:** "Arms"
*   **Default Feature Type:** "Appendage_Manual"
*   **Default Capabilities:** `[MANIPULATION, ENCLOSURE, IMPACT, FRICTION, PENETRATION]`
*   **Default Receptivities:** `[MANIPULATION]`
*   **Default Properties:**
    *   `dexterity`: 4
    *   `strength`: 4
    *   `penetration_size`: 2

**Component Blueprint: `penis`** (Present in `Template_Humanoid_Male`)
*   **Default Zone:** "Groin"
*   **Default Feature Type:** "Appendage_Genital"
*   **Default Capabilities:** `[PENETRATION, FRICTION]`
*   **Default Receptivities:** `[MANIPULATION, FRICTION, IMPACT]`
*   **Default Properties:**
    *   `size`: 5
    *   `girth`: 5
    *   `shape`: "Human"
    *   `firmness`: 5
    *   `sensitivity`: 4

**Component Blueprint: `vagina`** (Present in `Template_Humanoid_Female`)
*   **Default Zone:** "Groin"
*   **Default Feature Type:** "Orifice_Genital"
*   **Default Capabilities:** `[ENCLOSURE, FRICTION]`
*   **Default Receptivities:** `[PENETRATION, MANIPULATION, FRICTION]`
*   **Default Properties:**
    *   `capacity`: 5
    *   `depth`: 6
    *   `elasticity`: 4
    *   `muscle_control`: 3
    *   `sensitivity`: 4

**Component Blueprint: `anus`**
*   **Default Zone:** "Anal"
*   **Default Feature Type:** "Orifice_Anal"
*   **Default Capabilities:** `[ENCLOSURE]`
*   **Default Receptivities:** `[PENETRATION, MANIPULATION, FRICTION]`
*   **Default Properties:**
    *   `capacity`: 3
    *   `depth`: 8
    *   `elasticity`: 3
    *   `muscle_control`: 3
    *   `sensitivity`: 3

**Component Blueprint: `breasts`**
*   **Default Zone:** "Chest"
*   **Default Feature Type:** "Mound"
*   **Default Capabilities:** `[ENCLOSURE]`
*   **Default Receptivities:** `[MANIPULATION, IMPACT, FRICTION]`
*   **Default Properties:**
    *   `size`: 4
    *   `sensitivity`: 3
    *   `firmness`: 4

**Component Blueprint: `nipples`**
*   **Default Zone:** "Chest"
*   **Default Feature Type:** "Nipple"
*   **Default Capabilities:** `[]`
*   **Default Receptivities:** `[MANIPULATION]`
*   **Default Properties:**
    *   `size`: 2
    *   `sensitivity`: 4

**Component Blueprint: `hair_head`**
*   **Default Zone:** "Head"
*   **Default Feature Type:** "Hair"
*   **Default Capabilities:** `[]`
*   **Default Receptivities:** `[MANIPULATION]`
*   **Default Properties:**
    *   `length`: "Short"
    *   `style`: "Messy"
    *   `texture`: "Soft"
    *   `natural_color`: "Brown"
    *   `dyed_color`: "None"

*This appendix provides a baseline. The full, exhaustive list of all humanoid component blueprints will be maintained in `Core_Data_Library.md`.*