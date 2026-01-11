# Persona: Implementation Lead
**Goal:** Feasibility, Tooling, and Roadmap.

## Initial Assessment: Build-Ready Status

### 1. Data Contract Readiness
The `SceneGraph` v1.6 is extremely detailed. From a dev perspective, we have enough here to build the **Phase Controller**. 
*   **Infrastructure Need:** We need a `PhaseManager` class that handles the state machine ( -2 to PR). Each transition must check the `DiagnosticsArtifact`.

### 2. UI/UX: The "Hard Gate" Problem
In "Interactive Mode," the system stops.
*   **Drafting the Wizard:** We need a "Wizard" that can display the `SceneIR` (the beats) *before* the rendering. If the user hates the beats, they must be able to "Reject & Repair" right then.
*   **Tooling:** A "Tension Visualizer" (line graph) for the `EnergyCurveSpec` would be a high-value internal tool for debugging the model's output.

### 3. The "Phase Envelope" Linter
We need a literal "String Scanner" or "Linter" for ENV-01/02.
*   **Implementation:** Before the output is shown to the user or passed to the next phase, a script must check for forbidden patterns (e.g., Markdown Headers, dialogue indicators, "PANEL X").
*   **Auto-Rejection:** This should be the first "Hard Gate" to save on token costs.

### 4. Milestone 1 Recommendation
Don't build the whole engine yet. Build a **"Kernel Validator Stub"**.
*   **Component 1:** A Python script that takes a JSON `SceneIR` and runs the BEAT/PATTERN/ENERGY gates.
*   **Goal:** Prove the "Deterministic Validator" can catch a "Red Team Hallucination."

---
**Verdict:** High coding complexity, but we have a clear specification. Phase 2 (SceneIR) is the "Skeleton" that everything hangs on.
