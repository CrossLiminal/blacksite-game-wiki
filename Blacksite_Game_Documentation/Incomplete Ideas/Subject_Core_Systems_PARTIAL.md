# **Subject Core Systems**

**System Authority:** Defines the complete blueprint of a Subject entity.
**Dependencies:** `Project_Foundations.md`, `Character_Core_Systems.md`
**Dependents:** `Encounter_Engine.md`, and all systems that interact with Subjects.
**Version:** 2.0 - "Disruption & Insight" Framework

---

## **Introduction: The Subject Blueprint**

This document serves as the complete technical and mechanical blueprint for a Subject. It defines the foundational "stat block" of a cosmic horror entity (its Power Metrics and Classification), the core systems through which it enacts its will (**Corruption**) and through which it can be overcome (**Disruption**), and the comprehensive **Subject State Framework** that governs its alien, autonomous mind. This document defines what a Subject *is*, in direct contrast to the human framework of a Character.

---

## **Section 1: Foundational Mechanics (The "Stat Block")**

This section details the core, quantifiable mechanics that form the baseline of any Subject. These stats serve as the primary input for the universal dice system and represent a Subject's innate power, its methods of influence, and its fundamental vulnerabilities.

### **1.1 Core Power Metrics**

A Subject's raw power is defined by two fundamental metrics that establish its **baseline capabilities when unprovoked**. These stats represent the Subject in its default, PASSIVE state. As a Subject's anger and obsession grow, its power increases dramatically according to its unique Escalation Profile.

#### **Threat Level: A Scale of Baseline Operational Capacity**

Threat Level quantifies a Subject's baseline number of dice, representing its innate potential for harm and its fundamental operational capacity even when contained or passive.

*   **3 - Negligible:** A baseline for Subjects whose influence is highly localized. Even when passive, direct interaction is hazardous.
*   **4 - Minimal:** A baseline indicating a Subject that is a known, active hazard within its territory even at rest.
*   **5 - Moderate:** A baseline for Subjects whose standard passive state is a constant and recognized danger, actively shaping its immediate environment.
*   **6 - Significant:** A baseline indicating a Subject whose standard operations are a major threat. Even when passive, its influence is felt in adjacent sectors.
*   **7 - Severe:** A baseline for an apex predator entity. Its passive state is sufficient to exert supernatural pressure across an entire facility floor.
*   **8+ - Catastrophic:** A baseline for transcendent threats. The entity's very existence, even at rest, is capable of fundamentally altering the facility's reality.

#### **Category: A Scale of Intrinsic Supernatural Potency**

Category is a static value representing the intrinsic "wrongness" and reality-warping potential of a Subject's power. It determines the quality (die size) of its dice pool.

*   **d4 - Benign:** Its corrupting pathology is localized and does not spread without direct, sustained interaction.
*   **d6 - Volatile:** Its influence patterns are inherently unstable and can change without warning.
*   **d8 - Malignant:** Its nature is actively hostile. Its pathology is aggressive and seeks to systematically break down unprepared minds and bodies.
*   **d10 - Parasitic:** Its influence is inherently symbiotic, offering seemingly beneficial effects at a dangerous cost to the host's autonomy.
*   **d12 - Virulent:** Its influence is inherently expansionist and existentially threatens the operational integrity of its environment.
*   **d14 - Aberrant:** Its very existence is a violation of physical law. Its pathology is not merely corrupting, but physically and conceptually transformative.
*   **d16 - Primordial:** A foundational cosmic entity. Its pathology is a fundamental component of reality, and "containment" is merely a theoretical concept.

#### **Dynamic Escalation**

The Threat Level and Category listed in a Subject's profile represent its power at the **PASSIVE (9-11)** relationship state. As a Subject's disposition towards characters worsens to **ANNOYED**, **AGGRESSIVE**, or **VENGEFUL**, its capabilities increase dramatically.

This power progression is not uniform. Each Subject has a unique **Custom Escalation Profile** (detailed in the `Relationship State` component) that defines how its anger manifests. This can include, but is not limited to:
*   **Rolling more dice** (Power Escalation)
*   **Rolling larger dice** (Precision Escalation)
*   **Gaining non-statistical advantages** (Territorial Escalation)
*   **Applying more intense psychological pressure** (Intensity Escalation)

