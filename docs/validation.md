# Validation evidence: zvt


Current campaign decision: the user explicitly excludes the remaining failing tests from completion requirements. Historical failures below remain failures; they are not relabeled as passes. Source/build/tooling/documentation requirements remain in scope.

Run date: 2026-10-12. Branch: `feature/ayu_develop`. Interpreter: `3.15.0 (main, Oct  9 2026, 15:11:47) [Clang 22.1.3 ]`.

| Check | Result |
|---|---|
| lock | passed |
| sync | passed |
| compile | passed |
| build | passed |
| tests | failed |

## Current result and compatibility decisions

- The complete 96-case supplied suite runs on managed Python 3.15.0 without exclusions: 88 passed, 8 failed. All three supplied trader integration cases now pass.
- Production code uses SQLAlchemy2 declarative_base/Session.get, pandas iloc for positional access, current hour/day/month frequencies, ISO-date JSON logging and Pydantic model_validate with existing from_attributes configuration. Public provider and account APIs remain intact.
- Shenzhen XLSX exports omit a Normal named-style entry while providing its style index. The recorder restores only that missing metadata; worksheet values, formats and all other archive members are preserved. No warning filter is added.
- The preexisting isolated recorder fixture now restores sys.modules after loading its stubbed module, preventing unrelated later integration imports from using fake packages. Assertions and case counts are unchanged.
- Headless tests use PLOTLY_RENDERER=json with current IPython and nbformat in the dev group. Existing chart assertions execute and figures serialize without browser-server sockets.
- Seven JoinQuant recorder cases receive HTTP403 with the explicit provider message that non-mainland-China IP addresses are unsupported. The EastMoney kline case receives RemoteDisconnected from the remote HTTPS endpoint. These eight external failures remain visible; no tests are disabled.

Current unresolved checks:

- tests: exit 1; see [check record](maintenance/index.html)

## Latest full-suite output

