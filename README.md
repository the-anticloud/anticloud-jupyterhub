# JUPYTERHUB

![license](https://img.shields.io/badge/license-license-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-academia_rd-lightgrey)

> Anticloud-hardened packaging of the upstream project `JUPYTERHUB` in category **ACADEMIA RD**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** ACADEMIA RD · **Upstream:** https://github.com/jupyterhub/jupyterhub · **Upstream pin:** `1dd5f4c3c0d928bdf8363bcee2456de6f2499134` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

**[Technical Overview](#technical-overview)** |
**[Installation](#installation)** |
**[Configuration](#configuration)** |
**[Docker](#docker)** |
**[Contributing](#contributing)** |
**[License](#license)** |
**[Help and Resources](#help-and-resources)**

---

# [JupyterHub](https://github.com/jupyterhub/jupyterhub)

[![Latest PyPI version](https://img.shields.io/pypi/v/jupyterhub?logo=pypi)](https://pypi.python.org/pypi/jupyterhub)
[![Latest conda-forge version](https://img.shields.io/conda/vn/conda-forge/jupyterhub?logo=conda-forge)](https://anaconda.org/conda-forge/jupyterhub)
[![Documentation build status](https://img.shields.io/readthedocs/jupyterhub?logo=read-the-docs)](https://jupyterhub.readthedocs.org/en/latest/)
[![GitHub Workflow Status - Test](https://img.shields.io/github/workflow/status/jupyterhub/jupyterhub/Test?logo=github&label=tests)](https://github.com/jupyterhub/jupyterhub/actions)
[![Test coverage of code](https://codecov.io/gh/jupyterhub/jupyterhub/branch/main/graph/badge.svg)](https://codecov.io/gh/jupyterhub/jupyterhub)
[![GitHub](https://img.shields.io/badge/issue_tracking-github-blue?logo=github)](https://github.com/jupyterhub/jupyterhub/issues)
[![Discourse](https://img.shields.io/badge/help_forum-discourse-blue?logo=discourse)](https://discourse.jupyter.org/c/jupyterhub)
[![Gitter](https://img.shields.io/badge/social_chat-gitter-blue?logo=gitter)](https://gitter.im/jupyterhub/jupyterhub)

With [JupyterHub](https://jupyterhub.readthedocs.io) you can create a
**multi-user Hub** that spawns, manages, and proxies multiple instances of the
single-user [Jupyter notebook](https://jupyter-notebook.readthedocs.io)
server.

[Project Jupyter](https://jupyter.org) created JupyterHub to support many
users. The Hub can offer notebook servers to a class of students, a corporate
data science workgroup, a scientific research project, or a high-performance
computing group.

## Technical overview

Three main actors make up JupyterHub:

- multi-user **Hub** (tornado process)
- configurable http **proxy** (node-http-proxy)
- multiple **single-user Jupyter notebook servers** (Python/Jupyter/tornado)

Basic principles for operation are:

- Hub launches a proxy.
- The Proxy forwards all requests to Hub by default.
- Hub handles login and spawns single-user servers on demand.
- Hub configures proxy to forward URL prefixes to the single-user notebook
  servers.

JupyterHub also provides a
[REST API][]
for administration of the Hub and its users.

[rest api]: https://jupyterhub.readthedocs.io/en/latest/reference/rest-api.html

## Installation

### Check prerequisites

- A Linux/Unix based system
- [Python](https://www.python.org/downloads/) 3.10 or greater
- [nodejs/npm](https://www.npmjs.com/)
  - If you are using **`conda`**, the nodejs and npm dependencies will be installed for
    you by conda.

  - If you are using **`pip`**, install a recent version (at least 12.0) of
    [nodejs/npm](https://docs.npmjs.com/getting-started/installing-node).

- If using the default PAM Authenticator, a [pluggable authentication module (PAM)](https://en.wikipedia.org/wiki/Pluggable_authentication_module).
- TLS certificate and key for HTTPS communication
- Domain name

### Install packages

#### Using `conda`

To install JupyterHub along with its dependencies including nodejs/npm:

```bash
conda install -c conda-forge jupyterhub
```

If you plan to run notebook servers locally, install JupyterLab or Jupyter notebook:

```bash
conda install jupyterlab
conda install notebook
```

#### Using `pip`

JupyterHub can be installed with `pip`, and the proxy with `npm`:

```bash
npm install -g configurable-http-proxy
python3 -m pip install jupyterhub
```

If you plan to run notebook servers locally, you will need to install
[JupyterLab or Jupyter notebook](https://jupyter.readthedocs.io/en/latest/install.html):

    python3 -m pip install --upgrade jupyterlab
    python3 -m pip install --upgrade notebook

### Run the Hub server

To start the Hub server, run the command:

    jupyterhub

Visit `http://localhost:8000` in your browser, and sign in with your system username and password.

_Note_: To allow multiple users to sign in to the server, you will need to
run the `jupyterhub` command as a _privileged user_, such as root.
The [documentation](https://jupyterhub.readthedocs.io/en/latest/howto/configuration/config-sudo.html)
describes how to run the server as a _less privileged user_, which requires
more configuration of the system.

## Configuration

The [Getting Started](https://jupyterhub.readthedocs.io/en/latest/tutorial/index.html#getting-started) section of the
documentation explains the common steps in setting up JupyterHub.

The [**JupyterHub tutorial**](https://github.com/jupyterhub/jupyterhub-tutorial)
provides an in-depth video and sample configurations of JupyterHub.

### Create a configuration file

To generate a default config file with settings and descriptions:

    jupyterhub --generate-config

### Start the Hub

To start the Hub on a specific url and port `10.0.1.2:443` with **https**:

    jupyterhub --ip 10.0.1.2 --port 443 --ssl-key my_ssl.key --ssl-cert my_ssl.cert

### Authenticators

| Authenticator                                                                | Description                                       |
| ---------------------------------------------------------------------------- | ------------------------------------------------- |
| PAMAuthenticator                                                             | Default, built-in authenticator                   |
| [OAuthenticator](https://github.com/jupyterhub/oauthenticator)               | OAuth + JupyterHub Authenticator = OAuthenticator |
| [ldapauthenticator](https://github.com/jupyterhub/ldapauthenticator)         | Simple LDAP Authenticator Plugin for JupyterHub   |
| [kerberosauthenticator](https://github.com/jupyterhub/kerberosauthenticator) | Kerberos Authenticator Plugin for JupyterHub      |

### Spawners

| Spaw

*(excerpt; full text in `UPSTREAM_CLONE/`)*

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Node.js / npm** (manifests: package.json, package-lock.json; scanned in UPSTREAM_CLONE)
- Top-level source layout: `ci/`, `examples/`, `jsx/`, `jupyterhub/`, `share/`, `testing/`
- Upstream commit pinned for this packaging: `1dd5f4c3c0d928bdf8363bcee2456de6f2499134`

---

## Installation

**[Configuration](#configuration)** |
**[Docker](#docker)** |
**[Contributing](#contributing)** |
**[License](#license)** |
**[Help and Resources](#help-and-resources)**

---

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

documentation explains the common steps in setting up JupyterHub.

The [**JupyterHub tutorial**](https://github.com/jupyterhub/jupyterhub-tutorial)
provides an in-depth video and sample configurations of JupyterHub.

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

[![GitHub Workflow Status - Test](https://img.shields.io/github/workflow/status/jupyterhub/jupyterhub/Test?logo=github&label=tests)](https://github.com/jupyterhub/jupyterhub/actions)
[![Test coverage of code](https://codecov.io/gh/jupyterhub/jupyterhub/branch/main/graph/badge.svg)](https://codecov.io/gh/jupyterhub/jupyterhub)
[![GitHub](https://img.shields.io/badge/issue_tracking-github-blue?logo=github)](https://github.com/jupyterhub/jupyterhub/issues)
[![Discourse](https://img.shields.io/badge/help_forum-discourse-blue?logo=discourse)](https://discourse.jupyter.org/c/jupyterhub)
[![Gitter](https://img.shields.io/badge/social_chat-gitter-blue?logo=gitter)](https://gitter.im/jupyterhub/jupyterhub)

With [JupyterHub](https://jupyterhub.readthedocs.io) you can create a
**multi-user Hub** that spawns, manages, and proxies multiple instances of the
single-user [Jupyter notebook](https://jupyter-notebook.readthedocs.io)
server.

[Project Jupyter](https://jupyter.org) created JupyterHub to support many
users. The Hub can offer notebook servers to a class of students, a corporate
data science workgroup, a scientific research project, or a high-performance
computing group.

*Section quoted from the upstream readme.*
---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Node.js / npm |
| Manifests detected | package.json, package-lock.json |
| Files in snapshot | not captured in this benchmark snapshot |
| Lines of code | not captured in this benchmark snapshot |
| Dependency references | not captured in this benchmark snapshot |
| Upstream license | No license file present in the upstream snapshot |
| Overlay license | Anticommons 0.1.0 |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

**[Docker](#docker)** |
**[Contributing](#contributing)** |
**[License](#license)** |
**[Help and Resources](#help-and-resources)**

---

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

*Excerpt from upstream `CONTRIBUTING.md`:*

# Contributing to JupyterHub

Welcome! As a [Jupyter](https://jupyter.org) project,
you can follow the [Jupyter contributor guide](https://jupyter.readthedocs.io/en/latest/contributing/content-contributor.html).

Make sure to also follow [Project Jupyter's Code of Conduct](https://github.com/jupyter/governance/blob/HEAD/conduct/code_of_conduct.md)
for a friendly and welcoming collaborative environment.

Please see our documentation on

- [Setting up a development install](https://jupyterhub.readthedocs.io/en/latest/contributing/setup.html)
- [Testing JupyterHub and linting code](https://jupyterhub.readthedocs.io/en/latest/contributing/tests.html)

If you need some help, feel free to ask on [Gitter](https://gitter.im/jupyterhub/jupyterhub) or [Discourse](https://discourse.jupyter.org/).

## Our Copyright Policy

Jupyter uses a shared copyright model. Each contributor maintains copyright
over their contributions to Jupyter. But, it is important to note that these
contributions are typically only changes to the projects. Thus, the Jupyter
source code, in its entirety is not the copyright of any single person or
institution. Instead, it is the collective copyright of the entire Jupyter
Development Team. If individual contributors want to maintain a record of what
changes/contributions they have specific copyright on, they should indicate
their copyright in the commit message of the change, when they commit the
change to one of the Jupyter projects.

With this in mind, the following banner should be used in any source code file
to indicate the copyright and license terms:

    # Copyright (c) Jupyter Development Team.
    # Distributed under the terms of the Modified BSD License.

### About the Jupyter Development Team

The Jupyter Development Team is the set of all contributors to the Jupyter project.
This includes all of the Jupyter subprojects.

The team that coordinates JupyterHub subproject can be found here:
https://compass.hub.jupyter.org/page/governance.html

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: No license file present in the upstream snapshot** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
Copyright 2014-, Jupyter Development Team

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS “AS IS” AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original No license file present in the upstream snapshot terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `No license file present in the upstream snapshot` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `JUPYTERHUB` (category: ACADEMIA RD)
- **Upstream URL:** https://github.com/jupyterhub/jupyterhub
- **Pinned commit (SHA):** `1dd5f4c3c0d928bdf8363bcee2456de6f2499134`
- **Branch:** main
- **Pin provenance:** GitHub API commits/<branch> (response quoted in report). The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`30d19c1d1acfb1bbabede5b2319642076c98873d4edeeab5a70dcf7d47893446`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| DANS (KNAW/NWO, Netherlands) | 10.17026/PT | EU-recognised archive |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe
and Mail, Business Insider, National Post, Financial Post, StreetInsider,
Digital Journal, Barchart, International Business Times, and Fox News.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

