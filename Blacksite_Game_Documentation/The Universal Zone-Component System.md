## **The Universal Zone-Component System**

**System Authority:** Defines the universal framework for the physical and systemic composition of all entities.
**Dependencies:** `Project_Foundations.md`
**Dependents:** `Entity_Core_Systems.md`, `Character_Core_Systems.md`, `Subject_Core_Systems.md`, `Hazard_Systems.md`, `Encounter_Engine.md`.
**Version:** 6.0 - Unified Exposure State Architecture

---

### **Introduction**

This document provides the complete architectural blueprint for the **Universal Zone-Component System**, the foundational framework used to define the physical and systemic nature of every entity in *Beware the Blacksite*. This single, unified system is used to model everything from a baseline human Character to a reality-defying Subject, ensuring that all physical interactions are governed by a consistent, robust, and flexible set of rules.

The system is built on a philosophy of **composition over categorization**. An entity is not defined by a rigid class, but is instead **composed** of a collection of modular, reusable parts. This allows for near-infinite variety in entity design and provides a powerful, logical framework for the game's core themes of transformation and body horror.

This document will detail the three core pillars of this architecture:

1.  **Hierarchical Zones:** An entity's physical profile is a map of `Zone`s, which can contain nested `Sub-Zone`s for granular detail. These `Zone`s act as the primary containers for all physical components and their collective states.

2.  **Hierarchical Components:** `Zone`s contain `Component`s, which can in turn contain their own `Sub-Component`s. This creates a clear physical hierarchy that mirrors real anatomy and allows for the modeling of complex, dependent body parts.

3.  **Composition via `Traits`:** A component's function, properties, and even its sub-components are not unique to that part. Instead, they are inherited from a library of modular, reusable `Traits`. A complex component like a penis is simply a composition of granular Traits such as `Is_Appendage`, `Can_Penetrate`, and `Is_Erogenous`.

---

### **Section 1: The Entity Profile Structure**

The complete physical and systemic makeup of an entity is defined within its **Entity Profile**. This is the top-level container for all the data described in this document. While different entity types may give this profile a thematic name (e.g., a Character's `Anatomy Profile` or a Subject's `Manifestation Profile`), they all adhere to the same fundamental structure.

The Entity Profile is composed of two primary parts: the **`Structural Profile`**, which defines the entity's physical parts, and the **`Systemic Profiles`**, which define its non-physical, background systems.

#### **1.1: The `Structural Profile` (The Map of Zones)**

The `Structural Profile` is the definitive map of an entity's physical or quasi-physical form. It is structured as a **dictionary of `Zone`s**, where each `Zone` serves as a primary container for a major region of the body.

This "Zone as Container" model is the core of the system's architecture. A `Zone` can contain not only a list of root-level `Component`s but also more granular, nested `Sub-Zone`s. This hierarchical structure provides the flexibility needed to model complex anatomy and layered clothing.

**Example Data Structure:**
*This example illustrates the full hierarchy, from the parent `Torso` Zone down to a `nipples` Sub-Component, showing how states, properties, and modifications can exist at each level.*
```
Structural_Profile: {
  // A top-level Zone, representing the entire torso.
  "Torso": {
    // --- Zone-level Data ---
    "exposure_state": "Covered", // e.g., by a Shirt
    "properties": { "general_description": "A well-defined torso." },
    "modifications": [],

    // --- Nested Sub-Zones ---
    "sub_zones": {
      "Torso_Chest": {
        // --- Sub-Zone specific Data ---
        "exposure_state": "Covered", // e.g., by a Bra underneath the Shirt
        "properties": { "description": "A broad, muscular chest." },
        "modifications": [
          { "Type": "Scarification", "Subtype": "Ritual_Markings", "Location": "Across the collarbone" }
        ],
        
        // A list of the components within this Sub-Zone.
        "components": [
          {
            // --- Component Data (Breasts) ---
            "ID": "breasts_01",
            "Traits": ["Fleshy_Mound", "Has_Nipples"],
            "properties": { "size": 5, "firmness": 4, "sensitivity": 3 },
            "states": { "condition": "Normal", "in_use_by": null },
            "modifications": [],
            
            // This component contains its own Sub-Components.
            "sub_components": {
              "nipples": { 
                // --- Sub-Component Data (Nipples) ---
                "ID": "nipples_01", 
                "Traits": ["Erogenous_Node"],
                "properties": { "size": 2, "sensitivity": 5, "state": "Erect" },
                "states": { "condition": "Normal", "in_use_by": null },
                "modifications": [
                  { "Type": "Piercing", "Subtype": "Barbell", "Material": "Steel" }
                ]
              }
            }
          }
        ]
      },
      "Torso_Abdomen": {
        // --- Sub-Zone specific Data ---
        "exposure_state": "Covered", // e.g., by a Corset
        "properties": { "definition": "Toned" },
        "modifications": [
          { "Type": "Tattoo", "Subtype": "Elaborate_Script", "Description": "A sprawling black-ink tattoo covers the abdomen." }
        ],
        "components": [
          { "ID": "abdomen_surface_01", "Traits": ["Flesh_Surface"], ... }
        ]
      }
    },
    // The root Zone has no direct components in this example.
    "components": [] 
  }
}
```

#### **1.2: The `Systemic Profiles`**

Alongside the physical profile, every entity possesses a collection of **`Systemic Profiles`**. These are distinct, top-level objects that model the entity's non-physical, background systems. They provide the core mechanical stats and passive capabilities that influence the entity's state and actions.

The standard systemic profiles are:

*   **`Frame`:** Defines the core mechanical stats of the entity's entire physical frame, such as height, muscle tone, and flexibility.
*   **`Senses`:** Models the entity's ability to perceive the world through vision, hearing, scent, and other senses.
*   **`Chemistry`:** Models the entity's complete biochemical state, including scents, pheromones, and cyclical reproductive states.

