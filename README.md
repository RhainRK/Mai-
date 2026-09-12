# MAI v0.9.6

MAI is a local-first AI character runtime with persistent memory, configurable identity, typed tools, voice support, and avatar integration.

This release combines runtime hardening, security fixes, and a cleaner public distribution intended for local experimentation and development.

## Security notice for earlier versions

A security review of the v0.9.4 baseline identified two notable issues:

* **Tool authorization weaknesses** — tools outside the current turn's advertised selection could execute, and empty permission sets could restore permissive defaults.
* **Prompt-injection exposure** — compressed conversation content could be reintroduced with system-level authority.

These issues were addressed in v0.9.5 and the fixes are included in v0.9.6.

Earlier private configurations could also automatically treat the local operator as MAI's creator. The public build removes that automatic assumption and requires creator identity to be configured explicitly.

## Public-release changes

* Removes credentials and private runtime configuration.
* Excludes `.env` files, runtime databases, logs, recordings, caches, and generated audio.
* Removes account-specific voice configuration.
* Removes generated training datasets and ships with an empty training seed.
* Includes security-review documentation and dependency-check results.
* Includes source checksums for release-integrity verification.
* Retains MAI's local-first architecture and configurable identity system.

## Validation

The release candidate completed the following checks:

* **129 tests passed**
* **1 test skipped**
* Python source compilation passed.
* Archive-integrity checks passed.
* Source-checksum validation passed.
* Limited credential-pattern scanning found no known embedded credentials in the release package.

## Known limitations and remaining risks

The current security review is not exhaustive.

Known or documented areas for further hardening include:

* sensitive information potentially appearing in diagnostic or application logs;
* speech-service tokens being transmitted through URLs in some configurations;
* incomplete historical-data erasure guarantees;
* incomplete dependency auditing for several optional voice, training, and external-service components;
* risks introduced when local-only services are exposed to remote networks;
* existing Git history is outside the scope of the packaged-source audit.

Users should keep API keys and other credentials in local environment configuration and should not commit `.env` files or runtime data to version control.

## Status

MAI v0.9.6 is an **experimental source preview**, not a production security certification.

The audit identified and addressed specific weaknesses in earlier builds, but no claim is made that the software is free of vulnerabilities. No exploitation or credential compromise has been established by this review.

MAI is distributed without a software licence. No rights to use, modify, or redistribute the source are granted unless permission is provided separately.

