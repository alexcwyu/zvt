# zvt: portable verification records

<!-- current-documentation-provenance -->
Documentation reviewed: 2026-10-13 / Git source base: `85e215aa7abd2093ea7fde1a00378c13f473641f` / [Current architecture and feature guide](../ayu-develop.md).
Historical execution commands/results below retain their original dates and scope; this metadata update is not a new application test run.
<!-- /current-documentation-provenance -->


Full raw logs are retained in the workspace maintenance evidence, not distributed here. Hashes identify those original logs. A successful build or selected test subset does not imply a full test-suite pass. Commands containing <workspace> describe the original execution environment.

[Machine-readable records](verification.json) · [Repository validation summary](../validation.md)

## Executed commands

| Check | Exit | Duration | Command | Outcomes |
| --- | ---: | ---: | --- | --- |
| build | 0 | 4.23s | `uv build --python 3.14` | Successfully built dist/zvt-0.13.4.tar.gz<br>Successfully built dist/zvt-0.13.4-py3-none-any.whl |
| build-python315-final | 0 | 2.57s | `uv build` | Successfully built dist/zvt-0.13.4.tar.gz<br>Successfully built dist/zvt-0.13.4-py3-none-any.whl |
| compile | 0 | 0.62s | `/Users/alex/.local/share/uv/python/cpython-3.14-macos-aarch64-none/bin/python3.14 -m compileall -q src` | See exit status; no test-count assertion. |
| compile-clean-source | 0 | 0.38s | `uv run --no-sync python -Werror::SyntaxWarning -m compileall -q -f src` | See exit status; no test-count assertion. |
| compile-python315-final-recorded | 0 | 0.14s | `uv run --frozen --all-extras --all-groups python -m compileall -q src tests` | See exit status; no test-count assertion. |
| dependency-add-final-recorded | 0 | 0.04s | `uv add --group dev ipython nbformat` | See exit status; no test-count assertion. |
| lock-3.14 | 0 | 0.31s | `uv lock --upgrade --python 3.14` | See exit status; no test-count assertion. |
| lock-3.15 | 0 | 0.3s | `uv lock --upgrade --python 3.15` | See exit status; no test-count assertion. |
| lock-python315-final | 0 | 0.55s | `uv lock --upgrade` | See exit status; no test-count assertion. |
| lock-python315-source-supported | 0 | 0.58s | `uv lock --upgrade --python 3.15` | See exit status; no test-count assertion. |
| sync-3.14 | 0 | 0.87s | `uv sync --all-extras --all-groups --python 3.14` | See exit status; no test-count assertion. |
| sync-python315-final | 0 | 0.16s | `uv sync --frozen --all-extras --all-groups` | See exit status; no test-count assertion. |
| sync-python315-source-supported | 0 | 4.91s | `uv sync --all-extras --all-groups --python 3.15` | See exit status; no test-count assertion. |
| tests | 1 | 80.98s | `uv run --no-sync python -m pytest` | 44 failed, 52 passed in 74.73s (0:01:14) |
| tests-pandas-sqlalchemy-compatibility | 1 | 725.33s | `uv run --no-sync python -m pytest` | 25 failed, 71 passed in 721.34s (0:12:01) |
| tests-python315-current-apis | 1 | 130.4s | `env PLOTLY_RENDERER=json uv run --frozen --all-extras --all-groups python -m pytest tests -v` | =================== 9 failed, 87 passed in 128.83s (0:02:08) =================== |
| tests-python315-final-all-accounts | 1 | unrecordeds | `env PLOTLY_RENDERER=json uv run --frozen --all-extras --all-groups python -m pytest tests -v` | =================== 8 failed, 88 passed in 119.10s (0:01:59) =================== |
| tests-python315-full-positional-account | 1 | 108.87s | `env PLOTLY_RENDERER=json uv run --frozen --all-extras --all-groups python -m pytest tests -v` | ================== 11 failed, 85 passed in 106.91s (0:01:46) =================== |
| tests-python315-headless-current-source | 1 | 119.43s | `env PLOTLY_RENDERER=json uv run --no-sync python -m pytest -vv -o faulthandler_timeout=60` | ================== 24 failed, 72 passed in 117.63s (0:01:57) =================== |
| tests-python315-headless-isolated-mocks | 1 | 25.1s | `env PLOTLY_RENDERER=json uv run --no-sync python -m pytest -vv -o faulthandler_timeout=60` | See exit status; no test-count assertion. |
| versions-final | 0 | 0.18s | `uv run --frozen --all-extras --all-groups python -c import sys, importlib.metadata as m; print(sys.version); print('\n'.join(sorted(d.metadata['Name']+'=='+d.version for d in m.distributions())))` | See exit status; no test-count assertion. |
| wheel-probe-3.14 | 2 | 0.05s | `uv sync --all-extras --all-groups --python 3.14 --no-build --no-install-project` | See exit status; no test-count assertion. |
| wheel-probe-3.15 | 2 | 1.73s | `uv sync --all-extras --all-groups --python 3.15 --no-build --no-install-project` | See exit status; no test-count assertion. |