*Designer's Note: The full, detailed structure of each `Systemic Profile` is defined in Section 6 of this document.*

---

### **Section 2: The Hierarchical Zone System**

The `Zone` is the primary organizational unit of an entity's `Structural Profile`. It is not merely a label, but a functional container that groups `Component`s and other `Sub-Zone`s, managing their collective state and serving as the primary point of interaction for any game system that deals with broad areas of the body.

#### **2.1: `Zone` as a Hierarchical Container**

Every entity's `Structural Profile` is a dictionary of its top-level `Zone`s (e.g., `"Head"`, `"Torso"`, `"Groin"`). To provide the necessary granularity for complex anatomy and layered equipment, a `Zone` is a recursive structure that can contain its own dictionary of `Sub-Zone`s.

This hierarchical `Zone -> Sub-Zone` structure allows for the precise definition of an entity's form. Both `Zone`s and `Sub-Zone`s serve as containers for two primary collections:

*   **`components` (List):** A list of all root-level `Structural_Component` objects that reside directly within that `Zone` or `Sub-Zone`.
*   **`properties` and `modifications`:** Dictionaries and lists that hold descriptive data and persistent modifications (like large tattoos or scars) that apply to the entire region.

#### **2.2: `Zone`-Based States**

To model area-of-effect conditions that affect an entire region of the body, key states are managed at the `Zone` (and `Sub-Zone`) level. These states logically cascade downwards, affecting all components and sub-zones contained within unless a more specific state on a child component overrides them.

*   **`exposure_state`:**
    *   **Purpose:** This state tracks the coverage of a Zone by clothing or environmental factors. It is the primary mechanic for managing nudity and exposure, and a key factor in determining which actions are available.
    *   **Values:** A string from a fixed list, with each value implying different levels of access: `"Fully_Exposed"`, `"Partially_Exposed"`, `"Covered"`, `"Obstructed"`, `"Blocked"`.
    *   **Logic:** This state is typically set by equipment. A simple piece of clothing like a shirt applies the `"Covered"` state to the parent `"Torso"` zone. This state is then inherited by all its sub-zones (`Torso_Chest`, `Torso_Abdomen`). A more specific item, like a bra, could then apply its own `"Covered"` state only to the `"Torso_Chest"` sub-zone, creating a layered effect.

---

### **Section 3: Standardized Property Scales**

To ensure mechanical consistency and ease of balancing across all entities, all quantifiable `properties` within a `Structural_Component` or `Systemic_Profile` adhere to one of three universal scales. These scales provide a clear, human-readable measure of an entity's capabilities.

#### **3.1: The `Magnitude` Scale (1-10+)**

*   **Purpose:** Used for most quantifiable physical measurements, such as `size`, `capacity`, `strength`, `firmness`, and `flexibility`. It represents a linear progression of raw power or physical dimension.
*   **Scale:**
    *   **1-2:** Minimal or deficient.
    *   **3-4:** Below average; a noticeable limitation.
    *   **5-6:** Average human baseline.
    *   **7-8:** Above average; notably skilled or well-endowed.
    *   **9-10:** Exceptional; peak human potential.
    *   **11+:** Supernatural; beyond the limits of normal biology.

#### **3.2: The `Sensitivity` Scale (1-5)**

*   **Purpose:** Used to measure responsiveness to physical and emotional stimuli. It is the primary scale for properties like `sensitivity` and `pain_threshold`.
*   **Scale:**
    *   **1:** Numb or completely unresponsive.
    *   **2:** Low sensitivity; dulled.
    *   **3:** Normal human baseline.
    *   **4:** High sensitivity; acute.
    *   **5:** Hypersensitive; overwhelmingly responsive.

#### **3.3: The `Control` Scale (1-5)**

*   **Purpose:** Used to measure an entity's conscious mastery over a specific bodily function. It is the primary scale for properties like `muscle_control` and `gag_reflex`.
*   **Scale:**
    *   **1:** No conscious control; purely reflexive.
    *   **2:** Minimal or clumsy control.
    *   **3:** Moderate, average control.
    *   **4:** Good, well-practiced control.
    *   **5:** Perfect, absolute mastery.

---

### **Section 4: The `Structural_Component`**

The `Structural_Component` is the universal building block for all physical and quasi-physical parts of an entity. It is a highly flexible data structure whose function is defined entirely by the data it contains. A component's role—be it a primarily descriptive part like skin or a fully interactive one like a hand—is determined by the `Traits` it is composed of, which populate its various fields.

#### **4.1: The Core Structure**

A `Structural_Component` is a dictionary containing the following top-level keys. Each key is essential for defining the component's identity, function, and current state.

*   **`ID`:** A unique, queryable identifier string for the specific component instance (e.g., `"mouth_01"`, `"breasts_upper_pair"`). This ID must be unique across the entire entity.
*   **`Traits`:** A list of strings identifying the `Trait` blueprints inherited by this component. These `Traits` (detailed in Section 5) are responsible for populating the `properties`, `capabilities`, `receptivities`, and `sub_components` fields with their default data.
*   **`properties`:** A dictionary containing the component's semi-permanent, defining characteristics.
*   **`capabilities`:** A list of tags defining the actions this component can **perform**.
*   **`receptivities`:** A list of tags defining the actions that can be **done to this component**.
*   **`states`:** A dictionary containing the component's volatile, temporary conditions.
*   **`modifications`:** A list of all applied, persistent modifications like tattoos or brands that are specific to this component.
*   **`sub_components`:** A dictionary containing any nested `Structural_Component`s that are physically and functionally dependent on this parent component.

