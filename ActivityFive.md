## Activity 5
a. Measure the mean value for each of the waveforms using Analysis/Avg adjusting the time span
for the following cases:
i. 10 complete cycles of the steady-state waveforms.
ii. 2 cycles and a fraction of a third one of the steady-state waveforms.
iii. Several cycles (around 50) of the steady-state waveforms.

=> Mean value of vo, iL are shown in Figure X (sim_Act5ai.png) for 10 cycles, Figure Y (sim_Act5ai_2.33Cycles.png) for 2 and a fraction of a third cycle, and Figure Z (sim_Act5ai_50PlusCycles.png) for Several cycles (around 50).

See results compiled in Table X below:
Time span | vo (V) | iL (A)
10 cycles, 4.897, 0.265
2.33 cycles, 4.865, 0.271
~50 cycles, 4.975, 0.254


b. Discuss on the differences among the three cases. What would be a good practice for measuring
the mean value?

=> As we increased the cycles, the vo and iL average drifted towards their steady state values of 5V and 0.25 A respectively. If allowed to average over infinite steady-state cycles, it approach those values +/- the peak of the ripple.

c. Zoom in to get 5 complete cycles and measure the peak values for the inductor current
waveform using the Measure tool and show the maximum values using Mark Data Point.
(Measure menu).

=> The peak iL current at 5 complete steady state cycles is 0.379 A. See Figure XX (sim_Act5c_PeakCurrent.png) for zoomed in snapshot.

d. Save a copy of the inductor current vs. time plot and measurements.

=> See Figure XX (sim_Act5d_CurrentWaveformFull.png) for inductor current vs. time plot measurement.