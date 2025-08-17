Yes, that makes perfect sense. Thank you for that crucial piece of context about the encounter tables. That single detail—that Subjects have the agency to *put themselves on the tables* while other threats are static or random—is a brilliant mechanical expression of your core themes. It solidifies the difference between an intelligent predator and a simple hazard.

With that in mind, your idea for a **modular Hazard Profile** is absolutely the way to go. It's far more flexible and powerful than the simple stat block I proposed. It allows you to build a wide variety of "ancillary threats" using a simple, unified system.

Let's design this modular framework. We'll create a library of **Hazard Components** that you can mix and match to build anything from a simple pressure plate trap to a complex "mini-mindless subject" like a Processed Personnel.

---

### **The Modular Hazard System (To be documented in `Ancillary_Threats.md`)**

**Core Concept:** An Ancillary Threat is an entity or object that can trigger an encounter. Its behavior and capabilities are defined by a collection of simple, modular components.

---

#### **The Hazard Component Library**

This is a menu of components to choose from when building a new threat. A simple trap might only have two or three of these. A Processed Personnel might have five or six.

**1. Core Profile Components (Required for all Hazards)**

*   **Hazard ID:** `processed_personnel_01`, `b3_pressure_plate`
*   **Description:** A brief, clinical description for the game's internal use.
*   **Hazard Rating (Dice Pool):** An integer (e.g., 2-5 dice). The baseline number of dice it rolls.
*   **Instability Die (Die Size):** A die size (d4-d10). The size of dice it rolls.

**2. Trigger Component (Choose One)**

*   **Proximity Trigger:** Activates when a character enters its defined area (e.g., a specific room or tile).
*   **Interaction Trigger:** Activates when a character interacts with a specific object (e.g., opening a locker, using a computer terminal).
*   **Random Trigger:** Has a chance to activate whenever a character is in a designated zone. This is your "random encounter" sphere.
*   **Conditional Trigger:** Activates when a specific game state is met (e.g., the power goes out, a specific character's `Stability` drops below `Low`).

**3. Behavior Component (Choose One or more)**

*   **Static Behavior:** The hazard performs the same action every time it acts.
    *   *Example: "Deal 2d6 Vitality damage."*
*   **Patterned Behavior:** The hazard cycles through a simple, predefined list of actions.
    *   *Example: Action 1: "Grapple." Action 2: "Constrict."*
*   **Reactive Behavior:** The hazard has a simple "if-then" logic tree.
    *   *Example: "IF character attempts to escape, THEN use 'Trip' action. ELSE, use 'Attack' action."*
*   **Pursuit Behavior:** If triggered, this hazard will follow the player through a set number of rooms or for a set duration. (Perfect for chases).

**4. Interaction Components (Optional, for more complex threats like Processed Personnel)**

*   **Multi-Stage Encounter Component:** Defines a simple, linear encounter flow. This is key for your "mini-mindless subjects."
    *   *Stage 1: Chase. Stage 2: Grapple. Stage 3: Dominate.*
    *   Each stage has its own success/failure conditions to move to the next.
*   **Vulnerability Component:** Defines a specific weakness. An interaction with this component bypasses or ends the encounter.
    *   *Vulnerability Type: `Acumen_Nerd_Check`*
    *   *Vulnerability Type: `Item_Crowbar`*
*   **Loot/Reward Component:** Defines what the player gets for successfully overcoming the hazard (e.g., an item, access to a new area).

**5. Effect Components (Choose one or more)**

*   **Direct Meter Damage Effect:** The most common effect. Deals damage to Vitality, Stability, or Inhibition.
*   **Status Effect Application Effect:** Applies a temporary `Status Effect` (e.g., `Bleeding`, `Dazed`).
*   **Minor Corruption Effect:** Applies a small, fixed amount of `Corruption` points. Unlike Subjects, this is likely a flat amount without complex resistance mechanics. This reinforces that Subjects are the *masters* of corruption, while these are just echoes.
*   **Environmental Effect:** Changes the state of the room (e.g., locks the doors, fills the room with gas).

---

### **Example Hazard Profiles**

Let's build two examples using this system:

**1. Simple Trap: The Faulty Electrical Panel**

*   **Core Profile:** `ID: b2_elec_panel_01`, `Rating: 2`, `Instability: d6`
*   **Trigger:** `Interaction Trigger` (when player tries to use it)
*   **Behavior:** `Static Behavior` ("Electrical Shock")
*   **Effect:** `Direct Meter Damage` (2d6 Vitality), `Status Effect Application` (`Dazed` for 1 turn)

**2. Complex Hazard: The "Stalker" Processed Personnel**

*   **Core Profile:** `ID: pp_stalker_01`, `Rating: 3`, `Instability: d8`
*   **Trigger:** `Random Trigger` (in the B2 Habitation Block)
*   **Behavior:** `Pursuit Behavior` (follows for 3 rooms)
*   **Interaction:** `Multi-Stage Encounter Component`
    *   *Stage 1: Pursuit (Success = player escapes; Failure = triggers Stage 2)*
    *   *Stage 2: Altercation (A series of opposed checks to fight it off)*
    *   *Stage 3: Submission (A sexual encounter if the altercation is lost)*
*   **Interaction:** `Vulnerability Component` (Vulnerable to a `Physique + Jock` check to barricade a door during the pursuit).
*   **Effect:** `Direct Meter Damage` (Stability during pursuit, Vitality during altercation), `Minor Corruption Effect` (during submission).