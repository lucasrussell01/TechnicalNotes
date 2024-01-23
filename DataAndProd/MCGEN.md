# Monte Carlo Contact Information

## McM Request

Twiki: `https://cms-pdmv.gitbook.io/project/`

McM Website: `https://cms-pdmv-prod.web.cern.ch/mcm/`

Usually easiest to clone an existing request.

Chosen `Campaign` and `Dataset` will fix various characteristics. 

Make sure to set generator parameters:
- `cross section` (e.g 0.01 pb)
- `filter efficiency` : 1
- `filter efficiency error` : 0
- `match efficiency` : 1
- `match efficiency error` : 0

and finally:
- `Total Events` 
- `size event`
- `time event`

Once request created put small (dummy) event `size` and `time` values, then return to menu and press `get test`.

Run this on `afs`, it will output the `time` and `size` per events -> Replace the dummy values on McM

-> Take note of the `PrepId` for the request.


-> Once everything is checked move to next step (validation)


## Creating Tickets

Go to `McM` page: `https://cms-pdmv-prod.web.cern.ch/mcm/` and click `Mccm` tab.


Click the `Create new MccM ticket` button, choose PWG.

Set prioritisation (2 for POG samples).

Add `Requests` and `Chains` (campaign dependant).

Commit the ticket.


## Fragments

Typically available here: `https://github.com/cms-sw/genproductions/tree/master/genfragments`

In here you need to specify/make changes if e.g. you want a different tune (CP5 or CUETP8M1), PSWeights etc...

Make sure the gridpack is on `/cvmfs` and specify the path in the fragment.

Example of a fragment: `https://cms-pdmv-dev.cern.ch/mcm/public/restapi/requests/get_fragment/B2G-RunIISummer17wmLHEGS-00001/0`
## Gridpacks

### Making gridpacks: 

Find the `proc` and `run` cards in `https://github.com/cms-sw/genproductions`.

Guides for the two main generators:

- MadGraph5aMCatNLO: 
```https://twiki.cern.ch/twiki/bin/viewauth/CMS/QuickGuideMadGraph5aMCatNLO ```

- Powheg:
```https://twiki.cern.ch/twiki/bin/viewauth/CMS/PowhegBOXPrecompiled```

Run: 

```
./gridpack_generation.sh <name of process card without _proc_card.dat> <folder containing cards relative to current location>
```
(Creates a `.tar` file)

### LHE Files

Unpack the `.tar` file:
```
tar -xf <filename>
```

Run CMS script:
```
./runcmsgrid.sh <nEvents> <randomSeed> <cpu>
```

and check `cmsgrid_final.lhe`

LHE file codes:
- -1: initial state
- 2: Intermediate state
- 1: Final State


