# Polygon Dynamics

**Follow rational trajectories across connected square-tiled surfaces, retaining crossings, topology and stopping conditions.**

[Run](#run-an-experiment) · [Contract](docs/CONTRACT.md) · [Research profile](#research-profile) · [Scope](docs/SCOPE.md)

## Notation Systems

**Frontier Tooling and Instrumentation for Digital Futures.** We develop computational instruments and operational tooling connecting scientific methods, specialist computation and human expertise.

[Notations Systems Terminal](https://github.com/giasonpooni/Notations-Systems-Terminal) coordinates supported investigations; this provider owns topology validation and trajectory computation. Cartesian Graphics develops interactive worlds, simulation technology and digital IP, without turning this mathematical reference into a general game-navigation solver. [Organization profile](https://github.com/giasonpooni/Notations-Systems-Terminal/blob/b41b84922d4963a9206202029afd1e78b9451f9c/PUBLIC_POSITIONING.md).

| Identity | Scope |
| --- | --- |
| Current repository | `Polygon-Trajectory-Experiments` |
| Import / CLI module | `translation_surface_dynamics` |
| Proposed NET target | `geometry.polygon_dynamics` |
| Implemented profile | Bounded rational straight-line flow on connected square-tiled translation surfaces |

The friendly operation is not a newly registered command. Right/up tile permutations define gluings; left/down use inverses. Arbitrary polygon gluings and vertex continuation are unsupported. The included three-square L-shaped surface has genus two, so the reference is not limited to the flat torus.

Segments and boundary times use rational arithmetic. Results retain request, gluing validation, genus/vertex classes, directed crossings, segments, invariants, stop policy and SHA-256 digests. This does not establish ergodicity, physical accuracy or cryptographic proof of execution.

## Run an experiment

Python 3.11+; no runtime dependencies:

```sh
python -m pip install .
python -m translation_surface_dynamics < examples/request.json
```

PowerShell:

```powershell
Get-Content -Raw examples/request.json | python -m translation_surface_dynamics
```

Installed API:

```python
import json
from translation_surface_dynamics import run, validate_request

with open("examples/request.json", encoding="utf-8") as source:
    request = validate_request(json.load(source))
result = run(request)
print(result["status"], result["gluing_validation"]["genus"])
print(result["final_state"], result["artifact_digest"])
```

The example completes at time `3`, tile `1`, position `["1/4", "5/6"]`, after four gluing events. [Torus-cover fixture](examples/torus-cover.json) provides a genus-one analytical comparison with different tile transitions.

## Completion and bounds

| Status | Meaning |
| --- | --- |
| `completed` | Requested duration covered, including a single endpoint edge gluing |
| `stopped_at_vertex` | Two edges reached together; no continuation chosen |
| `event_budget_exhausted` | Next boundary reached but gluing not applied |

Partial results retain a valid prefix and pending edges. Vertex/budget stops remain partial even with `remaining = "0"`. Regular and singular vertices both stop; starts must be strictly interior.

Limits: 1–32 tiles; 0–1,024 edge events; reduced rational strings with 64-bit numerators/denominators; duration and direction magnitudes at most 1,024. Arithmetic beyond 256 bits fails without an artifact. The CLI accepts at most 32 KiB and rejects duplicate keys, nonfinite values and unsupported fields. [Full contract](docs/CONTRACT.md).

## Verify the implementation

```sh
python -m unittest discover -s tests -v
python -m pip install "setuptools>=77" wheel
python scripts/check_installed.py
```

Tests cover torus unfolding, genus two, inverse flow, noninvolutive gluings, near-corner ordering, stops, malformed input and digest recomputation. The installed-wheel check uses a separate environment outside the checkout. Existing CI targets Windows/Linux; this documentation does not rerun or newly qualify it.

## Component boundary

Declared gluing and motion pass through input/topology validation, bounded affine flow and retained artifacts. NET owns revision binding, investigation retention and presentation through its separately versioned adapter. Provider availability does not establish installation in a deployed workbench.

General polygon gluings, arbitrary real directions, vertex continuation, Jacobi fields and moduli-space exploration remain outside the profile. [Contributor invariants](CONTRIBUTING.md) · [Stack role](docs/STACK_ROLE.md).

## Research profile

**Question:** which trajectory and topological distinctions survive changes of representation, and when must an operation stop rather than invent continuation?

Use analytical unfolding, inverse flow, near-corner cases and bounded prefixes as specimens. Separate exact rational statements from floating-point displays and partial results from completed trajectories. Shared graphical vocabulary with games or GIS is not evidence of shared physical semantics.

[Research protocol](https://github.com/giasonpooni/Notations-Systems-Terminal/blob/b41b84922d4963a9206202029afd1e78b9451f9c/RESEARCH_PROGRAMME.md). New language/CUDA providers, representation-minimality claims and performance improvements require explicit implementation and tests. This documentation adds no runtime, telemetry or authority.

## License and compatibility

[MIT](LICENSE). Existing imports, operation/schema IDs, digests, source pins and notices remain unchanged. No source, tests, dependency, licence, permissions or release state changes. Public-interest/private-IP positioning does not transfer rights or establish nonprofit status.