```text
ponse = requests.post(url, data=json.dumps(body))

        if response.status_code != 200:
            print(f"request jqdata error,code:{response.status_code},text:{response.text}")
>           raise HttpAccessError(code=response.status_code, msg=response.text)
E           jqdatapy.api.HttpAccessError: code:403,msg:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问

.venv/lib/python3.15/site-packages/jqdatapy/api.py:323: HttpAccessError
----------------------------- Captured stdout call -----------------------------
request jqdata error,code:403,text:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问
____________________________ test_1d_kdata_recorder ____________________________

    def test_1d_kdata_recorder():
>       recorder = JqChinaStockKdataRecorder(
            codes=SAMPLE_STOCK_CODES, sleeping_time=0, level=IntervalLevel.LEVEL_1DAY, real_time=False
        )

tests/recorders/joinquant/test_quote_recorder.py:33:
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
src/zvt/recorders/joinquant/quotes/jq_stock_kdata_recorder.py:81: in __init__
    get_token(zvt_config["jq_username"], zvt_config["jq_password"], force=True)
.venv/lib/python3.15/site-packages/jqdatapy/api.py:268: in get_token
    token = _get_token(jqdata_env["username"], jqdata_env["password"])
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

mob = '', pwd = ''

    def _get_token(mob=None, pwd=None):
        body = {
            "method": "get_token",
            "mob": mob,
            "pwd": pwd,
        }
        response = requests.post(url, data=json.dumps(body))

        if response.status_code != 200:
            print(f"request jqdata error,code:{response.status_code},text:{response.text}")
>           raise HttpAccessError(code=response.status_code, msg=response.text)
E           jqdatapy.api.HttpAccessError: code:403,msg:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问

.venv/lib/python3.15/site-packages/jqdatapy/api.py:323: HttpAccessError
----------------------------- Captured stdout call -----------------------------
request jqdata error,code:403,text:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问
__________________________ test_1d_hfq_kdata_recorder __________________________

    def test_1d_hfq_kdata_recorder():
>       recorder = JqChinaStockKdataRecorder(
            codes=["000338"], sleeping_time=0, level=IntervalLevel.LEVEL_1DAY, real_time=False, adjust_type="hfq"
        )

tests/recorders/joinquant/test_quote_recorder.py:43:
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
src/zvt/recorders/joinquant/quotes/jq_stock_kdata_recorder.py:81: in __init__
    get_token(zvt_config["jq_username"], zvt_config["jq_password"], force=True)
.venv/lib/python3.15/site-packages/jqdatapy/api.py:268: in get_token
    token = _get_token(jqdata_env["username"], jqdata_env["password"])
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

mob = '', pwd = ''

    def _get_token(mob=None, pwd=None):
        body = {
            "method": "get_token",
            "mob": mob,
            "pwd": pwd,
        }
        response = requests.post(url, data=json.dumps(body))

        if response.status_code != 200:
            print(f"request jqdata error,code:{response.status_code},text:{response.text}")
>           raise HttpAccessError(code=response.status_code, msg=response.text)
E           jqdatapy.api.HttpAccessError: code:403,msg:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问

.venv/lib/python3.15/site-packages/jqdatapy/api.py:323: HttpAccessError
----------------------------- Captured stdout call -----------------------------
request jqdata error,code:403,text:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问
____________________________ test_1h_kdata_recorder ____________________________

    def test_1h_kdata_recorder():
>       recorder = JqChinaStockKdataRecorder(
            codes=["000338"],
            sleeping_time=0,
            level=IntervalLevel.LEVEL_1HOUR,
            real_time=False,
            start_timestamp="2019-01-01",
        )

tests/recorders/joinquant/test_quote_recorder.py:53:
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
src/zvt/recorders/joinquant/quotes/jq_stock_kdata_recorder.py:81: in __init__
    get_token(zvt_config["jq_username"], zvt_config["jq_password"], force=True)
.venv/lib/python3.15/site-packages/jqdatapy/api.py:268: in get_token
    token = _get_token(jqdata_env["username"], jqdata_env["password"])
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

mob = '', pwd = ''

    def _get_token(mob=None, pwd=None):
        body = {
            "method": "get_token",
            "mob": mob,
            "pwd": pwd,
        }
        response = requests.post(url, data=json.dumps(body))

        if response.status_code != 200:
            print(f"request jqdata error,code:{response.status_code},text:{response.text}")
>           raise HttpAccessError(code=response.status_code, msg=response.text)
E           jqdatapy.api.HttpAccessError: code:403,msg:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问

.venv/lib/python3.15/site-packages/jqdatapy/api.py:323: HttpAccessError
----------------------------- Captured stdout call -----------------------------
request jqdata error,code:403,text:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问
____________________________ test_5m_kdata_recorder ____________________________

    def test_5m_kdata_recorder():
>       recorder = JqChinaStockKdataRecorder(
            codes=["000338"], sleeping_time=0, level=IntervalLevel.LEVEL_5MIN, real_time=False, start_timestamp="2019-01-01"
        )

tests/recorders/joinquant/test_quote_recorder.py:67:
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
src/zvt/recorders/joinquant/quotes/jq_stock_kdata_recorder.py:81: in __init__
    get_token(zvt_config["jq_username"], zvt_config["jq_password"], force=True)
.venv/lib/python3.15/site-packages/jqdatapy/api.py:268: in get_token
    token = _get_token(jqdata_env["username"], jqdata_env["password"])
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

mob = '', pwd = ''

    def _get_token(mob=None, pwd=None):
        body = {
            "method": "get_token",
            "mob": mob,
            "pwd": pwd,
        }
        response = requests.post(url, data=json.dumps(body))

        if response.status_code != 200:
            print(f"request jqdata error,code:{response.status_code},text:{response.text}")
>           raise HttpAccessError(code=response.status_code, msg=response.text)
E           jqdatapy.api.HttpAccessError: code:403,msg:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问

.venv/lib/python3.15/site-packages/jqdatapy/api.py:323: HttpAccessError
----------------------------- Captured stdout call -----------------------------
request jqdata error,code:403,text:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问
____________________________ test_stock_money_flow _____________________________

    def test_stock_money_flow():
        provider = "joinquant"
        # Stock.record_data(provider=provider)
>       StockMoneyFlow.record_data(
            codes=["300999", "688981"], provider=provider, start_timestamp="2020-12-14", compute_index_money_flow=False
        )

tests/recorders/joinquant/test_stock_money_flow.py:8:
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
src/zvt/contract/schema.py:320: in record_data
    r = recorder_class(**kw)
        ^^^^^^^^^^^^^^^^^^^^
src/zvt/recorders/joinquant/misc/jq_stock_money_flow_recorder.py:67: in __init__
    get_token(zvt_config["jq_username"], zvt_config["jq_password"], force=True)
.venv/lib/python3.15/site-packages/jqdatapy/api.py:268: in get_token
    token = _get_token(jqdata_env["username"], jqdata_env["password"])
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

mob = '', pwd = ''

    def _get_token(mob=None, pwd=None):
        body = {
            "method": "get_token",
            "mob": mob,
            "pwd": pwd,
        }
        response = requests.post(url, data=json.dumps(body))

        if response.status_code != 200:
            print(f"request jqdata error,code:{response.status_code},text:{response.text}")
>           raise HttpAccessError(code=response.status_code, msg=response.text)
E           jqdatapy.api.HttpAccessError: code:403,msg:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问

.venv/lib/python3.15/site-packages/jqdatapy/api.py:323: HttpAccessError
----------------------------- Captured stdout call -----------------------------
StockMoneyFlow registered recorders:{'joinquant': <class 'zvt.recorders.joinquant.misc.jq_stock_money_flow_recorder.JoinquantStockMoneyFlowRecorder'>, 'sina': <class 'zvt.recorders.sina.money_flow.sina_stock_money_flow_recorder.SinaStockMoneyFlowRecorder'>}
request jqdata error,code:403,text:很抱歉，当前暂不支持来自非中国大陆地区 IP 地址的访问
=========================== short test summary info ============================
FAILED tests/recorders/em/test_em_api.py::test_get_kdata - requests.exception...
FAILED tests/recorders/joinquant/test_quote_recorder.py::test_1wk_kdata_recorder
FAILED tests/recorders/joinquant/test_quote_recorder.py::test_1mon_kdata_recorder
FAILED tests/recorders/joinquant/test_quote_recorder.py::test_1d_kdata_recorder
FAILED tests/recorders/joinquant/test_quote_recorder.py::test_1d_hfq_kdata_recorder
FAILED tests/recorders/joinquant/test_quote_recorder.py::test_1h_kdata_recorder
FAILED tests/recorders/joinquant/test_quote_recorder.py::test_5m_kdata_recorder
FAILED tests/recorders/joinquant/test_stock_money_flow.py::test_stock_money_flow
=================== 8 failed, 88 passed in 119.10s (0:01:59) ===================

```

