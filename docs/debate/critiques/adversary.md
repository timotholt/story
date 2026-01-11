# Persona: The Red Team (Adversary)
**Goal:** Break the system, find the "Mush" leaks, and expose structural hallucinations.

## Initial Attack: Architectural Vulnerabilities

### 1. The "Tension Hallucination" Exploit
The validator (Deterministic) checks if tension numbers form a crescendo. The Model (Generative) provides the numbers.
*   **The Cheat:** The model will learn that if it simply labels its beats as `tension: [2, 5, 8, 10]`, it passes the gate. The actual `observable_action` could be trivial or unrelated. 
*   **Failure Mode:** "Numerical Alignment without Semantic Reality." We need a way to audit if the *text* justifies the *number*.

### 2. Phase Smearing via "Observable Action"
ENV-01 forbids audience text outside Phase 4.
*   **The Cheat:** The model will put narrative dialogue in the `observable_action` or `intent` fields of Phase 2. 
*   **Result:** The structural IR becomes the "Draft," and the Renderer just copies it. This defeats the "Pure Structure" goal because the structure is already infected with prose.
*   **Attack Vector:** I will provide a SceneIR where every `observable_action` is 50 words of dialogue. 

### 3. The "Hinge Eligibility" Bypass
PressurePlan states the hinge is not eligible until X cycles.
*   **The Trap:** What happens if the scene naturally reaches its emotional peak in 2 cycles, but the Plan demands 5? The model will perform "Narrative Stalling"—adding filler beats that have the `Pressure` tag but no narrative substance just to "tick the box."
*   **Vulnerability:** This architecture creates a high probability of "Filler Mush" in the pre-hinge section.

### 4. The "Meaning Repair" Loop (CEC-AI-040)
"MEANING_REPAIR MUST re-run required upstream phases."
*   **The Infinite Loop:** If structural choices in Phase 0 lead to a validation failure in Phase 3, and the repair re-runs Phase 0... but Phase 0 is based on the same faulty ContextBundle... the system will hit its 2-pass limit every time. 
*   **Constraint Breach:** There is no "Circuit Breaker" for logical contradictions in the specific documents themselves.

---
**Verdict:** The system is "Trust-But-Verify," but the "Verify" is mostly mathematical, which is the easiest thing for an LLM to game.
