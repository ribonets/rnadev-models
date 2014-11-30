Transcriptional Switches {#transcriptional-switches .unnumbered}
------------------------

![*(A)* Transcriptional OFF switch transcriptional and *(B)*
transcriptional ON switch as described by @dawid:2009. (figure copied
from original publication)](dawid_transcription)

[fig:dawid]

To construct transcriptionally controlled systems as depicted in
Figure [fig:dawid], again the formation of long and short sRNA/mRNA
complexes is the key mechanism. A transcriptional OFF switch is turned
on without sRNA. Essentially, the induction of sRNA results in the
formation of the short complex. Translated into our model, see
Figure [fig:transcriptional-off], $F$ binds to $U$ and $C_{short}$ is
formed. This binding triggers the formation of a rho-independent
terminator within the mRNA’s 5’UTR. RNAP is released and thereby
transcription stopped. The short complex is not only degraded with the
rate $k_{50}$ but also dissociates with rate $k_{40}$ into sRNA $F$ and
a the short mRNA piece, but without a associated polymerase. The latter
cannot be elongated any more and therefore a new species was introduced,
namely $Q$, which gets degraded with rate $k_{92}$.

<span>l X</span> $Q$ &$\dotsc$ short mRNA (5’UTR) terminated and
therefore without polymerase\

![Graph representation of the transcriptional OFF system. To construct
an transcriptional OFF switch sRNA (green) and mRNA (blue) species
interact and form complexes (cyan). The complex formation with rate
$k_{30}$ and dissociation with rate $k_{40}$ is indicated by
double-headed arrows. The formation of a short sRNA/mRNA complex
(C$_{short}$) has an irreversible effect as terminator folding is
triggered and thereby mRNA transcription is terminated. Therefore, the
C$_{short}$ dissociates into sRNA ($F$) and a short mRNA fragment ($Q$)
which is degraded.](figures/graph-transcriptional-off)

[fig:transcriptional-off]

To implement the transcriptional OFF switch as ODE system the above
described system has been adapted. Equations that have been changed or
added are written down in the following equation. The remaining ones,
i.e. $\frac{dS}{dt}$, $\frac{dW}{dt}$ and $\frac{dP}{dt}$, can be
assumed to be equal to the system described above.

$$\label{transcriptional_off}
    \begin{split}
      \frac{dC_{short}}{dt} &= k_{30}F \cdot U-(k_{40}+k_{50})C_{short} \\
      \frac{dC_{long}}{dt} &= k_{30}F \cdot R-(k_{40}+k_{50})C_{long} \\
      \frac{dU}{dt} &= k_2S-(k_3+k_9)U-k_{30}U \cdot F \\
      \frac{dR}{dt} &= k_3U-k_9R+k_{40}C_{long}-k_{30}R \cdot F \\
      \frac{dF}{dt} &= k_{22}W-k_{92}F+k_{40}(C_{short}+C_{long})-k_{30}(U+R)F\\
      \frac{dQ}{dt} &= k_{40}C_{short}-k_{92}Q \\
      \frac{dX}{dt} &= k_4(U+R+C_{long})-k_5X \\
    \end{split}$$
