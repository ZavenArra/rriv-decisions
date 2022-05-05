# Marking the status of pulled files on the device

* Status: proposed
* Deciders: JakeH, ZavenA, KenC
* Date: 2022-05-05

Technical Story: {description | ticket/issue URL} <!-- optional -->

## Context and Problem Statement

Files on the device that have already been download need to be identifiable.  Users of the CLI will want to pull only new files, but also at times pull all files.  There are several options for how files can be marked as pulled.

## Decision Drivers <!-- optional -->

* Simplicity of code that can identify new files vs. files that are already downloaded
* Power use by the SDCard reader
* Robustness to failure of the RTC chip

## Considered Options

1. Use a timestamp stored in EEPROM
2. Copy files to a different folder on the SDCard
3. Append a suffix to files that have been pulled

## Decision Outcome

Chosen option: "{option 1}", because {justification. e.g., only option, which meets k.o. criterion decision driver | which resolves force {force} | … | comes out best (see below)}.

### Positive Consequences <!-- optional -->

* {e.g., improvement of quality attribute satisfaction, follow-up decisions required, …}
* …

### Negative Consequences <!-- optional -->

* {e.g., compromising quality attribute, follow-up decisions required, …}
* …

## Pros and Cons of the Options <!-- optional -->

### {option 1}

{example | description | pointer to more information | …} <!-- optional -->

* Good, because {argument a}
* Good, because {argument b}
* Bad, because {argument c}
* … <!-- numbers of pros and cons can vary -->

### {option 2}

{example | description | pointer to more information | …} <!-- optional -->

* Good, because {argument a}
* Good, because {argument b}
* Bad, because {argument c}
* … <!-- numbers of pros and cons can vary -->

### {option 3}

{example | description | pointer to more information | …} <!-- optional -->

* Good, because {argument a}
* Good, because {argument b}
* Bad, because {argument c}
* … <!-- numbers of pros and cons can vary -->

## Links <!-- optional -->

* {Link type} {Link to ADR} <!-- example: Refined by [ADR-0005](0005-example.md) -->
* … <!-- numbers of links can vary -->
