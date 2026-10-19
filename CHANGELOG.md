# CHANGELOG
All notable changes to this project will be documented in this file. `[Unreleased]` section at the top, will be used to track upcoming changes.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

<!-- When updating the Changelog:

- Please follow Keep a Changelog guiding principles: https://keepachangelog.com/en/1.1.0/#how.
- Make sure you add your entry to the correct section.

Thankyou! -->

<!-- All available sections in the Changelog:

### Added
* #### Categories
* #### Event Classes
* #### Profiles
* #### Objects
* #### Platform Extensions
* #### Dictionary Attributes

### Improved
* #### Categories
* #### Event Classes
* #### Profiles
* #### Objects
* #### Platform Extensions
* #### Dictionary Attributes

### Bugfixes

### Deprecated

### Breaking changes

### Misc

-->

## [Unreleased]


## [v1.2.0] - October 16th, 2026

### Added
* #### Objects
  1. Extended `image` with `is_public` (reused from core), `source_resource_uid`, `root_device_type`, and `virtualization_type` for AWS machine image (AMI) findings. Extended `resource_details` with `state`/`state_id`, narrowing the generic core `state_id` via an inline, resource-type-agnostic lifecycle enum (Pending/Active/Suspended/Deprovisioned/Failed/Transient) that maps across AWS resource types (AMI, EC2, etc.).
  1. Extended `affected_package` with `workload_state`, `workload_state_id`, and `workload_state_reason` so vulnerability findings can state whether a vulnerable package is part of the workload the affected resource runs (Inspector package runtime reachability for EC2 and container images).
* #### Dictionary Attributes
  1. Added `source_resource_uid`, `root_device_type`, and `virtualization_type` as `string_t`.
  1. Added `workload_state_id` as an `integer_t` enum (Unknown/Active/Inactive/Other) with sibling `workload_state` as a `string_t`, and `workload_state_reason` as a `string_t` enum of the scanner evidence values (`PACKAGE_IN_DOCKERFILE_WORKLOAD_PATH`, `PACKAGE_NOT_IN_DOCKERFILE_WORKLOAD_PATH`, `PROCESS_OBSERVED_IN_EC2_RUNTIME`, `PROCESS_NOT_OBSERVED_IN_EC2_RUNTIME`).


## [v1.1.0] - May 22nd, 2026

### Added
* #### Event Classes
  1. Added `Remediation Target Finding` event class to the Findings category. Identifies resources that, when remediated, resolve or reduce severity of grouped findings.
  1. Added `Network Scan Finding` event class to the Findings category.
* #### Objects
  1. Added `remediation_outcome`, `contributing_finding`, and `remediation_step` objects for remediation impact tracking. Extended `remediation` with `is_immediate` and `post_remediation_steps`.
  1. Added `adjusted_metric` object for CVSS environmental metric modifications. Extended `cvss` with `adjusted_score`, `adjusted_vector_string`, and `adjusted_metric_list`. Extended `vulnerability` with `vendor_score`.
  1. Added `port_scan_result` object for per-port scan probe outcomes.
  1. Added `network_scan_info` object for scan job metadata.
  1. Added `content_policy_filter` and `guardrail_evaluation_result` objects for AI guardrail content filter results.
* #### Dictionary Attributes
  1. Added `adjusted_score` as a `float_t`, `adjusted_vector_string` as a `string_t`, and `adjusted_metric_list` as an array of `adjusted_metric` objects.
  1. Added `cvss_metric` and `update_reason` as `string_t`, and `vendor_score` as a `float_t`.
  1. Added `target_trait` as a `trait` object, `remediation_outcome` as a `remediation_outcome` object, and `contributing_findings` as an array of `contributing_finding` objects.
  1. Added `resolved_findings_count`, `severity_reduction_findings_count`, `severity_unchanged_findings_count` as `integer_t`.
  1. Added `updated_severity` as a `string_t`, `updated_severity_id` as an `integer_t` enum, and `updated_traits` as an array of `trait` objects.
  1. Added `is_immediate` as a `boolean_t` and `post_remediation_steps` as an array of `remediation_step` objects.
  1. Added `likelihood_id` as an `integer_t` enum and `likelihood` as a `string_t`. Aligns with NIST SP 800-30 Rev. 1 qualitative likelihood scale.
  1. Added `network_scan_info` as a `network_scan_info` object, `port_info` as a `port_info` object, and `port_scan_result_list` as an array of `port_scan_result` objects.
  1. Added `scan_duration` as a `timespan` object and `scanner_endpoint` as a `network_endpoint` object.
  1. Added `tcp_banner` as a `string_t`.
  1. Added `content_policy_filters` as an array of `content_policy_filter` objects.
  1. Added `guardrail_evaluation_result` as a `guardrail_evaluation_result` object.

### Improved
* #### Event Classes
  1. Added `likelihood` and `likelihood_id` to `Detection Finding` (class 2004).
  1. Added `guardrail_evaluation_result` to `Detection Finding` (class 2004).
* #### Objects
  1. Added `labels` to the `node` object for grouping nodes into named subgraphs.
  1. Added `labels` and `privilege_attack_info_list` to the `edge` object.
  1. Added `org` to the `at_least` constraint in the `user` object.
  1. Added `tcp_banner`, `tls`, and `http_response` to the `port_scan_result` object.

## [v1.0.0]

Initial release of AWS's OCSF Extension