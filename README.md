# Digital Traffic Light Control System

A purely digital hardware design for an intersection traffic light controller. This project utilizes discrete logic gates and JK flip-flops to dynamically manage traffic flow based on vehicle detection and precise timing counters, completely eliminating the need for analog timing components like 555 timers.

---

## 🚀 Key System Features
* **Dynamic Vehicle Detection:** The system optimizes traffic flow by prioritizing the main street's green light. State transitions are only initiated when a vehicle physically triggers the side street's sensor.
* **Precise Digital Timing:** Utilizes cascaded counters built entirely from JK flip-flops to enforce strict signal durations.
* **Pure Logic Implementation:** Avoids unreliable analog RC timing circuits, relying entirely on combinatorial logic gates to process counter outputs and execute seamless signal transitions.
* **Robust State Memory:** Employs discrete flip-flops to securely latch and store the active operational state of the intersection lights.

---

## ⏱️ Timing Specifications

The digital counters are strictly calibrated to enforce the following signal durations before evaluating the next state transition:
* **Main Street Green Light:** 25 Seconds
* **Transition / Yellow Light:** 4 Seconds 

---

## 📐 System Architecture

The control system is divided into three primary digital subsystems:

1. **State Memory (The Registers):** A network of JK Flip-Flops that hold the current active state of the intersection (e.g., Main Green / Side Red).
2. **Timing Counters:** A synchronous counting circuit built from flip-flops that increments with the clock. It generates the exact 25-second and 4-second delays required for safe intersection management.
3. **Combinatorial Control Logic:** A network of AND, OR, and NOT gates that actively reads the vehicle detection sensors and the current timer values to determine exactly when to trigger the flip-flops into the next state.

### High-Level Signal Flow

```text
[ Vehicle Detection Sensor ] ──┐
                               ▼
[ Clock ] ──► [ JK Flip-Flop Timing Counters ] ──► [ Combinatorial Logic Network ]
                                                           │
                                                           ▼
[ Side Street Signals ] ◄── [ JK State Memory ] ◄──────────┘
[ Main Street Signals ] ◄──

🔬 Simulation & Verification

This logic circuit was successfully modeled and validated using digital simulation software. The simulation confirms that the counter resets properly upon state changes, the logic gates correctly route the priority constraints, and the intersection never enters an unsafe state (e.g., Green-Green).
