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
Is1 = Vs/(R + R_shunt + Rs)
Is1 = 12 V/(500 + 1 + 2)
Is1 = 23.86 mA

This is the fundamental component of Is_RMS since the harmonic distorition comes from the current ripple.

Method: Let's use phasor analysis to find the output current, then convert to the time domain. We know the output voltage is |Vs| so we need to restrict our final result waveform to be positive, or io(t) = Is*|sin(wt + phi)|

As shown in Figure X, if we denote Vs2 phasor as the source voltage after the source inductor and resistor drop:

Vs2 = Vs - (j*w*Ls + Rs)*is

If we simplify the output impedance as seen by Vs2:
Zo = (1/(j*w*C)//R) + j*w*L + Rshunt

Lastly, we know that is = iL = io
Therefore combining our equations, we get:
io*Zo = Vin2
io*Zo = Vs - io*(j*w*Ls + Rs)

Plugging in our values and solving for io:
io = 12/(0.002*j*w + 503)

Now converting back domain, with consideration for how the output is rectified:
io(t) = |Io| * sin(wt + angle(io))
(box) io(t) = 23.86 * |sin(120pi*t - 0.001498)|

Note: |Io| is equal to Is1 calculated earlier, which is a good sign!

Taking the fourier series, we can analyze the harmonic content:

|sin x| = 2/pi - 4/pi * summation(cos(2n*x)/(4n^2 - 1)){n=1, inf}

So |sin 120pi*t| = 2/pi - 4/pi * summation(cos(240*n*pi*t)/(4n^2 - 1)){n=1, inf}

Since the io and vin2 are basically in phase, we can approximate the harmonics without accounting for the phase shift.

Figure X (FourierAbsSinx.png): Image showing abs(sin x) fourier series.

If we're analysing which harmonics contribute to the signal the most, the peak (when cosine equal 1) of each harmonic is given by (ignoring the current amplitude):

Ip,n = 4/(pi*(4*n^2 - 1))

We know the fundamental (f = 120 Hz, n=1) will provide the most power, so comparing the power contribution as:

(Ip,n/Ip1)^2 x 100%
where Ip1 = 4/(3pi)

Table X
n, Ipn_peak, % Contribution
1, 4/(3pi), 100%
2, 4/(15pi), 4.00%
3, 4/(35pi), 0.73%
4, 4/(63pi), 0.23%
5, 4/(99pi), 0.092%

-----
Figure X (Act1Circuit03_FFT.png), PSIM FFT simulation of circuit three

Table X: Circuit three Is frequency harmonics
f (Hz), Amplitude (mA)
60, 62.3
180, 47.93
300, 43.54
420, 38.99
540, 22.02
660, 11.67
780, 4.738

Figure X1 (Act1Circuit03_TimeDomainTHD.png)

The fundamental is 60 Hz, and so from the simulation in Figure X1, we get THD = 1.403.

Calculating the THD using the 6 harmonics with the most power:
THD = sqrt(summation(Ish^2){h!=1})/Is1

Crest factor = Is_peak/Is_RMS
Figure X2: [alt text](image.png)
(box) Crest factor = 0.267