#### **44.2: The `properties` Dictionary**
This dictionary holds the component's "stat block"—its inherent, semi-permanent characteristics. These values are typically set at creation (based on inherited `Traits`) and are only changed by significant, permanent effects like `Metamorphosis` corruption. Example properties include `size`, `capacity`, `sensitivity`, `material`, `shape`, `firmness`, and any other defining physical feature, including stateful properties like a `knot` or `flare` object for components with those traits.

#### **4.3: The `states` Dictionary in Detail**
This dictionary tracks the component's current, moment-to-moment condition during gameplay. These values are highly volatile and are frequently updated by the game engine.

*   **`exposure_state` (Component-Level Override):**
    *   **Purpose:** To handle specific, targeted coverage (e.g., nipple pasties, a cock ring) that is more granular than its parent `Zone`. This state, when set to a value other than `Default` or `null`, **overrides** the `exposure_state` inherited from the parent `Zone`.
    *   **Values:** A string from the fixed list of exposure states: `"Fully_Exposed"`, `"Partially_Exposed"`, `"Covered"`, `"Obstructed"`, `"Blocked"`.
    *   **Example:** A character might be topless (`Torso_Chest` zone is `"Fully_Exposed"`), but wearing nipple pasties. The `nipples` sub-component would have its personal `exposure_state` set to `"Partially_Exposed"`, correctly reflecting its specific state and altering which actions can target it.

*   **`condition`:**
    *   **Purpose:** Defines the component's current physical status.
    *   **Values:** A string from a fixed list, such as `"Normal"`, `"Sore"`, `"Damaged"`, `"Numb"`, `"Sensitized"`.

*   **`in_use_by` (List of Interactions):**
    *   **Purpose:** Tracks all direct, physical interactions currently involving this specific component. This is a crucial piece of data for the engine's positional logic to determine if a body part is "busy."
    *   **Structure:** A **list** of interaction objects. The list is empty by default.
    *   **Interaction Object Structure:** When a component is in use, an object is added to the list with the structure: `{ "agent": Entity_ID, "tool": Component_ID }`.

    *   **Logic and Hierarchy:**
        *   **Multiple Interactions on a Single Component:** A single component can be involved in multiple interactions if the `Encounter_Engine`'s positional logic deems them physically compatible based on the current encounter state (stances, component sizes, etc.).
            *   **Example (Double Penetration):** A `vagina` component's `in_use_by` list could contain two separate interaction objects: `{ agent: "Entity_A", tool: "penis_01" }` and `{ agent: "Entity_B", tool: "dildo_01" }`. This is a valid state if the engine's positional logic determines that the character's `Stance` and the component's `capacity` allow for it.

        *   **Sub-Component State Propagation:** The state of a sub-component directly affects the availability of its parent. The `Encounter_Engine` is responsible for checking the full hierarchy to get a complete picture of a component's status.
            *   **Example (Sounding and Handjob):** A `penis` component has a `urethra` sub-component.
                1.  An actor (`Actor_A`) uses a sound on the character's `urethra`. The `urethra`'s `in_use_by` list is populated: `[ { agent: "Actor_A", tool: "sound_01" } ]`.
                2.  Now, the **same actor** (`Actor_A`) wishes to also give a handjob to the parent `penis` component.
                3.  The engine validates this new action. It checks the `penis` component's own `in_use_by` list (which is empty) and then also checks the `in_use_by` list of its sub-components.
                4.  The engine's positional logic determines that an external `FRICTION` action (the handjob, using `Actor_A`'s hand) is not in conflict with the ongoing internal `PENETRATION` action on the `urethra` (using the sound). The fact that the agent is the same is irrelevant to the physical compatibility check.
                5.  The action is valid. The `penis` component's `in_use_by` list is now populated: `[ { agent: "Actor_A", tool: "hand_01" } ]`.
                6.  The result is a complex, simultaneous state that the system correctly models: the `penis` is actively being stimulated by the actor's hand, while its `urethra` sub-component is simultaneously being stimulated by a sound held by the same actor.

#### **4.4: The `sub_components` Dictionary**
This dictionary allows for the creation of a direct, physical hierarchy, modeling parts that are intrinsically linked to a parent component.
*   **Purpose:** To contain other `Structural_Component` objects that are dependent on the parent component.
*   **Logic:** This creates a clear and unbreakable anatomical link. A `breasts` component, for example, will contain a `nipples` sub-component. A `mouth` component will contain a `tongue` sub-component.
*   **Engine Interaction:** The engine can target sub-components directly via their parent (e.g., `{ target_component: "breasts_01", target_sub_component: "nipples" }`). The engine's positional logic will determine how the state of a parent component (like being `in_use_by`) affects the accessibility and availability of its sub-components.

---

### **Section 5: The Trait System (Composition over Inheritance)**

The power and flexibility of the Universal Zone-Component System come from its compositional nature. A `Structural_Component` is not a monolithic, hard-coded object; it is a simple container whose function, properties, and even sub-components are defined by the modular, reusable **`Traits`** it is composed of.

#### **5.1: Design Philosophy**

The Trait system is the definitive "single source of truth" for all shared anatomical properties and functions. Instead of defining the properties for a "penis" and a "tentacle" separately and duplicating data, we define granular Traits like `Is_Appendage` and `Can_Penetrate`. A component is then built by simply inheriting the list of Traits that accurately describe it.

This approach provides three key benefits:
1.  **Efficiency:** We define a property like `size` or a capability like `PENETRATION` only once, within a single Trait. Any component that needs it simply inherits that Trait.
2.  **Consistency:** All components that share a Trait are guaranteed to have the same core set of properties and functions, which makes the engine's logic predictable and robust.
3.  **Flexibility:** Creating new and unique body parts, for characters or aliens, becomes a simple matter of composing a new combination of existing, simple Traits.

#### **5.2: The Trait Data Structure**

A `Trait` is a blueprint, stored in the `Core_Data_Library.md`, that acts as a package of data to be stamped onto a `Structural_Component`. A single Trait can contain any or all of the following:

