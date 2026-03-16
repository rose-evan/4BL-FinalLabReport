# Project Overview — 4BL Final Lab Report

## Experiment Title
Investigation of Eddy Currents as Analyzed by a Magnet Falling Through a Conductive Copper Pipe

## Course
Physics 4BL, UCLA — January 2026

## Group
- **Members:** Charles Knudsen, Saif Almassry, Evan Rose
- **Group Number:** 3

## Experiment Summary
A neodymium cylinder magnet is dropped through two vertical tubes of equal length: a clear
plastic/acrylic tube (control) and a copper pipe (experimental). Sensing coils wrapped around
each tube at measured intervals detect the magnet's passage via induced voltage pulses. An ESP32
microcontroller records the peak voltage (V_peak) and timestamp for each coil trigger.

In the plastic tube there is no magnetic braking, so the magnet is in free fall — V_peak increases
with each coil and scales as √h. This run calibrates the coils: plotting V_peak vs √h gives a
linear fit whose slope converts measured voltage to instantaneous velocity.

In the copper pipe, eddy currents in the pipe walls create a magnetic drag force proportional to
velocity. The magnet decelerates rapidly and reaches a terminal velocity, visible as a plateau in
V_peak across successive coils.

## Physical Principles
- **Faraday's Law**: ε = -N dΦ_B/dt
- **Generator effect / V_peak ∝ v**: ε = -N(dΦ_B/dz)·v → V_peak proportional to instantaneous velocity
- **Lenz's Law**: induced effects oppose their cause (upward braking force on magnet)
- **Ohm's Law**: I = ε/R
- **Free-fall kinematics** (calibration): v(h) = √(2gh) → V_peak vs √h is linear
- **Magnetic drag force**: F_d = -bv (b = magnetic drag coefficient)
- **Equation of motion**: m(dv/dt) = mg - bv
- **Terminal velocity**: v_t = mg/b (plateau in V_peak profile)

## Measurement Method
- 5–6 sensing coils (~50–100 turns each, 30 AWG magnet wire) at measured intervals along each tube
- ESP32 microcontroller: fast ADC sampling, threshold trigger, captures V_peak and timestamp per coil
- Data output: (Time, Coil #, V_peak) → Python analysis
- Voltage divider resistors protect ESP32 if V > 3.3 V

## Calibration Procedure
1. Drop magnet through plastic tube (free fall, no braking)
2. Record V_peak at each coil position h
3. Plot V_peak vs √h → linear fit gives calibration constant (slope = V/velocity units)
4. Use calibration to convert all V_peak readings to instantaneous velocities

## Hypothesis
1. V_peak in each sensing coil is linearly proportional to the magnet's instantaneous velocity
2. In the copper pipe: V_peak plateaus across successive coils (terminal velocity reached)
3. In the plastic tube: V_peak continues increasing proportional to √h (free fall)

## Key Results (from Abstract)
- Average velocity through copper pipe: **0.10 ± 0.01 m/s**
- Average velocity through plastic tube: **2.10 ± 0.05 m/s**
- Result supports hypothesis: eddy currents produce significant magnetic drag

## Equipment / Apparatus
- 1× neodymium cylinder magnet (fits loosely in pipes)
- 1× clear acrylic/PVC pipe
- 1× copper pipe (same diameter as plastic)
- 5–6 sensing coils (50–100 turns, 30 AWG magnet wire)
- 1–2× ESP32 microcontrollers
- Resistors (voltage divider, protects ESP32)
- Lab stands and clamps (hold pipes vertical)

## Report Sections Status
- [x] Title / Authors / Abstract — drafted
- [x] Introduction/Theory — drafted (expanded with V_peak ∝ v, calibration eq, terminal velocity)
- [ ] Methods/Experimental Setup — TODO
- [ ] Results and Analysis — TODO
- [ ] Conclusion — TODO
- [ ] Appendix — TODO

## Source Files
- `main.tex` — primary LaTeX document

## References
- Young & Freedman, *University Physics with Modern Physics*, Pearson
- Kingman et al. (2002), "An inexpensive apparatus for studying magnetic braking," *AJP*
- Amrani & Paradis (2006), "Faraday's Law of Induction," *Physics Education*
- Physics 4BL Lab Slides, UCLA Department of Physics and Astronomy
