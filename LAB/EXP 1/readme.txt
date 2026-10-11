
clc; clear; close all;

c = 3e8;
a = 22.86e-3;
b = 10.16e-3;
f = 10e9;

fc10 = c/(2*a);
fc11 = (c/2)*sqrt((1/a)^2+(1/b)^2);
k0 = 2*pi*f/c;
beta = k0*sqrt(1-(fc10/f)^2);

fprintf('TE10 Cutoff = %.3f GHz\n',fc10/1e9);
fprintf('TM11 Cutoff = %.3f GHz\n',fc11/1e9);
fprintf('TE10 Beta = %.2f rad/m\n',beta);

x = linspace(0,a,100);
y = linspace(0,b,50);
[X,Y] = meshgrid(x,y);

subplot(1,2,1);
imagesc(x*1000,y*1000,sin(pi*X/a));
colorbar; title('TE10 E-Field');
xlabel('x (mm)'); ylabel('y (mm)');

subplot(1,2,2);
imagesc(x*1000,y*1000,sin(pi*X/a).*sin(pi*Y/b));
colorbar; title('TM11 Field Pattern');
xlabel('x (mm)'); ylabel('y (mm)');

