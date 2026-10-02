# Wild Herbarium — Case Study

Wild Herbarium is an offline-friendly mobile field guide for wild plants, starting with the Ukrainian Carpathians and the area around Shypit.

I am building it as an independent product and work across the full stack: product decisions, mobile architecture, backend, structured botanical data, and AI-assisted identification.

## My role

I am the founder and developer of the project.

My work includes:

- product architecture and feature design
- Flutter application development
- offline-first local data and caching
- Supabase/PostgreSQL backend work
- Edge Functions and API boundaries
- botanical and taxonomic data modeling
- AI-assisted plant identification workflows
- safety and look-alike logic
- automated data processing and verification
- testing and quality control

## Mobile architecture

The client is built with Flutter and follows a clean, modular architecture.

Main technologies:

- Flutter / Dart
- Riverpod
- GoRouter
- Drift
- gen-l10n

The app is designed to work well with unstable or missing connectivity. Curated content is cached locally, and the selected region remains local to the device rather than becoming part of a public backend profile.

## Backend

The backend uses Supabase and PostgreSQL, with Edge Functions acting as the public application boundary.

A key architectural rule is that the Flutter client does not directly query external biodiversity or identification providers. External sources and provider-specific logic stay behind backend boundaries, which makes the client simpler and gives the system one place to control validation, mapping, caching, and policy.

The backend includes structured data for plants, translations, taxonomy, media, regions, and editorial content.

## AI-assisted plant identification

Wild Herbarium is not designed around a single model response.

The identification flow is built as a multi-step pipeline:

1. a user provides one or more plant photos;
2. the system evaluates whether the input is usable;
3. an AI provider generates a shortlist of likely candidates;
4. additional checks can be used when the result is uncertain or safety-sensitive;
5. the user chooses the final plant rather than having the system silently persist a guess.

The pipeline is designed around uncertainty rather than pretending that image identification is always reliable.

Important concerns include:

- visually similar species
- potentially unsafe look-alikes
- poor or incomplete photos
- provider disagreement
- accepted taxonomy vs provider-specific names
- keeping temporary model suggestions separate from confirmed user data

## Taxonomy and data quality

A large part of the project is not UI work but data quality.

I work with structured botanical datasets, accepted names, synonyms, regional occurrence, conservation information, and media licensing.

Provider observations are mapped back to the project's own taxonomy instead of allowing external provider naming to become the source of truth automatically.

This is especially important for a plant product because an answer can be technically plausible while still being taxonomically outdated, regionally wrong, or unsafe.

## AI agents in the development workflow

I also use AI agents as part of the engineering process itself.

Typical tasks include:

- implementation and refactoring
- backend work
- research and source review
- structured data preparation
- repetitive verification
- debugging
- planning multi-step migrations
- comparing outputs from different approaches

I do not treat agent output as automatically correct. For larger tasks I define scope, invariants, acceptance criteria, and verification steps, then review the resulting changes.

## Current direction

The project is being developed beyond a simple plant encyclopedia.

The broader direction includes:

- field observations and a personal herbarium
- region-aware discovery
- AI-assisted identification
- educational content
- safer handling of uncertain plant matches
- a larger curated Ukrainian plant catalog

Most of the production code and data repositories are private, so this page is intended as a public overview of the engineering work without exposing private implementation details or datasets.
