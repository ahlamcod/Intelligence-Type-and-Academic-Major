# Intelligence-Type-and-Academic-Major
A small research-based Python/ML experiment exploring whether a person's Multiple Intelligences profile can be used to identify academic majors with similar intelligence distributions.

🎯 Objective

The idea is simple:

Can a person's Multiple Intelligences profile be compared with research-derived intelligence profiles of academic majors to identify the closest major?

The experiment:

Presents an 80-item Multiple Intelligences questionnaire.
Calculates the user's scores across 8 intelligence dimensions.
Builds an 8-dimensional intelligence vector.
Compares the user's vector with research-derived major vectors.
Uses K-Nearest Neighbors (KNN) to identify the closest major profiles.

The project intentionally remains a small standalone Python/ML experiment rather than a production application.

📚 Research Basis

The major intelligence profiles used in this experiment are derived from the dissertation:

Reiners, 2023 — Auburn University

Dissertation PDF

The dissertation investigates the relationship between Multiple Intelligences and academic majors and reports intelligence distributions for different majors.

The major vectors used in this project come from the dissertation's Tables 3–9.

This source is explicitly acknowledged for intellectual honesty and methodological transparency: the major profiles are not values invented for this experiment.

🧪 Multiple Intelligences Questionnaire

The dissertation identifies the Multiple Intelligences Inventory for Adults (MIIA) by Thomas Armstrong (2000), adapted from Shearer's Multiple Intelligences Developmental Assessment Scales (MIDAS, 1999).

The MIIA measures eight intelligence dimensions with 10 items per intelligence, giving a total of 80 items.

Intelligence dimensions
#	Intelligence
1	Linguistic
2	Logical-Mathematical
3	Spatial
4	Bodily-Kinesthetic
5	Musical
6	Interpersonal
7	Intrapersonal
8	Naturalistic
Questionnaire used in this experiment

For the MVP, we use an Armstrong-derived Multiple Intelligences Checklist consisting of 80 statements covering the same eight intelligence dimensions.

Each selected statement contributes 1 point to its corresponding intelligence.

Therefore, each intelligence receives a score from:

0 → 10

which is then normalized to:

0 → 1

and represented as an 8-dimensional vector.

⚠️ Methodological note

The dissertation's original Appendix 2 was not available to us.

Therefore, this project does not claim that the questionnaire is an exact reproduction of the instrument administered in the dissertation.

Instead, the experiment uses the Armstrong-derived 80-item checklist that could be independently located and verified for the MVP.

This distinction is intentionally documented to keep the experiment transparent about its methodology.

🧮 From Questionnaire to Vector

Suppose a user obtains:

Linguistic            0.30
Logical-Mathematical  0.90
Spatial               0.40
Bodily-Kinesthetic   0.60
Musical               0.30
Interpersonal         0.40
Intrapersonal         0.90
Naturalistic          0.30

The user's profile becomes:

[0.3, 0.9, 0.4, 0.6, 0.3, 0.4, 0.9, 0.3]

Each major has its own corresponding research-derived vector.

The experiment then compares these vectors using Euclidean distance.

🤖 Recommendation Method

The recommendation system uses K-Nearest Neighbors (KNN).

The major profiles are normalized from percentages:

0–100%

to:

0–1

The user's vector is already represented on the same scale.

KNN then searches for the major vectors with the smallest Euclidean distance from the user's vector.

Why KNN?

This experiment does not attempt to train a predictive model from a large dataset.

Instead, the problem is treated as a similarity/search problem:

Find the research-derived major profiles that are geometrically closest to the user's intelligence profile.

The current experiment returns the 3 closest major profiles.

📊 Example Result

My own test produced:

Multiple Intelligences Profile
Intelligence	Score
Linguistic	30%
Logical-Mathematical	90%
Spatial	40%
Bodily-Kinesthetic	60%
Musical	30%
Interpersonal	40%
Intrapersonal	90%
Naturalistic	30%

8-dimensional vector:

[0.3, 0.9, 0.4, 0.6, 0.3, 0.4, 0.9, 0.3]
Top intelligences
🧠 Logical-Mathematical — 90%
🪞 Intrapersonal — 90%
🏃 Bodily-Kinesthetic — 60%
KNN Major Recommendations
Rank	Major	Distance	Similarity
🥇 1	Finance	1.2521	55.73%
🥈 2	Business Analytics	1.2560	55.59%
🥉 3	Information Systems	1.2605	55.44%

The important point is that KNN compares the complete 8-dimensional profile, rather than simply selecting a major based on the user's strongest individual intelligence.

🔬 The Experiment

The public-facing question behind this project is:

If you already chose a major or career, does this research-based result actually reflect your reality?

If you try the experiment, consider sharing:

Your MI profile
Your recommended majors
Your actual major or career
Whether the profile feels accurate
Whether the recommended major matches your experience

The goal is not to prove that the algorithm is "correct".

The goal is to explore whether the relationship reported in the research produces interesting and recognizable results when applied to individual profiles.

🚧 Current Scope

This is an MVP / exploratory experiment.

Currently:

✅ 80-item questionnaire
✅ 8-dimensional MI scoring
✅ Normalized user vector
✅ Research-derived major vectors
✅ Euclidean distance
✅ KNN recommendation
✅ Top-3 major recommendations
🚧 Larger validation dataset
🚧 Statistical evaluation
🚧 Cross-validation
🚧 More academic majors
🚧 More rigorous comparison with alternative recommendation methods

The current similarity percentage should therefore be interpreted as a distance-based similarity indicator, not as a probability that a person belongs to or will succeed in a particular major.

📁 Project Structure
Intelligence-Type-Major/
│
├── notebook/
│   └── intelligence_major.ipynb
│
├── data/
│   └── ...
│
├── README.md
└── requirements.txt
🛠️ Technologies
Python
NumPy
Pandas
scikit-learn
Jupyter Notebook
ipywidgets
📖 References
Primary research source

Reiners, 2023 — Auburn University

Dissertation investigating the relationship between Multiple Intelligences and academic majors.

Dissertation PDF

Questionnaire source

The questionnaire used in this MVP is an Armstrong-derived Multiple Intelligences Checklist, adapted from:

Thomas Armstrong — 7 Kinds of Smart

The checklist version used for the experiment was obtained from the Discovering Gifts in Middle School – Tribes TLC® Multiple Intelligences Checklist / tally sheet.

⚖️ Research Transparency

A few distinctions are important:

The major profiles are research-derived, based on the dissertation's reported tables.
The questionnaire is not claimed to be an exact copy of the dissertation's administered instrument, because the original Appendix 2 was unavailable.
KNN is used as a similarity mechanism, not as a scientifically validated career prediction model.
The resulting recommendation should be interpreted as an experimental comparison, not professional academic or career advice.

The purpose of documenting these limitations is to make the experiment reproducible and intellectually honest.

💡 Try It Yourself

Take the questionnaire, generate your profile, and see what happens.

Then ask yourself:

Does the result actually describe you?

If you've already chosen a major or career, I'd especially love to know whether the recommendation matches your real experience.

📌 Disclaimer

This project is an independent educational/research experiment.

It does not claim that Multiple Intelligences determine academic ability, career success, or suitability for a particular major.

The recommendations are based solely on similarity between the user's questionnaire-derived vector and the research-derived major profiles used in this experiment.
