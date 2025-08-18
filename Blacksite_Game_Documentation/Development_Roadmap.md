# **Official Development Roadmap - The Golden Master**

**Core Principle:** This roadmap is built around the finalized documentation hierarchy and the `Core_Encounter_Engine` as the central coordinator. The goal of Phase 1 is to achieve "Design Complete" status.

---

## **Phase 1: Architectural Finalization & Design Completion 📋**

### **1.1 Foundational Documents**

*   **`Project_Constitution.md`:**
    *   **Status:** **Design Complete.**

*   **`Project_Foundations.md`:**
    *   **Status:** **Design Complete.**
    *   [ ] **(NEW)** Add a high-level reference to the **Facility Medical Integration** system, noting that physical (but not psychological) changes can be reversed. This will point to the full mechanics in `Facility_Environment_Systems.md`.
    *   [ ] **(TODO)** Complete the **"Universal Gameplay Rules"** section.
        *   [ ] Document the formal rules for **Meter Damage vs. Meter Penalties**.
        *   [ ] Create a master list of **Meter Recovery Methods** (e.g., Rest, Medical Items, Companion Support).
        *   [ ] Provide a clear list of **Example Attribute + Skillset Pairings** to guide content creation.

### **1.2 The Engines**

*   **`Encounter_Engine.md`:**
    *   [ ] **(REVISED)** Write this document, formally defining the **"Hybrid Model v3.2"** as the core architecture.
    *   [ ] Document the **"Tick-Based" World State** as the fundamental time progression mechanic.
    *   [ ] Detail the **Dual Encounter Trigger System**, clearly separating the **Subject Encounter Check** (AI-driven, highest priority) from the **Hazard Encounter Check** (location-based, lower priority).
    *   [ ] Formally design the **Subject AI's Three-Tier Exploration State** (`OBSERVE`, `HAUNT`, `INITIATE`).
        *   [ ] Define the mechanics for **`Presence Effects`** as the narrative output of the `HAUNT` state.
        *   [ ] Design the **`Stalking Intensity`** counter as the mechanic for escalating a prolonged `HAUNT`.
        *   [ ] Create the master list of **`HAUNT Response Actions`** available to characters (e.g., `Prepare Defenses`, `Hide`).
    *   [ ] Formally design the **`Interest Cache`** and **`Awareness Saturation`** systems as the core drivers for the Subject's targeting AI.
    *   [ ] Formally design the **`Ambient Psychology`** system detailing companion reactions, including how it is triggered by game states (like `HAUNT`).
    *   [ ] Formally add the **Hierarchical Choice** system to the UI interaction model.

*   **`Exploration_Engine.md` (New Document):**
    *   [ ] Write this document, defining navigation, discovery, and the "Euclidean Betrayal" system.
    *   [ ] Finalize Core Loop Hybrid Model (From Separate Ideas Document)
    *   [ ] Formally design the **"Ambient Psychology"** and **Hierarchical Choice** systems.

*   **`Narrative_Engine.md` (New Document):**
    *   [ ] **(CRITICAL PRIORITY)** Define the **`Scene Requirement Data Structure`** (the "Intent Packet").
    *   [ ] Detail the Micro-Template and Variable Dictionary architecture.
    *   [ ] **(NEW)** Under the "Micro-Template Architecture" task, add a specific requirement to design text templates that can **dynamically alter their descriptions** based on the presence of `special_senses` tags, particularly for synesthesia.

### **1.3 Core Entity Systems**

*   **`Entity_Core_Systems.md` (New Document, CRITICAL PRIORITY):**
    *   [ ] **(NEW)** Create this new Tier 2 document to define the universal frameworks shared by all entities.
    *   [ ] **(NEW)** Write the **"Universal Structural Component System"** section, defining the `Descriptive`, `Systemic`, and `Interactive` component family and all associated mechanics (Capabilities, States, Size Mismatch, etc.).
    *   [ ] **(NEW)** Write the core framework for the universal **`Relationship State`** component.
    *   [ ] **(NEW)** Write the core framework for the universal **`Climax State`** component.

