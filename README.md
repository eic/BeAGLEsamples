# BeAGLEsamples

All samples are produced with BeAGLE Version 1.03.02
Metadata has all the log files, with all information needed for the simulations.
Runcards has all the inputfiles, one associates with each simulation sample. 

Recent updates:
Convert output root file to HEPMC format using [eic-smear v1.1.17](https://github.com/eic/eic-smear/releases/tag/1.1.17) and [afterburner v0.2.1](https://github.com/eic/afterburner/releases/tag/v0.2.1)

Notes:
- eAg 9x115 (`runcards/eAg_9x115_*_DIS.inp`): afterburner has no eAg preset, so these samples used `abconv -p ip6_eAu_100x9`. In v0.2.1 that preset has the same beam settings as `ip6_eRu_115x9` and `ip6_eCu_115x9`.
- eAg 9x115 Q2set (`runcards/eAg_9x115_Q2set{1,2,3}.inp`): a separate sample from `eAg_9x115_*_DIS.inp`, produced in November 2026. It uses the eAu 9x100 cards with A/Z 107/47 and ion momentum 115, and the pythia card `pythiacards/eAg_9x115_Q2set_S3ALL003`. Q2 1–10, 10–100 and 100–10000, each 10 jobs × 5E5 events. Source: [eic/BeAGLE-DIS](https://github.com/eic/BeAGLE-DIS) tag `eAg_DIS_9x115_v1.0`. Converted with eic-smear 1.2.3 and afterburned with afterburner v0.2.1 using `ip6_eCu_115x9`, the closest preset (it has the same beam settings as `ip6_eAu_100x9` and `ip6_eRu_115x9`). The per-event `MRMN, ESTI+AMRCL0(2)` debug lines are removed from the logs `metadata/eAg_9x115_Q2setN.J.out` (J = job 0–9).
- eD 9x130 (`runcards/eD_9x130_DIS_*.inp`): BeAGLE generation is from May 2026. Its logs record the original May post-processing. The June 2026 reprocessing (eic-smear 1.1.17, afterburner v0.2.1, `ip6_eD_130x9`) is recorded separately in `metadata/reprocessing.jun.2026.dis.eD.9.130`.
- afterburner v0.2.1 `abconv --version` reports 0.1.3 ([eic/afterburner#43](https://github.com/eic/afterburner/issues/43)).
- With any named preset, v0.2.1 writes `afterburner_config_name auto` and beam energy/PDG 18/18/11 into the HepMC run info. These are unset defaults ([eic/afterburner#45](https://github.com/eic/afterburner/issues/45)); the `ab_*` attributes hold the applied settings.
