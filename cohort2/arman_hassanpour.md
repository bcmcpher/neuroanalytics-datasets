# Arman Hassanpour

[LinkedIn](https://www.linkedin.com/in/arman-hassanpour)

## Background

I am a computational neuroscientist and machine learning researcher
working at the intersection of artificial intelligence, clinical
neuroscience, and multimodal data integration. My research focuses on
developing explainable machine learning frameworks that clinicians can
genuinely trust and act on — not just models that perform well on
benchmarks.

I hold a Ph.D. in Hearing Science from Western University, where my
dissertation focused on speech intelligibility assessment using automatic
speech recognition, spanning [deep learning](../deep-learning.md) for audio processing, acoustic
modeling, and psychoacoustics. Prior to that, I completed an M\.Sc. in
Mechatronics Engineering with a focus on signal processing, and a B\.Sc.
in Computer Engineering with a specialization in embedded systems.

My technical experience spans transformer-based speech models, multimodal
sensor fusion, on-device machine learning for iOS and embedded systems,
and end-to-end ML pipeline development using TensorFlow, PyTorch, and
scikit-learn. I have also co-founded Sensalog Inc., a digital health
company developing a wearable medical device platform for at-home
monitoring of Parkinson's disease symptoms, where I served as CTO and
led the design and deployment of real-time multimodal ML systems — an
experience that deeply shaped my appreciation for the gap between
research and clinical deployment.

I am currently a CNS Cohort 2 Postdoctoral Fellow at Western University,
working under the supervision of Dr. Angela Roberts in the School of
Communication Sciences and Disorders. My fellowship is funded by The
Hilary & Galen Weston Foundation (2026–2028).

## Project

Neurodegenerative diseases such as [Alzheimer's disease](../research_topics/alzheimers.md),
[Parkinson's disease](../research_topics/parkinsons.md), and
[vascular cognitive impairment](../research_topics/dementia.md) represent a
growing challenge for aging populations worldwide. Each condition affects the brain
differently — disrupting speech, movement, cognition, and brain
structure in distinct but often overlapping ways — making early and
accurate diagnosis a significant clinical challenge.

This project develops a multimodal machine learning framework for the
early detection, differential diagnosis, and monitoring of disease
progression across these three conditions. Rather than relying on a
single data source, the framework integrates four complementary
modalities: speech and acoustic features, motor and gait signals,
cognitive assessment data, and neuroimaging biomarkers. By fusing these
data streams into a unified model, the goal is to capture a richer and
more complete picture of each patient's neurological profile than any
single modality could provide alone.

A central design principle of this framework is clinical
interpretability. The framework is built to reveal not only what
prediction a model makes, but which features — and which combinations
of features across modalities — are driving that prediction. This
level of transparency is essential for clinical trust and adoption: a
model that cannot explain its reasoning will not be used, regardless
of its accuracy.

The framework is developed using two major Canadian open neuroscience
datasets — the Ontario Neurodegenerative Disease Research Initiative
(ONDRI), accessed via [Brain-CODE](../data/portals/brain-code.md), and the Comprehensive Assessment of
Neurodegeneration and Dementia study (COMPASS-ND), accessed via LORIS.
Together, these datasets provide rich, longitudinal, multimodal data
across the target diagnostic groups and healthy controls. A key
validation goal is cross-dataset generalizability — ensuring that
models trained on one dataset transfer effectively to the other, a
critical requirement for real-world clinical deployment.

Ultimately, this work aims to produce tools that support clinicians in
identifying neurodegenerative disease earlier, distinguishing between
conditions that present similarly, and tracking how those conditions
evolve over time — with the transparency needed to make those tools
genuinely trustworthy in practice.

## Tools & Resources I Used

<!--
Scholars: this is your testimonial section - see contributing/bio-template.md

In ~150 words, first person, tell someone starting today:
  - What problem made you go looking for a tool?
  - What did you try, and what did you settle on?
  - What was genuinely hard about adopting it?
  - What would you tell someone starting today?

Link the pages you used, e.g.
[fMRIPrep](../tools/brain_imaging/fmriprep.md), [BIDS](../tools/data_management/bids.md)

Concrete beats comprehensive.
-->
