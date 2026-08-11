# Third-Party Software Notices

GearTrack depends on third-party open-source software. GearTrack's proprietary
license applies only to GearTrack itself and does not replace or restrict the
licenses of these third-party components.

The versions below correspond to GearTrack 0.1.0 and its `uv.lock` file. The
source ZIP contains GearTrack source code and build configuration; Docker and
`uv` retrieve the referenced runtime components when the user builds and starts
the application.

## Production Python dependencies

| Component | Version | License | Project / license information |
| --- | ---: | --- | --- |
| argon2-cffi | 25.1.0 | MIT | <https://github.com/hynek/argon2-cffi> |
| argon2-cffi-bindings | 25.1.0 | MIT | <https://github.com/hynek/argon2-cffi-bindings/blob/main/LICENSE> |
| asgiref | 3.12.1 | BSD-3-Clause | <https://github.com/django/asgiref> |
| cffi | 2.1.0 | MIT-0 | <https://github.com/python-cffi/cffi> |
| dj-database-url | 3.1.2 | BSD-3-Clause | <https://github.com/jazzband/dj-database-url> |
| Django | 5.2.16 | BSD-3-Clause | <https://github.com/django/django/blob/main/LICENSE> |
| Gunicorn | 26.0.0 | MIT | <https://github.com/benoitc/gunicorn/blob/master/LICENSE> |
| packaging | 26.2 | Apache-2.0 OR BSD-2-Clause | <https://github.com/pypa/packaging/blob/main/LICENSE> |
| psycopg2-binary | 2.9.12 | LGPL-3.0-or-later with OpenSSL exception | <https://github.com/psycopg/psycopg2/blob/master/LICENSE> |
| pycparser | 3.0 | BSD-3-Clause | <https://github.com/eliben/pycparser/blob/main/LICENSE> |
| Segno | 1.6.6 | BSD-3-Clause | <https://github.com/heuer/segno/blob/master/LICENSE> |
| sqlparse | 0.5.5 | BSD-3-Clause | <https://github.com/andialbrecht/sqlparse/blob/master/LICENSE> |
| WhiteNoise | 6.12.0 | MIT | <https://github.com/evansd/whitenoise/blob/main/LICENSE> |

Platform-specific dependencies listed in `uv.lock` are installed only when
their environment markers match. For example, the `tzdata` Python package is a
Windows-specific Django dependency and is not installed in GearTrack's Linux
production image.

Development-only dependencies such as pytest and pytest-django are excluded
from the production image by `uv sync --frozen --no-dev` and are therefore not
listed as production components above.

## Build and runtime platform components

GearTrack's Docker configuration also references the following projects. These
components are obtained from their upstream images or repositories during the
customer's local Docker build and startup.

| Component | Reference | License information |
| --- | --- | --- |
| CPython | `python:3.13-slim` base image | <https://docs.python.org/3/license.html> |
| Debian | Base operating-system userspace in `python:3.13-slim` | <https://www.debian.org/legal/licenses/> |
| uv | Copied from `ghcr.io/astral-sh/uv` | <https://github.com/astral-sh/uv/blob/main/LICENSE-MIT> and <https://github.com/astral-sh/uv/blob/main/LICENSE-APACHE> |
| PostgreSQL | `postgres:16` container image | <https://www.postgresql.org/about/licence/> |

## No endorsement

The names of third-party projects and contributors are used only for
attribution. Their inclusion does not imply endorsement of GearTrack by those
projects or contributors.

## Obtaining license texts and source

The links above identify the upstream projects and their license texts. Exact
resolved package versions and integrity hashes are recorded in `uv.lock`.
Corresponding source distributions can be obtained from the upstream project
repositories and the Python Package Index.

If GearTrack is distributed in the future as a prebuilt Docker image rather
than as a source ZIP, the image distribution should additionally retain all
license and notice files shipped in its Python packages, base image, and
operating-system packages.
