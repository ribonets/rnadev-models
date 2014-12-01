# Transcriptional Switches

To construct transcriptionally controlled systems, again the formation of long and short sRNA/mRNA
complexes is the key mechanism. A transcriptional OFF switch is turned
on without sRNA. Essentially, the induction of sRNA results in the
formation of the short complex. This binding triggers the formation of a rho-independent
terminator within the mRNA’s 5’UTR. RNAP is released and thereby
transcription stopped. The short complex is not only degraded but also dissociates 
into sRNA and a the short mRNA piece, but without a associated polymerase. The latter
cannot be elongated any more and therefore a new species was introduced for this purpose.

![Graph representation of the transcriptional-off riboswitch](http://ribonets.github.io/rnadev-models/transcriptional-off/graph-transcriptional-off.svg)

Graph representation of the transcriptional OFF system. To construct
an transcriptional OFF switch sRNA (green) and mRNA (blue) species
interact and form complexes (cyan). The complex formation and dissociation 
is indicated by double-headed arrows. The formation of a short sRNA/mRNA complex
has an irreversible effect as terminator folding is
triggered and thereby mRNA transcription is terminated. Therefore, the
short complex dissociates into sRNA and a short mRNA fragment without polymerase
which is degraded.

![Table of literals](http://ribonets.github.io/rnadev-models/transcriptional-off/lit-transcriptional-off.svg)

Using this literals we can describe the ODE system of this model as

![ODEs](http://ribonets.github.io/rnadev-models/transcriptional-off/ode-transcriptional-off.svg)

## Downloads

* [CellDesigner XML](minimalsystemTranscriptionalOFF_CellDesigner.xml)
* [SBML l2v4](minimalsystemTranscriptionalOFF_SBMLExport_l2v4.xml)

