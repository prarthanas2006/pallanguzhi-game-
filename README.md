# Qiskit Fall Fest 2026 — Project Submission Template
**IIIT Kottayam Quantum Hackathon (24-Hour Sprint)**

> ⚠️ **CRITICAL INSTRUCTIONS FOR PARTICIPANTS:**
> 1. **Do NOT rename or delete the section headings** below. The automated AI evaluation and filtering system relies on this exact Markdown structure to parse and grade your project.
> 2. Replace all placeholder text enclosed in `[brackets]` with your project's details.
> 3. **Commit History Audit:** All project commits must be timestamped strictly within the 24-hour hackathon window (between **October 10, 2026 at 7:05 PM** and **October 11, 2026 at 7:05 PM**). Commits observed outside this window will result in **immediate disqualification**.
> 4. Ensure all Jupyter Notebooks have their cells **run and outputs displayed** before pushing.
> 5. Starter resources and reference guides are located in the [`references/`](./references/) folder.
> 6. **Tech Stack Flexibility:** You are free to use any external frameworks/technologies (e.g., Streamlit, React, Pygame, FastAPI, NetworkX) for your frontend, app logic, or classical baselines. However, **Qiskit MUST power the quantum core** of your project.
> 7. **Full Event Guide & Rules:** For full schedule details, track inspirations, submission steps, and grading focus areas, refer to [`HACKATHON_GUIDE.md`](./HACKATHON_GUIDE.md).

*(You may delete the instructions box above when preparing your final repository submission)*

---

# Project Title

## Project Metadata

* **Project Title:** `[Pallanguzhi game incorporating Qiskit quantum circuit simulations]`
* **Team Name:** `[Prarthana S]`
* **Chosen Track:** `[Track 1: Quantum Games & Interactive Puzzles OR Track 2: Open-Domain Optimization & Real-World Solvers]`
* **Video Presentation Link:** `[https://drive.google.com/file/d/1vjVd27F2lJEN7ppj3RCicBIIjUJcfZwj/view?usp=drive_link]`
  *(⚠️ Crucial: Ensure link access is set to "Anyone with the link can view" on Google Drive or "Unlisted / Public" on YouTube. Locked/inaccessible links cannot be scored!)*
* **Live Demo Timestamp in Video:** `[06:25]` *(e.g., "Demo starts at 03:45")*

### Team Members (Max 4 members)
| Name | Email | GitHub Username |
| :--- | :--- | :--- |
| `[Prarthana S]` | `[prarthana.s2006@gmail.com]` | `[@prarthanas2006]` |


---

## 1. Project Overview & Motivation

* **Summary (3–4 sentences):**  
  `[Quantum Pallanguzhi, an interactive digital version of the traditional Tamil board game Pallanguzhi, enhanced with quantum computing using Qiskit.You play against an AI opponent that uses measurement outcomes from a three-qubit quantum circuit to select a valid pit.Three Hadamard gates create a superposition of eight possible outcomes, which are measured to select pits.A two-qubit entangled Bell-state circuit generates correlated measurement outcomes. Depending on the result, two opposite pits either each gain two stones or remain unchanged.]`

* **Why this problem / game?**  
  `[I actually wanted to see the digital version of some Indian traditional game in action and also to learn how quantum generated measurements influences gameplay.]`

---

## 2. Quantum Architecture & Mechanics

* **Core Quantum Principles Used:**  
  `[Superposition (H gate), Quantum Measurement , Quantum Entanglement (Bell states),Probabilistic outcomes]`

* **How the Quantum Circuit is Integrated:**  
  `[Quantum states are mapped to game actions through measurement outcomes. The Qiskit circuits generate possible outcomes, and the classical game logic translates those outcomes into pit selections or changes to the board.The game doesn't solve an optimization problem. The circuit does not guarantee a strategically strong move.]`

* **Circuit Details:**  
  * **Number of Qubits:** `[3 qubits for pit selection; 2 qubits for Quantum Link]`
  * **Key Gates Used:** `[H, CX, Measurement]`
  * **Primitives Used:** `[shot-based quantum circuit simulation using Qiskit Aer simulator]`
  * **Other Technologies Used:** `[Python, HTML, CSS, JavaScript and IPython display]`

```python
# Optional: Paste a representative snippet of your core Qiskit circuit code here
```

---

## 3. Repository Structure & How to Run

### Project Structure
```text
├── README.md               # Project documentation (this file)
├── requirements.txt        # Python dependencies
├── src/                    # Source code scripts or game application
│   └── main.py             # Main entry point (or streamlit app)
├── notebooks/              # Jupyter notebooks containing experiments
│   └── solution.ipynb      # Main runnable notebook with outputs
└── references/             # Hackathon reference guides (Track 1 & Track 2)
```

### Installation & Execution Instructions

> 💡 **Environment Recommendation:** This project was developed and tested using Google Colab. No local Python installation or physical quantum computer is required.

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/prarthanas2006/pallanguzhi-game-.git]
   cd [pallanguzhi-game-]
   ```
2. **Install dependencies:**
   ```bash
   !pip install qiskit qiskit-aer
   ```
3. **Run the project / demo:**
   ```bash
   # Open Google Colab.

Open the project notebook (.ipynb) from your GitHub repository, or upload it to Colab.

Run the notebook cells in order.

Wait for the interactive Quantum Pallanguzhi game board to appear.

Play against the AI and explore the Quantum Link feature and measurement statistics.

