<div align="center">

# tap-bitso

<div>
  <a href="https://github.com/reservoir-data/tap-bitso/blob/main/LICENSE">
    <img alt="License" src="https://img.shields.io/github/license/reservoir-data/tap-bitso"/>
  </a>
  <a href="https://results.pre-commit.ci/latest/github/reservoir-data/tap-bitso/main">
    <img alt="pre-commit.ci status" src="https://results.pre-commit.ci/badge/github/reservoir-data/tap-bitso/main.svg"/>
  </a>
  <a href="https://scientific-python.org/specs/spec-0000/">
    <img alt="SPEC 0 — Minimum Supported Dependencies" src="https://img.shields.io/badge/SPEC-0-green"/>
  </a>
  <a href="https://github.com/astral-sh/ruff">
    <img src="https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/charliermarsh/ruff/main/assets/badge/v2.json" alt="Ruff" style="max-width:100%;">
  </a>
  <a href="https://github.com/astral-sh/uv">
   <img alt="uv" src="https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/uv/main/assets/badge/v0.json"/>
  </a>
  <a href="https://pypi.org/p/tap-bitso/">
    <img alt="Python versions" src="https://img.shields.io/pypi/pyversions/tap-bitso"/>
  </a>
</div>

Singer tap for the [Bitso API](https://bitso.com/api_info).

Built with the Meltano [SDK](https://gitlab.com/meltano/sdk) for Singer Taps.

</div>

## Installation

```bash
uv tool install git+https://github.com/reservoir-data/tap-bitso.git
```

## Configuration

### Accepted Config Options

A full list of supported settings and capabilities for this
tap is available by running:

```bash
tap-bitso --about
```

| Field      | Description             | Type           | Required | Default                 |
|------------|-------------------------|----------------|----------|-------------------------|
| `key`      | Bitso API Key           | `string`       | yes      |                         |
| `secret`   | Bitso API Secret        | `string`       | yes      |                         |
| `base_url` | Bitso API URL           | `string`       | no       | `https://api.bitso.com` |
| `books`    | Tickers to get data for | `list(string)` | no       | `["btc_mxn"]`           |

### Source Authentication and Authorization

This tap handles the [digest access authentication for the Bitso API](https://docs.bitso.com/bitso-api/docs/authentication).

## Usage

You can easily run `tap-bitso` by itself or in a pipeline using [Meltano](www.meltano.com).

### Executing the Tap Directly

```bash
tap-bitso --version
tap-bitso --help
tap-bitso --config CONFIG --discover > ./catalog.json
```

## Developer Resources

### Initialize your Development Environment

```bash
uv sync
```


### Create and Run Tests

Create tests within the `tap_bitso/tests` subfolder and
  then run:

```bash
uv run pytest
```

You can also test the `tap-bitso` CLI interface directly using `uv run`:

```bash
uv run tap-bitso --help
```


### Testing with [Meltano](https://www.meltano.com)

_**Note:** This tap will work in any Singer environment and does not require Meltano.
Examples here are for convenience and to streamline end-to-end orchestration scenarios._

Next, install Meltano (if you haven't already) and any needed plugins:

```bash
# Install meltano
uv tool install meltano
# Initialize meltano within this directory
cd tap-bitso
meltano install
```

Now you can test and orchestrate using Meltano:

```bash
# Test invocation:
meltano invoke tap-bitso --version

# OR run a test EL pipeline:
meltano run tap-bitso target-sqlite
```

### SDK Dev Guide

See the [dev guide](https://sdk.meltano.com/en/latest/dev_guide.html) for more instructions on how to use the SDK to
develop your own taps and targets.
