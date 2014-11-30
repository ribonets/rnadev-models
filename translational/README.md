# Translational Switch

To construct a translational ON or OFF switch the two independent reaction networks of sRNA and
mRNA expression need to interact in such a way that they implement the
desired logic. On the biological level this means the formation of
complexes by the sRNA and mRNA species. A complex is built from two RNA
species and can fall apart in its components again or can also be degraded. 
Complex formation makes the RBS
(in)accessible and thereby translation is (reduced) induced. Graph
representation of the implemented translational system is shown in the 
figure below and additional literals are explained in the subsequent table

![Graph representation of the translational riboswitch](http://ribonets.github.io/rnadev-models/translational/graph-translational.svg)

In case of a translational OFF switch the translation (re-)initiation
rate for the unbound mRNA species should be much
bigger than the initiation rate for the complexes.
To model a translational ON switch the opposite has to be
true. This is the only necessary change to switch form a translational
OFF switch to an ON switch.

![Table of literals](http://ribonets.github.io/rnadev-models/translational/lit-translational.svg)

Using this literals we can describe the ODE system of this model as

![ODEs](http://ribonets.github.io/rnadev-models/translational/ode-translational.svg)

## Downloads
### ON switch:
* [CellDesigner XML](minimalsystemTranslationalON_CellDesigner.xml)
* [SBML l2v4](minimalsystemTranslationalON_SBMLExport_l2v4.xml)

### OFF switch:
* [CellDesigner XML](minimalsystemTranslationalOFF_CellDesigner.xml)
* [SBML l2v4](minimalsystemTranslationalOFF_SBMLExport_l2v4.xml)
