
clc; clear; close all;

f = 8:0.1:12;
S11 = zeros(size(f));
S21 = ones(size(f));
S12 = S21;
S22 = S11;

subplot(2,1,1);
plot(f,20*log10(abs(S11)+1e-10),f,20*log10(abs(S21)));
grid on; title('S11 and S21');
xlabel('Frequency (GHz)'); ylabel('Magnitude (dB)');
legend('S11','S21');

RL = Inf;
IL = -20*log10(S21(21));
eta = S21(21)^2*100;

fprintf('Return Loss = Infinite dB\n');
fprintf('Insertion Loss = %.2f dB\n',IL);
fprintf('Efficiency = %.2f%%\n',eta);
fprintf('Operating Frequency = 10 GHz\n');

