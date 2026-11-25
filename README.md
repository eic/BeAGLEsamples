# BeAGLEsamples

All samples are produced with BeAGLE Version 1.03.02
Metadata has all the log files, with all information needed for the simulations.
Runcards has all the inputfiles, one associates with each simulation sample. 

Recent updates:
Convert output root file to HEPMC format using [eic-smear v1.1.17](https://github.com/eic/eic-smear/releases/tag/1.1.17) and [afterburner v0.2.1](https://github.com/eic/afterburner/releases/tag/v0.2.1)

Exceptions:
- eAg 9x115 (`runcards/eAg_9x115_*_DIS.inp`): the afterburner step used a private afterburner build (it reports version 0.1.3), not the afterburner v0.2.1 release, with `abconv -p ip6_eAu_100x9`. Afterburner has no eAg preset. In v0.2.1, `ip6_eAu_100x9` has the same beam settings as `ip6_eRu_115x9` and `ip6_eCu_115x9`. In these outputs the HepMC run info shows `afterburner_config_name auto` and beam energies/PDG `18/18/11`, but those labels are wrong: the settings applied were the `ip6_eAu_100x9` ones.