*   **`Character_Core_Systems.md` (Finalization):**
    *   [X] Refine new document format and rules **(Condensed all complete tasks)**
    *   [ ] Update Genesis Framework for FULL Character Creation rules for States.
    *   [ ] Formally define the **`Character Psychology Output Interface`** **[TODO: Pending `Narrative_Engine` design]**.
    *   [ ] **(NEW)** Integrate the **"Affinity-Weighted Expression"** model for branching corruption tracks (`Dominion`, `Exposure`, `Communion`).
        *   [ ] Add the **`Expression Affinity`** data structure (e.g., `{Dominant: 0, Submissive: 0}`) to the Character State Framework.
        *   [ ] Formally document how `Character Nature` provides the starting `Affinity Scores`.
        *   [ ] Define the mechanic for how in-game experiences modify `Affinity Scores` over time (as a positive/negative reinforcement loop).
        *   [ ] Update the `Psychological Integration` component to use `Affinity Scores` as a primary weight when generating `Intents` for these tracks.

*   **`Character_Core_Systems.md` (Update Dependencies):**
    *   [ ] **(REVISED)** Update document dependencies. New dependency: `Entity_Core_Systems.md`.
    *   [ ] **(REVISED)** Refactor the `Anatomy Profile` section to be an *implementation* of the Universal Structural Component System.
    *   [ ] **(RE-EVALUATE)** Review `Relationship` and `Climax` state sections to ensure they align with the new core frameworks from `Entity_Core_Systems.md`.

*   **`Subject_Core_Systems.md` (Major Refinement):**
    *   [X] Refine and finalize the **Two-Vector Corruption System** (`Corruption Bleed` + `Direct Application`).
    *   [X] Formally add the **"One Subject at a Time"** rule as a constitutional principle.
    *   [X] Design the **"Disruption"** mechanic and the **"Insight" System** for discovering weaknesses.
    *   [X] Add a section on **"Intersubject Dynamics"** (Rivalries/Synergies).
    *   [ ] Add a design note clarifying that the **`Fixation Matrix` is the Subject's equivalent of a `Nature` component.**
    *   [ ] Add the `Climax State Component` to the `Subject State Framework`.
    *   [ ] Formally define the `Psychological Integration` and `Subject Psychology Output Interface`.
    *   [ ] **(NEW)** Add a design note to consider creating a **Subject** whose primary form of attack or corruption is the application of a **Synesthesia `Corruption Vector`**.

*   **`Subject_Core_Systems.md` (Update Dependencies):**
    *   [ ] **(REVISED)** Update document dependencies. New dependency: `Entity_Core_Systems.md`.
    *   [ ] **(REVISED)** Create the `Manifestation Profile` section as an *implementation* of the Universal Structural Component System. **(This is our next writing task).**
    *   [ ] **(RE-EVALUATE)** Review `Relationship` and `Climax` state sections to ensure they align with the new core frameworks.

*   **`Hazard_Systems.md` (New Document):**
    *   [ ] Write this document, detailing the **Modular Hazard Component Library**. (Has separate Ideas Document)
    *   [ ] Detail the **"Psychology Shim"** integration.

*   **`Hazard_Systems.md` (Update Dependencies):**
    *   [ ] **(REVISED)** Update document dependencies. New dependency: `Entity_Core_Systems.md`.
    *   [ ] **(REVISED)** Ensure that `Processed Personnel` and other corporeal Hazards use the Universal Structural Component System for their physical forms.

### **1.4 Progression & Environment**

*   **`Character_Progression_Systems.md` (Major Overhaul):**
    *   [ ] Define Character Tier System
    *   [ ] Overhaul the **Status Effects** and **Perk** systems, including a **"Perk Acquisition Mechanic."**
    *   [ ] Overhaul the **Equipment Framework**, adding "Cosmetics" and the **"Clothing as Defensive Bonus"** model.
    *   [ ] Formally document the **Equipment Control** subsystem, including:
        *   [ ] The rules for **Keyholding**.
        *   [ ] The definition and application of **Consent Status** (`CONSENTING` vs. `FORCED`).
        *   [ ] The design principle that the controlling entity's nature determines the **type of equipment selected**.
    *   [ ] Design and document the **"Off-Screen Resolution System."**
    *   [ ] **(HIGH PRIORITY)** Design the **"Player Agency vs. Transformation" Framework** for resisting physical changes.
    *   [ ] **(NEW)** Design the **Synesthesia System** as a gameplay mechanic:
        *   [ ] Formally add **Synesthesia** as a potential **`Corruption Perk`**, likely resulting from the `Enthrall` or `Metamorphosis` tracks.
        *   [ ] Design a temporary **`Status Effect`** that can induce a chaotic, short-term version of synesthesia.
    *   [ ] **(NEW/HIGH PRIORITY)** Design and document the **"Corruption Threshold Progression System."**
        *   [ ] Formally define the relationship between `Thresholds` (limiters) and `Corruption Vectors` (drivers).
        *   [ ] Establish the total number of `Corruption Thresholds` (e.g., 20).
        *   [ ] Create the formal table of **escalating point costs** for reaching each new threshold.
        *   [ ] Rebalance the initial threshold costs to be achievable with the new, lower output of the "Corruption Budget" system, while ensuring later thresholds require facing more powerful Subjects.

