# SBML Models

In this git repository we set up a system to model RNA
designs over time. Therefore we built a network context, which models
important cellular processes such as transcription, translation and
degradation as system of ordinary differential equations (ODEs) with a
more or less “realistic” parameter set.

We investigated a system published in 2011 by the Keasling lab
[carothers et. al 2011], which has been used to evaluate self-cleaving
ribozymes and ligand triggered aptazymes. We modularized the ODE system
such that different regulatory mechanisms, e.g. translational ON
switches based on sRNA-mRNA interaction or a riboswitch sensor, can be
encoded into the framework.

First, the original ODE system was reduced to model transcription,
translation and degradation of an mRNA and the produced protein. 
Subsequently this system was extended to
describe translational ON/OFF and transcriptional ON/OFF switches. 

The developed models are available in the according sub-directory:
* [minimal](https://github.com/ribonets/rnadev-models/tree/master/minimal)
* [translational](https://github.com/ribonets/rnadev-models/tree/master/translational)
* [transcriptional-off](https://github.com/ribonets/rnadev-models/tree/master/transcriptional-off)
* [transcriptional-on](https://github.com/ribonets/rnadev-models/tree/master/transcriptional-on)

There we provide a short summary of each model and their implementation in ODE and SBML format. We are happy to provie further details about the system setups, e.g. used parameters, upon request.




