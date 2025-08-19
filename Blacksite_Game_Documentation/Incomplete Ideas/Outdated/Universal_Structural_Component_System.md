# **The Universal Structural Component System**

**System Authority:** Unified framework for defining the physical form of all entities (Characters, Subjects, Hazards).
**Dependencies:** None - this is a foundational framework.
**Dependents:** `Character_Core_Systems.md`, `Subject_Core_Systems.md`, `Core_Encounter_Engine.md`
**Version:** 2.0 - Standardized Component Architecture

---

## **1. System Overview & Design Philosophy**

The Universal Structural Component System is a unified framework for defining the physical (or quasi-physical) form of any entity in the game, from human Characters to alien Subjects and corporeal Hazards.

### **Core Principles**

1. **Universal Integration:** A single, consistent component architecture used by all entities, simplifying the `Core_Encounter_Engine`.
2. **Modular Flexibility:** Forms are collections of modular components, allowing everything from standard humans to eldritch horrors.
3. **Function over Form:** Components define what they can do and what can be done to them, not rigid anatomical labels.

---

## **2. The Component Family**

An entity's form consists of three distinct component types:

### **2.1 Descriptive Components**
- **Purpose:** Narrative flavor and appearance data for the `Narrative_Engine`
- **Structure:** ID + narrative tags (no mechanical values)
- **Not targetable in encounters**

```
Descriptive_Component {
    id: String              # Unique identifier
    tags: Array[String]     # Pure narrative descriptors
}
```

### **2.2 Systemic Components**  
- **Purpose:** Passive/active effects that influence the game world
- **Structure:** ID + mechanical properties that create effects
- **Not directly targetable, but mechanically relevant**

```
Systemic_Component {
    id: String              # Unique identifier
    properties: Dictionary  # Mechanical values that affect gameplay
}
```

### **2.3 Interactive Components**
- **Purpose:** Physical interaction points for the `Core_Encounter_Engine`
- **Structure:** Full mechanical framework for encounter resolution
- **Directly targetable in encounters**

```
Interactive_Component {
    # See Section 6 for full structure
}
```

---

## **3. Core Capabilities & Receptivities**

The system uses a minimal set of enums to define all possible interactions:

```
enum Capability {
    CAN_PENETRATE,      # Penis, fingers, tongues, tentacles
    CAN_MANIPULATE,     # Hands, tongues, tentacles, feet
    CAN_SQUEEZE,        # Thighs, hands, internal muscles
    CAN_STRIKE          # Hands, feet, tails, implements
}

enum Receptivity {
    ACCEPTS_PENETRATION,   # Vagina, anus, mouth, etc.
    ACCEPTS_MANIPULATION,  # Most components
    ACCEPTS_CONSTRICTION,  # Neck, limbs
    ACCEPTS_IMPACT         # Buttocks, face, breasts
}
```

For an action to be valid, the actor's component must have the required `Capability` and the target must have the matching `Receptivity`.

---

## **4. Standardized Property Scales**

All quantifiable properties use one of three universal scales:

- **Magnitude Scale (1-10+):** Physical measurements (Size, Capacity, Strength, Force)
  - 1-2: Minimal
  - 3-4: Below Average  
  - 5-6: Average
  - 7-8: Above Average
  - 9-10: Exceptional
  - 11+: Supernatural

- **Sensitivity Scale (1-5):** Responsiveness to stimuli
  - 1: Numb
  - 2: Low
  - 3: Normal
  - 4: High
  - 5: Hypersensitive

- **Control Scale (1-5):** Conscious mastery over function
  - 1: No Control
  - 2: Minimal
  - 3: Moderate
  - 4: Good
  - 5: Perfect

---

## **5. Required Properties by Capability/Receptivity**

Each capability and receptivity mandates specific properties:

### **CAN_PENETRATE**
```
Required Properties:
- size: Magnitude (1-10+)
- shape: String ("Human", "Canine", "Equine", "Tentacle", etc.)
- features: Array (["Knot", "Sheath", "Flare", "Ridged", "Barbed"])
- firmness: Magnitude (1-10+)
```

### **ACCEPTS_PENETRATION**
```
Required Properties:
- capacity: Magnitude (1-10+)
- depth: Magnitude (1-10+)
- elasticity: Magnitude (1-10+)
- sensitivity: Sensitivity (1-5)
- texture: String ("Smooth", "Ribbed", "Textured")
- features: Array (["Self_Lubricating", "Muscular", "Modified"])
- lubrication: Magnitude (1-10+)
```

