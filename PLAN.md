---
this_file: PLAN.md
---

# Implementation plan

## Parsing and rendering

- **Preserve Markdown formatting and special characters on round trips.** Compare input and output for hard breaks, escaped punctuation and nested blocks. Check that the preserve_format option changes the result.
- **Resolve differences between parser adapters.** Compare table bodies, images, fenced code and strikethrough from both backends, including the resulting HTML and Markdown. Check capability flags against actual output.
- **Verify reference definitions and TOC marker replacement.** Render a reference link and parse it back. Place a TOC marker between paragraphs and check the generated list replaces it there.

## Extensions and transformers

- **Resolve extension dependencies.** Exercise registration in reverse dependency order, missing dependencies and cycles. The manager currently requires prerequisites to be registered first.
- **Support MyST syntax, custom directives and custom blocks.** Check a directive through parsing, transformation and both renderers.
- **Provide five runnable extension examples.** Run the examples against the documented extension hooks and check their output.
- **Implement cross-references, citations and footnote reordering.** Check target resolution, repeated citations and footnote ordering after edits.

## Performance and CLI

- **Profile and optimise measured hot paths.** Compare the same documents against reference parsers and the original target of twice the fastest pure-Python runtime.
- **Implement document caching and incremental parsing.** Compare cached and incrementally updated results with a fresh parse after an edit.
- **Provide a Fire CLI with batch processing, watch mode and Rich output.** Run the installed command on one file, a batch and a changed file. Check output and error status.

## Documentation and testing

- **Check public API docstring coverage.** Compare the API reference against the public classes and methods and document any omissions.
- **Write a cookbook with at least 20 examples and example projects.** Run the examples against the installed package.
- **Raise test coverage above 95%.** Measure with pytest-cov and exercise uncovered branches.
- **Verify fuzz coverage and security behaviour.** Exercise malformed Markdown with both parsers and check rendering of untrusted input. Reproduce the flat-list property with a dash as the item text.

## Packaging and maintenance

- **Create a conda-forge recipe.** Build the package from the recipe and import it in a fresh environment.
- **Add issue templates and a code of conduct.** Check the issue forms and contributor-facing links.
- **Set a release schedule.** Record the agreed cadence alongside the release instructions.

## Longer-term research

- **Assess streaming parsing and an async API.** Compare memory use on a large input and identify operations that benefit from asynchronous execution.
- **Assess WebAssembly, language server and collaborative editing support.** Record feasibility and constraints for each proposed integration.
