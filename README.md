# BeAGLEsamples

Run cards, PYTHIA cards and logs for the BeAGLE 1.03.02 samples used in ePIC production.

| Directory | Contents |
|---|---|
| `runcards/` | BeAGLE input files, one per sample |
| `pythiacards/` | PYTHIA cards that the run cards read |
| `metadata/` | Log files, with the settings each simulation ran with |

## Post-processing versions

BeAGLE output is converted to HepMC3 with [eic-smear](https://github.com/eic/eic-smear) and then passed through the [afterburner](https://github.com/eic/afterburner). The number after the dash in a dataset name, as in `BeAGLE1.03.02-4.0`, is the version of that post-processing.

| Dataset version | eic-smear | afterburner | What changed |
|---|---|---|---|
| **4.0** (current) | [1.2.3](https://github.com/eic/eic-smear/releases/tag/1.2.3) | [v0.2.1](https://github.com/eic/afterburner/releases/tag/v0.2.1) | eic-smear upgraded from 1.1.17 to 1.2.3 |
| 3.1 | [1.1.17](https://github.com/eic/eic-smear/releases/tag/1.1.17) | [v0.2.1](https://github.com/eic/afterburner/releases/tag/v0.2.1) | |

New samples use the 4.0 chain. eic-smear 1.1.17 applies only to the samples listed with it below.

## Samples with notes

| Sample | Run cards | Generated | eic-smear | Afterburner preset |
|---|---|---|---|---|
| eAg 9x115 Q2set (4.0) | `runcards/eAg_9x115_Q2set{1,2,3}.inp` | November 2026 | 1.2.3 | `ip6_eCu_115x9` |
| eAg 9x115 DIS | `runcards/eAg_9x115_*_DIS.inp` | June 2026 | 1.1.17 | `ip6_eAu_100x9` |
| eD 9x130 DIS | `runcards/eD_9x130_DIS_*.inp` | May 2026, reprocessed June 2026 | 1.1.17 | `ip6_eD_130x9` |

### eAg 9x115 Q2set

- **A separate sample** from `eAg_9x115_*_DIS.inp`.
- **Cards:** the eAu 9x100 cards with A/Z 107/47 and ion momentum 115, and the PYTHIA card `pythiacards/eAg_9x115_Q2set_S3ALL003`.
- **Size:** Q2 1–10, 10–100 and 100–10000, each 10 jobs × 5E5 events.
- **Source:** [eic/BeAGLE-DIS](https://github.com/eic/BeAGLE-DIS) tag `eAg_DIS_9x115_v1.0`.
- **Afterburner preset:** there is no eAg preset. `ip6_eCu_115x9` is the closest, and it has the same beam settings as `ip6_eAu_100x9` and `ip6_eRu_115x9`.
- **Logs:** `metadata/eAg_9x115_Q2setN.J.out` (J = job 0–9). The per-event `MRMN, ESTI+AMRCL0(2)` debug lines are removed.

### eAg 9x115 DIS

- **Afterburner preset:** there is no eAg preset, so these samples used `ip6_eAu_100x9`. In v0.2.1 that preset has the same beam settings as `ip6_eRu_115x9` and `ip6_eCu_115x9`.

### eD 9x130 DIS

- **Generation:** May 2026. The logs record the original May post-processing.
- **Reprocessing:** June 2026, with eic-smear 1.1.17 and afterburner v0.2.1. It is recorded separately in `metadata/reprocessing.jun.2026.dis.eD.9.130`.

## Afterburner v0.2.1 quirks

- **Version string:** `abconv --version` reports 0.1.3 ([eic/afterburner#43](https://github.com/eic/afterburner/issues/43)).
- **Run info:** with any named preset, v0.2.1 writes `afterburner_config_name auto` and beam energy/PDG 18/18/11 into the HepMC run info. These are unset defaults ([eic/afterburner#45](https://github.com/eic/afterburner/issues/45)). The `ab_*` attributes hold the applied settings.
