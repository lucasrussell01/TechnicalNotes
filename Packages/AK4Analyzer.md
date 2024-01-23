# Analyzer to skim through AK4 jets with CHS


Code will be stored in this repository: `lucasrussell01/AK4Analyzer.git`

## CMSSW Setup

CMS setup and grid certificate:
```
source /vols/grid/cms/setup.sh
voms-proxy-init -voms cms -valid 192:00 --out ~/cms.proxy
```

Use CMSSW_13_0_2:

```
scramv1 project CMSSW CMSSW_13_0_2
cd CMSSW_13_0_2/src
cmsenv
```

Clone the GitHub repo:
```
git clone git@github.com:lucasrussell01/MLAnalyzer.git
```
```
cd AK4Analyzer
```

To make a skeleton analyzer:

```
mkedanlzr AK4Analyzer
```
compile:

```
scramv1 b -j8
```