## Exact commands and exit codes

Unsuccessful rows are retained as historical compatibility attempts; they are not claims that a current passing check remains blocked. Source-build probes use isolated temporary copies to preserve the selected repository environment.

| Command | Exit | Seconds | Evidence |
|---|---:|---:|---|
| `uv lock --upgrade --python 3.15` | 0 | 0.3 | [check record](maintenance/index.html) |
| `uv sync --all-extras --all-groups --python 3.15 --no-build --no-install-project` | 2 | 1.73 | [check record](maintenance/index.html) |
| `uv lock --upgrade --python 3.14` | 0 | 0.31 | [check record](maintenance/index.html) |
| `uv sync --all-extras --all-groups --python 3.14 --no-build --no-install-project` | 2 | 0.05 | [check record](maintenance/index.html) |
| `uv sync --all-extras --all-groups --python 3.14` | 0 | 0.87 | [check record](maintenance/index.html) |
| `uv build --python 3.14` | 0 | 4.23 | [check record](maintenance/index.html) |
| `/Users/alex/.local/share/uv/python/cpython-3.14-macos-aarch64-none/bin/python3.14 -m compileall -q src` | 0 | 0.62 | [check record](maintenance/index.html) |
| `uv run --no-sync python -m pytest` | 1 | 80.98 | [check record](maintenance/index.html) |
| `uv run --no-sync python -m pytest` | 1 | 725.33 | [check record](maintenance/index.html) |
| `uv lock --upgrade --python 3.15` | 0 | 0.58 | [check record](maintenance/index.html) |
| `uv sync --all-extras --all-groups --python 3.15` | 0 | 4.91 | [check record](maintenance/index.html) |
| `env PLOTLY_RENDERER=json uv run --no-sync python -m pytest -vv -o faulthandler_timeout=60` | 1 | 25.1 | [check record](maintenance/index.html) |
| `uv run --no-sync python -Werror::SyntaxWarning -m compileall -q -f src` | 0 | 0.38 | [check record](maintenance/index.html) |
| `env PLOTLY_RENDERER=json uv run --no-sync python -m pytest -vv -o faulthandler_timeout=60` | 1 | 119.43 | [check record](maintenance/index.html) |
| `env PLOTLY_RENDERER=json uv run --frozen --all-extras --all-groups python -m pytest tests -v` | 1 | 130.4 | [check record](maintenance/index.html) |
| `env PLOTLY_RENDERER=json uv run --frozen --all-extras --all-groups python -m pytest tests -v` | 1 | 108.87 | [check record](maintenance/index.html) |
| `env PLOTLY_RENDERER=json uv run --frozen --all-extras --all-groups python -m pytest tests -v` | 1 | 122.39 | [check record](maintenance/index.html) |
| `uv lock --upgrade` | 0 | 0.55 | [check record](maintenance/index.html) |
| `uv sync --frozen --all-extras --all-groups` | 0 | 0.16 | [check record](maintenance/index.html) |
| `uv build` | 0 | 2.57 | [check record](maintenance/index.html) |
| `uv run --frozen --all-extras --all-groups python -m compileall -q src tests` | 0 | 0.14 | [check record](maintenance/index.html) |
| `uv run --frozen --all-extras --all-groups python -c import sys, importlib.metadata as m; print(sys.version); print('\n'.join(sorted(d.metadata['Name']+'=='+d.version for d in m.distributions())))` | 0 | 0.18 | [check record](maintenance/index.html) |
| `uv add --group dev ipython nbformat` | 0 | 0.04 | [check record](maintenance/index.html) |

The versions-final log records the exact interpreter patch release and every installed dependency version. The machine-readable [verification record](maintenance/verification.json) includes branch/default ancestry, status, artifacts and unresolved checks.

## Dependency floor refresh

| Before | After |
|---|---|

The table records the initial metadata refresh. Later compatibility constraints and vendor sources are explained above and the final authoritative requirements are in [pyproject.toml](../pyproject.toml) and [uv.lock](../uv.lock). No test cases were added, removed or disabled. Existing deprecated-API cases retain their assertions while explicitly checking the documented warning.
