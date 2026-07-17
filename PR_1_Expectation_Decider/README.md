# PR_1 — Expectation Decider

A concise analysis notebook that uses `student_data.csv` to demonstrate empirical probability,
conditional probability, the binomial distribution, and an example application of Bayes' theorem.

Dataset

- Rows: ~200 students, columns include `final_exam_pass`, `study_hours`, `attendance`, `group_discussion`, `previous_scores`

Core concepts

- Experiment: a process with uncertain outcome.
- Outcome: a single result of an experiment.
- Sample space: set of all possible outcomes.
- Event: a condition of interest (e.g., pass).
- Empirical probability: observed frequency from data.
- Theoretical probability: model-based probability.
- Conditional probability: probability given another event.

Defined events

- Event A: student passes the final exam.
- Event B: student studies > 10 hours/week.
- Event C: student attendance > 80%.

Empirical vs. theoretical

- Empirical probability computed from dataset counts.
- Theoretical values are used for illustrative comparisons.

Probability calculations

- Joint probability: P(A ∩ B) = count(A and B) / total.
- Marginal probability: P(A) = count(A) / total.
- Conditional probability: P(A|B) = P(A ∩ B) / P(B).

Contingency table

- Construct a 2×2 table for `group_discussion` vs `final_exam_pass`.
- Use joint, marginal, and conditional probabilities to interpret relationships.

Independence test

- Compare P(Pass|GroupDiscussion=Yes) to P(Pass).
- If similar → approximately independent; otherwise dependent.

Random variable and binomial model

- Define X = number of passes in n=3 randomly selected students.
- Binomial formula: P(X=k) = C(n,k) · p^k · (1−p)^(n−k).
- Expected value: E[X] = Σ k·P(X=k).
- Variance: Var(X) = Σ (k − E[X])^2·P(X=k).

Venn diagrams

- Visualize overlaps for study hours and attendance.
- Fallback to simple charts if `matplotlib-venn` is unavailable.

Bayes' theorem example

- Demonstrates P(A|B) = [P(B|A)·P(A)] / P(B) with illustrative numbers.
- Uses law of total probability to relate marginal and conditional probabilities.

Key formulas

- Empirical probability: P(E) = favorable / total.
- Binomial: P(X=k) = C(n,k)·p^k·(1−p)^(n−k).
- Expected value: E[X] = Σ k·P(X=k).
- Variance: Var(X) = Σ (k − E[X])^2·P(X=k).
- Bayes' theorem: P(A|B) = [P(B|A)·P(A)] / P(B).

Usage

1. Ensure `student_data.csv` is in the repository root.
2. Install requirements: `pip install pandas matplotlib matplotlib-venn`
3. Open `PR_1.ipynb` in Jupyter: `jupyter notebook PR_1.ipynb`
4. Run cells sequentially to reproduce analyses and figures.

Notes

- Fix the attendance threshold: use `df['attendance'] > 80` (not `> 0.8`).
- Venn diagrams are optional; notebook handles missing optional packages.
- The binomial model assumes independent draws with replacement; adjust for finite populations if needed.