### **CAN_MANIPULATE**
```
Required Properties:
- dexterity: Control (1-5)
- grip_type: String ("Precise", "Crushing", "Gentle", "Clawed")
- features: Array (["Sticky", "Webbed", "Extra_Joints"])
```

### **CAN_SQUEEZE**
```
Required Properties:
- strength: Magnitude (1-10+)
- surface_area: String ("Small", "Medium", "Large", "Extensive")
- features: Array (["Soft", "Firm", "Lactating", "Furred"])
```

### **CAN_STRIKE**
```
Required Properties:
- force: Magnitude (1-10+)
- impact_type: String ("Blunt", "Sharp", "Stinging")
- features: Array (["Clawed", "Spiked", "Electrified"])
```

### **ACCEPTS_CONSTRICTION**
```
Required Properties:
- resilience: Magnitude (1-10+)
- vital_type: String ("Airway", "Blood_Flow", "Neural")
- features: Array (["Reinforced", "Sensitive", "Protected"])
```

### **ACCEPTS_IMPACT**
```
Required Properties:
- padding: Magnitude (1-10+)
- sensitivity: Sensitivity (1-5)
- features: Array (["Bruises_Easily", "Scarred", "Toughened"])
```

---

## **6. Interactive Component Structure**

```
Interactive_Component {
    # Core Identifiers
    id: String                    # Unique identifier
    zone: String                  # Body region for targeting
    feature_type: String          # High-level categorization
    
    # Action Framework
    capabilities: Array[Capability]
    receptivities: Array[Receptivity]
    
    # Required Properties (based on capabilities/receptivities)
    properties: Dictionary
    
    # Dynamic State
    exposure_state: Enum          # Covered/Partially_Exposed/Fully_Exposed
    condition: Enum               # Normal/Sore/Damaged/Numb/Sensitized
    in_use_by: Dictionary         # {agent: entity_id, tool: component_id}
    
    # Modifications
    modifications: Array          # Piercings, tattoos, brands, etc.
}
```

---

## **7. Size Mismatch & Accommodation Mechanics**

The Resonance Adaptation Field allows survival of impossible interactions with consequences:

### **Size Differential = Target.capacity - Actor.size**

- **Extreme Mismatch (≤ -5):** Major Vitality damage + "Severe_Trauma" status
- **Severe Mismatch (-4 to -3):** Moderate Vitality damage + "Stretched" status  
- **Moderate Mismatch (-2 to -1):** Minor Vitality damage + "Sore" status
- **Comfortable Match (0 to +2):** No penalties
- **Loose Match (≥ +3):** Reduced stimulation effectiveness

### **Accommodation Trauma Status Effect**
Multi-stage adaptation process:
1. **"Raw":** Significant penalties, Vitality drain
2. **"Tender":** Moderate penalties, hypersensitivity
3. **"Adapted":** Penalties fade, capacity permanently increases by 1

---

## **8. Standard Humanoid Template**

### **Interactive Components**

