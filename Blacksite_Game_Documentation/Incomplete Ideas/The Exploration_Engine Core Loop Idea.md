## Blueprint A **The `Exploration_Engine` Core Loop: Hybrid Model v3.2 (Definitive)**

### **Design Philosophy**

This model synthesizes a dynamic, simulated world with the deliberate pacing of a narrative adventure game. Its purpose is to create a gameplay loop that feels tense, unpredictable, and intelligent, while remaining clear and focused for the player. The core principle is that **mundane threats are a function of the environment, while Subject encounters are a direct act of an intelligent, hostile will.** This is achieved by running two parallel encounter systems, with the Subject's decisions always taking precedence.

The design is built on the foundational assumption that **the party is almost always split up.** The engine follows the Player Character, while companions operate as autonomous agents elsewhere on the floor, reinforcing themes of isolation and vulnerability.

### **Core Components**

1.  **The "Tick-Based" World State:** The game world advances in discrete "ticks." Every meaningful player action (e.g., moving rooms, interacting with an object) constitutes one tick, during which the entire world state updates.

2.  **On-Grid Entities (Player, Companions, NPCs):** These characters have a persistent presence on the floor map. Their location is always known.

3.  **Off-Grid Entities (Subjects & Proactive Hazards):** To create a sense of sudden, supernatural intrusion, Subjects and wandering Hazards do not have a persistent token on the map. They exist "off-stage," and their appearance is managed by the encounter trigger system.

### **The Dual Encounter Trigger System**

When the player's action advances a tick, the engine performs two separate checks in a strict order of priority.

#### **System 1: The Subject Encounter Check (Highest Priority)**

A Subject's appearance is not random; it is an act of will.

**The Subject's AI & `Interest Cache`:**
A Subject's `Psychology System` maintains a dynamic, ranked list of its current targets—its `Interest Cache`. This score is calculated each tick for every character on the floor based on:
*   **`Fixation Matrix`:** High interest in characters whose state or location matches the Subject's obsessions.
*   **`Relationship Score`:** High interest in characters with whom it has a hostile relationship.
*   **Proximity & Recency:** Minor interest from recent interactions or being nearby.

**`Awareness Saturation`:**
To ensure no character remains invisible forever, every character slowly accumulates a hidden `Awareness` score with each `Active` Subject on the floor. This represents the inevitable notice of a supernatural predator. Once `Awareness` crosses a threshold, the character is permanently added to the Subject's `Interest Cache`, ensuring they are always a potential target.

**The Subject's Three-Tier Action State:**
Based on its `Interest Cache`, the Subject's AI chooses one of three states for its "tick action":

1.  **State 1: OBSERVE (Default):** The Subject is not focused on any particular character or area. The floor is in its baseline state.

2.  **State 2: HAUNT (The Stalking Phase):** The Subject has become interested in one or more characters and decides to focus its `Presence`.
    *   **Targeted Haunting:** The `HAUNT` state is targeted at the character(s) with the highest `Interest` scores. A Subject can haunt multiple characters simultaneously, with a **Primary Target** (highest interest) and **Secondary Targets**.
    *   **`Presence Effects`:** The engine triggers narrative alterations to the room descriptions around the haunted characters, providing evidence that the Subject is nearby. These effects are more intense for the Primary Target.
    *   **Analyst Feedback:** This state triggers Analyst warnings, which may be directed at the player about a companion's dangerous situation, creating strategic dilemmas.
    *   **`Stalking Intensity`:** For every consecutive tick a character is haunted, a hidden `Stalking Intensity` counter increases. This can cause `Presence Effects` to become more aggressive and Analyst warnings more urgent, pressuring the characters to act.
    *   **HAUNT Response Actions:** A character being actively haunted gains access to new, contextual exploration actions (e.g., `[Prepare Defenses]`, `[Hide]`) to try and de-escalate the situation.

3.  **State 3: INITIATE (The Ambush):** The Subject's AI decides to strike.
    *   **The Command:** The engine receives the `INITIATE` command. A Subject Encounter is triggered, overriding all other possibilities.
    *   **Priority & Tie-Breaking:** If multiple Subjects attempt to `INITIATE` in the same tick (a rare event), the right to attack is won by the Subject with the highest priority, determined by: **Relationship Score (most hostile) → Threat Level → Category → 1d6 Roll-Off.**
.
#### **System 2: The Hazard Encounter Check (Lower Priority)**

This system only runs if the Subject's AI does **not** choose to `INITIATE` an encounter during the current tick. This handles all mundane, environmental, and low-level threats.

**The Room's Properties:**

*   **`Hazard Manifest`:** A static, pre-defined list of all non-Subject encounters possible in a specific room. This ensures all mundane threats are location-specific and logical.
    *   *Example: An engine room's manifest might contain `[Hazard_Steam_Pipe, Hazard_Processed_Personnel]`, while a library's might contain `[Hazard_Whispering_Book, Hazard_Processed_Personnel]`.*
*   **`Background Danger`:** A low, static score (e.g., 5-15) representing the baseline chance of a mundane threat in that room.

**The Hazard Trigger:**

1.  The engine rolls 1d100.
2.  If the roll is less than or equal to the room's `Background Danger` score, a Hazard encounter is triggered.
3.  The engine then consults the room's `Hazard Manifest` to select the specific Hazard to be encountered.

### **Summary of the Gameplay Loop**

