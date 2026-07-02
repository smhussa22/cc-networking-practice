# Splunk

## Overview

Splunk is a platform for searching, monitoring, and analyzing machine-generated data. It ingests logs, metrics, and events from any source, indexes them, and provides a powerful search language (SPL) for operational intelligence, security monitoring, and alerting.

## Conceptual Questions

- What is Splunk?
- What problem does Splunk solve?
- What is an indexer?
- What is a forwarder?
- What is a Universal Forwarder (UF)?
- What is a Heavy Forwarder (HF)?
- What is the difference between Universal and Heavy Forwarders?
- What is a search head?
- What is a search head cluster?
- What is an indexer cluster?
- What is a deployment server?
- What is a cluster master (now called manager node)?
- What is a license master?
- What is an index?
- What is a bucket?
- What is a hot bucket?
- What is a warm bucket?
- What is a cold bucket?
- What is a frozen bucket?
- What is the bucket lifecycle?
- What is retention policy?
- What is `inputs.conf`?
- What is `outputs.conf`?
- What is `props.conf`?
- What is `transforms.conf`?
- What is `indexes.conf`?
- What is SPL (Search Processing Language)?
- What is a search command?
- What is a transforming command?
- What is a generating command?
- What is a streaming command?
- What is a field extraction?
- What is rex?
- What is KV Store?
- What is a lookup?
- What is a saved search?
- What is an alert?
- What is a scheduled report?
- What is a dashboard?
- What is a Splunk app?
- What is the Splunk Add-on for Unix and Linux?
- What is the Splunk Add-on for Windows?
- What is Splunk Enterprise Security (ES)?
- What is Splunk ITSI?
- What is Splunk Observability Cloud?
- What is HTTP Event Collector (HEC)?
- What is the difference between HEC and a Splunk forwarder?
- What is sourcetype?
- What is source?
- What is host?
- What is index (as a field vs. as a data store)?
- What is `_time`?
- What is `_raw`?

## Deep Dive Questions

- Describe the Splunk data pipeline from ingestion to search.
- What happens when data arrives at a Universal Forwarder?
- What is input-time processing?
- What is parse-time processing?
- What is index-time processing?
- What is search-time field extraction?
- How does Splunk break events from a stream (line-breaking)?
- What is `SHOULD_LINEMERGE`?
- What is `BREAK_ONLY_BEFORE`?
- What is `MUST_BREAK_AFTER`?
- How does Splunk extract timestamps from events?
- What is `TIME_FORMAT`?
- What is `TIME_PREFIX`?
- What is `MAX_TIMESTAMP_LOOKAHEAD`?
- What is a field alias?
- What is a calculated field?
- What is an event type?
- What is a tag?
- How does Splunk's TSIDX (Time-Series Index) structure enable fast searches?
- What is a bloom filter in Splunk's indexing?
- What is a rawdata journal?
- What is the metadata file in a bucket?
- How does replication factor work in an indexer cluster?
- What is the search factor?
- What is the difference between replication factor and search factor?
- What is a site in a multisite indexer cluster?
- What is site_replication_factor?
- What is site_search_factor?
- How does the search head dispatch a search across indexers?
- What is map-reduce in the context of Splunk search?
- What is a subsearch?
- What is a `join` command and when is it used?
- What is an `append` command?
- What is `inputlookup` and `outputlookup`?
- What is `stats` vs `eventstats` vs `streamstats`?
- What is `eval`?
- What is `where` vs `search`?
- What is `transaction` command and when is it expensive?
- What is a `tstats` command and why is it faster than `stats`?
- What is a data model?
- What is an accelerated data model?
- What is CIM (Common Information Model)?
- What is `pivot`?
- How does Splunk ES use correlation searches?
- What is a notable event in Splunk ES?
- What is risk-based alerting?

## Why Questions

- Why use Splunk instead of ELK (Elasticsearch, Logstash, Kibana)?
- Why use a Heavy Forwarder instead of a Universal Forwarder?
- Why use HEC instead of a Splunk forwarder for application logs?
- Why use data model acceleration instead of raw searches?
- Why use `tstats` instead of `stats`?
- Why is the `transaction` command expensive?
- Why does Splunk use a flat file structure for buckets instead of a database?
- Why use an indexer cluster instead of a single indexer?
- Why use a search head cluster instead of a single search head?
- Why is the replication factor independent of the search factor?
- Why use CIM for security use cases?

## Coding Questions

- Write a SPL query that counts events by source over the last 24 hours.
- Write a SPL query that extracts a field using rex.
- Write a SPL query that uses stats to compute average response time per host.
- Write a SPL query that uses eval to create a derived field.
- Write a SPL query that uses lookup to enrich events with asset data.
- Write a SPL query that uses tstats on an accelerated data model.
- Write a SPL query that detects failed login attempts by user.
- Write a SPL query that identifies top 10 source IPs by event count.
- Write a SPL query that uses timechart to plot events over time.
- Write a SPL query that uses transaction to group related events.
- Write a SPL query that uses join to correlate two data sources.
- Write a props.conf stanza that extracts a custom timestamp format.
- Write a transforms.conf stanza that extracts fields using REPORT.
- Write an inputs.conf stanza that monitors a log file.

## Edge Cases

- What happens when a forwarder cannot reach the indexer?
- What happens when disk space on an indexer is exhausted?
- What happens when a bucket's hot-to-warm rollover is delayed?
- What happens when frozen data needs to be restored?
- What happens when a search takes longer than the search timeout?
- What happens when the replication factor cannot be met due to indexer failures?
- What happens when two forwarders send the same data to the indexer (duplicate events)?
- What happens when a timestamp cannot be extracted from an event?

## Debugging Scenarios

- Search results are missing events from a specific time period. How do you investigate?
- A Splunk alert is not firing even though matching events exist. How do you debug?
- Ingestion rate drops suddenly. What do you check?
- Search performance is degrading. How do you investigate?
- A forwarder is not sending data. What do you check?
- A dashboard is showing no data. How do you troubleshoot?
- Indexer cluster replication is falling behind. How do you investigate?
- Field extraction is not working for a new log format. How do you debug props.conf?

## System Design Questions

- Design a Splunk deployment for a large enterprise with 500GB/day of log volume.
- Design a Splunk indexer cluster for high availability.
- Design a multisite Splunk deployment across two data centers.
- Design a Splunk-based security operations center (SOC) platform.
- Design a log ingestion pipeline from Kafka to Splunk.
- Design a Splunk retention strategy for compliance requirements.
- Design an alert pipeline that routes Splunk alerts to PagerDuty.

## Related Topics

- [Kafka](../kafka/questions.md)
- [NetFlow](../netflow/questions.md)
- [System Design](../system-design/questions.md)
- [Debugging](../debugging/questions.md)
- [AWS](../aws/questions.md)