```
mouth_01:
    zone: "Head"
    capabilities: [CAN_PENETRATE, CAN_MANIPULATE]
    receptivities: [ACCEPTS_PENETRATION]
    properties: {
        # From CAN_PENETRATE (tongue)
        size: 2,
        shape: "Flexible",
        features: [],
        firmness: 3,
        # From CAN_MANIPULATE (tongue)
        dexterity: 3,
        grip_type: "Gentle",
        # From ACCEPTS_PENETRATION
        capacity: 4,
        depth: 5,
        elasticity: 3,
        sensitivity: 3,
        texture: "Smooth",
        lubrication: 3,
        # Component-specific
        gag_control: 3,
        teeth_type: "Human"
    }

hands_01:
    zone: "Arms"
    capabilities: [CAN_PENETRATE, CAN_MANIPULATE, CAN_SQUEEZE, CAN_STRIKE]
    receptivities: [ACCEPTS_MANIPULATION]
    properties: {
        # From CAN_PENETRATE (fingers)
        size: 2,
        shape: "Tapered",
        features: [],
        firmness: 4,
        # From CAN_MANIPULATE
        dexterity: 5,
        grip_type: "Precise",
        # From CAN_SQUEEZE
        strength: 4,
        surface_area: "Medium",
        # From CAN_STRIKE
        force: 3,
        impact_type: "Blunt",
        # From ACCEPTS_MANIPULATION
        sensitivity: 2
    }

feet_01:
    zone: "Legs"
    capabilities: [CAN_MANIPULATE, CAN_SQUEEZE, CAN_STRIKE]
    receptivities: [ACCEPTS_MANIPULATION]
    properties: {
        dexterity: 2,
        grip_type: "Clumsy",
        strength: 3,
        surface_area: "Small",
        force: 4,
        impact_type: "Blunt",
        sensitivity: 2
    }

penis_01: (conditional - if present)
    zone: "Groin"
    capabilities: [CAN_PENETRATE]
    receptivities: [ACCEPTS_MANIPULATION]
    properties: {
        size: 5,
        shape: "Human",
        features: [],
        firmness: 4,
        sensitivity: 4
    }

vagina_01: (conditional - if present)
    zone: "Groin"
    capabilities: [CAN_SQUEEZE]
    receptivities: [ACCEPTS_PENETRATION, ACCEPTS_MANIPULATION]
    properties: {
        strength: 3,
        surface_area: "Small",
        features: [],
        capacity: 5,
        depth: 6,
        elasticity: 4,
        sensitivity: 4,
        texture: "Ribbed",
        lubrication: 3
    }

anus_01:
    zone: "Groin"
    capabilities: [CAN_SQUEEZE]
    receptivities: [ACCEPTS_PENETRATION, ACCEPTS_MANIPULATION]
    properties: {
        strength: 3,
        surface_area: "Small",
        features: [],
        capacity: 3,
        depth: 8,
        elasticity: 3,
        sensitivity: 3,
        texture: "Smooth",
        lubrication: 1
    }

clitoris_01: (conditional - if present)
    zone: "Groin"
    capabilities: [] # Can gain CAN_PENETRATE if size >= 4
    receptivities: [ACCEPTS_MANIPULATION]
    properties: {
        sensitivity: 5,
        size: 1,
        arousal_response: 5
    }

urethra_01: (universal)
    zone: "Groin"
    capabilities: []
    receptivities: [ACCEPTS_PENETRATION, ACCEPTS_MANIPULATION]
    properties: {
        capacity: 1,
        depth: 4,
        elasticity: 2,
        sensitivity: 4,
        texture: "Smooth",
        features: [],
        lubrication: 1
    }

testicles_01: (conditional - if present)
    zone: "Groin"
    capabilities: []
    receptivities: [ACCEPTS_MANIPULATION, ACCEPTS_IMPACT]
    properties: {
        sensitivity: 4,
        padding: 1,
        quantity: 2
    }

nipples_01:
    zone: "Chest"
    capabilities: []
    receptivities: [ACCEPTS_MANIPULATION, ACCEPTS_IMPACT]
    properties: {
        sensitivity: 4,
        padding: 2,
        size: 1,
        state: "Normal" # Can be "Puffy", "Inverted", "Erect"
    }

surface_chest:
    zone: "Chest"
    capabilities: [CAN_SQUEEZE]
    receptivities: [ACCEPTS_MANIPULATION, ACCEPTS_IMPACT]
    properties: {
        strength: 2,
        surface_area: "Large",
        features: [], # Can include ["Breasts", "Lactating"]
        sensitivity: 2,
        padding: 3
    }

surface_hips:
    zone: "Hips"
    capabilities: [CAN_SQUEEZE]
    receptivities: [ACCEPTS_MANIPULATION, ACCEPTS_IMPACT]
    properties: {
        strength: 3,
        surface_area: "Large",
        features: [],
        sensitivity: 2,
        padding: 4
    }

surface_legs:
    zone: "Legs"
    capabilities: [CAN_SQUEEZE]
    receptivities: [ACCEPTS_MANIPULATION]
    properties: {
        strength: 4,
        surface_area: "Extensive",
        features: [],
        sensitivity: 2
    }

vulnerable_neck:
    zone: "Head"
    capabilities: []
    receptivities: [ACCEPTS_CONSTRICTION, ACCEPTS_MANIPULATION]
    properties: {
        resilience: 2,
        vital_type: "Airway",
        features: [],
        sensitivity: 3
    }
```

### **Systemic Components**

```
chemistry_01:
    properties: {
        pheromone_production: 3,
        pheromone_receptivity: 3,
        heat_cycle_state: "None",
        heat_cycle_intensity: 0,
        scent_signature: "Natural_Human"
    }

senses_01:
    properties: {
        vision_acuity: 5,
        hearing_acuity: 5,
        scent_acuity: 3,
        touch_sensitivity: 3,
        special_senses: []
    }

breeding_signals_01:
    properties: {
        fertility_display: 3,
        attraction_modifier: 3,
        territorial_marking: false,
        breeding_appeal: 3 # Derived value
    }
```

### **Descriptive Components**

