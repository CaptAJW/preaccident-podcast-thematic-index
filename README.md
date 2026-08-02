PreAccident Podcast Thematic Index

The PreAccident Podcast contains a large body of practical safety knowledge developed across hundreds of episodes. That depth is valuable, but it also makes the archive difficult to navigate when a listener is looking for material on a specific subject.

This repository provides a structured thematic index of the podcast archive. It organizes the strongest and most relevant episodes into seven safety themes and publishes ranked Top 10, Top 25, and Top 50 lists for each theme.

The index is intended for safety professionals, operational leaders, investigators, educators, researchers, students, and practitioners who want to use the podcast as a targeted learning resource rather than browse the archive only in chronological order.

What This Repository Contains

The repository contains 21 published Markdown reports:

seven Top 10 lists;

seven Top 25 lists;

seven Top 50 lists.

Each theme has its own folder. The three lists within that folder are cumulative:

the Top 10 is the most focused starting point;

the Top 25 includes the Top 10 and expands the listening path;

the Top 50 includes the Top 25 and provides the broadest published treatment of the theme.

Rankings represent strength of thematic fit. They do not represent overall episode quality, popularity, importance, production value, or agreement with the views expressed in an episode.

An episode may appear in more than one theme when the available metadata supports a substantive connection to multiple subjects.

Themes

Theme

Focus

Human Performance, Error, and Accountability

How people perceive conditions, make decisions, adapt, succeed, and make mistakes within organizational systems, including how organizations interpret and respond to those actions.

Learning from Events and Investigations

How organizations understand accidents, incidents, near misses, failures, and other outcomes through investigation, causal analysis, evidence development, debriefing, and corrective learning.

Operational Learning, Worker Engagement, and Work-as-Done

How organizations learn from frontline expertise and everyday operations through worker engagement, listening, Learning Teams, observation, and comparison of work-as-done with work-as-imagined.

Leadership, Management, and Organizational Change

How leaders and managers create conditions for safe and effective work and how organizations introduce, implement, adopt, and sustain change.

Culture, Trust, and Psychological Safety

How shared norms and relationships affect trust, openness, communication, worker voice, psychological safety, and the ability to raise concerns and learn.

Systems Complexity, Resilience, and Crisis Adaptation

How complex systems behave and how people and organizations maintain, adapt, recover, and create capacity under variability, disruption, uncertainty, and crisis conditions.

Risk, Controls, Procedures, and Operational Assurance

How organizations identify hazards, understand risk, design and verify controls, plan critical work, use procedures and rules, and determine whether safeguards and safety systems function as intended.

How the Source Data Was Collected

The project began by collecting publicly accessible metadata from the PreAccident Podcast archive hosted on Podbean.

A Python-based scraping and data-collection process was used to retrieve and preserve the available structured information in JSON format. The collected information included, where available:

episode and post titles;

descriptions;

publication dates;

episode numbers;

media URLs;

page or permalink information;

content-type indicators;

republication indicators;

other record-level metadata exposed through the public site.

The process did not download or redistribute the podcast audio. It did not rely on private, authenticated, or restricted data.

The resulting working corpus contained 1,162 metadata records, of which 1,157 were ranking-eligible. Those figures are record counts, not unique episode counts. The public archive contains approximately 608 episodes, along with related posts, republications, repeated media references, and other records that can create more than one metadata entry for the same underlying audio.

This distinction matters. A raw metadata record is not automatically a unique podcast episode.

Why JSON Was Used

JSON provided a stable, machine-readable format for preserving the scraped archive data and processing it deterministically.

Each record could be evaluated using consistent fields rather than relying on manual browsing or copy-and-paste notes. JSON also made it possible to:

preserve the original record identifier;

compare records across different retrieval passes;

identify missing or duplicate identifiers;

resolve repeated media URLs;

distinguish original publications from republications;

join authoritative metadata back into ranked outputs;

validate complete packet coverage;

generate final Markdown reports consistently.

The working data remained file-based throughout the project. The process did not depend on a database, vector store, or opaque recommendation system.

Python Processing Workflow

Python was used to turn the collected JSON corpus into a controlled set of thematic outputs.

The major processing stages were:

Corpus preparationThe scraped records were normalized into a master JSON dataset. Record identifiers, media URLs, publication information, descriptions, and eligibility fields were checked for consistency.

Taxonomy developmentA seven-theme taxonomy was developed and locked before final ranking. Each theme included a definition, subordinate concepts, inclusion criteria, exclusion criteria, and boundaries with related themes.

Candidate retrievalPython scripts searched the ranking-eligible corpus for records that might fit each theme. Retrieval used theme-specific phrases, contextual terms, title evidence, description evidence, and pre-lock gate patterns.

Media deduplicationCandidate pools were deduplicated using the media URL so that multiple metadata records pointing to the same audio would not compete as separate episodes.

Complete candidate assessmentEvery candidate in a packet received an individual thematic relevance assessment. Records were not accepted merely because they contained a keyword.

Qualification controlThe general qualification threshold was a relevance score of 7 or higher on a 10-point scale.

Supplemental retrieval where neededWhen the initial candidate pool did not provide sufficient depth, one controlled supplemental search was run against the remaining unreviewed corpus.

Comparative rankingQualifying records were ranked from strongest to weakest thematic fit within each theme.

Cutoff reviewWhere records near the Top 50 publication boundary were closely comparable, a targeted cutoff review was performed without reopening the full ranking.

