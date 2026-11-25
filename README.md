# BeAGLEsamples

All samples are produced with BeAGLE Version 1.03.02
Metadata has all the log files, with all information needed for the simulations.
Runcards has all the inputfiles, one associates with each simulation sample. 

Recent updates:
Convert output root file to HEPMC format using [eic-smear v1.1.17](https://github.com/eic/eic-smear/releases/tag/1.1.17) and [afterburner v0.2.1](https://github.com/eic/afterburner/releases/tag/v0.2.1)

Notes:
- eAg 9x115 (`runcards/eAg_9x115_*_DIS.inp`): afterburner has no eAg preset, so these samples used `abconv -p ip6_eAu_100x9`. In v0.2.1 that preset has the same beam settings as `ip6_eRu_115x9` and `ip6_eCu_115x9`.
- afterburner v0.2.1 `abconv --version` reports 0.1.3 ([eic/afterburner#43](https://github.com/eic/afterburner/issues/43)).
- With any named preset, v0.2.1 writes `afterburner_config_name auto` and beam energy/PDG 18/18/11 into the HepMC run info. These are unset defaults; the `ab_*` attributes hold the applied settings.
