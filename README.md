# am-modulator-and-super-heterodyne-am-reciever

This presents the design and simulation of an Amplitude Modulator and Superheterodyne AM Receiver implemented entirely using discrete components without relying on integrated circuits (ICs).
Developed and tested in Proteus, the project demonstrates how fundamental RF communication concepts can be realized using only transistors, diodes, capacitors, resistors, and tuned LC circuits.

The objective of this work was to explore the core analog principles behind AM generation and detection, understand the superheterodyne receiver architecture, and verify functional transmission and demodulation through practical circuit-level simulation.

## Project Motivation

Modern communication systems depend heavily on IC-based RF modules and DSPs that conceal the inner analog operations.
This project intentionally avoids such abstraction — focusing instead on fundamentals of modulation and frequency conversion using classical analog circuitry.

By constructing both the modulator and receiver from discrete components, we gain direct insight into:

How carrier and message signals interact to form AM waveforms
How frequency translation (mixing) enables effective signal reception
The role of tuned filters, envelope detectors, and intermediate frequency (IF) stages in signal recovery
The goal was not just to simulate a functioning circuit, but to understand and visualize the signal behavior across each stage of transmission and reception.

## System Overview

*Transmitter — Amplitude Modulator*

The AM Modulator generates a high-frequency carrier signal and modulates it with a lower-frequency message input.
Modulation is achieved using transistor-based balanced modulation, where the instantaneous amplitude of the carrier varies proportionally with the message voltage.

## Key Stages:

**Message Signal Source:**
A low-frequency sinusoidal audio tone (typically 1 kHz).

**Carrier Oscillator:**
Tuned LC oscillator generating a stable RF carrier (e.g., 100–500 kHz).

**Amplitude Modulation Stage:**
A BJT configured as a collector-modulated class-C amplifier, combining carrier and message signals.

**Output Filter:**
LC filter to pass the desired AM signal and attenuate harmonics.

Result:

A standard AM waveform with controlled modulation depth (typically 70–80%).

 *Receiver — Superheterodyne AM Receiver*

The superheterodyne receiver converts the incoming RF signal to a fixed intermediate frequency (IF) before detection, ensuring consistent bandwidth and selectivity.

## Functional Blocks:

**RF Tuning Stage:**
Selects the desired AM station using a variable LC tank circuit.

**Mixer & Local Oscillator (LO):**
Generates an IF signal (e.g., 455 kHz) by mixing the incoming RF with a locally generated oscillator tone.

**IF Amplifier:**
Amplifies the intermediate frequency for stronger detection and improved signal-to-noise ratio.

**Detector (Envelope Detector):**
Uses a diode and RC network to recover the original audio envelope from the AM waveform.

**Audio Amplifier:**
A transistor-based common-emitter amplifier to reproduce the demodulated signal at audible levels.

# Design Methodology
Stage	Description	Components Used
Oscillator	LC Tank + Transistor feedback loop	Inductor, Capacitor, BJT
Modulator	Collector-modulated BJT circuit	BJT (e.g., 2N2222), RC coupling
Mixer	Non-linear transistor mixer	BJT or dual-diode
IF Stage	Tuned amplifier	LC tuned circuit, BJT
Detector	Diode-based envelope detector	Diode (1N4148), RC filter
Audio Stage	Transistor amplifier	BJT (e.g., BC547), capacitor coupling

Each stage was individually tested and tuned for correct operation before integration.

🧠 Simulation & Analysis

The complete transmitter-receiver pair was simulated in Proteus, allowing real-time visualization of:

Carrier generation

Modulated AM waveform

IF conversion and filtering

Envelope recovery (audio extraction)

Waveforms were verified using the Proteus virtual oscilloscope, confirming:

Correct modulation index behavior

Accurate intermediate frequency generation

Clean demodulated output with minimal distortion

## Observations

**Parameter	                                          Modulator Output                                  	Receiver Output**

Carrier Frequency	                                    100–500 kHz	                                      Tuned via LO
Modulation Frequency	                                1 kHz	                                            1 kHz (audio recovered)
Modulation Depth                                    	~75%	                                            Preserved post demodulation
IF Frequency	                                        —	                                                ~455 kHz
Audio Output	                                        —	                                                Clear and distortion-free

The project successfully demonstrated both modulation and superheterodyne reception entirely through discrete analog circuits.
