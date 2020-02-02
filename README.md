# kinfit-testbench

CMSSW_10_2_18

* https://github.com/tpmccauley/HeavyFlavorAnalysis/tree/kinfit
* https://github.com/drkovalskyi/Bmm5

`/store/data/Run2018A/Charmonium/MINIAOD/PromptReco-v2/000/316/239/00000/08BFAB4F-1359-E811-B01F-FA163E5285EC.root`

`voms-proxy-init --rfc --voms cms`

## HeavyFlavorAnalysis

`/SpecificDecay/test/cfg_recoWmhis.py`
*  Input: `/store/data/Run2018A/Charmonium/MINIAOD/PromptReco-v2/000/316/239/00000/08BFAB4F-1359-E811-B01F-FA163E5285EC.root`
*  Output: `reco.root`

`/SpecificDecay/test/cfg_recoCheck.py`
* Input: `reco.root`
* Output:
Kinematic fit code in `HeavyFlavorAnalysis/RecoDecay/*/BPHKinematicFit.*`: `KinematicParticleVertexFitter` and `KinematicConstrainedVertexFitter`

KPVF [src](https://github.com/cms-sw/cmssw/blob/CMSSW_10_2_X/RecoVertex/KinematicFit/src/KinematicParticleVertexFitter.cc)
[interface](https://github.com/cms-sw/cmssw/blob/CMSSW_10_2_X/RecoVertex/KinematicFit/interface/KinematicParticleVertexFitter.h)

`RefCountedKinematicTree KinematicParticleVertexFitter::fit(const std::vector<RefCountedKinematicParticle> &particles) const`

KCVF [src](https://github.com/cms-sw/cmssw/blob/CMSSW_10_2_X/RecoVertex/KinematicFit/src/KinematicConstrainedVertexFitter.cc)
[interface](https://github.com/cms-sw/cmssw/blob/CMSSW_10_2_X/RecoVertex/KinematicFit/interface/KinematicConstrainedVertexFitter.h)

```
RefCountedKinematicTree KinematicConstrainedVertexFitter::fit(const std::vector<RefCountedKinematicParticle> &part,
                                                             MultiTrackKinematicConstraint * cs,
                                                             GlobalPoint * pt)
```

Implementation in `HeavyFlavorAnalysis/SpecificDecay/src/BPHBuToJPsiKBuilder.cc`

cfg_recoWmhis.py:
bphWriteSpecificDecay -> bphHistoSpecificDecay

cfg_recoCheck.py:
checkBPHWriteDecay

```
[HeavyFlavorAnalysis/SpecificDecay/plugins]: ls
BPHHistoSpecificDecay.cc  BPHHistoSpecificDecay.h  BPHWriteSpecificDecay.cc  BPHWriteSpecificDecay.h
```

## Bmm

`Bmm5/NanoAOD/plugins/BxToMuMuProducer`

`fitBtoKJPsiMuMu`
`fitBtoKJPsiMuMuNew`

`Bmm5/Run2018ABC_NanoAOD.py`

nanoSequence + BxToMuMuSequence + BxToMuMuTables
