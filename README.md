# Hypothesis Testing

Exploratory analysis might discover patterns in data. Before any observed pattern goes in a report, one must ask: **could it just be chance?** Hypothesis testing aims to answer precisely that.

You build the answer in three steps. First the two ideas a test is made of: a **distribution**, whose area is a probability, and the **standard error**, which measures how much an average wobbles from one sample to the next. Then a single test worked out by hand, until the p-value is no longer a mystery number. Finally the tests you will reach for in any exploratory analysis, one for each kind of column pair, on restaurant bills and on New York taxi rides.

Notebooks 01 to 03 follow one group of animals throughout, the 68 Chinstrap penguins of the Palmer penguins dataset, so each notebook picks up exactly where the last one stopped:

```
01_distributions                     how are Chinstrap body masses spread?
        |                            (a curve, and areas under it)
        v
02_sampling_and_confidence_intervals how sure can we be of their average?
        |                            (the standard error, a 95% interval)
        v
03_how_a_test_works                  is the average really 3,700 g?
        |                            (one test, by hand, then in one line)
        v
04_hypothesis_testing_for_eda        which test for which pair of columns?
        |                            (worked on restaurant tips)
        v
05_hypothesis_testing_for_eda_exercise   the same, on your own
                                     (New York taxi rides)
```

All three datasets ship in `data/`, so every notebook runs on its own and offline.

## Learning Objectives

By the end of this repository, you should be able to:

**The building blocks (01, 02):**

- Fit a normal distribution to a column, read probabilities off it as areas, measure how unusual a value is with its z-score, and identify from the histogram when the normal curve is the wrong model.
- Compute the standard error of a mean, construct a 95% confidence interval from it, and state what the 95% refers to.

**The test itself (03):**

- State a null and an alternative hypothesis, compute the t-statistic and its p-value by hand as an area under the t-distribution, and confirm both with scipy in one line.
- Decide whether to reject the null hypothesis at a chosen significance level, choosing one or two tails from the wording of the question, and word the conclusion correctly.

**Testing during EDA (04, 05):**

- Choose the matching test for each pair of columns (correlation, t-test or Mann-Whitney U, ANOVA, chi-square) and the curve it compares against, checking its assumptions and switching to a robust alternative when they fail.
- Report an effect size next to every p-value, separate a significant result from an important one, and identify the multiple-testing trap in an exploratory analysis.

## Learning Path

**Scope** marks the core path every student is expected to complete. Optional lessons stay in the repository and are worth returning to, but the day does not depend on them. **Units** are indicative pacing, where one unit is 45 minutes.

| File / Folder | Description | Scope | Units |
| --- | --- | --- | --- |
| [**1 - Distributions**](01_distributions.ipynb) | Fit a normal curve to Chinstrap body mass, read probabilities off it as areas, go back from an area to a value, and meet the z-score and the number 1.96. Ends with a curve that fits badly, and a first look at the t, chi-square and F curves that tests compare their results with. | Core | 1.5 |
| [**2 - Sampling and Confidence Intervals**](02_sampling_and_confidence_intervals.ipynb) | Draw many samples and watch the average wobble, measure that wobble with the standard error, build a 95% interval for the Chinstrap average, and check by simulation what the 95% means. | Core | 1.25 |
| [**3 - How a Test Works**](03_how_a_test_works.ipynb) | Test whether Chinstraps average 3,700 g: hypotheses, the t-statistic by hand, the p-value drawn as an area, and the decision. Then the same test in one line of scipy, and why it agrees with the interval from 02. | Core | 2 |
| [**4 - Hypothesis Testing for EDA**](04_hypothesis_testing_for_eda.ipynb) | A worked exploratory session on restaurant bills: the matching test for each pair of columns, patterns that survive testing and one that does not, and the multiple-testing trap. | Core | 1.5 |
| [**5 - Hypothesis Testing for EDA: Exercise**](05_hypothesis_testing_for_eda_exercise.ipynb) | The same recipe on your own, on New York taxi rides: five questions, including a pattern that a test confirms but the way the data was recorded explains. | Core | 1.75 |

> [!TIP]
> Notebooks 01 to 03 are one story told in three parts. If a step in 03 feels like magic, the notebook it comes from is named at that point: go back to it rather than pushing on.

### Additional Folders and Files

| File / Folder | Description |
|---|---|
| [**Data**](data/) | `penguins.csv` for notebooks 01 to 03, `tips.csv` for 04 and `taxis.csv` for 05. |
| [**Solutions**](solutions/) | Reference solutions for notebooks 01, 02, 03 and 05. Notebook 04 is a worked guide and has no exercises. |
| [**pyproject.toml**](pyproject.toml) | Project configuration and dependencies. |
| [**uv.lock**](uv.lock) | Dependency lock file. |

## Setup

> [!NOTE]
> Throughout these steps, text in angle brackets like `<repo-name>` is a **placeholder**. Replace it, including the `< >` brackets, with your own value. For example, `cd <repo-name>` becomes `cd amle-hypothesis-testing`.

### 1. Create the Repository from the Template

Click **Use this template** on GitHub.

When creating the repository:

- Set yourself as the **Owner**
- Choose a repository name
- Disable **Include all branches**
- Click **Create repository**

> [!IMPORTANT]
> If you are working in pairs or groups, only **one person** should complete this step.

---

### 2. Add Collaborators (Pairs/Groups Only)

If working with teammates:

1. Open the repository on GitHub
2. Go to **Settings → Collaborators**
3. Add your teammates as collaborators
4. Share the repository link with your team

Teammates should accept the invitation before continuing.

---

### 3. Clone the Repository

Copy the SSH URL from the **Code** button on GitHub, then run:

```bash
git clone <copied-ssh-url>
```

The copied SSH URL will look like `git@github.com:<your-username>/<repo-name>.git`.

---

### 4. Move into the Project Folder and Install Dependencies

This installs all dependencies and creates a virtual environment in `.venv/`.

```bash
cd <repo-name>
uv sync
```

---

### 5. Open the Notebook

> [!NOTE]
> Make sure you open VS Code from the project root so it automatically detects the environment created by `uv sync`.

Launch VS Code in the project root folder:

```bash
code .
```

Then open `01_distributions.ipynb`, selecting the Python environment created by `uv sync` as the kernel. Work through the notebooks in order; all five are the core path.

## References & Further Reading

- [**scipy.stats**](https://docs.scipy.org/doc/scipy/reference/stats.html): Every distribution and every test used in this repository, in one module.
- [**Seeing Theory**](https://seeing-theory.brown.edu/): Interactive visual explanations of distributions, sampling and inference, the three ideas notebooks 01 to 03 build on.
- [**StatQuest: Hypothesis Testing and The Null Hypothesis**](https://www.youtube.com/watch?v=0oc49DyA3hU): The core idea of notebook 03 in fifteen minutes.
- [**StatQuest: p-values, what they are and how to interpret them**](https://www.youtube.com/watch?v=vemZtEM63GY): What a p-value does and does not tell you.
- [**ModernDive: Hypothesis Testing**](https://moderndive.com/v2/hypothesis-testing.html): A simulation-first treatment of the same ideas, for a second angle on them.
- [**StatQuest: P-hacking**](https://www.youtube.com/watch?v=HDCOUXE3HMM): Why the multiple-testing rules in notebooks 04 and 05 exist.
- [**palmerpenguins**](https://allisonhorst.github.io/palmerpenguins/): The dataset behind notebooks 01 to 03, collected by Dr Kristen Gorman at Palmer Station, Antarctica.
