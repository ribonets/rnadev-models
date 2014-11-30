Translational Switch {#translational-switch .unnumbered}
--------------------

![*(A)* Translational OFF switch *(B)* and a translational ON switch as
described by @rodrigo:2013. (figure copied from original publication)
](rodrigo_2013)

[fig:rodrigo]

To construct a translational ON or OFF switch, as shown in
Figure [fig:rodrigo], the two independent reaction networks of sRNA and
mRNA expression need to interact in such a way that they implement the
desired logic. On the biological level this means the formation of
complexes by the sRNA and mRNA species. A complex is built from two RNA
species and can fall apart in its components again with rates $k_{30}$
and $k_{40}$ respectively. The implementation of the complex formation
is similar to @shimoni:2007. With rate $k_{50}$ the complex of double
stranded RNA can also be degraded. Complex formation makes the RBS
(in)accessible and thereby translation is (reduced) induced. Graph
representation of the implemented translational system is shown in
Figure [fig:translational] and additional literals are explained in
Table [tab:translational].

![To construct sRNA induced translational ON/OFF switches, complexes
(shown in cyan) of sRNA and mRNA species are formed. For instance
$C_{short}$ is build from $U$ and $F$. Complexes are formed with rate
$k_{30}$ and dissociate with rate $k_{40}$. This is indicated by
double-headed arrows. Note that we differentiate between the translation
initiation rate $k_4$ of the mRNA species ($U$ and $R$) and the rate
$k_4'$ that corresponds to translation initiated on a complex
($C_{short}$ and $C_{long}$).](figures/graph-translational)

[fig:translational]

[tab:translational]

<span>l X</span> $C_{short}$ &$\dotsc$ short sRNA/mRNA complex ($U$ and
$F$)\
$C_{long}$ &$\dotsc$ long sRNA/mRNA complex ($R$ and $F$)\
$k'_{4}$&$\dotsc$ translation (re-)initiation rate for sRNA bound mRNA
(sequence dependent)\
$k_{30}$&$\dotsc$ complex formation rate (sequence dependent)\
$k_{40}$&$\dotsc$ complex dissociation rate (sequence dependent)\
$k_{50}$&$\dotsc$ complex degradation rate\

Equations that needed to be adapted or added are written down in the
following. The remaining ones, i.e. $\frac{dS}{dt}$, $\frac{dW}{dt}$ and
$\frac{dP}{dt}$ in this case, are equal to the system described above.
This is also true for all subsequent equation systems.

$$\label{eq:translational_off}
    \begin{split}
      \frac{dC_{short}}{dt} &= k_{30}F \cdot U-(k_3+k_{40}+k_{50})C_{short} \\
      \frac{dC_{long}}{dt} &= k_{30}F \cdot R+k_3C_{short}-(k_{40}+k_{50})C_{long} \\
      \frac{dU}{dt} &= k_2S-(k_3+k_9)U+k_{40}C_{short}-k_{30}U \cdot F \\
      \frac{dR}{dt} &= k_3U-k_9R+k_{40}C_{long}-k_{30}R \cdot F\\
      \frac{dF}{dt} &= k_{22}W-k_{92}F+k_{40}(C_{short}+C_{long})-k_{30}F(U+R)\\
      \frac{dX}{dt} &= k_4(U+R)+k'_{4}(C_{long}+C_{short})-k_5X \\
    \end{split}$$

In case of a translational OFF switch the translation (re-)initiation
rate $k_4$ for the unbound mRNA species $U$ and $R$ should be much
bigger than the initiation rate $k'_4$ for the complexes $C_{short}$ and
$C_{long}$. So $k_4>>k'_4$ in a fully functional switch where the RBS is
accessible in $U$ and $R$ and sequestered in $C_{short}$ and $C_{long}$.
To model a translational ON switch the opposite $k_4 << k_4'$, has to be
true. This is the only necessary change to switch form a translational
OFF switch to an ON switch.

For a explanatory, general system we just assumed the probability for
RBS accessibility to be 0.95 and 0.05 for accessible and inaccessible.
In the section “” we explain in detail how these rates can be estimated
for specific systems with known RNA sequences. Simulations of the
systems behavior over time for idealized translation OFF and ON switches
is shown in Figure [fig:transOnOff].

![*(top left)* Translational OFF switch without sRNA *(top right)*
Translational OFF switch with sRNA. (bottom left) Translational ON
switch without sRNA *(bottom right)* Translational ON switch with sRNA.
](figures/plot-translational-off "fig:") ![*(top left)* Translational
OFF switch without sRNA *(top right)* Translational OFF switch with
sRNA. (bottom left) Translational ON switch without sRNA *(bottom
right)* Translational ON switch with sRNA.
](figures/plot-translational-off-srna "fig:")\
![*(top left)* Translational OFF switch without sRNA *(top right)*
Translational OFF switch with sRNA. (bottom left) Translational ON
switch without sRNA *(bottom right)* Translational ON switch with sRNA.
](figures/plot-translational-on "fig:") ![*(top left)* Translational OFF
switch without sRNA *(top right)* Translational OFF switch with sRNA.
(bottom left) Translational ON switch without sRNA *(bottom right)*
Translational ON switch with sRNA.
](figures/plot-translational-on-srna "fig:")

[fig:transOnOff]
