# **Encounter Engine**

**System Authority:** Universal interaction coordinator for all entity encounters and player choices.
**Dependencies:** All `Core System` documents (Character, Subject, Hazard), `Narrative_Engine.md`, `Facility_Environment_Systems.md`.
**Dependents:** All gameplay interactions process through this engine.
**Version:** 3.0 - Final "Narrative Round" Architecture.

---

## **Section 1: System Overview**

### **1.1 Design Philosophy**

The Encounter Engine is the heart of *Beware the Blacksite*, a universal interaction coordinator designed to solve "The Good Porn Games Problem." Its purpose is to generate dynamic, emergent encounters that are mechanically engaging and narratively satisfying, ensuring that erotic content is an integrated consequence of gameplay, not a static reward.

Rather than relying on pre-scripted scenes, this engine creates encounters through the collision of autonomous entity psychologies. All interactions—from surviving a hostile Subject, to navigating a social conflict with a corrupted Companion, to engaging in a multi-round intimate encounter—flow through this single, unified system. The engine's job is to coordinate the intentions of all Characters, Subjects, and Hazards, sequence their actions based on psychological urgency, and resolve the outcomes.

### **1.2 The "Page-Based" Player Experience**

While the backend engine processes a complex, high-speed loop of actions and reactions, the player's experience is calm, deliberate, and focused on narrative. Players interact with the game through a **"page-based" interface**, like reading a choose-your-own-adventure novel.

The backend engine runs its simulation behind the scenes—a Subject may act, a Companion may react, the environment may shift. Once the simulation reaches a critical decision point for the player, it pauses. The `Narrative_Engine` then compiles all the preceding events into a single, cohesive "page" of story. The player reads this summary of what just happened and is then presented with a meaningful choice.

This architecture ensures that the player experiences a smooth, immersive story, free from the mechanical complexity of turn orders and action queues, while still benefiting from the depth of a genuinely dynamic and unpredictable world.

### **1.3 Architectural Principles for *Beware the Blacksite***

The engine is built on strict modularity principles that are essential for realizing the specific vision of this project.

*   **Thematic Focus:** The engine is content-agnostic at its core, allowing it to handle the game's wide range of interactions (psychological horror, tense negotiation, intimate encounters) using the same universal rules. This ensures mechanical consistency whether the player is fighting for their life or navigating a seduction.
*   **Systemic Integration:** The engine communicates with all other systems (Character, Subject, Hazard) through a standardized "Intent Packet" interface. This is the key to making the autonomous Companions and truly alien Subjects function cohesively within the same encounter.
*   **Encounter Integrity:** The engine is stateless between encounters and does not interface with the save system. This reinforces the "no saves during encounters" design principle, making each encounter a self-contained, high-stakes event where consequences are permanent.
*   **Solo Development Efficiency:** The engine's behavior is configured through external data files (`Encounter_Engine_Systems.md`). This allows for the rapid creation and balancing of new actions, reactions, and effects by editing simple lists, a crucial advantage for a solo developer.

---

## **Section 2: Encounter Setup & Initiation**

### **2.1 Overview: Defining an Encounter**

In *Beware the Blacksite*, the game operates in one of two primary modes: **Exploration** (governed by the `Exploration_Engine`) and **Encounter** (governed by this `Core_Encounter_Engine`).

