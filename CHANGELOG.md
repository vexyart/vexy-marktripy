# Changelog

All notable changes to marktripy will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Changed

- The documentation site now uses fly-january 0.4.0 or later (remote theme assets).
- Documentation builds now require fly-january 0.3.0 or later.
- Site now uses the fly-january 0.2.1 theme (chrome: none).

### Release setup

- The owner must configure or confirm the GitHub trusted publisher for the PyPI project `marktripy`: repository `vexyart/vexy-marktripy`, workflow `release.yml`, environment `pypi`.

### Completed backlog items

- AST validation checks node structure (`tests/test_hypothesis.py`, `TestASTValidation`).
- Heading levels can be shifted and normalised (`test_increase_heading_levels`, `test_normalize_headings`).
- Heading and element IDs support prefixes and existing IDs (`test_id_prefix`, `test_preserve_existing_ids`).
- Link collection and reference conversion work on the AST (`test_collect_links`, `test_convert_to_reference_links_numeric`).
- TOC generation supports a maximum heading depth (`test_generate_basic_toc`, `test_toc_with_max_level`).
- AST manipulation tests cover cloning, traversal and transformations (`tests/test_basic.py`, `tests/test_transformers.py`).
- Hypothesis generates ASTs and Markdown inputs for property tests (`tests/test_hypothesis.py`, 471f330).
- Benchmarks cover parsing, rendering, transformers and end-to-end workflows (`tests/test_benchmark.py`, 471f330).
- The Mistletoe parser adapter accepts Markdown input (`test_simple_paragraph` with the Mistletoe backend).
- Mistletoe tokens convert to the shared AST (`test_headings` and `test_parser_consistency`).
- The shared Markdown renderer serialises both adapters’ trees (`test_simple_paragraph`, `test_headings`).
- Markdown formatting options cover emphasis and list markers (`test_custom_emphasis_chars`, `test_custom_bullet_char`).
- The round-trip suite covers nested lists, emphasis, code and escaping (`tests/test_roundtrip.py`).
- Parser selection by name uses `ParserRegistry.create` (`test_simple_paragraph` runs with both names).
- Parser feature flags are available through `get_capabilities()` (see the preset examples in `src_docs/md/parsers.md`).
- The parser guide explains adapter trade-offs (`src_docs/md/parsers.md`).
- Extensions accept a configuration dictionary (`Extension.__init__`, 471f330).
- Keyboard key syntax has HTML and Markdown coverage (`tests/test_kbd_extension.py`).
- GFM strikethrough and task lists have parser and renderer coverage (`tests/test_gfm_extensions.py`).
- The extension development guide includes a custom highlight extension (`src_docs/md/extensions.md`).
- The API reference lists extension hooks and built-ins (`src_docs/md/api.md`).
- The extension guide documents renderer delegation, registration order and dependencies (`src_docs/md/extensions.md`).
- The user guide covers installation, parsing, transformation and rendering (`src_docs/md/.nav.yml`).
- The architecture guide diagrams the source layout and processing pipeline (`src_docs/md/architecture.md`).
- Integration tests exercise parser and renderer combinations and chained transformers (`test_parser_consistency`, `test_transform_pipeline`).
- PyPI packaging uses Hatch and VCS-derived versions (`pyproject.toml`, 471f330).
- Tagged releases use GitHub Actions (`.github/workflows/release.yml`, 315d0d5).
- GitHub Pages serves the built documentation from `docs/` (`.github/workflows/docs.yml`, a68b42d).
- The contributor guide covers local setup, tests and builds (`src_docs/md/contributing.md`).

## [0.2.0] - 2025-01-28

### Added
- Complete markdown-it-py parser adapter implementation
  - Token to AST conversion with full inline content support
  - Proper handling of all node types including nested structures
  - Plugin loading support for markdown-it-py extensions
- Full HTML renderer implementation
  - Support for all AST node types
  - Proper HTML escaping and attribute rendering
  - Context management for nested structures (lists, tables)
  - Configurable options (xhtml, breaks, langPrefix, etc.)
- Comprehensive test suite with 12 passing tests
  - Parser registration and functionality tests
  - HTML rendering tests including edge cases
  - AST manipulation tests (traversal, cloning, attributes)
- CI/CD pipeline with GitHub Actions
  - Multi-version Python testing (3.10, 3.11, 3.12)
  - Automated linting and formatting checks
  - Code coverage reporting with codecov
  - Release automation workflow
- Development tooling improvements
  - mypy configuration for type checking
  - Dependabot configuration for dependency updates
  - twine added for package publishing

### Fixed
- Heading content parsing now correctly processes inline tokens
- Token.tight attribute handled with safe fallback
- ASTNode clone method uses copy.copy for proper inheritance
- Inline formatting (strong/em) content captured correctly
- HTML attribute rendering excludes internal properties
- Walk method returns correct node count
- All ruff linter warnings resolved

### Changed
- Updated TODO.md to mark Phase 1 tasks as completed
- Enhanced WORK.md with detailed progress tracking

## [0.1.0] - 2025-01-28

### Added
- Initial project structure created with `uv` package manager
- Comprehensive `pyproject.toml` with all dependencies and tool configurations
- Core package architecture with modules: core, parsers, renderers, transformers, extensions, utils
- Abstract base classes and interfaces:
  - `ASTNode` hierarchy with all common Markdown element types (Document, Heading, Paragraph, Text, Emphasis, Strong, Link, Image, CodeBlock, InlineCode, List, ListItem, BlockQuote, HorizontalRule, Table, TableRow, TableCell)
  - `Parser` interface with preprocessing/postprocessing hooks and registry pattern
  - `Renderer` interface with context management and registry pattern
  - `Transformer` interface implementing visitor pattern with chaining support
  - `Extension` system with comprehensive hooks for parser rules, AST transformation, and rendering
- Registry pattern implemented across all major components for extensibility
- Integrated logging throughout using loguru
- Full type hints and comprehensive documentation for all classes and methods
- Development environment set up with Python 3.12, pytest, ruff, black, and hypothesis

### Infrastructure
- Configured pytest with coverage reporting
- Set up ruff linting with comprehensive rule selection
- Configured black code formatting with 100-character line length
- Added tool configurations for consistent development experience

### Dependencies
- Core: fire (CLI), rich (terminal UI), markdown-it-py (parser), mistletoe (parser), loguru (logging)
- Development: pytest, pytest-cov, ruff, black, hypothesis, mypy, twine

## 2026-10-18: documentation plugins

- Use MaterialX search, inherited metadata and a topic index; keep ordered navigation in awesome-nav.
- The documentation wrapper installs the plugins required by this site.
- Strict documentation build and rendered output checks passed.
