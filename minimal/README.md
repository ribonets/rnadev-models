Minimal System {#minimal-system .unnumbered}
--------------

A graph representation of the minimal system describing only the
transcription, translation and degradation processes is shown in
Figure [fig:min] and the meaning of the individual literals is given in
Table [tab:min].


![Alt text](http://ribonets.github.io/rnadev-models/minimal/graph-minimal.svg)
<img src="http://ribonets.github.io/rnadev-models/minimal/graph-minimal.svg">
![Graph representation of the minimal system. Edges that correspond to
an inflow or outflow of the system are indicated by dashed lines. An
outflow means always degradation ($\emptyset$) of a certain species.
Dotted lines indicate the influence of a modulator or catalyst on the
target species. Here they are used to model translation, the step where
the transition from the mRNA level (light blue vertices), which is
purely nucleotide based, to amino acids and thereby to the protein
expression level (dark blue vertices) takes place. All other (solid)
edges connect two vertices where, with a certain rate constant, one
species is consumed and the other is produced. For instance $S$ is
consumed with rate $k_2$ and produces $U$ with the same rate. The
meaning of the individual literals is given in
Table [tab:min].](graph-minimal.svg)

[fig:min]

In this model the process of RNA polymerase (RNAP) binding to the DNA
template is simplified to a single step where transcription is initiated
with rate $k_1$. The RNAP-DNA complex is represented by species $S$.
Transcription is elongated with rate $k_2$ and the 5’UTR of the mRNA is
produced ($U$ in the model). With growing mRNA length the risk that RNAP
dissociates from the DNA template before the complete mRNA transcript is
produced increases. This fact is reflected by the usage of a length
dependent transcription elongation rate $k_3$ to produce the full length
mRNA ($R$ in the model). As soon as the ribosome binding site (RBS) of
the mRNA leaves the RNAP-complex ribosomes can bind and initiate
translation. In our model this is indicated by the transition from $U$
and $R$ with rate $k_4$ to $X$ which represents the translation
initiation complex. To produce $X$ neither $U$ nor $R$ are consumed,
although the amount of $X$ depends on the concentration of both species
which therefore act as modulator or catalyst for this reaction. This
makes sense as the mRNA template is not consumed during translation and
can host many ribosomes. As soon as the translation initiation complex
is generated, the ribosome moves on and the RBS is accessible to host a
new ribosome. Therefore one mRNA induces several initiation complexes
during transcription which resembles nature.

The ODE system of the model is

$$\label{eq:minimal}
    \begin{split}
      \frac{dS}{dt} &= k_1-k_2S \\
      \frac{dU}{dt} &= k_2S-(k_3+k_9)U \\
      \frac{dR}{dt} &= k_3U-k_9R \\
      \frac{dX}{dt} &= k_4(U+R)-k_5X \\
      \frac{dP}{dt} &= k_5X-k_{11}P \\
    \end{split}$$

with a detailed description of the literals and rates in
Table [tab:min].

. [tab:min]

<span>l X</span> $S$ &$\dotsc$ mRNA initiation complex (equal to $I$ in
@carothers:2011)\
$U$ &$\dotsc$ 5’UTR transcribed with polymerase associated (equal to
$U_{ppp}$)\
$R$ &$\dotsc$ mRNA fully transcribed (equal to $R_{ppp}$)\
$X$ &$\dotsc$ translation initiation complex (equal to $T$)\
$k_1$ &$\dotsc$ transcription initiation rate (dependent on used
promoter)\
$k_2$ &$\dotsc$ transcription elongation rate for 5’UTR (dependent on
polymerase)\
$k_3$ &$\dotsc$ transcription elongation rate for coding region\
$k_4$ &$\dotsc$ translation (re-)initiation rate (sequence dependent)\
$k_5$ &$\dotsc$ translation elongation rate\
$k_9$ &$\dotsc$ mRNA degradation rate\
$k_{11}$&$\dotsc$ protein degradation rate\

This minimal system does not produce sRNA yet. To achieve this we added
the transcription of an sRNA in the same manner as we did it for the
mRNA, just without the distinction between short and long RNA species.
sRNA production can be done by a different promoter or polymerase, so we
need to introduce new rates. Rates with a second index “$2$” are sRNA
specific rates and are explained in Table [tab:minsrna]. The ODE system
given in ([eq:minimal]) is extended by the following two equations.

$$\label{eq:sRNA}
    \begin{split}
      \frac{dW}{dt} &= k_{12}-k_{22}W \\
      \frac{dF}{dt} &= k_{22}W-k_{92}F \\
    \end{split}$$

[tab:minsrna]

<span>l X</span> $W$ &$\dotsc$ sRNA initiation complex (like $S$ for
mRNA)\
$F$ &$\dotsc$ fully transcribed sRNA\
$k_{12}$&$\dotsc$ transcription initiation rate (dependent on used
promotor)\
$k_{22}$&$\dotsc$ transcription elongation rate (dependent on
polymerase)\
$k_{92}$&$\dotsc$ sRNA degradation rate\