*   **`properties`:** A block of semi-permanent properties and their default starting values that this Trait grants to a component.
*   **`capabilities`:** A list of `Capability` tags that this Trait adds to a component's capabilities list.
*   **`receptivities`:** A list of `Receptivity` tags that this Trait adds to a component's receptivities list.
*   **`sub_components`:** A rule for creating one or more default sub-components within the component.

#### **5.3: The Core `Capability` and `Receptivity` Tags**

These five pairs of tags form the fundamental vocabulary for all physical interaction in the game. The meaning of a tag is determined by whether it is in a component's `capabilities` or `receptivities` list.

| Tag | As a Capability (in the `capabilities` list) | As a Receptivity (in the `receptivities` list) |
| :--- | :--- | :--- |
| **`PENETRATION`** | Defines a component that can be used to penetrate. | Defines a component that can receive penetration. |
| **`MANIPULATION`** | Defines a component that can be used to touch, hold, grope, or restrain. | Defines a component that can be touched, held, groped, or restrained. |
| **`FRICTION`** | Defines a component that can be used to rub against a surface for stimulation. | Defines a component that can be rubbed against for stimulation. |
| **`ENCLOSURE`** | Defines a component that can be used to surround, squeeze, or constrict. | Defines a component that can be surrounded, squeezed, or constricted. |
| **`IMPACT`** | Defines a component that can be used to strike a surface. | Defines a component that can be struck. |

#### **5.4: The Trait Library (Examples)**
This section provides a conceptual look at how granular, atomic `Traits` are constructed and then composed to build a complex component. The full, exhaustive library of all Traits will be maintained in `Core_Data_Library.md`.

**Part 1: The Library of Granular Traits**

These are the simple, reusable "Lego bricks" of the system.

*   **Trait: `Is_Orifice`**
    *   **Purpose:** Defines the component as a cavity.
    *   **Grants:** `Feature_Type: "Orifice"`.

*   **Trait: `Is_Appendage`**
    *   **Purpose:** Defines the component as an appendage.
    *   **Grants:** `Feature_Type: "Appendage"`.

*   **Trait: `Can_Penetrate`**
    *   **Purpose:** Grants the ability to perform penetrative acts.
    *   **Grants:**
        *   `capabilities`: Appends `PENETRATION`.
        *   `properties`: `size`, `girth`, `firmness`, `shape`.

*   **Trait: `Is_Receptive_To_Penetration`**
    *   **Purpose:** Grants the ability to receive penetration.
    *   **Grants:**
        *   `receptivities`: Appends `PENETRATION`.
        *   `properties`: `capacity`, `depth`, `elasticity`.

*   **Trait: `Is_Erogenous`**
    *   **Purpose:** Makes a component sensitive to sexual touch.
    *   **Grants:**
        *   `properties`: `sensitivity`.
        *   `receptivities`: Appends `MANIPULATION`, `FRICTION`.

*   **Trait: `Has_Muscles`**
    *   **Purpose:** Grants the ability to actively squeeze or grip.
    *   **Grants:**
        *   `properties`: `muscle_control`.
        *   `capabilities`: Appends `ENCLOSURE`.

*   **Trait: `Has_Sub_Component_Clitoris`**
    *   **Purpose:** Adds a clitoris sub-component.
    *   **Grants:**
        *   `sub_components`: Adds a `clitoris` entry, which is a `Structural_Component` composed of Traits like `Is_Erogenous` and `Is_Appendage`.

**Part 2: Composition in Action**

A designer builds a complex component not by picking a big, pre-made package, but by composing a list of these small, granular Traits.

**Conceptual Build of a `vagina` Component Blueprint:**
*   **A designer would specify the following `Traits` list for the blueprint:**
    *   `"Is_Orifice"`
    *   `"Is_Receptive_To_Penetration"`
    *   `"Is_Erogenous"`
    *   `"Has_Muscles"`
    *   `"Has_Sub_Component_Clitoris"`
    *   `"Has_Sub_Component_Urethra"`
    *   `"Can_Self_Lubricate"`
    *   `"Can_Ejaculate"`

*   **The Resulting Component:** When the game creates a `vagina` component from this blueprint, it iterates through this list of Traits. It merges all the granted `properties`, concatenates all the `capabilities` and `receptivities` lists, and builds the specified `sub_components`. The final, fully-formed component is a complete, complex, and functional body part, built entirely from simple, reusable pieces.

#### **5.5: Integration with the Psychological Engine**

The `Traits` system, specifically the `capabilities` and `receptivities` it grants, is a primary input for an entity's `Psychology System` during its decision-making process. The AI is responsible for using this data to ensure the actions it proposes are both physically possible and logically sound.

**AI Feasibility Check (Sanity Checking):**
Before an AI's **Decision Engine** calculates the `Urgency Score` for a potential action, it performs a crucial feasibility check. This "sanity check" ensures the AI does not waste processing on or propose impossible actions to the `Encounter_Engine`.

The process is as follows:

1.  **Goal & Verb Selection:** The AI determines its high-level goal and the general "verb" of the action it wants to perform (e.g., "Penetrate," "Manipulate").