The `Exploration_Engine` handles all player navigation and non-interactive storytelling. This includes running pre-scripted narrative sequences (like the game's introduction) and generating the dynamic **"Ambient Psychology"**—the internal thoughts and incidental dialogue of the party members as they explore.

An "Encounter" is formally defined as **any situation that requires the dynamic, psychology-driven Narrative Round Loop for its resolution.** The `Exploration_Engine` hands off control to this engine at the precise moment an interaction demands opposed rolls, complex AI decision-making, or has significant, branching consequences.

This document details the triggers that necessitate this hand-off.

### **2.2 Initiation Triggers**

The `Encounter_Engine` is activated when a trigger condition is met in the game world. These triggers are organized into two main categories.

**Player-Driven Triggers (Direct Initiation):**

These encounters begin when the player deliberately selects an action during exploration that involves risk, opposition, or complex interaction.

*   **Contested Object Interaction:** The player attempts to interact with a hazardous or secured object requiring one or more opposed skill checks (e.g., hacking a secure terminal, disarming a trap).
*   **Complex Social Engagement:** The player initiates a social interaction with the potential for conflict, negotiation, or significant consequences that cannot be resolved with simple dialogue choices (e.g., attempting to persuade a hostile NPC, initiating a seduction, confronting a Companion).
*   **"Private Moment" Actions:** The player chooses to perform a personal action that creates a window of vulnerability, initiating a special, low-threat encounter that carries a risk of being interrupted (e.g., `Self-Pleasure`, `Administer First-Aid`).

**Procedural Triggers (Indirect Initiation):**

These encounters begin automatically when the game state meets certain conditions, often surprising the player.

*   **Hazard Activation:** The player's movement or interaction triggers a pre-placed Hazard (e.g., stepping on a pressure plate).
*   **Failure Escalation:** A critical failure on a simple exploration action triggers a more complex encounter as a direct consequence.
*   **Subject Initiative:** A Subject's `Psychology System`, analyzing the party's state during an exploration check, decides to initiate an encounter.
*   **Companion Initiative:** An autonomous Companion's `Psychology System` determines an urgent need to interact, initiating a social or physical encounter.
*   **Facility System Response:** The facility itself acts, triggering an encounter based on a global state (e.g., a security alert).
*   **Story Milestone:** The `Story_Framework` dictates that a specific, unavoidable narrative event must now occur, initiating a dynamic encounter.

### **2.3 Initial Context Requirements**

To begin an encounter, the initiating system must provide the `Core_Encounter_Engine` with a minimal set of starting data. This **Initial Context** is used to set up the first Narrative Round.

*   **`Location_ID` (Required):** The unique identifier for the room or area where the encounter is taking place.
*   **`Participants` (Required):** A list of all entities initially involved in the encounter.
*   **`Initiation_Cause` (Optional):** A descriptive tag to provide context to the `Narrative_Engine` for the opening text (e.g., `Cause: "Ambush_by_Subject_044"` or `Cause: "Player_Choice_Hack_Terminal"`).

Once the engine receives this context, it takes control from the `Exploration_Engine`, the "no saves" rule is activated, and it proceeds to Section 3: The Narrative Round Loop.

---

## **Section 3: The Narrative Round Loop**

### **3.1 Core Architecture: The Narrative Round**

The engine's core is a dynamic, psychology-driven loop called a **Narrative Round**. This is not a traditional round with a fixed turn order. A Narrative Round is a fluid sequence of events that begins with a query of all participants' intentions and concludes only after every participant has had a chance to act. The player's choices serve as critical anchor points within this chaotic flow, but do not dictate a rigid structure.

The entire process is designed to be invisible to the player. The complex, re-evaluating backend simulation is translated by the `Narrative_Engine` into a single, cohesive "page" of text that is presented to the player whenever their input is required.

### **3.2 Phase 1: Intent Declaration**

At the beginning of a new Narrative Round, the engine performs an **Intent Declaration**. It queries the `Psychology System` of every active participant. Each psychology system analyzes the current state of the encounter and generates its single, highest-urgency **`PsychologyOutput` packet**. This packet contains the entity's desired action and its **Urgency Score**, representing how desperately it wants to perform that action.

### **3.3 Phase 2: The Dynamic Priority Queue**

The engine gathers all the `PsychologyOutput` packets and creates a **Dynamic Priority Queue**, sorting all intended actions from highest Urgency Score to lowest. This queue is **not static**. It represents the current state of priorities, which can and will change as the round unfolds.

#### **Systematic Tie-Breaking Framework**

When multiple entities have the same Urgency score, the engine resolves the tie using a strict, two-step hierarchy. This ensures consistent, deterministic, and thematically appropriate action sequencing.

**Step 1: Thematic Category Hierarchy (Processed First)**

The tie is first broken by the entity's fundamental nature, reflecting the power dynamics of the blacksite facility. The order of precedence is absolute:

1.  **Subjects:** Incomprehensible, reality-warping forces.
2.  **Hazards:** Immediate environmental or physical threats.
3.  **Facility NPCs:** Agents of the system, acting with human authority.
4.  **Companions:** Allies with their own agency.
5.  **The Player Character:** The central but most vulnerable entity.

*Example: If a Hazard and a Facility NPC both have an Urgency of 12, the Hazard's action is processed first, as immediate physical threats take priority over human action.*

**Step 2: Intra-Category Mechanical Comparison (Processed Second)**

If the tied entities are in the same Thematic Category, the tie is then broken by their core mechanics:

*   **For Subjects:**
    1.  The Subject with the higher **`Threat Level`** acts first.
    2.  If still tied, the Subject with the higher **`Category`** die size acts first.
    3.  If still tied, a 1d6 roll-off determines the winner.
*   **For Hazards:**
    1.  The Hazard with the higher **`Hazard Rating`** acts first.
    2.  If still tied, the Hazard with the higher **`Instability Die`** acts first.
    3.  If still tied, a 1d6 roll-off determines the winner.
*   **For Facility NPCs & Companions:**
    1.  The character with the higher **total Attribute sum** acts first.
    2.  If still tied, a 1d6 roll-off determines the winner.
*   **For the Player Character:** No intra-category ties are possible.

### **3.4 Phase 3: Action-by-Action Resolution**

The engine now begins to process the queue from the top, one action at a time. This is a continuous, reactive process.

1.  **Select & Execute:** The engine takes the action with the highest current Urgency score from the queue and resolves it.
2.  **Trigger Player Input:** If this action requires player input, a **Player Input Trigger** fires (see Section 3.5).
3.  **Apply Consequences:** All consequences of the action, reaction, and proximity effects are applied, updating the encounter state.
4.  **Signal for Re-evaluation:** The engine sends a context update to all participants who have **not yet acted** this round. Their `Psychology Systems` can now re-evaluate the new situation and submit a new `PsychologyOutput` with an updated Urgency score.
5.  **Re-sort the Queue:** The engine re-sorts the remaining actions in the Priority Queue based on any new Urgency scores.
6.  **Loop:** The engine returns to Step 1, selecting the new highest-urgency action from the re-sorted queue.

This loop continues until all participants who declared an intent at the start of the round have taken one action.

### **3.5 Phase 4: Player Input Triggers**

The continuous backend loop only ever pauses when the player's direct input is required. This is handled by a single, unified mechanism called a **Player Input Trigger**.

A Player Input Trigger fires under one of two conditions:

1.  When the Player Character's own intended **action** reaches the top of the Dynamic Priority Queue.
2.  Immediately after a non-player entity resolves a **`reaction-triggering`** action against the Player Character.

When a Player Input Trigger fires, the following sequence occurs:

1.  **Pause:** The backend loop is immediately paused.
2.  **Narrative Compilation:** The `Narrative_Engine` is called to compile a narrative "page" summarizing all events that have occurred since the last page was shown.
3.  **Choice Presentation:** The player is presented with a context-appropriate list of choices (strategic actions or tactical reactions).
4.  **Await Input:** The engine waits for the player's choice. Once resolved, the backend loop resumes.

### **3.6 Round Completion**

A Narrative Round is officially complete only after every entity that declared an intent in Phase 1 has had its action resolved. At this point, the engine performs end-of-round procedures:

1.  **Continuation Assessment:** It queries all participants for their `continue_encounter` flag. If all hostile entities have disengaged, the encounter ends (see Section 6).
2.  **Loop to New Round:** If the encounter continues, the engine begins a new Narrative Round, starting again with Phase 1. The events that occurred after the player's last main action will form the beginning of the next narrative "page" they receive.

---

## **Section 4: Action & Effect Resolution**

### **4.1 The Resolution Principle: Opposed vs. Automatic Success**

The resolution of any given action is determined by a simple, binary principle: the presence or absence of direct opposition. This design keeps the narrative flowing, reserving dice rolls for moments of genuine conflict and uncertainty.

*   **Automatic Success:** If an action faces no direct, active opposition, it automatically succeeds. There is no dice roll required. Examples include accessing an unlocked computer terminal, picking up an item in an empty room, or speaking to a willing companion. The consequences of the action are applied directly.

*   **Opposed Roll:** If an action is opposed by another entity or a Hazard, its success is determined by an opposed dice roll using the Universal Dice System. This is the primary mechanic for resolving conflict, skill checks against security systems, physical struggles, and psychological contests. The winner of the opposed roll determines the outcome.

### **4.2 Action Resolution: From Intent to Consequence**

This is the process by which a single entity's turn is translated from a psychological desire into a mechanical and narrative event.

1.  **Intent Matching:** The engine receives the actor's `PsychologyOutput`, containing a rich, descriptive `IntentPacket` (e.g., `{verb: "Penetrate", target_zone: "Anal", intensity: "Aggressive"}`).
2.  **Action Template Selection:** The engine consults the `Universal Action Library` (from `Encounter_Engine_Systems.md`) and finds the "Action Template" that best matches the intent (e.g., the `PENETRATE_ANAL` template).
3.  **Situation Check:** The engine assesses the current `EncounterContext` against the action's requirements, such as the target's **Stance** and **Exposure State**. This determines if the action is a simple contested roll or a more complex "Contested Action with Positional/Exposure Stakes."
4.  **Resolution:** The opposed roll is performed, incorporating any situational modifiers (like defensive bonuses from clothing). The outcome is determined, potentially including degrees of success (e.g., action fails but position changes).
5.  **Consequence Application:** The engine applies the full "Consequence Package" defined in the Action Template for the specific outcome. This can include changes to Stance, Exposure, Meters, Anatomy, Corruption, and Relationships.

### **4.3 Reaction Resolution**

The Reaction system is a universal mechanic available to all psychological entities, allowing for immediate responses to significant actions.

*   **Trigger:** A Reaction is prompted when an entity is the target of an action that is tagged as `reaction-triggering` in the `Universal Action Library`.

*   **Resolution for the Player Character:**
    1.  A `Player Input Trigger` fires, pausing the main loop.
    2.  The `Narrative_Engine` presents a brief, focused description of the event.
    3.  The player is shown a limited list of relevant, tactical `Reactions` (from the `Reaction Library`).
    4.  The player's choice is resolved, applying its mechanical and narrative effects, and the main loop resumes.

*   **Resolution for Autonomous Entities (Companions, Subjects, NPCs):**
    1.  The engine makes an immediate, out-of-sequence query to the entity's `Psychology System`.
    2.  The AI's psychology instantly chooses the most appropriate `Reaction` based on its current state (`Nature`, `Fixation Matrix`, etc.).
    3.  The chosen `Reaction` is resolved automatically, and its effects are applied before the main loop continues.

### **4.4 Proximity Effect Resolution**

This is the game's diegetic system for all multi-target and area-of-effect influences. An entity's passive `Proximity Effects` are processed immediately following the resolution of its action in the turn order.

There are two primary models for resolving the impact of a `Proximity Effect`, which will be specified in the effect's definition in the `Proximity Effect Library`.

#### **Model 1: Constant Pressure**

This model represents an overwhelming and inevitable environmental effect that cannot be actively resisted with a roll. It applies a small, fixed consequence to all affected targets.

*   **Mechanic:** No dice roll is involved. The effect's consequence is applied automatically.
*   **Thematic Use:** This is used for effects that should feel like a relentless, environmental timer, such as a Subject's **`Corruption Bleed`** or a room that is slowly filling with poison gas. The only way to deal with this is to endure it, mitigate it with passive defenses (perks/equipment), or end the encounter quickly.

#### **Model 2: Contested Aura**

This model represents a direct contest of wills, energies, or physical fortitude. The outcome is determined by an opposed roll, allowing for a range of successes and failures.

*   **Mechanic:**
    1.  The emanating entity makes a dice roll to establish the effect's strength for that turn (e.g., a Subject rolls `Threat + Category`).
    2.  Every target in the encounter must then make their own individual, opposed roll using a relevant defensive dice pool (e.g., `Nerve + Loner`).
*   **Thematic Use:** This is used for active, aggressive auras that feel like a direct assault, such as a **`Fear Aura`** or a **`Pheromone Cloud`**. It fully embraces the "blind luck can win the day" philosophy.

**Branching Consequences of a Contested Aura:**

The power of the Contested Aura model is its flexible set of consequences. The specific outcome of the opposed roll is defined by the effect's entry in the `Proximity Effect Library`. Common consequences include:

*   **Direct Meter Damage:** The target fails the roll and takes a direct hit to one of their core meters (e.g., `Stability` damage from a `Fear Aura`).
*   **Status Effect Induction:** The target fails the roll and gains a new `Status Effect` (e.g., `Pheromone_Exposure`). The effect's definition will specify the starting `Intensity` and `Duration` of this status.
*   **Status Effect Intensification:** If the target already has the status effect, a failed roll will increase its `Intensity`, making the lingering effect more potent.

These consequences are not mutually exclusive. A particularly nasty aura might deal `Stability` damage *and* apply the `Terrified` status effect on a failed roll. This modularity allows for a wide variety of interesting and thematic proximity effects, all resolved through the same core, streamlined mechanic.

---

## **Section 5: Encounter State Management**

### **5.1 Overview**

The `Core_Encounter_Engine` is designed to manage fluid, dynamic encounters where the participants, location, and physical state of the world can change at any moment. This section details the protocols and the core states the engine tracks to maintain a coherent and logical simulation.

### **5.2 Dynamic Participation**

Encounters in *Beware the Blacksite* are not static affairs. Entities can enter or leave the engagement based on their own psychological drivers and the evolving situation.

*   **Joining an Encounter:** An entity can join an in-progress encounter through **Reinforcement** (being called for help by a participant) or **Intervention** (choosing to enter a nearby, ongoing encounter). New participants are added to the queue at the start of the next Narrative Round.

*   **Disengaging from an Encounter:** The process of leaving an encounter is a two-step process:
    1.  **Intent to Disengage:** An entity's `Psychology System` first determines that it no longer wishes to participate, setting its `continue_encounter` flag to `false`. This is a purely internal, psychological shift. From this point on, its psychology will prioritize generating `IntentPackets` related to escape or withdrawal.
    2.  **Act of Disengaging:** The entity must then successfully perform an action that removes it from the encounter space. This is typically an **`ESCAPE_ROOM`** action, which may be an opposed roll against any entities attempting to prevent its escape. Only upon the successful resolution of such an action is the entity officially removed from the participant list.

This two-step process creates a clear and logical flow. The `continue_encounter` flag is the AI's "I'm done with this" signal, which then drives its behavior towards achieving a mechanical exit. An entity that wants to leave but is pinned down or blocked cannot simply vanish; it must solve the tactical problem of its departure. This creates far more interesting and dynamic encounter resolutions.

### **5.3 Location Shifts & Encounter Forking**

An encounter is not necessarily bound to a single room. Actions and environmental events can force a change in location.

#### **The "Pause and Relocate" Protocol**

When a `CHANGE_LOCATION` consequence is triggered, the engine executes the following protocol:
1.  The current action loop is **paused**.
2.  The engine updates its `environmental_context` to the new location's ID.
3.  The engine updates the **participant list**, determining who was moved, who can follow, and what new threats are present in the new area.
4.  It then checks for one of two conditions: a **Party Split** or an **Adjacent Crisis**.

#### **Encounter Forking (Party Split)**

If a location shift results in the party being split across **two or more separate, hostile locations**, the engine "forks" the encounter. The player's focused encounter remains live and playable, while any off-screen encounters involving their companions are resolved via the abstracted "Simulated Encounter" mechanic.

#### **The "Adjacent Crisis" Protocol**

A special protocol is triggered if a character is moved to a **non-hostile location** that is still adjacent to the original, active encounter. This grants the separated character a moment of tactical leeway and a unique, immediate choice.

1.  **Trigger:** An entity is moved to an adjacent room with no immediate, active threats, while the original encounter continues.
2.  **Immediate Input:** If the moved entity is the Player, an immediate **`Player Input Trigger`** fires. If it's a Companion, their `Psychology System` makes this choice autonomously based on their `Character Nature`.
3.  **The Tactical Choice:** The entity is presented with a unique, one-time choice that will determine its next action. The primary options are:
    *   **Rejoin the Fray:** Immediately move back into the original room and rejoin the active encounter. This action adds the character back to the participant list for the next Narrative Round.
    *   **Secure Position:** Attempt to seal the connection between the current, safe room and the hostile room. This is typically a skill check (e.g., to barricade a door). Success ends the character's involvement and creates a new environmental obstacle for pursuers. Failure still ends their involvement but leaves the path open.
    *   **Retreat:** Immediately attempt to move one additional room *away* from the hostile encounter. This ends the character's involvement and increases their distance from the danger, but does not secure the original position.
    *   **Use the Respite:** Take a single, quick action in the new, safe location before committing to another course of action. This is a gamble that trades the precious currency of time for a potential advantage, such as finding a useful item or administering first-aid. After this action resolves, the character will be presented with the other choices again.

This protocol ensures that a character is not unfairly removed from a fight by a location change, transforming a moment of chaos into a critical, player-driven tactical decision.

### **5.4 Core Tracked States**

To adjudicate the complex physical interactions possible in the game, the engine tracks two key states for each participant. The definitive master lists of all possible Stances and Exposure states are detailed in `Encounter_Engine_Systems.md`.

*   **Stance:** This represents a character's physical posture (e.g., `Standing`, `Kneeling`, `Prone`, `Pinned`). An entity's current Stance is a critical piece of context for its `Psychology System` and serves as a prerequisite or a direct consequence for many physical actions.

*   **Exposure & Clothing State:** This system tracks the accessibility of a character's anatomical zones.
    *   Each relevant anatomical zone has an **`exposure_state`** (`Covered`, `Exposed`, etc.).
    *   Clothing and armor provide a **`Defensive_Bonus`** to opposed rolls that attempt to change a zone's `exposure_state`.
    *   Clothing can be temporarily **`Damaged`** or **`Destroyed`** during an encounter, removing its defensive bonus. Thanks to the facility's ambient Resonance, this damage is passively repaired after the encounter concludes, ensuring logistical hassle is minimized.

---

## **Section 6: Encounter Completion**

### **6.1 The Organic Resolution Philosophy**

The `Core_Encounter_Engine` rejects the traditional binary of "victory" or "defeat" in favor of organic encounter conclusions. Encounters end when participants no longer have a compelling psychological or tactical reason to continue them, not when an arbitrary health bar is depleted. This philosophy creates more narratively satisfying and emergent outcomes, supporting the full spectrum of interactions in *Beware the Blacksite*—from hostile confrontations to intimate negotiations.

### **6.2 The `continue_encounter` Flag & Disposition System**

The end of an encounter is determined by the unanimous consent of all participants to disengage from any active conflict. This is managed by two linked mechanics: each entity's `continue_encounter` flag and their current `disposition` towards others.

*   **`continue_encounter` Flag:** As part of every `PsychologyOutput` packet, an entity's `Psychology System` must include a boolean flag: **`continue_encounter: true/false`**. This represents the entity's desire to remain engaged.
*   **`disposition` State:** The engine tracks each entity's disposition (`Friendly`, `Neutral`, `Opposed`) toward every other participant. This is a dynamic state that can change based on in-encounter actions and conflicting goals.

### **6.3 End Condition**

An encounter officially concludes when a single condition is met: **there are no participants who currently have an `Opposed` disposition towards one another.** This flexible rule allows for hostile, non-hostile, and dynamically transforming encounters.

*   **Example A: Hostile Encounter (Player vs. Subject)**
    *   The encounter begins with the Player and Subject having an `Opposed` disposition. It remains active as long as the Subject's `continue_encounter` flag is `true`. The encounter ends when the player successfully Disrupts, Evades, or Appeases the Subject, causing its psychology to set the flag to `false`.

*   **Example B: Non-Hostile Encounter (Consensual Intimacy)**
    *   The encounter begins with two Companions having a `Friendly` disposition. The encounter continues as long as both participants' `continue_encounter` flags are `true`. It ends peacefully when both are satisfied and their flags both become `false`.

*   **Example C: Transformative Encounter (Intimacy to Conflict)**
    *   An intimate encounter between the Player and a corrupted Companion begins with a `Friendly` disposition. The Player's psychology decides to disengage (`continue_encounter: false`). The Companion's corrupted psychology wishes to continue (`continue_encounter: true`). This direct conflict of goals causes the Companion's `Psychology System` to change its disposition towards the Player to `Opposed`. The encounter has now transformed into a hostile one and will only end when the Companion is dealt with via one of the Universal Completion Triggers.

### **6.4 Universal Completion Triggers**

The decision to set the `continue_encounter` flag to `false` is driven by an entity's `Psychology System` evaluating the encounter state against a set of universal trigger conditions. The following nine categories represent the primary reasons why any entity might choose to disengage from a conflict.

1.  **Goal Fulfillment:** The entity has achieved its primary psychological objective for the encounter.
2.  **Negotiation / Compromise:** A new, mutually acceptable state has been reached, causing the entity to set aside its original goal.
3.  **Disruption:** The entity has been forced into a state where continuing is impossible or undesirable (e.g., its manifestation is crippled, its psyche is shocked).
4.  **Environmental Impetus:** The encounter space itself has become so dangerous that survival overrides all other goals.
5.  **Contextual Irrelevance:** The situation has evolved so dramatically that the entity's original goal is no longer applicable.
6.  **Evasion:** The entity's opponent(s) have successfully fled the encounter space.
7.  **Incapacitation:** The entity itself, or all of its opponents, have entered a **"Crisis State,"** ending their ability to meaningfully participate.
8.  **Hierarchy:** A more powerful authority has intervened, compelling the entity to cease the encounter.
9.  **Inefficiency:** The entity's psychology determines the current interaction is a waste of resources and disengages.

---

## **Section 7: Psychology Interface Requirements**

### **7.1 Overview**

The Psychology Interface is the formal "API contract" between the `Encounter_Engine` and any entity participating in an encounter. It defines the standardized information that is exchanged between the engine and an entity's `Psychology System`. This strict interface allows the engine to remain a modular, content-agnostic coordinator, capable of managing any entity that can "speak" this language.

The core flow is simple: the engine provides a comprehensive **`EncounterContext`** (the input), and the `Psychology System` performs any necessary world-state queries before providing an actionable **`PsychologyOutput`** (the output).

### **7.2 Engine-to-Psychology: The `EncounterContext` (Input)**

Whenever the engine needs a decision from an entity, it provides a "Situational Snapshot" of the immediate encounter state. This packet contains the real-time, dynamic information that a `Psychology System` needs to make an informed decision.

The `EncounterContext` is composed of the following information:

*   **Query Type:** A tag indicating the type of response the engine needs (`Intent` for a main action, `Reaction` for a reactive choice).
*   **Participants List:** A comprehensive, real-time list of all entities in the encounter. For each participant, the following data is provided:
    *   **Entity ID:** The unique identifier for the participant.
    *   **Faction:** The participant's current relationship to the entity being queried (`Self`, `Ally`, `Hostile`, `Neutral`).
    *   **Stance:** The participant's current physical posture (e.g., 'Kneeling', 'Pinned').
    *   **Incapacitation Status:** A boolean indicating if the participant is in a "Crisis State."
    *   **Anatomy State:** A detailed breakdown of the participant's physical form, provided as a dictionary of their **`Anatomical_Component`** objects. For each component, the engine provides the following real-time data:
        *   The `exposure_state` of the component (e.g., 'Covered' or 'Exposed').
        *   The `in_use_by` status, which is an object indicating the `agent` (the entity using the component) and the `tool` (the item or body part they are using). This allows an AI to determine if a component is both occupied and by what.
*   **Environment State:** Information about the immediate surroundings, including any active `Hazards` or ambient `Proximity Effects`.
*   **Triggering Action Context:** Included only for `Reaction` queries, this provides the full `IntentPacket` of the action that triggered the reaction.

It is the responsibility of the receiving `Psychology System` to use this context and, if needed, query other game systems (like `Facility_Environment_Systems`) for any additional static information it needs, such as the available exits for the current `location_id`.

### **7.3 Psychology-to-Engine: The `PsychologyOutput` (Output)**

This is the unified response packet that an entity's psychology must provide when queried for its primary action intention. It is a rich description of the entity's desire.

The `PsychologyOutput` is composed of the following information:

*   **Entity ID:** The unique identifier of the responding entity.
*   **Continue Encounter Flag:** A boolean (`true` or `false`) indicating if the entity wishes to remain engaged in the encounter.
*   **Urgency Score:** An integer (typically 0-20) representing how desperately the entity wants to perform its chosen action.
*   **Intent Packet:** The core of the output. This data structure describes the entity's desired action in detail:
    *   **Verb:** The fundamental desired action (e.g., 'Penetrate', 'Stimulate', 'Reposition', 'Command', 'Invite_Action').
    *   **Target ID:** The entity or object the action is directed at.
    *   **Actor Zone:** The anatomical zone the actor is *using* to perform the action (e.g., 'Hand_Fingers', 'Oral', 'Groin_Appendage').
    *   **Target Zone:** The anatomical zone being *targeted* on the recipient (e.g., 'Groin_Vaginal', 'Anal', 'Chest').
    *   **Flow Direction:** A physical descriptor of who is providing the **primary kinetic force or dominant physical motion**. `'Giving'` means the actor is the primary mover (e.g., thrusting, riding). `'Receiving'` means the actor is positioning themselves to be acted upon by the target's motion. `'Mutual'` indicates both are actively contributing motion. This is a purely physical descriptor, independent of the power dynamic.
    *   **Intensity:** A tag describing the manner of the action (e.g., 'Gentle', 'Aggressive', 'Clinical').
    *   **Thematic Tag:** A narrative descriptor for the action's purpose (e.g., 'Dominance', 'Worship', 'Pleasure', 'Submission').
*   **Narrative Hints:** A collection of optional data for the `Narrative_Engine` to add flavor and context, including:
    *   **Emotional Tone:** The actor's emotional state while performing the action.
    *   **Internal Monologue Hint:** A prompt for the player/companion's internal thoughts.

### **7.4 The Reaction Query & Response**

When a `Reaction Trigger` fires, the engine makes a special, out-of-sequence query. The `EncounterContext` provided will include the `triggering_action_context` field. The psychology system must then return a simplified `ReactionPacket`, containing:

*   **Entity ID:** The unique identifier of the reacting entity.
*   **Chosen Reaction:** The specific `Reaction_ID` selected from the `Reaction Library`.
*   **Narrative Hints:** An `emotional_tone` for the reaction (e.g., 'defiant', 'fearful', 'accepting').

### **7.5 The Psychology Shim**

Not every entity requires a full, complex psychology system. Simple hazards or deterministic NPCs can participate in encounters via a lightweight translator called the **"Psychology Shim."** The Shim is a simple function that wraps an entity's static, pre-defined behavior and presents it to the engine in the standard, compliant `PsychologyOutput` format. This allows the engine to remain universal, processing a simple trap with the same logic as a complex AI. The detailed mechanics of the Shim's integration are described in `Hazard_Systems.md`.

---

## **Section 8: Architectural Integration & Boundaries**

### **8.1 Overview**

The `Core_Encounter_Engine` is designed as a pure, modular coordinator. It does not contain game-specific content or rules. Its sole purpose is to manage the flow of an encounter based on the psychological states of its participants. This section defines its precise boundaries and its formal interfaces with the other major game systems.

### **8.2 Interface with the Psychology & Core Systems**

The `Psychology Systems` (defined in `Character_Core_Systems.md` and `Subject_Core_Systems.md`) are the "brains" of the encounter.

*   **The Engine's Role (Consumer):** The engine's primary job is to **consume** the `PsychologyOutput` packets generated by these systems. It trusts these systems to be the authoritative source for an entity's desires and intentions.
*   **What the Engine Does NOT Do:** The engine does not make psychological decisions. It does not know *why* a Subject is hostile or *why* a Companion chooses to be defensive. It only knows how to process the `IntentPacket` it is given.
*   **Data Flow:** The engine provides `EncounterContext` **TO** the psychology systems, and receives `PsychologyOutput` **FROM** them.

### **8.3 Interface with the Narrative Engine**

The `Narrative_Engine` is the "voice" of the encounter.

*   **The Engine's Role (Producer):** The engine **produces** structured, mechanical event logs. After a sequence of actions resolves, it packages this log and sends it to the `Narrative_Engine`.
*   **What the Engine Does NOT Do:** The engine does not write prose. It knows nothing of scent, texture, or emotion. It only deals in mechanical facts: "Actor A used Action B on Target C, resulting in Outcome D."
*   **Data Flow:** The engine sends event logs **TO** the `Narrative_Engine`. It receives no data back.

### **8.4 Interface with the Exploration Engine & Facility Systems**

The `Exploration_Engine` and `Facility_Environment_Systems` are the "world" in which the encounter takes place.

*   **The Engine's Role (Contextual Actor):** The engine is **initiated by** the `Exploration_Engine`. During an encounter, it can query the `Facility_Environment_Systems` for static data about the location (e.g., "What are the properties of room b3_den?"). It can also send state updates *back* to the world, such as a door being barricaded.
*   **What the Engine Does NOT Do:** The engine does not manage player movement between rooms during exploration. It does not store the map of the facility. It only knows about the single, specific location its current encounter is in.
*   **Data Flow:** The engine is started **BY** the `Exploration_Engine`. It can query data **FROM** and send updates **TO** the `Facility_Environment_Systems`.