---
layout: post
title: Using git for model configurations
---

## Setup

I use the MITgcm for modelling, and like most numerical models there are a number of configuration files.  When I create each model run I edit a file `input/gendata.py` and run this.  Typically at the top of this generation file, there is a `runname='Boo23'` variable set, and also a

```python
comments="""
Long multiline comment about the run.
"""
```

Sometimes `data` configuration files are edited by hand, sometimes inside the `gendata.py` script.  Sometimes data in `code/*` needs to be edited and the mitgcm executable recompiled.

The `gendata.py` script copies everything to `f'results/{runname}'` directory, usually softlinked to the scratch space on my disk.

## git and github integration

_Before_ all the above, I create a new project on github and clone it on the machine I'm interested in.  Usually this new repo is a copy of an old one with all the MITgcm configuration files in it.  To clone, do something like `git clone https://github.com/jklymak/MyModelSetup.git`

Edit the files, usually in `code` and `input` and then run `gendata.py`.  Inside `gendata.py` there is a block that looks like:

```python
runname='MyModelSetup27'
comments = f"""
Three-d version more dz, more dy, of Bute15 with long wind forcing,
No heat flux; no rbcs, actual bottom drag; turn off non hydrostatic
slope sides a bit.  Wavy...  Add Leith viscosity with default values.
Shorter 5d wind.  Even bigger receiving
basin with roughness in it.  Tau={wind**2*1e-3} N/m^2 ({wind} m/s) versus 0.225 N/m^2.
Lat = {lat}; f={f0}
Constant Nsq0={Nsq0}.
No wind startup = just turn it on.
Redo of Bute3d23, but with daily momentum diagnostics...
"""

outdir0=f'../results/{runname}/'

####################
# Lots of other stuff....
# ...
#

_log.info('doing this via git!!')

os.system(f'git commit -a -m "gendata for {runname}: {comments}"')
os.system('git push origin main')
os.system(f'git checkout -B {runname}')
os.system(f'git push origin {runname}')
os.system('git checkout main')
```

This works quite well and gives a list of branches, one for each model run, and you can easily get back to where you started.  See <https://github.com/jklymak/ButeWinds/> for an example.