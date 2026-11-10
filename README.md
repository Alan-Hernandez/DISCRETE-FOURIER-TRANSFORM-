# EXP 1 A : COMPUTATION OF DFT USING DIRECT AND FFT

# AIM: 

# To Obtain DFT and FFT of a given sequence in SCILAB. 

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 

clc;
clear;
clf;

xn = [1,2,3,4,4,3,2,1];

N = length(xn);
n = 0:N-1;
j = %i;

Xk = zeros(1, N);

// Direct DFT calculation
for k = 0:N-1
    for r = 0:N-1
        Xk(k+1) = Xk(k+1) + ...
            xn(r+1)*exp(-j*2*%pi*k*r/N);
    end
end

disp("DFT output:");
disp(Xk);

K = 0:N-1;
magnitude = abs(Xk);
phase = atan(imag(Xk), real(Xk));

subplot(3,1,1);
plot2d3(n, xn);
xtitle("Input Sequence", "n", "x(n)");

subplot(3,1,2);
plot2d3(K, magnitude);
xtitle("Magnitude Spectrum", "k", "|X(k)|");

subplot(3,1,3);
plot2d3(K, phase);
xtitle("Phase Spectrum", "k", "Phase (radians)")

clc;
clear;
clf;

xn = [1,2,3,4,4,3,2,1];
N = length(xn);
n = 0:N-1;

Xk = fft(xn);

disp("FFT output:");
disp(Xk);

K = 0:N-1;
magnitude = abs(Xk);
phase = atan(imag(Xk), real(Xk));

y = ifft(Xk);

subplot(2,2,1);
plot2d3(n, xn);
xtitle("Input Sequence", "n", "x(n)");

subplot(2,2,2);
plot2d3(K, magnitude);
xtitle("Magnitude Spectrum", "k", "|X(k)|");

subplot(2,2,3);
plot2d3(K, phase);
xtitle("Phase Spectrum", "k", "Phase (radians)");

subplot(2,2,4);
plot2d3(n, real(y));
xtitle("Inverse FFT Output", "n", "x(n)");

# OUTPUT: 
<img width="1534" height="1600" alt="image" src="https://github.com/user-attachments/assets/9cb6dd08-3a0b-432e-870c-9428687cfeb6" />


# RESULT: 
<img width="1600" height="904" alt="image" src="https://github.com/user-attachments/assets/68e2fc4b-d602-42ca-b951-d9bf1648ffcf" />
