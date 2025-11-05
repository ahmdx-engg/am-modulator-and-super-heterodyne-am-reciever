# am-modulator-and-super-heterodyne-am-reciever

This presents the design and simulation of an Amplitude Modulator and Superheterodyne AM Receiver implemented entirely using discrete components without relying on integrated circuits (ICs).
Developed and tested in Proteus, the project demonstrates how fundamental RF communication concepts can be realized using only transistors, diodes, capacitors, resistors, and tuned LC circuits.

The objective of this work was to explore the core analog principles behind AM generation and detection, understand the superheterodyne receiver architecture, and verify functional transmission and demodulation through practical circuit-level simulation.

## Project Motivation

Modern communication systems depend heavily on IC-based RF modules and DSPs that conceal the inner analog operations.
This project intentionally avoids such abstraction and focusing instead on fundamentals of modulation and frequency conversion using classical analog circuitry.

By constructing both the modulator and receiver from discrete components, we gain direct insight into:

How carrier and message signals interact to form AM waveforms
How frequency translation (mixing) enables effective signal reception
The role of tuned filters, envelope detectors, and intermediate frequency (IF) stages in signal recovery
The goal was not just to simulate a functioning circuit, but to understand and visualize the signal behavior across each stage of transmission and reception.

## System Overview

**Transmitter — Amplitude Modulator**

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

**Receiver — Superheterodyne AM Receiver**

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

The design process was carried out in several iterative stages, ensuring that each subsystem functioned correctly before integration.

**1. AM Modulator Design**

The modulation process was achieved using a BJT-based collector modulated amplifier, operating as a non-linear device to combine the carrier and message signals.
A low-frequency audio source (around 1 kHz) served as the message input, while a high-frequency LC oscillator (ranging from 100–500 kHz) generated the carrier.

The collector terminal of the transistor received the carrier signal, while the base was biased with the modulating signal.
This caused the collector current — and hence the amplitude of the carrier — to vary in proportion to the instantaneous amplitude of the modulating signal.

At the output, a tuned LC circuit selected the desired AM frequency while filtering out unwanted harmonics.
The resulting waveform displayed clear amplitude variation, confirming successful amplitude modulation.

**2. Superheterodyne Receiver Design**

The receiver was designed to emulate the classical superheterodyne architecture, which converts the received RF signal to a constant intermediate frequency before detection.
This structure offers higher sensitivity, selectivity, and stability compared to direct detection methods.

The RF tuning stage was built using a variable LC tank circuit to select the desired station frequency.
This signal was then fed into a mixer stage, constructed using a transistor operating in a non-linear region, which also received input from a local oscillator.
The non-linearity caused frequency mixing, generating sum and difference frequencies. The difference frequency (IF) — typically around 455 kHz — was selected using an LC filter.

The IF amplifier, also transistor-based, boosted the signal strength to make detection easier.
Next, an envelope detector using a diode and RC filter extracted the original modulation envelope — effectively recovering the transmitted audio signal.
Finally, a common-emitter amplifier stage amplified the recovered signal to a level suitable for observation or driving a small speaker.

Each of these stages was first simulated independently in Proteus and then connected sequentially to form the complete superheterodyne receiver.

## Simulation & Analysis

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

During simulation, the AM modulator produced a clear waveform showing amplitude variation corresponding to the input message.
By observing the modulator output on a virtual oscilloscope, the modulation depth was estimated to be around 70–80%, ensuring efficient modulation without distortion.

At the receiver end, when the RF tuning circuit was aligned with the transmitter’s carrier frequency, a stable signal was received and mixed down to the intermediate frequency.
The IF waveform displayed a clean envelope, and the subsequent demodulation stage successfully recovered the original 1 kHz audio tone.

Varying the local oscillator frequency verified the principle of heterodyning — as the IF remained constant while the RF input changed, demonstrating the characteristic advantage of the superheterodyne topology.
The audio amplifier output reproduced the same waveform as the transmitted message, confirming accurate signal recovery with minimal distortion.

Overall, the system successfully demonstrated the end-to-end transmission and reception of an amplitude-modulated signal using only analog discrete components.
