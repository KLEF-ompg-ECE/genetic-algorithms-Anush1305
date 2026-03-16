# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :** ANUSH THAK
**Student ID    :**2310040029 
**Date Submitted:**16/03/2026  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**

```
The `fitness()` function returns the total value of items packed in the knapsack, as long as the total weight does not exceed the maximum allowed. If the solution is overweight (total weight > MAX_WEIGHT), it scores 0 to penalize invalid solutions and ensure only feasible packings are considered.
```

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

```
`tournament_select()` randomly picks a group of individuals from the population and selects the one with the highest fitness. This increases the chance that higher-fitness individuals are chosen, promoting better solutions while still allowing some diversity.
```

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**

```
This line ensures the best solution from the current generation is always carried over to the next generation (elitism). It is important because it prevents losing the best-found solution due to random genetic operations, guaranteeing that the highest-value solution is preserved.
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of generations | 50 |
| Best value at generation 1 | 60 |
| Final best value | 77 |
| Total weight of best solution (kg) | 14.4 |
| Is solution valid (Yes / No) | Yes |

**Copy the printed packing list here:**
```
	Best Packing List
--------------------------------------
	+ Water bottle
	+ First aid kit
	+ Sleeping bag
	+ Torch
	+ Energy bars (x6)
	+ Rain jacket
	+ Map & compass
	+ Cooking stove
	+ Rope (10 m)
	+ Sunscreen
	+ Power bank
--------------------------------------
	Weight : 14.4 / 15.0 kg
	Value  : 77
	Valid  : Yes
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
The curve shows a rapid improvement in the first few generations as the population quickly finds better solutions. After about 10–15 generations, the curve begins to flatten, indicating that the algorithm is converging and further improvements are incremental. This demonstrates effective exploration followed by exploitation.
```

---

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, the experiment block has been copied three times for mutation rates 0.01, 0.05, and 0.30. Each block runs the genetic algorithm with a different mutation rate and saves the plot as `experiment_2a.png`, `experiment_2b.png`, and `experiment_2c.png`.
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve |
|--------------|-----------------|-------------|--------|----------------|
| 0.01         | 75              | 14.9        | Yes    | Slow rise, early plateau |
| 0.05         | 77              | 14.4        | Yes    | Fast rise, then plateau |
| 0.30         | 78              | 14.1        | Yes    | Chaotic, jumps, less stable |

**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*
```
With a low mutation rate (0.01), the algorithm improves slowly and may get stuck, as there is not enough diversity to escape local optima. At the default rate (0.05), the curve rises quickly and stabilizes, showing a good balance between exploration and exploitation. With a high mutation rate (0.30), the curve is more erratic, with frequent jumps and less stability, indicating too much randomness. The sweet spot is around 0.05, where the algorithm converges efficiently without losing good solutions.
```

**Which mutation_rate gave the best result? Why do you think that is?**
```
Mutation rate 0.30 gave the highest final value (78), but the result is less stable and may not always be reproducible. The default rate (0.05) consistently produces strong results and a stable curve, making it the most reliable setting for this problem.
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|------------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 | 77 | Balanced mutation rate gives stable, high-value solutions. |
| 2 — Mutation rate | mutation_rate = 0.30 | 78 | High mutation rate can find higher values but is less stable; default is most reliable. |

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
Genetic Algorithms are powerful for solving optimization problems like the knapsack, but their performance depends heavily on parameter settings. Mutation rate controls the balance between exploring new solutions and preserving good ones. Too little mutation leads to stagnation, while too much causes instability and loss of progress. The best results come from a balanced approach, where diversity is maintained without sacrificing the best solutions. Careful tuning and observation are essential for reliable convergence.
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, packing list pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
