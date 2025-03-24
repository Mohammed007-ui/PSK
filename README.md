# PSK
Aim

To implement and analyze Phase Shift Keying (PSK) modulation and demodulation for digital communication systems.

Tools required
Software:

Python (NumPy, Matplotlib)

MATLAB (Optional)

Hardware (if applicable):

Signal generator

Oscilloscope

SDR (Software Defined Radio)

Program
import numpy as np
import matplotlib.pyplot as plt

# Parameters
fc = 10  # Carrier frequency (Hz)
fs = 1000  # Sampling frequency (Hz)
T = 1  # Duration (s)
bits = [1, 0, 1, 1, 0, 1]  # Binary data

# Time vector
t = np.linspace(0, T, fs, endpoint=False)

# PSK Modulation
carrier = np.sin(2 * np.pi * fc * t)
psk_signal = np.array([])

for bit in bits:
    phase = np.pi if bit else 0  # BPSK: 0° for 0, 180° for 1
    psk_signal = np.append(psk_signal, np.sin(2 * np.pi * fc * t + phase))

# Plotting
plt.figure(figsize=(12, 6))
plt.subplot(2, 1, 1)
plt.title("Original Bits")
plt.step(range(len(bits)), bits, where='post')
plt.grid()

plt.subplot(2, 1, 2)
plt.title("PSK Modulated Signal")
plt.plot(np.linspace(0, T * len(bits), len(psk_signal)), psk_signal)
plt.grid()
plt.tight_layout()
plt.show()

Output Waveform

![Image](https://github.com/user-attachments/assets/1e2bc58c-6b4f-4a55-8bea-df652f2e85f9)

Results

PSK modulation successfully encoded binary data (0s and 1s) as 0° and 180° phase shifts in the carrier wave, demonstrating clear phase transitions at bit boundaries. The output waveform shows distinct phase reversals corresponding to the input bit pattern [1,0,1,1,0,1].  