1.  The player takes an action, advancing the game by one **tick**.
2.  The engine updates the **`Interest Cache`** and **`Awareness Saturation`** for all `Active` Subjects.
3.  The engine checks with each **`Active` Subject's AI**. The highest-priority Subject's decision is processed.
    *   If the choice is **`INITIATE`**, a Subject Encounter begins. The process stops.
    *   If the choice is **`HAUNT`**, narrative `Presence Effects` are generated for the targeted character(s), `Stalking Intensity` may increase, and new response actions become available.
4.  If no Subject encounter was initiated, the engine performs the **Hazard Check** for the player's current location.
5.  The `Narrative_Engine` compiles the outcome of the player's action, any abstract companion updates, and any `Presence Effects` into the next **"page"** of text.
6.  The game pauses and presents this new page to the player, awaiting their next choice.

This model provides a robust and thematically rich foundation for the exploration experience, balancing intelligent, predatory horror with logical environmental challenges and meaningful player agency.

---

## Blueprint B **The `Exploration_Engine.md` Core Loop with Companion Integration**

### **1. Core Philosophy**

The `Exploration_Engine` is the default state of the game and its "world clock." Its purpose is to create a tense, dynamic, and intelligent exploration loop that reinforces the themes of isolation and predatory horror. The core principle is that **mundane threats are a function of the environment, while Subject encounters are a direct act of an intelligent, hostile will.** This is achieved by managing a "tick-based" world state and running a **Dual Encounter Trigger System**. The entire design assumes the **party is almost always split up**, with the engine tracking autonomous companions.

### **2. The "Tick-Based" World State**

*   **The Tick:** The game world advances in discrete "ticks." Every significant player action (e.g., moving, searching, using an item) advances the world state by one tick.
*   **On-Grid Entities:** Player Characters and Companions have a persistent, known location on the facility map.
*   **Off-Grid Entities:** Subjects and wandering Hazards exist "off-stage" and are introduced into the world via the trigger system.

### **3. Companion Autonomy & The Strategic AI Loop**

The engine is responsible for directing the autonomous companions during each tick.

1.  **Goal Query:** The engine queries the `Psychological Integration` component of every companion for their active, prioritized **`Character Goal`**.
2.  **Purposeful Action:** Based on the highest-priority goal, the engine directs the companion's action for that tick (e.g., "Move towards `room_infirmary`").
3.  **Off-Screen Resolution:** If a companion's action triggers a Hazard, the engine initiates the **"Off-Screen Resolution System,"** an abstracted encounter. The results are logged, and the player may be notified.

### **4. The Dual Encounter Trigger System**

At the end of each tick, the engine runs two checks in a strict order of priority.

#### **System 1: The Subject Encounter Check (Highest Priority)**
*   **The Subject's AI & `Interest Cache`:** Each Subject's `Psychology` maintains a dynamic, ranked **`Interest Cache`** of all characters on the floor. This score is calculated each tick based on the Subject's `Fixation Matrix`, its `Relationship Score` with the character, proximity, and recency.
*   **`Awareness Saturation`:** To ensure no character remains hidden forever, every character slowly accumulates a hidden **`Awareness`** score with each active Subject. Once a threshold is crossed, the character is permanently added to that Subject's `Interest Cache`.
*   **The Subject's Three-Tier Action State:** Based on its `Interest Cache`, the Subject's AI chooses one of three states for its "tick action":

    1.  **State 1: OBSERVE (Default):** The Subject is passive.
    2.  **State 2: HAUNT (The Stalking Phase):** The Subject has become interested in one or more characters and focuses its `Presence` on them.
        *   **Targeted Haunting:** The `HAUNT` state is targeted at the character(s) with the highest `Interest` scores, with a **Primary Target** and optional **Secondary Targets**.
        *   **`Presence Effects`:** The engine triggers narrative alterations to the room descriptions around the haunted character(s), providing evidence that the Subject is nearby (e.g., flickering lights, strange noises, temperature drops). These effects are more intense for the Primary Target.
        *   **`Stalking Intensity`:** For every consecutive tick a character is haunted, a hidden `Stalking Intensity` counter increases, making `Presence Effects` more aggressive and Analyst warnings more urgent.
        *   **HAUNT Response Actions:** A character being actively haunted gains access to new, contextual exploration actions (e.g., `[Prepare Defenses]`, `[Hide]`) to try and de-escalate the situation.
    3.  **State 3: INITIATE (The Ambush):** The Subject's AI decides to strike. It sends an `INITIATE` command, and a Subject Encounter is triggered, overriding all other possibilities. Tie-breaking between multiple Subjects is handled by a clear priority system (Relationship Score -> Threat Level -> Category -> d6 roll).

#### **System 2: The Hazard Encounter Check (Lower Priority)**
*   **Mechanism:** This probabilistic check only runs if no Subject chose to `INITIATE`.
*   **The Trigger:** The engine rolls 1d100 against the **`Background Danger`** score of the *player's current room*.
*   **The Content:** If successful, the specific Hazard is chosen from the room's static **`Hazard Manifest`**, ensuring environmental threats are logical and location-specific.

### **5. The Narrative Output Loop**

1.  **Ambient Psychology Query:** After all mechanical updates for the tick are resolved, the engine queries the `Psychology` of the player and any co-located companions for "Ambient" thoughts and incidental dialogue.
2.  **Compilation & Hand-off:** The engine compiles a complete package of all the tick's events (the player's action result, off-screen companion updates, Subject `Presence Effects`, and ambient psychology) and hands it off to the **`Narrative_Engine`**.
3.  **The Final Page:** The `Narrative_Engine` translates this package into the final, cohesive "page" of text that is presented to the player, at which point the game pauses, awaiting the action that will trigger the next tick.
