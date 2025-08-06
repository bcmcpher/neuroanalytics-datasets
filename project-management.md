# Project Management Tools

## Dataset Hosting

Based on the sources, several resources are available to host and
share neuroimaging datasets, ranging from domain-specific repositories
to general-purpose platforms, all designed to support Research Data
Management (RDM) and Open Science principles.

### Dedicated Neuroimaging Data Repositories

These repositories are specifically recognized within the neuroimaging
and neuroscience research community:

*   **LORIS:** This system was customized for data entry, storage, and
	dissemination of the PREVENT-AD program data.
	*   The PREVENT-AD cohort uses **two LORIS databases** for data
		dissemination: one for **Open Access** (for basic demographics
		and longitudinal neuroimaging raw data, e.g.,
		`https://openpreventad.loris.ca`) and one for **Registered
		Access** (for sensitive material like cognitive, medical,
		neurosensory, genetic, and CSF data, e.g.,
		`https://registeredpreventad.loris.ca`).
	*   The PREVENT-AD repositories are also discoverable via the
		**Canadian Open Neuroscience Platform (CONP)** interface
		(`https://portal.conp.ca`).

*   **OpenNeuro:** This platform is listed as a repository for data
	sharing.
	*   It is considered **very popular for neuroimaging data**,
		especially data following the Brain Imaging Data Structure
		(**BIDS**) standard.
	*   It is designed for **publishing** certain neuroimaging
		modalities, uses the BIDS standard, and supports **version
		control**. However, it generally does not offer access
		control, though there may be an embargo period.

*   **Brainlife:** This platform is available for **work and
	publishing** of neuroimaging data.
	*   It supports the **BIDS** standard and offers **access
		control** and **version control**.

*   **OMEGA (Open MEG Archive):** This repository is specifically
	mentioned as the place where the raw MEG and T1-weighted MRI scans
	from PREVENT-AD participants are available.

*   **NITRC (Neuroimaging Tools and Resources Clearinghouse):** This
	repository publishes neuroimaging data, tools, and other
	resources.
	*   It **already hosts popular datasets** such as ABIDE, OASIS,
		and ADHD\_200.
	*   It offers access control and provides a file preview function.

*   **DANDI:** This repository publishes **physiology** data and
	supports the **BIDS** standard, **access control**, and **version
	control**.

*   **NeuroVault, TemplateFlow, and EBRAINS:** These platforms are
	listed as options for sharing **derived data and results**.

### General-Purpose Data Repositories

These platforms can host various types of research data, including
neuroimaging data derivatives:

*   **Zenodo:** This platform is a repository used for publishing
	**any** kind of data.
	*   It is often utilized in the context of open science for
		uploading and installing community-developed pipelines (like
		those used in Nipoppy).
	*   It is considered intuitive to navigate, offers access control,
		and supports version control, although it has storage limits.

*   **OSF (Open Science Framework):** This tool promotes open,
	centralized workflows throughout the research lifecycle, including
	**storing and analyzing collected data**.
	*   It is suitable for **work and publishing** of **any** data
		type.
	*   It provides a unique, **persistent uniform resource locator
		(URL)** or digital object identifiers (DOIs) and archival
		resource keys (ARKs).
	*   It features built-in **version control** and allows
		third-party add-ons or integrations.

*   **Figshare:** This repository is used for publishing **any** type
	of data.
	*   It is noted for being fast in up- and download, which is good
		for handling big data in large chunks.

*   **NDA (National Database for Autism Research) (Implied):** Listed
	as a repository for publishing **any human data**.

*   **GIN:** This tool is used for both **work and publishing** and
	can handle **any** kind of data.

### Considerations for Choosing a Repository

When selecting a repository, researchers should ideally submit data to
a **domain or discipline-specific, community-recognized
repository**. Discipline-specific repositories often have more
functionalities tailored for the type of data being
shared. Repositories ensure **long-term archiving** and preservation,
which differentiates them from collaborative development tools like
GitHub or GitLab. Repositories promote the **FAIR Principles**
(Findable, Accessible, Interoperable, Reusable) by assigning
persistent identifiers, using metadata standards (like BIDS),
providing licenses, and determining access levels.
