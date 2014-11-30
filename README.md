SBML Models {#sbml-models .unnumbered}
===========

In this git repository we set up a system to model RNA
designs over time. Therefore we built a network context, which models
important cellular processes such as transcription, translation and
degradation as system of ordinary differential equations (ODEs) with a
more or less “realistic” parameter set.

We investigated a system published in 2011 by the Keasling lab
[@carothers:2011], which has been used to evaluate self-cleaving
ribozymes and ligand triggered aptazymes (Figure [fig:carothers]). This
implementation provides exactly the network context model we were
looking for, including parameters for the various cellular processes. We
re-implemented the published ODE system and integrated it using the
XPPaut software [@Ermentrout:2002].

We modularized the ODE system
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



Parameters {#parameters .unnumbered}
----------

Most parameter values for the individual rates can be inferred from
literature. Here, we refer to parameters describing transcription and
translation of the *lacZ* gene in *E.coli* [@Kierzek16032001]. All rate
constants are determined using the relationship described in Table S1 of
@carothers:2011. However, some rates are sequence dependent and
therefore need to be adapted for every specific system. Below we
describe how these rates are estimated.

### Rates inferred from the literature {#lit_rates .unnumbered}

During initiation of transcription, the RNAP binds to the promoter
sequence in a duplex DNA (“closed complex”). The polymerase melts the
duplex DNA near the transcription start site, forming a transcription
bubble (“open complex”). The RNAP then catalyzes a phosphodiester
linkage of two initial rNTPS. Promoter complex formation and the
synthesis of the two rNTPs occur at the approximate rate of
$0.018\ s^{-1}$, i.e. $k1=0.018\ s^{-1}$ [@makela2011stochastic]. During
the elongation process, RNAP moves along the template strand in
$3'\rightarrow 5'$ direction, melting duplex DNA and adding rNTPs to the
nascent RNA sequence. The length of the mRNA chain that is synthesized
during RNAP clearance of the promoter region corresponds roughly to the
length of the mRNA’s 5’-UTR containing the RBS. This happens
approximately with a rate of $1\ s^{-1}$ [@Kierzek16032001], i.e.
$k_2=1\ s^{-1}$. The commonly accepted rate of RNAP movement is
$40\ nt\ s^{-1}$. For the 3072-nt-long gene transcript, the value of
this parameter is $k_3=0.018\ s^{-1}$. @yarchuk1992interdependence
observed that a decrease in the protein synthesis follows by a nearly
equivalent change in the steady-state mRNA level. This means that for
the less effective ribosome binding sites, the rate of mRNA degradation
exceeds or at least is not lower than the transcription initiation rate.
Otherwise, a significant mRNA level would be observed even in the case
of RBS practically unprotected by ribosomes [@Kierzek16032001]. Here,
the rate of mRNA decay is $k_9=0.011\ s^{-1}$ (half-life of $lacZ$ mRNA
is $63\ s$). Transcription and translation are coupled in prokaryotes,
in that translation can initiate after the RBS region is transcribed.
For *lacZ*, ribosome binding and thereby translation initiation has been
estimated to occur once per $3\ s$
[@sorensen1991absolute; @kennell1977transcription], i.e.
$k_4=0.33\ s^{-1}$. The elongation rate of the protein chain is
$k_{5}=0.015\ s^{-1}$, according to the commonly accepted ribosome
movement rate $(15\ aa\ s^{-1})$ and the length of *beta-galactosidase*
protein. The degradation rate is $k_{11}=0.002\ s^{-1}$, according to
the *beta-galactosidase* half-life of about $6\ min$
@makela2011stochastic.

Different rates for transcription and degradation of sRNAs exist in
literature and are often estimated fitting quantitative data
[@levine2007quantitative; @legewie2008small; @schmiedel2012multi; @guantes2012positive].
Here, we choose $k_{12}=0.072\ s^{-1}$ for the transcription initiation
rate, $k_{22}=0.74\ s^{-1}$ as elongation rate, given a 75-nt-long sRNA,
and the decay rate of free sRNA as $k_{92}=0.04\ s^{-1}$.

By base-pairing with the target mRNA, the sRNA molecules interfere with
the RBS or other sequence stretches, and consequently alter mRNA
translation and stability, but can also bind to proteins and thereby
modify protein activity [@wassarman20006s; @storz2011regulation]. Upon
binding, either both the mRNA and the sRNA are degraded (negative
regulation) or the sRNA positively affects protein expression, e.g by
promoting ribosome binding to target mRNAs. We make use of the knowledge
that sRNA can quickly turn off negatively regulated and quickly turn on
positively regulated genes. An idealized scenario is expected where
binding between sRNA and mRNA occurs extremely fast
$(k_{30}=3\ nM^{-1}\ s^{-1})$ and dissociation of the complex occurs at
the comparably low rate of $k_{40}=0.02\ s^{-1}$. The mRNA-sRNA complex
is degraded with the rate $k_{50}=0.05\ s^{-1}$.

### Calculation of sequence dependent rates {#seq_dep_rates .unnumbered}

To be able to describe an RNA based regulation system it is inevitable
to take the individual sequences and structures of the involved RNA
molecules into account. We introduced several rates which heavily depend
on the physiology of the implemented switch, including $k_{30}$,
$k_{40}$, $k_{73}$, $k_{4}$ and $k'_{4}$. These rates can be either
measured for each individual RNA device or, in case of an RNA design
approach, be predicted using thermodynamic calculations based on an
energy model. We use the ViennaRNA package implementing all for this
purpose necessary algorithms [@lorenz_viennarna_2011].

The formation of a heterodimeric RNA complex such as the formation of
the 5’UTR $U$ and the sRNA $F$ to the short complex $C_{short}$ with the
two rates $k_{30}$ and $k_{40}$ for the forward and reverse reaction,
respectively, can be modeled as suggested in
equation ([complex~r~ates]).

$$\label{complex_rates}
    \begin{split}
        R+F &\rightleftharpoons C_{long} : k_{30}/k_{40} \\
        \Delta G_{System} &= -RT \ln K \\
        K &= e^{- \frac{\Delta G_{System}}{RT} } \\
        K &= \frac{k_{30}}{k_{40}} \\
        k_{40} &=  e^{- \frac{\Delta G_{Binding}}{RT} } \\
        k_{30} &= K \cdot k_{40}
    \end{split}$$

$\Delta G_{System}$ resembles the free energy of the whole complex
calculated from the partition function by RNAcofold whereas $\Delta
G_{Binding}$ corresponds to the free energy of the binding sites only.
The latter is approximately equal to the energy necessary to dissociate
the two molecules. As we assume that this process is the rate limiting
step, it is possible to infer the dissociation rate $k_{40}$ from this
context. The formation rate $k_{30}$ is then calculated using the
dependency of those rates to $K$ in the thermodynamic equilibrium.

Another rate that can be directly predicted from the properties of the
implemented switch is the terminator hairpin formation rate $k_{73}$
used in the transcriptional systems. This rate is used to describe the
process of forming a terminator hairpin within the 5’UTR and therefore
release of the RNAP from the DNA template. The resulting terminated
transcript corresponds in our model to species $Q$. To predict the rate
of this process we need information about the folding path on the energy
landscape from the initial structure to the terminator hairpin
structure. A sufficient approximation is to only predict the saddle
point structure between those two states, as the time required to reach
this structure is rate limiting. We therefore describe this system as

$$\label{eq:folding_rate}
    \begin{split}
        U &\rightharpoonup Q : k_{73} \\
        \Delta G &= -RT \ln K \\
        K &= e^{- \frac{\Delta G}{RT} } \\
        k_{73} &= e^{- \frac{\Delta G_{Saddle}-\Delta G_{U}}{RT} }
    \end{split}$$

where $\Delta G_{Saddle}$ is the free energy of the saddle point
structure between $U$ and $Q$, and $\Delta G_U$ reflects the free energy
of species $U$. The saddle point structure can be found by using the
*RNA::find\_saddle(seq, struct1, struct2, width)* function implemented
in the Vienna RNA package. $k_{73}$ is then derived from the energy
difference between the original state and the saddle state. It is worth
noting, that a co-transcriptional folding simulation using e.g.
*Kinwalker* [@geis_folding_2008] will lead to even better approximations
than this thermodynamic model but is also more demanding.

For the translational systems it is crucial to model the process of the
ribosome binding to the RBS of the different mRNA species, such as $U$,
$R$, $C_{short}$ and $C_{long}$. The amount of translation initiation
complexes $X$ depends on the accessibility of the binding site of each
aforementioned species and therefore on the ensemble of secondary
structures of the RNA molecules. The accessibility can be easily
calculated from the partition function as the probability of the RBS
site not forming any secondary structure is equal to

$$\label{eq:initiation_rate}
    \begin{split}
        P(\text{RBS unbound}) &= 1 - \frac{ \sum_{\forall i \in \text{RBS}} \sum_{0 \leq j \leq n}^{j \neq i} P_{ij} }{|RBS|} \\
    \end{split}$$

where $n$ is the length of the RNA sequence and $P_ij$ is equal to the
probability that position $i$ and $j$ form a base-pair. The original
translation initiation rate $k_{4}$ from the literature multiplied with
the derived probability results in a model of a sequence dependent
initiation process. Using this approach we are able to describe
translational systems, including direct OFF and indirect ON or OFF
switches.

