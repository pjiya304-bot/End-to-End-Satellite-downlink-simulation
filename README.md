# Satellite Downlink simulation
Simulation of an end-to-end satellite communication downlink - modeling propagation through vacuum and Earth's atmosphere, noise, attenuation and signal recovery at the receiver-built in GNU Octave as a foundational project ahead of a follow-up project introducing a jammer and adaptive filter.

# Overview
This project models the full physics-layer chain of a satellite downlink: a transmitted QPSK signal travels through a simulated vacuum and atmospheric channel which is degraded by attenuation, noise and phase effects and is then reconstructed at the receiver. The goal is to demonstrate how a satellite link maintains signal integrity across a long, lossy and noisy channel.

# Setup
**Tool used:** GNU Octave (MATLAB-compatible syntax), run via Octave Online
**Modulation Scheme:** QPSK (Quadrature Phase Shift Keying) using I/Q signal representation
**Pulse Shaping:** Root Raised Cosine (RRC) filter at the transmitter, to control bandwidth and inter-symbol interference (ISI)
**Channel Model:** Free-space (vacuum) path loss, atmospheric attenuation, additive noise and phase effects introduced during propagation

# How It Works
1. Data bits are mapped to QPSK symbols and represented as an I/Q signal.
2. the I/Q signal is pulse-shaped using an RRC filter to limit bandwidth and reduce ISI.
3. The shaped signal passes through the simulated channel: vacuum path loss, atmospheric attenuation, additive noise and phase distortion are applied.
4. At the receiver, a matched RRC filter is applied to the received signal, reversing the pulse shaping and minimising ISI.
5. The filtered signal is demodulated back into the original transmitted bits.
6. Constellation diagrams are plotted before and after the channel to visualize the degradation and recovery.

# Core Functions
**Transmitter:** QPSK mapping + RRC pulse shaping
**Channel:** Path loss calculation, atmospheric attenuation modeling, noise addition, phase shift application
**Receiver:** Matched Filtering (RRC) + demodulation + bit recovery
**Link Budget Analysis:** SNR calculation across the link to characterize signal quality
**Visualization:** Constellation diagram generation (transmitted vs received)

# Future Improvements
1. Extend this simulation with an active jammer and an adaptive LMS notch filter, to model interference and signal recovery under jamming(covered in a separate follow-up project)
2. Different modulation scheme - extend beyond QPSK and compare performance/bandwidth trade-offs.
3. Forward error correction (FEC) - add channel coding(e.g. convolutional codes or Reed-Soloman) to demonstrate error correction on top of the existing link.
4. Doppler Shift modeling - satellites move relative to ground stations, so simulating Doppler effects would make the channel model more realistic.
