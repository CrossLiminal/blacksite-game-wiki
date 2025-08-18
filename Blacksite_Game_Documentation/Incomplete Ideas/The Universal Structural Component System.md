# **The Universal Structural Component System**

### **1. System Overview & Design Philosophy**

This document outlines the **Universal Structural Component System**, a unified framework for defining the physical (or quasi-physical) form of any entity in the game, from human Characters to alien Subjects and even corporeal Hazards like Processed Personnel.

The core philosophy is built on three key principles:

1.  **Universal Integration:** A single, consistent component architecture is used for all entities. This dramatically simplifies the `Core_Encounter_Engine`'s logic, as it only needs to understand one "language" for physical interaction, regardless of whether it's resolving a kiss between two characters or an attack from a tentacled horror.
2.  **Modular Flexibility:** An entity's form is described as a collection of modular components. This allows for the representation of anything from a standard human body to a non-corporeal psychic presence, all using the same foundational building blocks.
3.  **Function over Form:** The system prioritizes defining what a component *does* and what *can be done to it* over rigid anatomical labels. This provides the flexibility needed to handle a vast range of physical and sexual interactions in a logical, rules-based manner.

An entity's complete physical description—be it a Character's **`Anatomy Profile`** or a Subject's **`Manifestation Profile`**—is simply a collection of the components defined in this system.

### **2. The Component Family**

An entity's form is defined by a collection of components from three distinct, function-specific types.

#### **2.1 `Descriptive_Component`**
*   **Purpose:** The Psychology & Narrative Layer. These components provide flavor, descriptive detail, and high-level information for the `Psychology System` and `Narrative_Engine`. They are not directly targetable in encounters.
*   **Structure:** Contains an `ID` (e.g., `hair_01`) and a `properties` dictionary for descriptive tags (e.g., `hair_color: "Blonde"`, `voice_pitch: "Husky"`, `skin_texture: "Smooth"`).
*   **Character Examples:** `Build`, `Skin`, `Hair`, `Voice`.
*   **Subject Examples:** `Aura`, `Resonance_Field`, `Psychic_Signature`.

#### **2.2 `Systemic_Component`**
*   **Purpose:** The Internal State Layer. These components model an entity's internal, systemic functions that have a passive or active effect on the world.
*   **Structure:** Contains an `ID` (e.g., `chemistry_01`) and a `properties` dictionary for mechanical values (e.g., `pheromone_production: 4`, `heat_cycle_state: "Peak"`, `sensory_acuity: 5`).
*   **Character Examples:** `Chemistry`, `Senses`, `Breeding_Signals`.
*   **Subject Examples:** `Pollen_System`, `Psychic_Monitoring_Field`.

#### **2.3 `Interactive_Component`**
*   **Purpose:** The Direct Interaction Layer. These are the "nouns" of the `Core_Encounter_Engine`—the physical (or quasi-physical) points on an entity that can be targeted by an action. This is the most complex and important component type.
*   **Structure:** Contains the full suite of fields needed for encounter resolution. These are detailed in the next section.

### **3. The `Interactive_Component` in Detail**

This component is the heart of all physical gameplay. It is defined by its inherent characteristics (`properties`) and its temporary conditions (`states`).

#### **Core Descriptors**

*   **`ID`:** A unique, queryable identifier (e.g., `mouth_01`, `reproductive_vine_A`).
*   **`Zone`:** The broad region of the entity where the component is located. This is used for high-level AI targeting and for resolving area-of-effect interactions like clothing coverage (e.g., `Oral`, `Chest`, `Appendages`, `Core`).
*   **`Feature_Type`:** A simple, high-level "noun" tag used for AI categorization and quick identification (e.g., `Orifice`, `Appendage`, `Mound`).

#### **`properties`: Inherent Characteristics**
These are the semi-permanent, defining traits of the component. They change rarely, typically only through permanent corruption.

*   **`name`:** The human-readable name of the component (e.g., "Mouth", "Clawed Hand").
*   **`capacity`:** A `Magnitude` scale value representing how much the component can accommodate.
*   **`size`:** A `Magnitude` scale value representing the component's own dimensions.
*   **`sensitivity`:** A `Sensitivity` scale value for responsiveness to stimuli.
*   **Other Properties:** A flexible list including `material`, `shape`, `texture`, etc.

#### **`states`: Temporary Conditions**
These are volatile conditions that change frequently during gameplay.

*   **`exposure_state`:** The component's current level of coverage (`Covered`, `Partially_Exposed`, `Fully_Exposed`).
*   **`condition`:** The component's current status (`Normal`, `Sore`, `Damaged`, `Numb`, etc.).
*   **`in_use_by`:** Tracks if the component is currently occupied in an interaction.

#### **The Action Framework: `Capabilities` and `Receptivities`**

This is the core mechanic that allows for flexible and logical interaction. For an action to be valid, the actor's component must have the required `capability` and the target's component must have the corresponding `receptivity`.

