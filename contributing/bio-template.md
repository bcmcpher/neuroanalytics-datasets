# Scholar page template

Copy this skeleton when you add or update your own page under `cohort1/` or
`cohort2/`. Keeping the same shape across pages lets the topic and method hubs
link back to everyone consistently.

```markdown
# Your Full Name

<optional: website, GitHub, Google Scholar links>

## Background

Where you came from and what you work on.

## Project: Your project title

What you are doing in the CNS program, and why.

## Tools & Resources I Used

<your testimonial - see below>

## Open-Source Contributions

<optional: packages, toolboxes, or teaching you want to point at>
```

## Writing the "Tools & Resources I Used" section

This is the part of your page that other people will get the most out of, and it
is the one part nobody else can write for you.

Documentation explains *how* a tool works. It never explains why a working
researcher decided the switch was worth the disruption. That is the gap this
section fills. Someone arriving in the program next year is deciding whether to
invest a week learning BIDS, or containers, or a preprocessing pipeline — a
peer's honest account of that decision is worth more than any feature list.

Aim for **about 150 words, written in the first person**. Four prompts:

- **What problem made you go looking for a tool?** Start from the friction, not
  the software.
- **What did you try, and what did you settle on?** Dead ends are useful — they
  save the next person the same detour.
- **What was genuinely hard about adopting it?** The setup cost, the concepts
  that took a while to click, the thing the docs gloss over.
- **What would you tell someone starting today?** The one sentence you wish
  you'd been told.

**Concrete beats comprehensive.** One tool described honestly is more useful than
six listed without comment. It is completely fine to write about a tool you
ended up abandoning, or one you still find awkward — that is real information.

### Link out as you go

Point at the pages in this book so your account connects to the reference
material. From a page in `cohort1/` or `cohort2/`, use `../`:

```markdown
[fMRIPrep](../tools/brain_imaging/fmriprep.md)
[BIDS](../tools/data_management/bids.md)
[PREVENT-AD](../data/databases/prevent-ad.md)
[deep learning](../deep-learning.md)
```

See [Tom George's page](../cohort2/tom_george.md) for an example of a scholar
page that links out to the datasets, modalities, and methods it draws on.

### An example of the shape

> I came in wanting to run a preprocessing pipeline on ONDRI and assumed the
> hard part would be the modelling. It was not — it was that every dataset I
> touched was laid out differently, and my scripts broke on each one. I spent a
> week converting to [BIDS](../tools/data_management/bids.md) and resented it
> the whole time. The payoff was that [fMRIPrep](../tools/brain_imaging/fmriprep.md)
> then ran essentially without configuration, and so did every QC tool after it.
> The genuinely hard part was the metadata: the validator is strict, the error
> messages assume you already know the spec, and I lost two days to a JSON field
> I had misread. If you are starting now, convert one subject by hand before you
> automate anything — you will understand the spec far faster than by reading it.

*(Illustrative only — replace with your own account.)*