*   **`Facility_Environment_Systems.md` (Major Refactor):**
    *   [ ] Strip out all navigation and exploration mechanics.
    *   [ ] Create this document as the pure **template and rulebook for creating floors**.
    *   [ ] **(NEW)** Formally document the full **Facility Medical Integration** system here, including the **Protective Injection Protocol**'s contraceptive and resistance effects, and the rules for **Medical Reversal Services**.
    *   [ ] **(NEW)** Update the formal template for a floor's `_Framework.md` document to include a new required section: **"Intersubject Dynamics Matrix."**
        *   [ ] This section will define the `Rivalry/Synergy/Indifference` state between all Subjects residing on that specific floor.

### **1.5 Engine & Systems Libraries**

*   **`Knowledge_Base.md` (New Document):**
    *   [ ] **(NEW)** Write this new document to define the global, party-wide knowledge database.
    *   [ ] Define the data structure for storing `Insights`, lore entries, and other discovered information.
    *   [ ] Detail its API for other systems (e.g., `Knowledge_Base.Has_Insight()`).
    *   [ ] Explain its diegetic connection to The Analyst and the "Facility Tablet" UI.

*   **`Erotic_Content_Atlas.md` (New Document):**
    *   [ ] **(NEW)** Create this new document to serve as the master implementation and style guide for all fetish content.
    *   [ ] For each EIV and Content Flag, create an entry detailing:
        *   [ ] A clear definition of the fetish.
        *   [ ] Its core psychological drivers.
        *   [ ] Guidelines for its narrative and thematic representation in-game.
        *   [ ] Notes on its mechanical implementation and interaction with core systems (CSF, Agency, etc.).

*   **`Core_Data_Library.md` (New Document):**
    *   [ ] **(NEW)** Create the **`Structural_Template_Library`** section.
        *   [ ] Define the data structure for a `Structural Template`.
        *   [ ] Create the initial set of base templates (e.g., `Template_Humanoid`, `Template_Networked`, `Template_NonCorporeal`).

*   **`Encounter_Engine_Library.md` (New Document):**
    *   [ ] Create this document to serve as the "database" for the Encounter Engine.
    *   [ ] **Universal Action Library:** Define "Action Templates" and list core Intents (e.g., `ATTACK`, `RESTRAIN`, `SEDUCE`, `PENETRATE`).
    *   [ ] **Reaction Library:** Create the master list of all universal `Reactions`.
    *   [ ] **Proximity Effect Library:** Create the master list of all passive auras and their resolution models.
    *   [ ] **Stance & Position Library:** Create the master list of all possible entity stances.
    *   [ ] **(NEW)** Add a new major section: **"The Consequence Package Library."**
        *   [ ] Define the data structure for a `Consequence Package`.
        *   [ ] Create the initial packages required for the Disruption system (e.g., `Standard_Disruption_Failure`, `Cunning_Subject_Failure`, `Messy_Disruption_Tie`).
    *   [ ] **(NEW)** Add a new major section: **"The Disruption Action Library."**
        *   *Designer's Note: This is a thematic organization within the `Universal Action Library`, not a separate system.*
        *   [ ] Formally document that Disruption Actions are standard actions whose `Prerequisites` check the `Knowledge_Base`.
        *   [ ] Create template entries for the initial B3 Subject Disruption actions, referencing the new Consequence Packages.

