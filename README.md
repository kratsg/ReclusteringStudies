# ReclusteringStudies - A RootCore Package

This is a package for studying the xAOD reclustering code being developed by Giordon.

## Installing
The last stable analysis base used is **2.3.12**. To install,
```bash
rcSetup Base,2.3.12
git clone https://github.com/kratsg/ReclusteringStudies.git
git clone https://github.com/kratsg/xAODJetReclustering.git
rc checkout_pkg atlasinst/Institutes/UChicago/xAODAnaHelpers/tags/xAODAnaHelpers-00-00-04
source xAODAnaHelpers/scripts/ElectronEfficiencyCorrectionPatch_Base.2.1.29.sh
rc checkout_pkg atlasoff/Reconstruction/Jet/JetSubStructureUtils/tags/JetSubStructureUtils-00-02-08
rc checkout_pkg atlasoff/Reconstruction/Jet/JetSubStructureMomentTools/tags/JetSubStructureMomentTools-00-01-14
rc find_packages
rc compile
```

### Jet Reclustering

Using `xAODAnaHelpers`, we provide an easy way for you to enable jet reclustering in a job. In particular, given a `json` file

```json
[
  {
    "class": "JetReclustering",
    "configs": {
      "m_inputJetName": "AntiKt4LCTopoJets",
      "m_outputJetName": "AntiKt10LCTopoJetsRCAntiKt4LCTopoJets",
      "m_radius": 1.0,
      "m_debug": false,
      "m_outputXAODName": "output"
    }
  }
]
```

and running `xAH_run.py input.root  --config config.json` is a minimal working example. You can include this in an algorithm chain. If you are on UCTier3, you can run the following example code

```
xAH_run.py "/share/t3data3/kratsg/xAODs/mc14_13TeV.1103*/*.root*" --config=ReclusteringStudies/data/recluster.json -f -v
```

with a json configuration file (an example one is found in [data/recluster.json](data/recluster.json)).

#### Authors
- [Giordon Stark](https://github.com/kratsg)
