# Signal Processing & Modulation in MATLAB

## Description
This repository contains **only executable MATLAB code** that implements signal processing and digital-communications components: signal generation, I/Q modulation and demodulation, pulse shaping, channel simulation (AWGN and simple multipath), matched filtering, symbol detection and demapping, equalization, BER testing, and visualization (time-domain plots, spectra, eye diagrams and constellations).
Only scripts (`*.m`), functions (`*.m`) and minimal data files (`*.mat`) required to reproduce the practical results (plots, audio, constellations, PSDs, BER tests) are kept here.  
Design goals: easy to run examples, consistent file naming, one short `README.md` per lab folder with the exact commands needed to reproduce figures and outputs, and modular helper functions in a shared `lib/` if necessary. Recommended MATLAB version: R2021b or later.

## Contents (detailed)
Each `labN/` folder contains the MATLAB artifacts required to run that lab’s experiments. Filenames use underscores (no spaces) and each runnable script includes a short header describing inputs/outputs and MATLAB version tested.

### Lab 1 — Basic signals, modulation primitives
- `Sinusoid.m` — script/function to generate and plot continuous sinusoids; parameters: frequency, amplitude, duration, sampling rate.
- `SquareWave.m` — generate square pulses for time-domain visualization and spectral content.
- `DSB_signal.m` — generate Double SideBand (DSB) modulated signal from a baseband message; demonstrates multiplication by carrier and basic bandpass behavior.
- `IQ_signal.m` — build an I/Q modulated signal from two orthogonal baseband messages and visualize I and Q components.
- Purpose: reproduce time-domain plots, FFT spectra and simple audio playback when applicable.

### Lab 2 — I/Q demodulation & filtering
- `IQ_demod_sinusoid.m` — coherent I/Q demodulator for synthetic sinusoidal messages; shows baseband recovery and lowpass filtering.
- `IQ_demod_voice.m` — same pipeline applied to a recorded voice vector (`voices.mat`) to reproduce audio demodulation examples.
- `hb_filter.mat` (optional) — helper FIR/IIR filter coefficients used by demod scripts (if generated with filterDesigner).
- Purpose: reproduce recovered audio, compare spectra before/after filtering, and measure reconstruction error.

### Lab 3 — Digital transmitter primitives
- `random_bits.m` — generate pseudo-random bit sequences with configurable length and bit-probability.
- `mapping.m` — map bit groups to constellation symbols (BPSK, QPSK, 16-QAM) with amplitude normalization.
- `pulse_srrc.m` — generate Square-Root Raised Cosine pulses for pulse shaping (parameterizable roll-off, span, samples-per-symbol).
- `digital_TX_continuous.m` — continuous-time transmitter script: mapping → pulse shaping → upconversion → output signal.
- Purpose: produce transmit waveform, visualize symbol stream, and export signal for channel experiments.

### Lab 4 — Receiver front-end, matched filter, and visualization
- `digital_TX_RX.m` — end-to-end example combining TX, channel (AWGN / simple multipath), matched filtering, and symbol sampling.
- `channel_impulse_response.m` — generate simple channel models (single-tap, two-tap with delay and attenuation).
- `represent_eye_diagram.m` — utility to create eye diagrams from sampled matched-filter outputs.
- `represent_constellation.m` — utility to plot received constellation points and annotate decision boundaries.
- Purpose: reproduce eye diagrams, constellations, BER vs SNR traces and matched-filter behavior.

### Lab 5 — Detection, demapping & equalization
- `Symbol_detector.m` — decide transmitted symbols from sampled outputs (handles BPSK/QPSK decision rules).
- `Demapper.m` — convert decided symbols back to bit streams and compute bit errors.
- `Equalizer.m` — implements a simple linear equalizer (ZF or MMSE) or adaptive LMS equalizer for short channel impulse responses.
- `BER_test.m` — script to sweep SNR and compute BER curves for chosen modulation and equalizer settings.
- Purpose: reproduce BER plots, show the effect of equalization, and compare theoretical vs empirical performance.

### Shared utilities and data (optional)
- `lib/` — optional folder for shared helper functions: plotting helpers, pulse generators, filter wrappers.
- `voices.mat`, `example_signals.mat` — optional small `.mat` files containing example voice or test signals used by scripts.

---