*   **`Character_Core_Systems_Library.md` (New Document):**
    *   [ ] Create this new document to serve as the "database" for the Character Core Systems.
    *   [ ] Create the **`Senses` Library:**
        *   [ ] Define the master list of all valid **`special_senses` tags**, including all planned variants of synesthesia (e.g., `synesthesia_audio_visual`, `synesthesia_audio_tactile`, `synesthesia_thermo_erotic`).
    *   [ ] Define **Character Nature** Libraries
        *   [ ] **`Core Drives` Library:** Create the master list of all valid `core_drives` (e.g., "Seek_Knowledge," "Ensure_Ally_Safety," "Acquire_Power").
        *   [ ] **`Default Responses` Library:** Create the master list of all valid `default_responses` and their sub-properties (e.g., `stress_response` options: "Analyze," "Action," "Freeze").
        *   [ ] **`Behavioral Weights` Library:** Define the master list of all `Intent` categories that can be weighted (e.g., "Aggressive_Actions," "Supportive_Actions," "Investigative_Actions").
        *   [ ] **`Corruption Affinity` Library:** Confirm that the valid keys for this dictionary are the seven official `Corruption_Track` names.
    *   [ ] Create the **`Relationship Progression` Library:**
        *   [ ] Define the master list of all valid relationship-modifying events (e.g., `life_saving_action`, `minor_disagreement`).
        *   [ ] Assign the specific, tweakable numerical values for each event.
    *   [ ] Create the **`Control Comfort` Library:**
        *   [ ] Define the precise, time-based numerical values that govern the progression rate of `control_comfort` for each relationship tier (`LOYAL`, `COOPERATIVE`, etc.).
    *   [ ] Create the **`Arousal System` Library:**
        *   [ ] Define the master list of all valid positive and negative **`Arousal Pressure Sources`** (e.g., `pressure_denial`, `pressure_pheromones`, `pressure_dysphoria`).
        *   [ ] Assign the specific, tweakable numerical values for each pressure source.
        *   [ ] Document the master list of **`Relief Mechanisms`** and their default effectiveness values.
    *   [ ] Create the **`Climax System` Library:**
        *   [ ] Define the master list of all valid **`Climax_Type`** tags (e.g., `Pleasure`, `Stress_Relief`, `Forced`).
        *   [ ] Document the default **`Post-Climax State` Status Effects** associated with each climax type, including their mechanical effects and durations.
        *   [ ] Define the standard **`climax_cooldown` duration** as a tweakable value.
    *   [ ] Create the **`Refractory Period` Library:**
        *   [ ] Define the **`Base_Duration`** value.
        *   [ ] Document the formula for calculating the final duration, ensuring it includes both the character's **`refractory_rate`** and a modifier based on their **`Current Arousal` at the moment of climax**.
        *   [ ] Detail the specific mechanical effects of the `Refractory Period` status effect.
    *   [ ] Create the **`Eroticism Profile` Library:**
        *   [ ] Define the master list of all valid **`Content_Flag` keys** that can be tracked in an `Eroticism Profile` (e.g., `watersports`, `bondage_equipment`, `worship_scenarios`). This list will likely be derived from the EIV framework.
        *   [ ] Document the default **`Affinity Score` modifiers** for key in-game events (e.g., `positive_consensual_climax_modifier: +2.0`, `traumatic_forced_climax_modifier: -3.0`).
        *   [ ] For each `Corruption` threshold that affects the profile, define the specific `Content_Flag` it targets and the numerical value of the forced modification.
    *   [ ] Create the **`Corruption Theme` Library:**
        *   [ ] Define the data structure for a **`Corruption Theme`** (e.g., "Hyena," "Botanical").
        *   [ ] For each theme, create data blocks for each of the seven **`Corruption Tracks`**.
        *   [ ] Within each track, create entries for each **`Threshold (1-10)`**, detailing the specific, permanent CSF modifications that are applied at that level of accommodation (e.g., the specific `Anatomy Profile` changes for `Metamorphosis`, the `Behavioral Weight` shifts for `Dominion`, etc.).
    *   [ ] Create the **`Psychological Integration` Library:**
        *   [ ] Define the specific percentage ranges for the **4-Stage Meter Psychology** (e.g., `Crisis: 0%`, `Low: 1-24%`, etc.) as tweakable constants.
        *   [ ] Document the baseline **"meta-weights"** for the **State Priority Hierarchy**, defining the default multiplicative power of each psychological driver (e.g., `Meter_Crisis_Weight`, `Compulsive_Arousal_Weight`).
        *   [ ] Create a master list of all valid **`Emotional Tone`** tags (e.g., "Desperate," "Confident," "Resigned") that can be output for the `Narrative_Engine`.
        *   [ ] Create a master list of template formats for **`Internal Monologue Hint`s**.
    *   [ ] **(NEW)** Create the **`Expression Affinity` Library:**
        *   [ ] Define the master list of all valid `Affinity` keys (e.g., `Dominant`, `Submissive`, `Exhibitionist`, `Voyeur`, `Idol`, `Devotee`).
        *   [ ] Document the default starting `Affinity Score` values for all core companions based on their `Character Nature`.
        *   [ ] Assign the specific, tweakable numerical modifiers for key in-game events that influence affinity (e.g., `successful_dominant_action_modifier: +1.0`, `traumatic_submissive_event_modifier: +1.5`).

    *   **`Subject_Core_Systems_Library.md` (New Document):**
        *   [ ] **(NEW)** Create this new document to serve as the "database" for the Subject Core Systems.
        *   [ ] **(NEW)** Create the **`Corruption Focus` Profile Library**, defining the master list of all valid budget distribution models and their percentage values.
        *   [ ] **(NEW)** Create the **`Fixation Matrix` Libraries** section to define the master lists of all valid options for the `Fixation Matrix` component.
            *   [ ] **`Designation` Library:** Create the master list of all valid `Designation` tags (e.g., "Territorial Predator," "Spiritual Nexus").
            *   [ ] **`Core_Fixations` Library:** Create the master list of all valid `Core_Fixation` tags and their general intent (e.g., "Enforce_Territory," "Test_Prey_Resilience").
            *   [ ] **`Stimuli_Responses` Library:** Create the master list of all valid `stimulus` keys and the `response` tags their AI can generate (e.g., `stimulus_territorial_intrusion` -> `response: "Escalate_Aggression"`).
            *   [ ] **`Behavioral_Weights` Library:** Define the master list of all action categories or EIVs that can be weighted (e.g., "weight_worship_actions," "weight_restraint_actions").
            *   [ ] **`Disruption_Triggers` Library:** Create the master list of all valid conceptual `Disruption_Trigger` tags (e.g., "Desecration," "Cognitive_Dissonance," "Sensory_Overload").
        

