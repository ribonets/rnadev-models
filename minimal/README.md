# Minimal System

A graph representation of the minimal system describing only the
transcription, translation and degradation processes is shown in
the figure below and the meaning of the individual literals is given in the 
subsequent table.

![Graph representation of the minimal system](http://ribonets.github.io/rnadev-models/minimal/graph-minimal-srna.svg)

Graph representation of the minimal system. Edges that correspond to
an inflow or outflow of the system are indicated by dashed lines. An
outflow means always degradation of a certain species.
Dotted lines indicate the influence of a modulator or catalyst on the
target species. Here they are used to model translation, the step where
the transition from the mRNA level (light blue vertices), which is
purely nucleotide based, to amino acids and thereby to the protein
expression level (dark blue vertices) takes place. All other (solid)
edges connect two vertices where, with a certain rate constant, one
species is consumed and the other is produced.

The ODE system of the model is

![ODEs](http://ribonets.github.io/rnadev-models/minimal/ode-minimal-srna.svg)

with a detailed description of the literals and rates in

![Table of literals](http://ribonets.github.io/rnadev-models/minimal/lit-minimal-srna.svg)

## Downloads

* [CellDesigner XML](minimalsystemsrna_CellDesigner.xml)
* [SBML l2v4](minimalsystemsrna_SBMLExport_l2v4.xml)


