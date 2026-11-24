# this_file: WORK.md

## Current state

- The contributor guide describes the existing PyPI Trusted Publishing workflow. The owner needs to confirm the publisher for `vexyart/vexy-marktripy`, workflow `release.yml`, environment `pypi`.
- `bash -n publish.sh` and `actionlint .github/workflows/release.yml` passed. Live publishing was not exercised.
- `./build.sh docs` completed with zero warnings using fly-january 0.2.1 and unbranded chrome.
- `uv run pytest -q` ran 102 tests. 101 passed. In `test_parse_lists`, Hypothesis generated `items=['-']`. The fixture expects a flat list, but its Markdown input `- -` creates a nested list.