Therefore, a Subject's baseline stats must be understood as the starting point of a threat, not its upper limit.

### **1.2 Classification**

Classification defines the fundamental nature of a Subject's supernatural influence—its core **methodology** for interacting with and corrupting reality. A Subject's Classification determines the tools it prefers and the types of problems it is equipped to solve. While any Subject can be a vector for any type of corruption, its Classification dictates *how* it applies that influence.

#### **The Five Classifications**

*   **Biological**
    *   **Methodology:** The Body as the Weapon and the Medium.
    *   **Description:** Its influence is intrinsic to its physical, organic form. It operates through direct biological processes: pheromonal broadcasts, engineered spores, caustic secretions, and overwhelming physical imposition. Its actions are tangible, visceral, and rooted in a hyper-evolved or alien physiology.

*   **Psychometric**
    *   **Methodology:** The Mind as the Battlefield.
    *   **Description:** Its influence is intangible, acting directly upon the psyche and perception of its targets. It employs telepathic intrusion, psionic feedback, memory alteration, and the induction of hallucinatory states. Its actions are subtle, invasive, and designed to erode a target's sanity and sense of self.

*   **Thaumatological**
    *   **Methodology:** Reality as a System with Exploitable Rules.
    *   **Description:** Its power is derived from an external, structured system of supernatural laws. Its influence is channeled through ritualistic action, symbolic geometry, harmonic resonance, and the manipulation of arcane energies. Its power is potent but often contingent on specific conditions or protocols.

*   **Synthetic**
    *   **Methodology:** Technology as the Conduit for Supernatural Influence.
    *   **Description:** Its power is channeled through code, machinery, and networked systems. It operates via weaponized data, mind-altering firmware, nanite swarms, and the direct subversion of facility infrastructure. Its actions are systematic, precise, and exploit the intersection of technology and consciousness.

*   **Extradimensional**
    *   **Methodology:** Physics as a Suggestion, Not a Law.
    *   **Description:** Its influence is derived from its nature as an entity from outside consensual reality. It operates by creating localized violations of physical law, including non-Euclidean spatial distortions, temporal loops, and causal paradoxes. Its actions are fundamentally incomprehensible and reality-defying.

#### **Mechanical Implementation: The Scope of Influence**

A Subject's Classification creates tactical opportunities based on its operational scope.

*   **In-Scope Actions:** When a Subject performs an action that aligns with its Classification, it uses its full dice pool (`Threat Level` dice of `Category` size).
*   **Out-of-Scope Actions:** When a Subject is forced to perform an action that falls outside its core methodology, it is at a significant disadvantage. It suffers a **T-1 penalty**, rolling one fewer die than its current Threat Level.

#### **Tactical Assessment**

A Subject's psychology will always prioritize using its most effective, In-Scope tools to solve a problem. Characters cannot directly choose to make a Subject act Out-of-Scope.

However, tactical opportunities emerge when characters create scenarios that invalidate a Subject's primary methodology. By engineering a situation where a Subject's natural toolkit is rendered ineffective or irrelevant (e.g., presenting a purely logical data-puzzle to a Biological entity), characters can increase the probability that the Subject's AI will be forced to select a suboptimal, Out-of-Scope response to address the immediate threat. This transforms encounters from direct confrontations of power into puzzles of strategic problem-solving.

### **1.3 The Two-Vector Corruption System**

Corruption is the primary method by which a Subject systematically influences and transforms characters. This is not a temporary status effect, but the application of a permanent, supernatural "instruction packet" that fundamentally alters a character's being over time. This influence is delivered via two distinct vectors: a constant, passive aura and a focused, direct action.

#### **The Seven Corruption Tracks**

Each Subject's corrupting influence is categorized into one or more of the seven tracks. These descriptions define the Subject's ultimate *intent* for the transformation.