Enrichment and validationRanked records were rejoined with authoritative metadata and checked for missing IDs, invalid subordinate concepts, duplicate record IDs, duplicate media URLs, republications, and rank continuity.

Final report generationPython generated the Top 10, Top 25, and Top 50 Markdown reports from the validated final ranking data.

Final-output verificationEach theme was checked to confirm that the published lists exactly matched the appropriate segments of the full ranked pool and that all reports existed and were nonempty.

Retrieval Was Not Ranking

The candidate-retrieval process was intentionally separated from the thematic judgment and ranking process.

A record could receive a high retrieval score because it contained several relevant words or phrases, but that did not automatically make it a strong thematic fit. Retrieval scores were used only to find records that warranted review.

The following were not sufficient by themselves:

a single keyword;

generic safety language;

guest credentials;

boilerplate descriptions;

promotional text;

incidental references to risk, learning, leadership, culture, procedures, or resilience;

title similarity without record-specific supporting description evidence.

Final rankings were based on comparative thematic relevance, not on keyword density.

Ranking and Qualification Rules

The general scoring scale ranged from 0 through 10.

Records scoring 7 through 10 were treated as qualifying unless a separate documented control applied. The final rankings preserved the original relevance score and confidence associated with each record.

The project also applied the following controls:

record IDs had to be complete and unique;

media URLs had to be complete and unique within each ranked pool;

original publications were preferred over republications;

rankings had to be consecutive;

records could not be silently added or removed during revision;

cutoff reviews were limited to the specified review range;

records outside an authorized review range remained frozen;

final Top 10, Top 25, and Top 50 outputs had to exactly match the corresponding portions of the full ranking.

Two depth-sensitive themes required expressly documented below-threshold exception handling to complete a Top 50. Those records were preserved with their original scores and were not represented as having met the general score-7 qualification threshold.

Final Ranked-Pool Sizes

The complete final ranked pools were:

Theme ID

Final ranked pool

human_performance_accountability

60

event_learning_investigation

51

operational_learning_work_as_done

60

leadership_change

59

culture_trust_psychological_safety

50

systems_resilience_crisis

50

risk_controls_operational_assurance

54

Only the first 50 records are published in each Top 50 report. Records ranked above 50 were retained as reserves in the underlying final data.

Repository Structure

README.md
LICENSE

human_performance_accountability/
  human_performance_accountability_top_10.md
  human_performance_accountability_top_25.md
  human_performance_accountability_top_50.md

event_learning_investigation/
  event_learning_investigation_top_10.md
  event_learning_investigation_top_25.md
  event_learning_investigation_top_50.md

operational_learning_work_as_done/
  operational_learning_work_as_done_top_10.md
  operational_learning_work_as_done_top_25.md
  operational_learning_work_as_done_top_50.md

leadership_change/
  leadership_change_top_10.md
  leadership_change_top_25.md
  leadership_change_top_50.md

culture_trust_psychological_safety/
  culture_trust_psychological_safety_top_10.md
  culture_trust_psychological_safety_top_25.md
  culture_trust_psychological_safety_top_50.md

systems_resilience_crisis/
  systems_resilience_crisis_top_10.md
  systems_resilience_crisis_top_25.md
  systems_resilience_crisis_top_50.md

risk_controls_operational_assurance/
  risk_controls_operational_assurance_top_10.md
  risk_controls_operational_assurance_top_25.md
  risk_controls_operational_assurance_top_50.md

What Is and Is Not Published Here

This repository is primarily a publication repository for the final thematic lists and supporting documentation.

Depending on the repository contents, it may not include:

the complete scraped JSON corpus;

intermediate assessment packets;

validation artifacts;

temporary ranking files;

every Python utility used during development;

internal working notes.

The published Markdown lists are the final outputs intended for public use.

Important Limitations

This is a metadata-grounded index.

The analysis used titles, descriptions, publication information, media references, and related public metadata. It was not based on complete audio transcription or a full listening review of every episode.

The rankings therefore represent a structured professional judgment about thematic relevance based on the available metadata. They are not definitive statements about the complete content, quality, or value of an episode.

Additional limitations include:

some episode descriptions are more detailed than others;

older metadata may be incomplete;

some posts may reference the same underlying media;

titles and descriptions may change after publication;

episode pages may be moved, removed, or republished;

metadata may not capture every subject discussed in the audio;

a thematically important episode may rank lower if the available public description provides limited supporting evidence.

Podcast Content and Rights

This repository does not host or redistribute podcast audio.

Podcast titles, descriptions, artwork, audio, trademarks, and other original third-party content remain the property of their respective rights holders. Links in the published lists direct users to the original podcast pages or media sources where available.

License

Except for third-party material, the original taxonomy, thematic classifications, rankings, methodology, repository structure, and explanatory text in this repository are licensed under the terms identified in the repository's LICENSE file.

The repository license does not grant rights to podcast audio, artwork, episode descriptions, trademarks, or other third-party material.

Corrections and Updates

Corrections are welcome.

Open an issue if you identify:

a broken episode link;

an incorrect title or metadata field;

a duplicate or republication concern;

a record that appears under the wrong theme;

a ranking issue supported by the published metadata;

a missing episode that appears to have strong record-specific support for a theme.

Please identify the theme, list, rank, episode title, and the basis for the requested correction.

Acknowledgment

The PreAccident Podcast is created and hosted by Todd Conklin.

This index is an independent navigation and research aid shared with his encouragement. Its purpose is to make the podcast archive easier to explore, teach from, study, and apply.
