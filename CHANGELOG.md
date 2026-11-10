# Changelog

All notable changes to CUATRO are documented here.
This project adheres to [Semantic Versioning](https://semver.org/).

## [1.0.0] — 2026-11-10

First public release.

### Added
- Four-classifier viral detection over assembled contigs: VirSorter2 and geNomad
  (marker-gene content, backbone tools), Deep6 and ViraLM (sequence composition,
  support tools).
- Four-tier confidence assignment (A/B/C/D) in `05_build_master_table`.
- Optional host screen (`00_host_screen`) that flags host-mapping contigs
  without removing them.
- CheckV integration for completeness and contamination estimates.
- Per-tier FASTA extraction (A, B, C, AB, ABC).

### Tier rules
- Tier B requires one backbone tool (VirSorter2 or geNomad) and at least one
  support tool (Deep6 or ViraLM). A backbone call alone does not reach a viral
  tier.
- The geNomad threshold for a Tier A solo call is hardcoded at 0.9, while the
  VirSorter2 equivalent is exposed as `--vs2_high`.
- The geNomad plasmid rule is evaluated before the Tier A rules, so a
  plasmid-flagged contig with a single strong backbone call is assigned
  `D_plasmid_flagged`.