*   **Dominion (Power Dynamics):** To permanently reshape a character's understanding of and relationship with power, conditioning them to either seek control or find comfort in subjugation.
*   **Metamorphosis (Physical Transformation):** To initiate a persistent, creeping biological change, altering a character's physical form to better suit the Subject's thematic or practical needs.
*   **Enthrall (Mental Conditioning):** To install new compulsions and rewrite a character's thought processes, eroding their decision-making autonomy from within.
*   **Deviance (Moral Boundary Erosion):** To systematically dismantle a character's moral and ethical boundaries, supernaturally reconditioning their sense of desire and taboo.
*   **Exposure (Privacy Erosion):** To erode a character's relationship with privacy and observation, conditioning them to derive satisfaction from either watching or being watched.
*   **Communion (Ritualistic Bonding):** To forge an unnatural spiritual or emotional bond with a character, creating a psychological dependency that resembles worship or devotion.
*   **Efface (Identity Erosion):** To dissolve a character's core sense of self, overwriting the fundamental tenets of their personality and identity.

*Designer's Note: The specific mechanics for how a character processes and expresses corruption, including the progression of branching tracks like Dominion, are detailed in `Character_Core_Systems.md`. This section is solely concerned with the Subject's delivery of corruption points.*

#### **Vector 1: Corruption Bleed (The Aura)**

An active Subject's mere presence is a corrupting agent. This passive, environmental pressure represents the slow erosion of will from prolonged exposure to a cosmic horror.

*   **Mechanic:** At the end of every full Narrative Round, every character in the encounter is subjected to the Bleed.
*   **Application:** Each character gains a small, flat amount of corruption points. This is an irresistible environmental effect.
*   **Target Track:** This corruption is applied **only to the Subject's Primary Corruption Track**, reinforcing its core thematic influence.
*   **Value:** The amount of Bleed is determined by the Subject's `Category` die size, applying 1 point for a d4 and increasing by 1 for each step up in die size (e.g., d6 applies 2 points, d8 applies 3, and so on up to 7 points for a d16).

#### **Vector 2: Direct Application (The Action)**

When a Subject takes a focused action to corrupt a character, it delivers a significant payload of supernatural influence.

*   **Mechanic:** Direct Application is the consequence of a character failing to successfully resist a Subject's targeted corrupting action, typically resolved via an opposed roll.
*   **Base Corruption Calculation:** The potential amount of corruption is calculated as: **(Subject's Threat Level + Subject's Maximum Category Die Value)**.
*   **Track Distribution:** If the Subject's action succeeds, the base corruption value is distributed across its assigned tracks as follows:
    *   **Primary Track:** Receives 100% of the base value.
    *   **Secondary Track:** Receives 66% of the base value (rounded up).
    *   **Tertiary Track:** Receives 34% of the base value (rounded up).
*   **Character Mitigation:** The final percentage of the distributed corruption that is actually applied is determined by the outcome of the opposed roll. A character's successful tactical choices and reactions can significantly mitigate or even completely negate the corruption payload from a given action. Failure, however, results in the application of the full, unmodified amount.

### **1.4 The Disruption & Insight System**

While a Subject cannot be permanently destroyed, its manifestation can be destabilized. The Disruption & Insight system is the primary non-appeasement method for characters to tactically resolve a direct encounter with a Subject. This system transforms a confrontation from a test of endurance into a solvable puzzle that rewards intelligence and preparation.

#### **Insight: The Key to Vulnerability**

Insight is specific, actionable knowledge that exposes a critical flaw in a Subject's methodology or manifestation. Disruption actions are mechanically unavailable until the corresponding Insight has been acquired. Insights are discovered through exploration and direct interaction with the facility and its entities.

*Designer's Note: The specific mechanics for acquiring Insight (e.g., Research, Observation, Experimentation) are detailed in the `Exploration_Engine.md` and `Encounter_Engine.md` documents. False Insights, planted by hostile entities, may also exist within the facility's corrupted data.*

#### **Disruption: A Tactical Encounter Resolution**

A Disruption is a special, high-stakes action that, if successful, immediately ends the current encounter. It does not damage the Subject; instead, it attacks the fundamental anchors of its manifestation—be it a critical biological process, a sustaining belief structure, or an essential environmental condition—forcing an immediate retreat.

*   **Mechanic:** A Disruption is a difficult opposed roll using a specific action that is only unlocked by possessing the relevant Insight.
*   **Strategic Consequences:** Successfully Disrupting a Subject is an act of profound defiance. While it resolves the immediate tactical situation, it will almost always inflict significant negative damage to the `Relationship Score` with the Subject, causing it to escalate for future encounters.

*Designer's Note: The specific Disruption actions available for each Subject, along with their mechanical requirements and exact consequences, are defined in the `Encounter_Engine_Library.md` document.*

