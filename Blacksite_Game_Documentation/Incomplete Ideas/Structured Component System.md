## **Design Document: The Universal Structural Component System**

### **1. System Overview & Design Philosophy**

This document outlines the **Universal Structural Component System**, a unified framework for defining the physical (or quasi-physical) form of any entity in the game, from human Characters to alien Subjects.

The core philosophy is built on three key principles:

1.  **Universal Integration:** A single, consistent component architecture is used for all entities. This dramatically simplifies the `Core_Encounter_Engine`'s logic, as it only needs to understand one "language" for physical interaction, regardless of whether it's resolving a kiss between two characters or an attack from a tentacled horror.
2.  **Modular Flexibility:** An entity's form is described as a collection of modular components. This allows for the representation of anything from a standard human body to a non-corporeal psychic presence, all using the same foundational building blocks.
3.  **Function over Form:** The system prioritizes defining what a component *does* and what *can be done to it* over rigid anatomical labels. This provides the flexibility needed to handle a vast range of physical and sexual interactions in a logical, rules-based manner.

### **2. The Component Family**

An entity's form is defined by a collection of components from three distinct, function-specific types.

#### **2.1 `Descriptive_Component`**
*   **Purpose:** The Psychology & Narrative Layer. These components provide flavor, descriptive detail, and high-level information for the `Psychology System` and `Narrative_Engine`. They are not directly targetable in encounters.
*   **Structure:** Contains an `ID` and a `properties` dictionary for descriptive tags (e.g., `hair_color`, `voice_pitch`, `skin_texture`).
*   **Examples:** `Build`, `Skin`, `Hair`, `Voice`.

#### **2.2 `Systemic_Component`**
*   **Purpose:** The Internal State Layer. These components model an entity's internal, systemic functions that have a passive or active effect on the world.
*   **Structure:** Contains an `ID` and a `properties` dictionary for mechanical values (e.g., `pheromone_production`, `heat_cycle_state`, `sensory_acuity`).
*   **Examples:** `Chemistry`, `Senses`.

#### **2.3 `Interactive_Component`**
*   **Purpose:** The Direct Interaction Layer. These are the "nouns" of the `Core_Encounter_Engine`—the physical (or quasi-physical) points on an entity that can be targeted by an action. This is the most complex and important component type.
*   **Structure:** Contains the full suite of fields needed for encounter resolution.

### **3. The `Interactive_Component` in Detail**

This component is the heart of all physical gameplay.

#### **Core Fields:**

*   **`ID`:** A unique, queryable identifier (e.g., `mouth_01`, `reproductive_vine_A`).
*   **`Zone`:** The broad region of the entity where the component is located. This is used for high-level AI targeting and for resolving area-of-effect interactions like clothing coverage (e.g., `Oral`, `Chest`, `Appendages`, `Core`).
*   **`Feature_Type`:** A simple, high-level "noun" tag used for AI categorization and quick identification (e.g., `Orifice`, `Appendage`, `Mound`).
*   **`properties`:** A dictionary for all other mechanical and narrative details (e.g., `name: "Mouth"`, `sensitivity: 3`, `capacity: 4`, `material: "Flesh"`).
*   **`in_use_by`:** A state field that tracks if the component is currently occupied in an interaction.
*   **`modifications`:** A list of any applied modifications like piercings or tattoos.

#### **The Action Framework: `Capabilities` and `Receptivities`**

This is the core mechanic that allows for flexible and logical interaction. Instead of rigid pairings, we define what a component can do and what can be done to it.

*   **`capabilities` (List of Tags):** Describes the actions this component can **perform**.
    *   *Examples: `Can_Manipulate` (for hands, tongues, tentacles), `Can_Penetrate` (for penises, fingers, vines), `Can_Enclose` (for hands, thighs, buttocks), `Can_Stimulate_Frottage` (for most skin surfaces).*
*   **`receptivities` (List of Tags):** Describes the actions that can be **done to this component**.
    *   *Examples: `Is_Receptive_To_Penetration`, `Is_Receptive_To_Manipulation`, `Is_Receptive_To_Frottage`.*

**How it Works:** For an action to be valid, the actor's component must have the required `capability` and the target's component must have the corresponding `receptivity`. This allows for a vast matrix of logical interactions (handjobs, tribadism, etc.) without hardcoded rules for every possible pairing.

### **4. Implementation Examples**

#### **Example A: A Character's `Anatomy Profile`**

A Character's profile is a collection of these components, with a focus on biological norms.

*   **`mouth` (Interactive_Component):**
    *   `Zone: "Oral"`
    *   `Feature_Type: "Orifice"`
    *   `capabilities: ["Can_Enclose", "Can_Manipulate_Oral"]`
    *   `receptivities: ["Is_Receptive_To_Penetration_Oral", "Is_Receptive_To_Manipulation_Oral"]`
    *   *Note: The "Tongue" is represented by the `Can_Manipulate_Oral` capability, not a separate component.*
*   **`hands` (Interactive_Component):**
    *   `Zone: "Arms"`
    *   `Feature_Type: "Appendage"`
    *   `capabilities: ["Can_Manipulate", "Can_Enclose", "Can_Penetrate_Manual"]`
    *   `receptivities: ["Is_Receptive_To_Manipulation"]`
*   **`buttocks` (Interactive_Component):**
    *   `Zone: "Hips"`
    *   `Feature_Type: "Mound"`
    *   `capabilities: ["Can_Enclose"]`
    *   `receptivities: ["Is_Receptive_To_Manipulation", "Is_Receptive_To_Frottage"]`

#### **Example B: A Subject's `Manifestation Profile` (Subject-067 "Maiden's Grip")**

A Subject's profile uses the exact same structure to describe its alien form.

*   **`primary_root_nexus` (Interactive_Component):**
    *   `Zone: "Core"`
    *   `Feature_Type: "Nexus"`
    *   `properties: { name: "Primary Root Nexus", material: "Supernatural Bark" }`
    *   `receptivities: ["Is_Receptive_To_Disruption_Chemical"]`
*   **`reproductive_vine_A` (Interactive_Component):**
    *   `Zone: "Appendages"`
    *   `Feature_Type: "Appendage"`
    *   `properties: { name: "Reproductive Vine", texture: "Smooth, pulsing" }`
    *   `capabilities: ["Can_Penetrate", "Can_Manipulate"]`
    *   `receptivities: ["Is_Receptive_To_Manipulation"]`
*   **`pollen_aura` (Systemic_Component):**
    *   `ID: "pollen_aura_01"`
    *   `properties: { effect: "Aphrodisiac", radius: "5 meters" }`

This universal system is simple for the game engine to parse, yet flexible enough to define any entity, ensuring all physical interactions in *Beware the Blacksite* are governed by a single, robust, and logical set of rules.