```
appearance_01:
    tags: ["average_height", "medium_build", "brown_hair", "blue_eyes"]

voice_01:
    tags: ["feminine_pitch", "clear_tone", "standard_accent"]
```

---

## **9. Example: Human Female Character**

```
Character: Sarah (Human Female, Tier 1)

INTERACTIVE COMPONENTS:
- mouth_01 (standard template)
- hands_01 (standard template)
- feet_01 (standard template)
- vagina_01 (present)
- clitoris_01 (present)
- urethra_01 (standard template)
- anus_01 (standard template)
- nipples_01 (standard template with features: ["Breasts"])
- surface_chest (with features: ["Breasts", "D_Cup"])
- surface_hips (standard template)
- surface_legs (standard template)
- vulnerable_neck (standard template)

SYSTEMIC COMPONENTS:
- chemistry_01 (standard template)
- senses_01 (standard template)
- breeding_signals_01 (standard template)

DESCRIPTIVE COMPONENTS:
- appearance_01: {tags: ["5ft_6in", "athletic_build", "red_hair", "green_eyes", "freckles"]}
- voice_01: {tags: ["alto_pitch", "warm_tone", "midwest_accent"]}

INITIAL STATES:
- All components: exposure_state: "Covered", condition: "Normal"
- All in_use_by: null
- All modifications: []
```

This character has all standard human female anatomy with no modifications, ready to be transformed through gameplay and corruption.

---

## **10. Subject Example: Den Mother**

```
Subject: Den Mother (Modified Humanoid Female Template)

STARTING TEMPLATE: Humanoid_Female

MODIFICATIONS FROM TEMPLATE:
- REMOVED: vagina_01 (replaced by pseudo-penis)
- REMOVED: clitoris_01 (became the pseudo-penis)
- ADDED: pseudo_penis_01 (enlarged clitoris)
- ADDED: urethra_01 (inside pseudo-penis)
- MODIFIED: mouth_01 → muzzle with fangs
- MODIFIED: hands_01 → clawed version
- KEPT: breasts, nipples, anus, all surface components

UNIQUE INTERACTIVE COMPONENTS:

- pseudo_penis_01:
    zone: "Groin"
    capabilities: [CAN_PENETRATE]
    receptivities: [ACCEPTS_MANIPULATION]
    properties: {
        size: 8, 
        shape: "Tapered", 
        features: ["Knot", "Barbed", "Retractable"],
        firmness: 5, 
        sensitivity: 4,
        pheromone_secretion: 6
    }

- urethra_01:
    zone: "Groin" 
    capabilities: []
    receptivities: [ACCEPTS_PENETRATION]
    properties: {
        capacity: 3,
        depth: 8, 
        elasticity: 2,
        sensitivity: 5,
        texture: "Smooth",
        features: [],
        lubrication: 2
    }

- mouth_01: (modified from template)
    zone: "Head"
    capabilities: [CAN_PENETRATE, CAN_MANIPULATE, CAN_STRIKE]
    receptivities: [ACCEPTS_PENETRATION]
    properties: {
        # Standard mouth properties with modifications
        size: 3, shape: "Tapered", features: [],
        firmness: 4, dexterity: 3, grip_type: "Crushing",
        force: 6, impact_type: "Sharp", capacity: 5,
        depth: 6, elasticity: 3, sensitivity: 3,
        texture: "Rough", lubrication: 4,
        # Unique properties
        teeth_type: "Carnivore", 
        jaw_strength: 7
    }

- clawed_hands_01: (modified from template)
    zone: "Arms"
    capabilities: [CAN_MANIPULATE, CAN_STRIKE, CAN_SQUEEZE]
    receptivities: [ACCEPTS_MANIPULATION]
    properties: {
        # Modified from human hands
        size: 3, shape: "Clawed", features: ["Clawed"],
        dexterity: 3, grip_type: "Crushing",
        strength: 8, surface_area: "Medium",
        force: 7, impact_type: "Sharp",
        sensitivity: 2
    }

ADDITIONAL SYSTEMIC COMPONENTS:
- pheromone_glands_01:
    properties: {
        aura_radius: 5, 
        effect_type: "Heat_Inducing",
        arousal_pressure: 4, 
        intensity_in_nest: 7
    }

STANDARD HUMANOID COMPONENTS RETAINED:
- feet_01, anus_01, nipples_01, surface_chest (with breasts), 
- surface_hips, surface_legs, vulnerable_neck
- chemistry_01, senses_01 (modified for enhanced smell), breeding_signals_01
```

This demonstrates how Subjects are built by modifying the standard humanoid template rather than creating from scratch.