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

![Graph representation of the translational riboswitch](http://ribonets.github.io/rnadev-models/minimal/graph-translational.svg)

The ODE system of the model is

![ODEs](http://ribonets.github.io/rnadev-models/minimal/ode-translational.svg)

with a detailed description of the literals and rates in

![Table of literals](http://ribonets.github.io/rnadev-models/minimal/lit-translational.svg)

In case of a translational OFF switch the translation (re-)initiation
rate for the unbound mRNA species should be much
bigger than the initiation rate for the complexes.
To model a translational ON switch the opposite has to be
true. This is the only necessary change to switch form a translational
OFF switch to an ON switch.

