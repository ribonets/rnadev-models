# Transcriptional ON Switch

In contrast to an off switch, a transcriptional ON switch is off per default and can be
switched on in presence of an sRNA. Here the short mRNA as well as the
short sRNA/mRNA complex can be further transcribed. However, in a sRNA free system huge amounts of will
form a terminator hairpin and therefore become the state without
polymerase, which will be degraded. The terminator hairpin formation happens with a newly
introduced rate, the hairpin formation rate. Expression of the sRNA and mRNA binding
disrupts terminator formation and increases protein expression.

![Graph representation of the transcriptional-on riboswitch](http://ribonets.github.io/rnadev-models/transcriptional-on/graph-transcriptional-on.svg)

Graph representation of the transcriptional ON system. The formation
of the short complex hinders terminator formation within the 5’UTR which in the switch’s default state triggers RNAP release.

![Table of literals](http://ribonets.github.io/rnadev-models/transcriptional-on/lit-transcriptional-on.svg)

Using this literals we can describe the ODE system of this model as

![ODEs](http://ribonets.github.io/rnadev-models/transcriptional-on/ode-transcriptional-on.svg)

## Downloads

* [CellDesigner XML](minimalsystemTranscriptionalON_CellDesigner.xml)
* [SBML l2v4](minimalsystemTranscriptionalON_SBMLExport_l2v4.xml)
* [SBML Mathematika](Mathematika_SBML_transcription-on_srna.xml)
* [ODE xppaut](transcriptional-on.ode)

