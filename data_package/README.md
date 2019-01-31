# The Impact of Result Diversification on Search Behaviour and Performance: Raw Entity Data
This GitHub Gist contains a package of files pertaining to the raw data created for the user study *The Impact of Result Diversification on Search Behaviour and Performance* by David Maxwell (d.maxwell.1@research.gla.ac.uk), Leif Azzopardi (leif.azzopardi@strath.ac.uk) and Yashar Moshfeghi (yashar.moshfeghi@strath.ac.uk). The article was published in the [*Information Retrieval Journal*](https://link.springer.com/journal/10791).

## Summary
Using the [TREC 2005 Robust Track](https://trec.nist.gov/data/t14_robust.html) (and TREC AQUAINT newswire collection), the study reported examined how user behaviour and performance varied when subjects used either a diversified (or not) retrieval systems while performing either an ad-hoc or aspectual retrieval task. While existing data available for the collection used was sufficient for the ad-hoc retrieval task, data to the best of our knowledge were not available for the aspectual tasks.

Considering entities within each of the documents identified as relevant in the TREC 2005 Robust Track for the topics used, we manually assessed each of the documents that were marked relevant by TREC assessors (via the TREC 2005 Robust Track QRELs file) for the five topics trialled in this study. The five topics were:

  * 341, Airport Security;
  * 347, Wildlife Extinction;
  * 367, Piracy;
  * 408, Tropical Storms; and
  * 435, Curbing Population Growth.

By examining the topic descriptions provided as part of the TREC 2005 Robust Track, we deduced and agreed upon different entities to extract for each topic's set of relevant documents. Unique entities were assigned their own identifier number. From here, after agreement (refer to the paper for more information), we were then in a position to generate a TREC diversity format QRELs file, which can, in turn, be used by evaluation tools such as [`ndeval`](https://trec.nist.gov/data/web/10/ndeval.c).


## Package (Gist) Contents
In this package, you will find the following files:
  * `trec2005_5topics.qrels`, the raw TREC 2005 Robust Track QRELs file for the five topics considered;
  * `desc_t341.txt`, the topic description for topic 341;
  * `desc_t347.txt`, the topic description for topic 347;
  * `desc_t367.txt`, the topic description for topic 367;
  * `desc_t408.txt`, the topic description for topic 408;
  * `desc_t435.txt`, the topic description for topic 435;
  * `entities.csv`, the raw entities identified (along with their topic and unique identifier number);
  * `trec2005_5topics_rels.dqrels`, the resultant TREC diversity format QRELs file for relevant documents;
  * `trec2005_5topics_nonrels.dqrels`, a TREC diversity format QRELs file for non-relevant documents (i.e. a TREC judgement of 0); and
  * `trec2005_5topics_combined.dqrels`, a TREC diversity format QRELS file combining both relevant and non-relevant documents.

*Note that the entire package can be downloaded as a ZIP file; click the `Download ZIP` file at the top right of this page.*

## File Structures
Topic descriptions are simple text files with the source topic title (first line) and description (second line onwards). These are provided for reference and are provided unchanged from the TREC 2005 Robust Track. `trec2005_topics.qrels` is also the TREC 2005 Robust Track QRELS file, but filtered to include only judgements for the five topics trialled.

The file `entities.csv` is a *NIX-formatted comma-separated value file (CSV). It consists of three columns: `topic`, `entityid` and `entitytext`. Assume that `topic` and `entityid` columns contain only integers, with the final `entitytext` column representing the entity as a string (e.g. the name of a seaworthy vessel for topic 367). Spaces and other non-alphanumeric characters (except commas) are permissible in the final column. `topic` represents the topic for the given entity, with `entityid` representing the unique identifier we assigned to each entity. These are not unique at a per-topic level. Note that `entities.csv` also contains a header line on the fist line.

The IDs provided in the `entityid` column then correspond to the entities listed in the `trec2005_5topics_*.dqrels` files. As previously mentioned, these are formatted as TREC diversity format files, with four columns separated by spaces. No headers are provided. On each line, the four columns represent:
  1. the topic number;
  2. the entity number (`entityid`);
  3. the AQUAINT document identifier; and
  4. `1` (denoting that the given entity appears within the listed document).
  
This structure is repeated over all three of the `.dqrels` files.

## Why Judge Non-Relevant Documents?
Documents listed in the source QRELs file that were judged to be non-relevant (i.e. judgement of 0) for the five topics considered were also examined. Taking the list of entities for a given topic (i.e. from `entities.csv`), we automatically examined each non-relevant document, looking for an exact term match for each entity. If a match was found within a document, the entity was assigned to that document. This was done as to introduce *noise* into our diversity QRELs. The `combined` diversity QRELs file was therefore used to perform ranking with the diversifying algorithm employed in the study. This was done to avoid rankings becoming too perfect, where only relevant material would have bubbled up to the top.

## Want to Use the Dataset?
We would love for you to use the dataset in your own experiments -- that's why we are releasing it! All we ask is that you cite our journal paper when referencing the dataset.

## Questions?
We'll be happy to answer any questions that you have with this dataset. Just send one of us an e-mail. David Maxwell (lead author) should be your primary point of contact.