2.  **Tool & Target Validation:** The AI then scans the available components (both its own and the target's) to find a valid pairing for that verb. This involves two key checks:
    *   **Capability Check:** Does the chosen `tool` component (e.g., its own `clitoris_01`) have the required `Capability` tag in its `capabilities` list (e.g., `PENETRATION`)?
    *   **Receptivity Check:** Does the chosen `target` component (e.g., the target's `vagina_01`) have the required `Receptivity` tag in its `receptivities` list (e.g., `PENETRATION`)?

3.  **Property Threshold Check:** If the tags are compatible, the AI performs a final check against the component `properties` to ensure the action is practically feasible.
    *   **Example (Size):** For a `PENETRATION` action, the AI will check if the `tool` component's `size` property meets or exceeds the game's global `minimum_penetration_threshold`. If `clitoris_01.properties.size` is 1 and the threshold is 2, the AI recognizes the action is physically impossible and discards it.
    *   **Example (State):** The AI will also check the current `states` of the components. If it wants to use its `hands`, but `hands.states.in_use_by` is not `null`, it knows its hands are busy and discards actions requiring them.

Only after an action has passed all of these internal feasibility checks will the AI consider it a valid candidate for `Urgency Score` calculation. This ensures that the `IntentPacket` sent to the `Encounter_Engine` is always for an action that is, to the best of the AI's knowledge, conceptually, mechanically, and physically possible in the current game state.

---

### **Section 6: The Systemic Profiles in Detail**

Alongside its `Structural Profile` of physical components, every entity possesses a collection of `Systemic Profiles`. These are distinct, top-level objects that model the entity's non-physical, background systems. They provide the core mechanical stats and passive capabilities that influence the entity's state and actions.

#### **6.1: The `Frame` Systemic Profile**

*   **Purpose:** To define the core physical statistics and descriptive tags of the entity's entire body frame.

*   **Detailed Structure:**

    *   **`height` (Integer):**
        *   **Description:** The entity's height in centimeters.
        *   **Mechanical Use:** A factor in positional logic and determining reach.

    *   **`muscle_tone` (Magnitude):**
        *   **Description:** A value on the `Magnitude` scale (1-10+) representing the visual definition of the entity's musculature. This is a primarily descriptive property.
        *   **Mechanical Use:** Serves as a primary input for calculating the `derived_build_type`.

    *   **`body_fat` (Magnitude):**
        *   **Description:** A value on the `Magnitude` scale (1-10+) representing the percentage and distribution of the entity's body fat. This is a primarily descriptive property.
        *   **Mechanical Use:** Serves as a primary input for calculating the `derived_build_type`.

    *   **`flexibility` (Magnitude):**
        *   **Description:** A value on the `Magnitude` scale (1-10+) representing the entity's physical pliability.
        *   **Mechanical Use:** A critical modifier for checks related to positioning, escaping restraints, and performing complex sexual acts. A high `flexibility` may allow a character to access zones that would otherwise have `Partial` or `Obstructed` accessibility.

    *   **`derived_build_type` (String):**
        *   **Description:** A narrative tag that is automatically calculated based on the interplay of `muscle_tone` and `body_fat`.
        *   **Mechanical Use:** Serves as a key descriptor for the `Psychology System`. A Subject with a `Fixation` on a specific body type will use this tag for target assessment.
        *   **Examples:** "Slender," "Average," "Athletic," "Voluptuous," "Hulking."

    *   **`derived_mass` (Integer):**
        *   **Description:** The entity's approximate mass in kilograms, automatically calculated from `height`, `muscle_tone`, and `body_fat`.
        *   **Mechanical Use:** Used by the engine for resolving physics-based actions like tackling or shoving where mass is a key factor.

#### **6.2: The `Senses` Systemic Profile**

*   **Purpose:** To model an entity's ability to perceive the world. This profile is the central hub for all sensory information, defining both the baseline effectiveness of each sense and any special, supernatural, or deficient capabilities. The game's engines query this profile for all perception-based checks and to determine an AI's situational awareness.

*   **Detailed Structure:** The profile is a dictionary of objects, one for each sense. Each sense is primarily defined by its `acuity` (its raw effectiveness) and a list of `tags` (any special qualities).

    *   **`vision`:**
        *   **`acuity` (Magnitude):** The entity's overall visual sharpness and ability to notice details. This is the primary value used for visual perception checks. (e.g., 3=Impaired/Myopic, 5=Normal Human, 7=Eagle-eyed, 10+=Supernatural).
        *   **`tags` (List of Strings):** A list of any special visual capabilities or deficiencies.
            *   *Examples: `["Low_Light_Vision"]` (negates penalties in dim light), `["Night_Vision"]` (negates penalties in darkness), `["Thermal_Vision"]`, `["Colorblind_Monochrome"]` (a negative tag).*

    *   **`hearing`:**
        *   **`acuity` (Magnitude):** The entity's ability to detect and distinguish sounds. Used for auditory perception checks. (e.g., 3=Hard of Hearing, 5=Normal, 7=Acute, 10+=Supernatural).
        *   **`tags` (List of Strings):** Special auditory capabilities.
            *   *Examples: `["Echolocation"]`, `["Sensitive_To_High_Frequency"]`.*

    *   **`scent`:**
        *   **`acuity` (Magnitude):** The entity's ability to detect faint or complex smells. Used for scent-based perception and tracking checks. (e.g., 1=Anosmic, 3=Normal Human, 5=Sensitive, 10+=Bloodhound).
        *   **`tags` (List of Strings):** Special olfactory capabilities. The `Pheromone_Analysis` tag is critical, as it unlocks the ability to interpret the meaning behind pheromonal signals, rather than just detecting them.
            *   *Examples: `["Pheromone_Analysis"]`, `["Scent_Tracker"]`.*

    *   **`touch`:**
        *   **`sensitivity` (Sensitivity):** The entity's general responsiveness to tactile stimuli. This acts as a global modifier for arousal gain from `MANIPULATION` and `FRICTION` actions. (e.g., 1=Numb, 3=Normal, 5=Hypersensitive).
        *   **`pain_threshold` (Sensitivity):** The entity's baseline resistance to pain. A low threshold means the entity is more susceptible to pain-based effects and intimidation.

    *   **`taste`:**
        *   **`acuity` (Magnitude):** The entity's ability to analyze substances through taste. This is used for specific investigation actions, like identifying a chemical compound.

    *   **`special`:**
        *   **`tags` (List of Strings):** This is the home for any transcendent or corrupted senses that defy normal classification.
            *   *Example: `["Synesthesia_Audio_Visual"]` (experiences sounds as colors), `["Psychic_Awareness"]` (can sense conscious minds nearby).*

#### **6.3: The `Chemistry` Systemic Profile**

*   **Purpose:** To model the entity's complete biochemical state. This profile is the single source of truth for all mechanics related to scents, pheromones, cyclical urges, and reproductive signals. It is a primary driver for the `Psychology System` and is frequently read by the `Encounter_Engine`'s Proximity Effects phase.

*   **Detailed Structure:** The profile is a collection of nested objects, each modeling a specific subsystem.

    *   **`base_scent_profile`:** Defines the entity's constant, passive scent for narrative description.
        *   **`primary_note` (String):** The most dominant or recognizable scent note (e.g., "Ozone," "Lilac," "Musk").
        *   **`secondary_note` (String):** A subtle undertone that adds complexity (e.g., "Petrichor," "Cinnamon," "Brine").
        *   **`intensity` (Magnitude):** How powerfully the base scent projects into the immediate area.

    *   **`pheromone_system`:** Models the entity's active, mechanically-relevant chemical signals.
        *   **`production_potency` (Magnitude):** The entity's baseline, innate strength for all pheromonal broadcasts.
        *   **`receptivity` (Sensitivity):** How strongly the entity is affected by the pheromones of others. This acts as a resistance or vulnerability modifier against proximity effects.
        *   **`current_broadcast` (Object):** The specific signal the entity is actively emitting right now. This is the primary data used for proximity effects.
            *   **`type` (String):** The nature of the signal being broadcast (e.g., "Arousal," "Fear," "Aggression," "Territorial," or "None").
            *   **`intensity` (Magnitude):** The final, calculated strength of the current broadcast (e.g., `production_potency` + bonus from a `Heat Cycle`).

    *   **`reproductive_system`:** Models all signals and states related to fertility and breeding.
        *   **`cycle_type` (String):** The nature of the entity's reproductive cycle (e.g., "Heat," "Rut," "Spawning," "Pollination").
        *   **`cycle_state` (String):** The current phase of the cycle ("None," "Building," "Peak," "Waning").
        *   **`cycle_intensity` (Magnitude):** The strength of the cycle's **internal** psychological and physical effects on the entity itself. This is a major driver for the `Psychology System`.
        *   **`fertility_display` (Magnitude):** How "visibly" fertile the entity appears (e.g., swollen features, glowing markings). This is a passive, visual signal.
        *   **`allure_modifier` (Magnitude):** The entity's esoteric, non-pheromonal "X-factor" for supernatural attraction.
        *   **`can_mark_territory` (Boolean):** A flag indicating if the entity has the ability to leave persistent scent marks in the environment.

    *   **`systemic_rates`:** Defines core biochemical rates of change.
        *   **`refractory_rate` (Magnitude):** Governs the speed of physiological and psychological recovery after climax.
        *   **`chemical_resistance` (Magnitude):** Governs resistance to non-pheromonal chemical agents like drugs or poisons.

    *   **`derived_breeding_appeal` (Magnitude):** This is a calculated, top-level value that represents the entity's total reproductive "signal strength." It is the sum of their `fertility_display`, `allure_modifier`, and any bonuses from their `pheromone_broadcast` and `cycle_state`. This is the single value queried by an observer's `Psychology System` (Character or Subject) to assess desirability and reproductive readiness.

---

### **Section 7: Overarching Mechanics**

This section details the global, engine-level mechanics that act upon the data defined in the previous sections. These are universal rules that govern complex physical interactions for all entities.

#### **7.1: Size Mismatch & Accommodation Mechanics**

The **Resonance Adaptation Field** that permeates the facility allows characters to survive physically impossible interactions, but this protection is not without significant cost and consequence. This system governs the outcomes when a `Structural_Component` with a `size` property attempts to interact with a component with a `capacity` property.

The `Encounter_Engine` calculates the **Size Differential** for the interaction (`capacity - size`). A significant negative differential (where the penetrating or enclosed object is much larger than the receiving component's capacity) triggers the following graduated consequences.

##### **Graduated Consequence System**

*   **Extreme Mismatch (Differential ≤ -5):**
    *   **Immediate Effect:** The target suffers major `Vitality` damage.
    *   **Status Effect:** Applies the **"Severe Trauma"** status, which inflicts multiple, significant penalties to physical actions and may cause ongoing damage for a long duration.
    *   **Narrative:** The `Narrative_Engine` will describe the Resonance Field working overtime to prevent catastrophic tissue damage, often with unsettling visual or sensory cues.

*   **Severe Mismatch (Differential -4 to -3):**
    *   **Immediate Effect:** The target suffers moderate `Vitality` damage.
    *   **Status Effect:** Applies the **"Stretched"** status, which inflicts penalties to movement and actions involving the affected `Zone`.

*   **Moderate Mismatch (Differential -2 to -1):**
    *   **Immediate Effect:** The target suffers minor `Vitality` damage.
    *   **Status Effect:** Applies the **"Sore"** status, which can cause minor penalties and social discomfort, and may be a source of `Arousal Pressure` for characters with a masochistic `Eroticism Profile`.

##### **The "Accommodation Trauma" Status Effect**
This is a special, multi-stage status effect that can be applied by a Severe or Extreme Mismatch, representing the body's horrifying adaptation process.
*   **Stage 1 - "Raw" (Short Duration):** The affected component is highly vulnerable, inflicting significant action penalties and a continuous minor `Vitality` drain.
*   **Stage 2 - "Tender" (Medium Duration):** Penalties lessen, but the component becomes hypersensitive, potentially doubling `Arousal` gain or `Stability` loss from interactions.
*   **Stage 3 - "Adapted" (Resolution):** All penalties fade. The `properties` block of the affected `Structural_Component` is now **permanently modified**: its baseline `capacity` is increased by 1. This represents a fundamental, corrupting alteration of the body's natural limits—the horror of "getting used to it."

##### **Subject-Specific Variations**
A Subject's unique nature can alter these consequences. For example, a Biological Subject might apply a secretion that reduces the initial `Vitality` damage but accelerates the "Accommodation Trauma" process, hastening the permanent change.

#### **7.2: Positional Logic & Accessibility Calculation**

An action's validity is not just determined by the `Capabilities` and `Receptivities` of the components involved. The `Encounter_Engine` must also determine if the action is **physically possible** given the current positions, stances, and ongoing interactions of all entities in the encounter. This is handled by the **Accessibility Calculation**.

##### **Design Philosophy**

Accessibility is not a static property of a component; it is a **dynamic state calculated by the engine for each potential interaction.** The accessibility of a character's `"Groin"` zone is different for an actor standing in front of them versus one standing behind them. This system allows for a fluid and realistic simulation of physical positioning without requiring a complex physics engine.

##### **The Accessibility Calculation Process**

Before an entity's `Psychology System` is presented with a list of actions, or before a player's choice is finalized, the `Encounter_Engine` performs this calculation for any action targeting a specific `Zone`.

1.  **Context Gathering:** The engine gathers the critical positional data:
    *   The `Stance` of the actor (e.g., `Standing`, `Kneeling`, `Prone`).
    *   The `Stance` of the target.
    *   The relative positioning of the actor to the target (e.g., `Front`, `Rear`, `Side`).
    *   The `in_use_by` lists of all components on both the actor and the target.

2.  **Rule Application:** The engine consults a library of **Positional Logic Rules**. These rules are a series of "if-then" statements that translate the context into an accessibility state.
    *   *Rule Example 1:* `IF Target_Stance is "Prone" AND Actor_Position is "Front", THEN Target_Zone "Torso_Back" Accessibility is "Obstructed".`
    *   *Rule Example 2:* `IF Target_Component "thighs" is in_use_by an "ENCLOSURE" action, THEN Target_Zone "Groin_Pubis" Accessibility is "Partial".`

3.  **State Assignment:** Based on the rules, the engine assigns one of the following `Accessibility` states to the target `Zone` *for that specific actor and action*:

##### **The Three Accessibility States**

*   **`Full`:** The `Zone` is completely accessible. Actions targeting it can be attempted without penalty.
*   **`Partial`:** The `Zone` is difficult to reach or interact with due to positioning. Actions targeting it are still possible but will incur a penalty (e.g., -1 die or a reduced die size or reduced climax gain).
*   **`Obstructed`:** The `Zone` is physically blocked or otherwise completely inaccessible to the actor from their current position. All actions targeting this `Zone` are invalid and will not be available for selection.

##### **Integration and Outcome**

The result of this calculation directly informs the game loop. An autonomous AI's `Psychology System` will receive a list of actions that has already been filtered by this logic, preventing it from attempting physically impossible actions. A player will see obstructed or penalized options grayed out or marked accordingly in their interface.

This system ensures that the complex, multi-entity interactions in an encounter are always grounded in a logical and believable physical reality.

---

### **Appendix A: Structural Templates**

This appendix provides conceptual, verbose examples of how the Universal Zone-Component System is used to build a complete entity. These "Structural Templates" serve as a starting point for entity creation.

*Designer's Note: The specific `Traits` listed and the exact number of `Zone`s are illustrative examples. The definitive, exhaustive lists of all `Zone`s, `Sub-Zone`s, `Component` Blueprints, and `Traits` will be maintained in the `Core_Data_Library.md`.*

---

### **Appendix A: Structural Templates**

This appendix provides conceptual, verbose examples of how the Universal Zone-Component System is used to build a complete entity. These "Structural Templates" serve as a starting point for entity creation.

*Designer's Note: The specific `Traits` listed and the exact number of `Zone`s are illustrative examples. The definitive, exhaustive lists of all `Zone`s, `Sub-Zone`s, `Component` Blueprints, and `Traits` will be maintained in the `Core_Data_Library.md`.*

---
#### **A.1: Template_Humanoid_Female**

This template represents a baseline human female, serving as the starting point for a player character or companion.

##### **Systemic Profiles:**

*   **`Frame`:** Contains baseline human values for `height`, `muscle_tone`, `body_fat`, and `flexibility`. The `derived_build_type` is "Average."
*   **`Senses`:** Contains baseline human values for all sensory acuities, with no special tags.
*   **`Chemistry`:** Contains baseline human values for pheromones and resistances, with the `cycle_state` set to "None."

##### **Structural Profile:**

*   **Zone: `Head`**
    *   **Components:**
        *   **`hair_head_01`:** A `Structural_Component` composed of `Traits` like `Is_Hair`. Its `properties` define its default color, length, texture, and style. Its `receptivities` include `MANIPULATION`.
        *   **`eyes_01`:** A `Structural_Component` whose `properties` define color.
        *   **`mouth_01`:** A `Structural_Component` composed of `Traits` such as `Is_Orifice`, `Is_Erogenous`, and `Has_Sub_Component_Tongue`.
            *   **Sub-Component: `tongue`:** This nested component is composed of `Traits` like `Is_Appendage` and `Can_Manipulate`.

*   **Zone: `Torso`**
    *   **Sub-Zone: `Torso_Neck`**
        *   **Components:**
            *   **`neck_01`:** A `Structural_Component` composed of `Traits` that grant it `receptivities` for `MANIPULATION` and `ENCLOSURE`, and a `property` flagging it as a `vital_point`.
    *   **Sub-Zone: `Torso_Chest`**
        *   **Components:**
            *   **`breasts_01`:** A `Structural_Component` composed of `Traits` like `Is_Fleshy_Mound`, `Is_Erogenous`, and `Has_Sub_Component_Nipples`. Its `properties` define `size`, `firmness`, etc.
                *   **Sub-Component: `nipples`:** Composed of the `Is_Erogenous_Node` Trait, giving it extremely high `sensitivity`.
    *   **Sub-Zone: `Torso_Abdomen`**
        *   **Components:**
            *   **`abdomen_01`:** A `Structural_Component` representing the surface of the stomach and navel, with `receptivities` for `MANIPULATION` and `FRICTION`.
    *   **Sub-Zone: `Torso_Back`**
        *   **Components:**
            *   **`back_01`:** A `Structural_Component` for the surface of the back.

*   **Zone: `Arms`**
    *   **Components:**
        *   **`hands_01`:** A `Structural_Component` composed of a suite of powerful `Traits` granting it `capabilities` for `MANIPULATION`, `ENCLOSURE`, `FRICTION`, `IMPACT`, and `PENETRATION` (representing fingers).

*   **Zone: `Hips`**
    *   **Components:**
        *   **`buttocks_01`:** A `Structural_Component` composed of `Traits` granting it `receptivities` for `IMPACT`, `MANIPULATION`, and `FRICTION`, and a `capability` for `ENCLOSURE`. Its `properties` define its `size` and `shape`.

*   **Zone: `Groin`**
    *   **Sub-Zone: `Groin_Pubis`**
        *   **Components:**
            *   **`vagina_01`:** A `Structural_Component` composed of Traits like `Is_Receptive_Orifice`, `Is_Erogenous`, `Has_Muscles`, and `Has_Sub_Component_Clitoris`.
                *   **Sub-Component: `clitoris`:** Composed of the `Is_Erogenous_Node` and `Can_Penetrate` Traits. *Designer's Note: The `Can_Penetrate` capability is only practically usable if corruption increases its `size` property beyond the minimum threshold.*
            *   **`hair_pubic_01`:** A `Structural_Component` for pubic hair.
            *   **`urethra_01`:** A `Structural_Component` composed of Traits like `Is_Receptive_Orifice` (with a very small `capacity`) and `Is_Erogenous`.
    *   **Sub-Zone: `Groin_Anal`**
        *   **Components:**
            *   **`anus_01`:** A `Structural_Component` composed of `Traits` like `Is_Receptive_Orifice` and `Has_Muscles`.

*   **Zone: `Legs`**
    *   **Components:**
        *   **`thighs_01`:** A `Structural_Component` with the `capability` for `ENCLOSURE` and `receptivities` for `MANIPULATION` and `FRICTION`.
        *   **`feet_01`:** A `Structural_Component` with `receptivities` for `MANIPULATION`.

---
#### **A.2: Template_Subject_Den_Mother**

This template demonstrates how a unique Subject is created by starting with a standard `Structural_Template` and then applying a series of modifications. This process of addition, removal, and alteration of components and Traits is the core of Subject design.

##### **Base Template:** `Template_Humanoid_Female`

##### **Systemic Profile Modifications:**

*   **`Frame`:** The `muscle_tone` and `height` properties are significantly increased from the human baseline.
*   **`Senses`:** The `scent.acuity` property is dramatically increased, and the `["Scent_Tracker"]` and `["Pheromone_Analysis"]` tags are added.
*   **`Chemistry`:** The `pheromone_system.production_potency` is increased. The `current_broadcast.type` frequently defaults to `"Territorial"` or `"Dominance"`. A new `reproductive_system.cycle_type` of `"Rut"` is added.

##### **Structural Profile Modifications:**

*   **Zone: `Head`**
    *   **Modified Component: `mouth_01`**
        *   The base `mouth` component's `Traits` are augmented with `Can_Strike`.
        *   Its `properties` are altered to reflect a more bestial muzzle, with `jaw_strength` increased and `teeth_type` changed to `"Carnivore"`.
    *   **Added Component: `ears_canine_01`**
        *   A new `Structural_Component` is added to this zone, composed of Traits that grant it high `hearing.acuity`.

*   **Zone: `Torso`**
    *   **Modified Component (within `Torso_Chest`): `breasts_01`**
        *   The `properties` of the breasts are altered to reflect a more maternal, multi-nippled configuration appropriate for a pack animal, potentially increasing the number of `nipples` sub-components.

*   **Zone: `Arms`**
    *   **Modified Component: `hands_01`**
        *   This component's `Traits` are augmented or replaced to change its `properties`. The `impact_type` for its `IMPACT` capability is changed to `"Sharp"`, and a `texture: "Clawed"` property is added.

*   **Zone: `Groin`**
    *   **Sub-Zone: `Groin_Pubis`**
        *   **Removed Component:** The `vagina_01` component from the base template is removed.
        *   **Modified Component:** The `clitoris` sub-component is moved out, promoted to a root-level component, and heavily modified (see `pseudopenis_01` below).
    *   **Sub-Zone: `Groin_Scrotal` (New for this template)**
        *   *This new Sub-Zone is added to house the new primary genital structure.*
        *   **Added Component: `pseudopenis_01`**
            *   This new `Structural_Component` is the result of the heavily modified `clitoris`. It is composed of `Traits` like `Is_Appendage`, `Can_Penetrate`, and `Is_Erogenous`, as well as unique, monstrous traits like `Has_Knot` and `Has_Barbs`.
            *   Its `properties` (`size`, `girth`, etc.) are set to supernatural levels.
            *   It contains its own `urethra` sub-component.

*   **Zone: `Hips`**
    *   **Added Component: `tail_canine_01`**
        *   A new `Structural_Component` is added to this zone, composed of Traits that give it `capabilities` for `IMPACT` and expressive `MANIPULATION`.

*   **General Modification:** `Structural_Component`s across many zones, like `back_01` and `legs_01`, would have their `properties` updated to reflect partial fur coverage.