*   **`capabilities` (List of Tags):** Describes the actions this component can **perform**.
    *   *Examples: `Can_Manipulate` (for hands, tongues), `Can_Penetrate` (for penises, fingers, vines), `Can_Enclose` (for hands, thighs), `Can_Stimulate_Frottage` (for most skin surfaces).*
*   **`receptivities` (List of Tags):** Describes the actions that can be **done to this component**.
    *   *Examples: `Is_Receptive_To_Penetration`, `Is_Receptive_To_Manipulation`, `Is_Receptive_To_Frottage`.*

*Designer's Note: The master lists of all valid `Zone`s, `Feature_Type`s, `Capabilities`, and `Receptivities` are maintained in the project's data libraries.*

### **4. Size Mismatch & Accommodation Mechanics**

The **Resonance Adaptation Field** allows characters to survive physically impossible interactions, but not without consequence. When an `Interactive_Component` with a `size` property attempts to interact with a component with a `capacity` property, the engine calculates the **Size Differential** (`capacity - size`). A negative differential triggers the following graduated consequences.

#### **Graduated Consequence System**

*   **Extreme Mismatch (Differential ≤ -5):**
    *   **Immediate Effect:** Major `Vitality` damage.
    *   **Status Effect:** Applies the **"Severe Trauma"** status, inflicting multiple penalties for a long duration.
    *   **Narrative:** The Resonance Field is described as working overtime to prevent catastrophic tissue damage.
*   **Severe Mismatch (Differential -4 to -3):**
    *   **Immediate Effect:** Moderate `Vitality` damage.
    *   **Status Effect:** Applies the **"Stretched"** status, inflicting penalties to movement and related actions.
*   **Moderate Mismatch (Differential -2 to -1):**
    *   **Immediate Effect:** Minor `Vitality` damage.
    *   **Status Effect:** Applies the **"Sore"** status, causing minor penalties and social discomfort.

#### **The "Accommodation Trauma" Status Effect**
This is a special, multi-stage status effect that can be applied by a Severe Mismatch. It represents the body's horrifying adaptation process.
*   **Stage 1 - "Raw" (Short Duration):** Significant action penalties and a continuous minor `Vitality` drain.
*   **Stage 2 - "Tender" (Medium Duration):** Moderate penalties and hypersensitivity to stimuli.
*   **Stage 3 - "Adapted" (Resolution):** Penalties fade. The component's baseline `capacity` property is **permanently increased by 1**, representing a corruption of the body's natural limits. This creates the horror of "getting used to it."

#### **Subject-Specific Variations**
The nature of a Subject can alter these consequences. For example, a Biological Subject might apply a secretion that reduces the `Vitality` damage but increases the rate of permanent `capacity` change, accelerating the accommodation process.

This universal system is simple for the game engine to parse, yet flexible enough to define any entity, ensuring all physical interactions in *Beware the Blacksite* are governed by a single, robust, and logical set of rules.

---

### **The "Structural Templates" System** - For `Core_Data_Library.md`

**Core Concept:** A Structural Template is a pre-defined collection of `Interactive_Component` `Systemic_Component` and `Descriptive_Component` objects that represents a common body plan or form. When creating a new entity, a designer can choose to start with a template, which pre-populates the `Anatomy/Manifestation Profile` with a standard, logical set of components and zones. The designer is then free to **customize** this template by adding new components, removing existing ones, or altering their properties.

**Why This is a Great Idea:**

1.  **Massive Efficiency:** Instead of defining a head, torso, two arms, and two legs from scratch for every humanoid, the designer can just select the "Humanoid" template. This saves a huge amount of time and reduces the chance of errors.
2.  **Enforced Consistency:** It guarantees that all entities based on the same template will have a consistent set of `Zone`s. This is a massive benefit for the `Encounter_Engine`'s positional logic. The engine will always know that a "Humanoid" template entity has a "Chest" zone and an "Oral" zone.
3.  **Thematic Grouping:** It allows us to group Subjects by their fundamental form, which is a powerful design tool.
4.  **Flexibility is Maintained:** This is not a rigid class system. A designer can start with the `Humanoid` template and then add a `Tail` component or a `Wings` component. It's a starting point, not a straitjacket.

### **Example Templates We Might Create**

*   **`Template_Humanoid`:** The standard bipedal form. (Used by Characters, Den Mother, Sacred Idol).
*   **`Template_Quadrupedal`:** A four-legged, more bestial form.
*   **`Template_Networked`:** A decentralized, plant-like or fungal form with a central nexus and multiple appendages. (Used by Maiden's Grip).
*   **`Template_Amorphous`:** A blob-like or shifting form with few defined, permanent components.
*   **`Template_NonCorporeal`:** A template for entities with no physical body, defining their quasi-physical interaction points. (Used by Looking Glass).