### **1.6 Content Blueprints & Story**

*   **`Antagonist_Catalog.md` (Major Update)**
    *   [ ] Perform a full content pass on The Other, The Architect, and The Resonance.
    *   [ ] Align their profiles, motivations, and methods with the "Blacksite Agency" theme.
    *   [ ] Detail how their psychology generates specific `Intents` for the Encounter Engine.

*   **`Companion_Catalog.md` (Major Update)**
    *   [ ] Perform a full content pass on the four core companions.
    *   [ ] For each companion, formally document their `Character Nature` component (core drives, goals, etc.).
    *   [ ] Detail how their `Character Nature` influences their `Psychology System` to generate specific `Intents`.
    *   [ ] **(NEW)** Formally document **The Analyst's** full character arc.
        *   [ ] Integrate the "Network Ghost" and "Identity Through Embodiment" concepts.
        *   [ ] Detail how their role as the manager of the `Knowledge_Base` feeds their character development and competence crisis.
    *   [ ] For each companion, formally document their **Starting Relationship Matrix**, defining their initial relationship values with the player and all other companions.

            |                 |  Player   |  Scholar  | Protector |Manipulator|  Analyst  |
            |-----------------|-----------|-----------|-----------|-----------|-----------|
            | **Player**      | —         | 4 (Neut.) | 4 (Neut.) | 3 (Neut.) | 3 (Neut.) |
            | **Scholar**     | 4 (Neut.) | —         | 6 (Coop.) | 0 (Rsnt.) | 3 (Neut.) |
            | **Protector**   | 3 (Neut.) | 6 (Coop.) | —         | 1 (Rsnt.) | 2 (Rsnt.) |
            | **Manipulator** | 3 (Neut.) | 3 (Neut.) | 3 (Neut.) | —         | 4 (Neut.) |
            | **Analyst**     | 4 (Neut.) | 4 (Neut.) | 4 (Neut.) | 4 (Neut.) | —         |

