# Reconstructing an Explanation

Use when an existing draft is full of framing but the source contains enough substance to explain the subject. This is a synthetic editing case, not a report about a real service. Its quality test is whether the reader can explain the observed behavior after the edit.

## Supplied facts and reader need

A document service stores an uploaded file and durably enqueues an indexing job before acknowledging the upload. ID lookup reads the stored file; keyword search reads an index that a worker updates later. A worker may receive a job again if it fails before acknowledging that job. Writing the same document ID replaces the existing index entry. No latency measurement or guarantee about recovery time is supplied.

The reader has seen a successful upload followed by an empty keyword result and wants to know why. The requested register is concise explanatory prose. Retain the difference between upload acknowledgement and the worker's job acknowledgement.

## Inflated draft

> This document provides a comprehensive understanding of upload and search. After reading it, you will be able to distinguish storage, acknowledgement, and indexing. Read the overview first and return to the terminology section if the concepts are unfamiliar. The following explanation is not a guarantee about all deployments.
>
> The source file is stored. A job is durably enqueued. Upload success does not mean indexing success. ID lookup and keyword search are different. A worker updates the index. Failure can lead to redelivery. Rewriting the same document ID replaces its index entry. These distinctions are important for understanding the system.

The first paragraph promises an explanation; the second lists its ingredients without connecting the observed symptom to them. Deleting the introduction alone leaves that second problem intact.

## An insufficient short edit

> Upload success does not mean search availability. Indexing runs asynchronously. Retries are supported.

This is shorter and broadly compatible with the facts, but it still leaves the reader to reconstruct the two read paths and the retry behavior. It also blurs whose acknowledgement controls redelivery. A shorter version is not automatically a better explanation.

## Revised passage

### Upload acknowledgement and search visibility

A successful upload confirms that the service has stored the file and durably enqueued its indexing job. The file is already available through ID lookup, but keyword search uses a separate index that the worker updates later. A keyword query can therefore return no match immediately after an acknowledged upload.

If the worker fails before acknowledging its job, the queue may deliver that job again. Writing the same document ID replaces its index entry, so processing the job again does not add a duplicate search result.

## Editorial decisions

The opening answers what the observed success means. The next sentence connects the two stores to the two read paths, and the third explains the reader's empty result. The second paragraph explains the supplied recovery behavior and its consequence. The explanation retains useful negation because it identifies an actual missing result and excludes a duplicate result under the stated write behavior.

The learning promise, reading tour, generic deployment disclaimer, and final importance statement have no remaining job. Their useful subject matter is now expressed as actual behavior. No new timing, universal delivery guarantee, or deployment fact was added. For a reader asking only about immediate search visibility, the recovery paragraph could be omitted; in a recovery guide it would remain and may need more supplied detail.

## Transfer to an authorized revision

Identify the supported proposition the reader needs, then arrange the supplied facts so the relation is recoverable. Use a concrete example when one is supplied or when the task authorizes a clearly marked teaching example. Preserve the source's voice where it works. If the source does not establish the relation, leave the uncertainty rather than smoothing it into a cause. Finish when the passage explains what the reader needs; neither a deletion quota nor a mandatory paragraph pattern establishes that result.
