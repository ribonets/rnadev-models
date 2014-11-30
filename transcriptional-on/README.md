In contrast a transcriptional ON switch is off per default and can be
switched on in presence of an sRNA, see Figure [fig:dawid]. A graph
representation of our implemented model is shown in
Figure [fig:transcriptional-on]. Here the short mRNA $U$ as well as the
short sRNA/mRNA complex ($C_{short}=U+F$) can be further transcribed
with rate $k_3$. However, in a sRNA free system huge amounts of $U$ will
form a terminator hairpin and therefore become $Q$, the state without
polymerase. The terminator hairpin formation happens with a newly
introduced rate $k_{73}$. Expression of the sRNA and mRNA binding
disrupts terminator formation and increases protein expression.

<span>l X</span> $k_{73}$ &$\dotsc$ terminator hairpin formation rate
(sequence dependent)\

![Graph representation of the transcriptional ON system. The formation
of the short complex ($C_{short}$) hinders terminator formation with
rate $k_{73}$ within the 5’UTR ($U$) which in the switch’s default state
triggers RNAP release.](figures/graph-transcriptional-on)

[fig:transcriptional-on]

A transcriptional ON switch can be described by the equation of the OFF
switch and the additional edits summarized below.

$$\label{transciptional_on}
    \begin{split}
      \frac{dC_{short}}{dt} &= k_{30}F \cdot U-(k_3+k_{40}+k_{50})C_{short} \\
      \frac{dC_{long}}{dt} &= k_{30}F \cdot R+k_3C_{short}-(k_{40}+k_{50})C_{long} \\
      \frac{dU}{dt} &= k_2S+k_{40}C_{short}-(k_3+k_9+k_{73})U-k_{30}U \cdot F \\
      \frac{dQ}{dt} &= k_{73}U-k_{92}Q \\
      \frac{dX}{dt} &= k_4(U+R+C_{short}+C_{long})-k_5X \\
    \end{split}$$

The general functionality of the implemented transcriptional systems is
shown in Figure [transcOnOff] where induction of the sRNA drastically
reduced protein expression in the OFF switch case and induces protein
expression in the ON switch case.

![*Top:* Transcriptional OFF switch without *(left)* and with *(right)*
sRNA. The sRNA (F) induced transcription termination clearly reduces the
amount of all mRNA ($S$,$U$ and $R$) and protein ($P$) species.
*Bottom:* Transcriptional ON switch without *(left)* and with *(right)*
sRNA. Here sRNA expression turns mRNA and protein expression
on.](figures/plot-transcriptional-off "fig:") ![*Top:* Transcriptional
OFF switch without *(left)* and with *(right)* sRNA. The sRNA (F)
induced transcription termination clearly reduces the amount of all mRNA
($S$,$U$ and $R$) and protein ($P$) species. *Bottom:* Transcriptional
ON switch without *(left)* and with *(right)* sRNA. Here sRNA expression
turns mRNA and protein expression
on.](figures/plot-transcriptional-off-srna "fig:")\
![*Top:* Transcriptional OFF switch without *(left)* and with *(right)*
sRNA. The sRNA (F) induced transcription termination clearly reduces the
amount of all mRNA ($S$,$U$ and $R$) and protein ($P$) species.
*Bottom:* Transcriptional ON switch without *(left)* and with *(right)*
sRNA. Here sRNA expression turns mRNA and protein expression
on.](figures/plot-transcriptional-on "fig:") ![*Top:* Transcriptional
OFF switch without *(left)* and with *(right)* sRNA. The sRNA (F)
induced transcription termination clearly reduces the amount of all mRNA
($S$,$U$ and $R$) and protein ($P$) species. *Bottom:* Transcriptional
ON switch without *(left)* and with *(right)* sRNA. Here sRNA expression
turns mRNA and protein expression
on.](figures/plot-transcriptional-on-srna "fig:")

[transcOnOff]

