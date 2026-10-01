# Activity 1 - Circuit three
(Figure of Act1Circuit03_Schematic.png)

## c
The THD can be calculated as (these are the source voltage and current):
THD = sqrt(summation{sh!=1}Ish^2)/Is1

equivalently...
Is = Is1*sqrt(1 + THD^2)
Is^2/Is1^2 - 1 = THD^2

where Is1 is the fundamental frequency of the source current.

We know at steady state, the Is = IL = Io.
And since the load determines how much current flows through from the source,
Is1 = Vs/(R + R_shunt)
Is1 = 12 V/(500 + 1)
Is1 = 23.95 mA

This is the fundamental component of Is_RMS since the harmonic distorition comes from the current ripple.