*   **`Story_Framework.md` (Brainstorm & Rewrite)**
    *   [ ] Brainstorm and formally design the mechanics of the **`Live_Documentation_System`**.
    *   [ ] Brainstorm and formally design the **four endings** based on the "low/suppressed corruption" mechanic.
    *   [ ] Perform a consistency pass to align the entire story with the "Blacksite Agency" theme and milestone-based progression.

---

## **Phase 2: Vertical Slice Implementation & Content Creation 🎨**

**Goal:** To transform the finalized design blueprints into a playable, tangible vertical slice of the game. This phase focuses on building the core functionality and creating the content for the initial player experience (Intro + Floors B3 & B2).
**Milestone:** "Vertical Slice Complete" - a functional, playable build that demonstrates all core systems working in concert, from exploration and ambient psychology to dynamic encounters and narrative resolution.

### **Key Objectives:**

*   **Engine & Systems Implementation:**
    *   [ ] Implement the foundational architecture of the `Core_Encounter_Engine`, `Exploration_Engine`, and `Narrative_Engine` in Godot.
    *   [ ] Build the backend for the `Character`, `Subject`, and `Hazard` Core Systems, allowing the creation of entity resources based on the design documents.
    *   [ ] Implement the `Encounter_Engine_Systems` database, creating the initial libraries for Actions, Reactions, and Proximity Effects.

*   **Content Creation:**
    *   [ ] Write and implement the full narrative and mechanical data for the game's **Introduction** sequence using the `Exploration_Engine`'s "Scene Runner."
    *   [ ] Build out the complete floor data for **B3 and B2** in their respective `_Framework.md` and `_Catalog.md` files. This includes room layouts, environmental storytelling, and the placement of all entities and discoveries.
    *   [ ] Create the full profiles and AI packages for the initial **Subjects** (e.g., Sacred Idol, Den Mother, Looking Glass) and any new B2 Subjects.
    *   [ ] Implement the five core **Companions** with their complete `Character State` and `Character Nature` components, ensuring their autonomous psychology functions.
    *   [ ] Populate the `Content_Catalogs` with all necessary **Perks, Status Effects, and Equipment** for the first two floors.

*   **User Interface & Experience:**
    *   [ ] Develop the initial UI based on the finalized design blueprint, including the party panel, narrative display, and contextual action buttons.
    *   [ ] Ensure the "Page-Based" narrative flow is functional and feels immersive.

---

## **Phase 3: Production, Polish, & Initial Release 🚀**

**Goal:** To expand the content from the vertical slice, perform rigorous testing and balancing, and prepare a polished build for the first public release.
**Milestone:** "Release Ready" - a stable, polished, and content-complete initial release package ready for distribution.

### **Key Objectives:**

*   **Content Expansion:**
    *   [ ] Build out and implement all content for Floor **B1** and the **Ground Floor**, completing the first major arc of the player's journey.
    *   [ ] Implement all remaining story milestones, narrative beats, and discoveries required for the initial release arc.
    *   [ ] Design and implement the first set of **Skillset Evolutions** as a late-game reward for players who complete the initial release content.

*   **Balancing & Quality Assurance:**
    *   [ ] Conduct extensive playtesting to balance encounter difficulty, resource economy, and corruption progression.
    *   [ ] Perform rigorous testing of the autonomous companion AI to ensure their behavior is intelligent, believable, and thematically appropriate.
    *   [ ] Hunt and squash bugs across all systems, with a focus on the complex interactions within the `Core_Encounter_Engine`.

*   **Polish & Enhancement:**
    *   [ ] Refine the UI/UX based on playtesting feedback.
    *   [ ] Add sound effects and ambient music to enhance the horror atmosphere.
    *   [ ] **(Optional Enhancement)** Implement the LLM integration layer for narrative polish, ensuring a functional fallback system is in place.

*   **Release Preparation:**
    *   [ ] Prepare the final game packages for distribution on target platforms (itch.io, F95Zone, etc.).
    *   [ ] Create all necessary store page assets, descriptions, and community materials.
    *   [ ] Finalize and implement the Content Consent menu and all necessary content warnings.