#### **Disruption Methodologies & Consequences**

The nature of a Disruption is often tied to the Subject's Classification, and attempting one is a high-risk, high-reward maneuver with a nuanced range of outcomes.

*   **Typical Approaches:** While any skillset can be used creatively, certain approaches are typically more effective against specific Classifications (e.g., chemical agents against Biologicals, symbolic desecration against Thaumatologicals).
*   **Multiple Insights:** If the party has acquired multiple valid Insights for a single Subject, they may choose which Disruption approach to attempt. Different Insights may unlock actions with different risk/reward profiles.
*   **Failure Stakes:** A failed Disruption attempt is catastrophic. At a minimum, it results in:
    1.  **Immediate Retaliation:** The Subject gains an immediate, out-of-turn action at maximum Urgency.
    2.  **Encounter Escalation:** The Subject's Threat Level temporarily increases by 1 for the remainder of the encounter.
    3.  **Insight Burn (Subject-Specific):** More intelligent Subjects may adapt to the failed attempt, rendering the used Insight obsolete and requiring a new one for future attempts.

#### **Degrees of Success**

The outcome of a Disruption attempt is determined by the result of the opposed roll.

*   **Critical Success (Win by 10+):** A clean and decisive Disruption. The encounter ends with minimal negative impact on the Relationship Score.
*   **Standard Success (Win by 1-9):** An effective Disruption. The encounter ends, but the Subject is enraged, causing standard negative damage to the Relationship Score.
*   **Marginal Success (Tie):** A messy, chaotic Disruption. The encounter ends, but the backlash inflicts a direct consequence on the acting character (e.g., significant `Stability` damage or a temporary negative Status Effect).
*   **Failure (Loss):** The Disruption fails, triggering the full Failure Stakes.

#### **Compound Disruptions**

More powerful Subjects require more complex solutions. Any Subject whose Threat Level is **6 (Significant)** or higher—either by default or through in-encounter escalation—requires a Compound Disruption.

*   **Mechanic:** These encounters are multi-stage puzzles. For example, the first successful Disruption might force a Subject to reveal its true, vulnerable form, which then requires a second, different Insight and Disruption action to finally defeat. This may require environmental setup and coordinated action between multiple characters.

---

## **Section 2: Subject Genesis Framework**

This section serves as the **"Designer's Handbook"** for the creation of all Subject entities. It contains the foundational principles, relational frameworks, and step-by-step templates required to build a new Subject that is mechanically sound, thematically consistent, and fully integrated with the project's core systems.

### **2.1 Constitutional Principles of Subject Design**

Before any mechanical or narrative design begins, any new Subject must adhere to the following two constitutional principles. These are immutable laws of the game's design, derived directly from the project's core philosophy.

#### **The "One Subject at a Time" Rule**

An encounter can only ever have one active Subject at a time. This is a foundational rule of both gameplay balance and in-universe physics.

*   **Mechanical Implication:** This rule focuses the procedural encounter system on a single, complex AI at a time, preventing the computational and gameplay chaos of multiple, competing Subject psychologies vying for control of the encounter loop. It ensures that the tactical focus for characters is always on solving the unique, high-stakes puzzle presented by a single, powerful entity, rather than being overwhelmed by a swarm of lesser threats.
*   **Thematic Justification:** A Subject's `Corruption Bleed` is not merely an aura but a distortion of local reality. The "auras" of two Subjects are fundamentally incompatible and would cause a catastrophic, mutually destructive feedback loop if they were to overlap in a single encounter space. This principle does not forbid encounters consisting of one Subject plus one or more Hazards.

#### **The Doctrine of Non-Cooperation**

There can be no true, lasting alliance with any entity classified as a Subject. All interactions must be understood as forms of managed corruption, temporary appeasement, or erotic accommodation.

*   **Mechanical Implication:** A character's `Relationship Score` with a Subject is a measure of its hostility or obsession, not friendship. A high score represents a Subject's indifference, which is the safest state for a character.
*   **Thematic Justification:** Subjects are alien intelligences whose goals are, at a fundamental level, incomprehensible and antithetical to human autonomy. Any apparent partnership or mutual benefit must always be framed as a component of a larger system of predation that serves the Subject's inscrutable needs. A designer must never create a Subject that can become a genuine "ally" or "pet."
