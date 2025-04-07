# EXP.NO.5-Simulation-of-Signal-Sampling-Using-Various-Types
5.Simulation of Signal Sampling Using Various Types such as
    i) Ideal Sampling
    ii) Natural Sampling
    iii) Flat Top Sampling

# AIM
To simulate signal sampling using various types such as:
       i) Ideal Sampling
       ii) Natural Sampling
       iii) Flat Top Sampling

# SOFTWARE REQUIRED
Google Colab

# ALGORITHMS
1. Define the parameters such as sampling frequency, time vector, sine wave frequency, and pulse width for the sampling process.
2. Generate the sine wave signal using the defined time vector and frequency.
3. Initialize output arrays for ideal, natural, and flat-top sampled signals.
4. Loop through the time vector with a step size based on the sampling period, calculating indices for each sample.
5. For each sample, update the output arrays: 
       - Ideal sampling assigns the sine wave value at each sampling point.
       - Natural sampling holds the signal value constant over the pulse width.
       - Flat-top sampling holds the sample value constant for the pulse width as well.
6. Plot the original sine wave and the three types of sampled signals in subplots to compare their behavior.

# PROGRAM
    import numpy as np
    import matplotlib.pyplot as plt

    # Parameters
    fs = 900          
    t = np.linspace(0, 1, fs) 
    f = 4.5               
    x = np.sin(2 * np.pi * f * t)  

    fs_sample = 45      
    Ts = 1 / fs_sample  
    pulse_width = 0.01  

    # Initialize outputs
    ideal_output = np.zeros_like(t)
    natural_output = np.zeros_like(t)
    flattop_output = np.zeros_like(t)

    # Sampling process
    for i in np.arange(0, 1, Ts):
        idx_start = int(i * fs)
        idx_end = min(len(t), int((i + pulse_width) * fs))
        sample_val = np.sin(2 * np.pi * f * i)
    
        # Ideal Sampling
        ideal_output[idx_start] = sample_val

        # Natural Sampling
        natural_output[idx_start:idx_end] = x[idx_start:idx_end]

        # Flat-top Sampling
        flattop_output[idx_start:idx_end] = sample_val

    # Plot the results
    plt.figure(figsize=(14, 10))

    # Ideal Sampling
    plt.subplot(3, 1, 1)
    plt.plot(t, x, 'lightgray', label="Input (Sine Wave)")
    plt.stem(t, ideal_output, 'blue', basefmt=' ', label="Ideal Sampled")
    plt.title("Ideal Sampling")
    plt.legend()

    # Natural Sampling
    plt.subplot(3, 1, 2)
    plt.plot(t, x, 'lightgray', label="Input (Sine Wave)")
    plt.plot(t, natural_output, 'green', label="Natural Sampled")
    plt.title("Natural Sampling")
    plt.legend()

    # Flat-top Sampling
    plt.subplot(3, 1, 3)
    plt.plot(t, x, 'lightgray', label="Input (Sine Wave)")
    plt.plot(t, flattop_output, 'red', label="Flat-Top Sampled")
    plt.title("Flat-Top Sampling")
    plt.legend()

    plt.tight_layout()
    plt.show()

# OUTPUT
![image](https://github.com/user-attachments/assets/9d596b33-ab31-44f0-9838-f0c8b578f65c)


 
# RESULT / CONCLUSIONS
Thus, the simulation of signal sampling using ideal sampling, natural sampling and flat-top sampling is carried out successfully.