Note: The game uses Qiskit AerSimulator to simulate quantum circuits on a classical computer. A physical quantum computer is not required.

  
   ```

---

## 4. Implementation Walkthrough & Live Demo

* **Walkthrough of Gameplay / Optimization Pipeline:**  
  `[Walkthrough of Gameplay / Quantum Processing Pipeline

The Quantum Pallanguzhi game integrates quantum circuit simulation with a traditional Pallanguzhi-style game board. The implementation combines Python and Qiskit for quantum simulation with HTML, CSS, and JavaScript for the interactive interface and gameplay.

Step 1: Initialize the Game

The game initializes a board containing fourteen pits, with seven pits on each player's side. Each pit initially contains six stones. The interface provides options to play against the AI, activate the Quantum Link feature, and start a new game.

Step 2: Generate Quantum Measurement Outcomes

The Python program constructs a three-qubit circuit using Hadamard gates. These gates create an equal superposition of eight computational-basis states. The circuit is executed using Qiskit AerSimulator, and its measurement outcomes are collected for use during gameplay.

Step 3: Execute Player Moves

The player selects a pit through the graphical interface. The JavaScript game logic distributes the stones according to the implemented sowing rules and calculates captures. These operations are performed classically.

Step 4: Perform AI Pit Selection

During the AI's turn, the game consumes a sampled outcome from the three-qubit circuit. The outcome is mapped to a candidate pit, and the game checks whether the selected pit is valid and nonempty. The AI retries unsuitable candidates and uses a classical fallback if necessary. The selected move is then executed using the classical gameplay rules.

Step 5: Activate Quantum Link

When the player activates Quantum Link, the game identifies a pair of opposite pits. A two-qubit circuit applies a Hadamard gate followed by a CNOT gate to prepare a Bell state. The circuit's measurement outcome determines the game event: an outcome of 11 adds two stones to each linked pit, while 00 leaves both pits unchanged in the ideal simulation.

Step 6: Display Results

The interface updates the board, stone counts, scores, and game status. A quantum laboratory panel displays measurement statistics, histograms, and Bell-state outcome information to help users understand the simulated quantum behavior.

Step 7: Complete the Game

The game checks its ending condition and calculates the final scores according to the implemented rules. The player can start a new game and explore different gameplay outcomes.

The expected demonstration illustrates how quantum circuit measurements can influence selected game mechanics. It demonstrates superposition, measurement, and Bell-state correlations through an interactive application while retaining classical logic for move validation, stone distribution, captures, and scoring.

The circuits are simulated using Qiskit AerSimulator on a classical computer; the project does not require physical quantum hardware.]`

* **Key Screenshots / Terminal Output:**  
  `[<img width="1211" height="759" alt="image" src="https://github.com/user-attachments/assets/c8533cbf-eca0-4918-bfbd-2453174ddaa7" />
]`

---

## 5. Classical vs. Quantum Comparison

* **Classical Baseline / Counterpart:**  
  `[The classical counterpart of the proposed game is a conventional Pallanguzhi game in which the AI selects a valid, nonempty pit using classical random selection or a simple rule-based strategy. In the quantum version, measurement outcomes generated by Qiskit circuits are used to influence the AI's pit selection. The Quantum Link feature additionally uses measurement outcomes from a simulated Bell-state circuit to determine correlated game events.]`

* **Comparative Analysis:**  
  `[The classical approach selects moves using conventional software logic, whereas the quantum-assisted version incorporates outcomes from simulated quantum circuits. The three-qubit Hadamard circuit generates eight equally probable measurement outcomes, which are mapped to candidate pit selections. The two-qubit Bell-state circuit generates correlated outcomes that control the Quantum Link feature.

The quantum-assisted version introduces a different gameplay mechanism, but the current implementation does not establish a quantum computational advantage or superior strategic performance. A quantitative comparison would require repeated gameplay experiments measuring scores, valid-move rates, captures, and win rates for both approaches under equivalent conditions.]`

---

## 6. Performance, Results & Limitations

* **Key Results & Observations:**  
  `[The project successfully integrates Qiskit quantum circuit simulation with an interactive Pallanguzhi game interface. The three-qubit circuit demonstrates superposition and measurement, while the two-qubit circuit demonstrates Bell-state preparation and correlated measurement outcomes. These outcomes influence AI pit selection and the Quantum Link feature, respectively.

The game combines Python, Qiskit, Qiskit AerSimulator, HTML, CSS, and JavaScript. Measurement results can be visualized through the quantum laboratory interface, allowing users to observe the relationship between quantum circuit outputs and game events.

The AI uses measurement outcomes to generate candidate moves and checks whether the selected pits are valid and nonempty. If suitable candidates cannot be obtained, the implementation can use a classical fallback. Quantitative claims about performance or strategic improvement require further testing.]`

* **Critical Reflection on Limitations:**  
  `[The quantum circuits are executed using Qiskit AerSimulator on a classical computer; therefore, the project does not demonstrate execution on physical quantum hardware or a quantum speedup.

The pit-selection circuit uses three qubits and produces eight computational-basis outcomes, so additional mapping and classical validation are required for a board containing fourteen pits. The current AI does not evaluate all possible board states or optimize moves using a quantum optimization algorithm.

Scaling the circuit to more qubits increases the number of possible computational-basis states exponentially. Although this creates a larger state space, it does not automatically improve gameplay or guarantee a better strategy.

On real noisy intermediate-scale quantum (NISQ) hardware, gate errors, imperfect measurements, and decoherence could change the observed outcome distributions and reduce the reliability of the Quantum Link behavior. Further work could include noise-model simulations, repeated trials, and comparisons with classical AI strategies using consistent evaluation metrics.

Future improvements could incorporate score-dependent move selection, more sophisticated classical and quantum-assisted strategies, and systematic performance evaluation.]`

---

## 7. References & Acknowledgments

* `[Cite any open-source libraries, GitHub repositories, or research papers you referenced during the hackathon.]`
* `[tools used: google Colab, Chat GPT for code assistance]`
