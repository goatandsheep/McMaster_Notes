# Tutorial 1

## 1

**Draw a sinusoidal signal with amplitude i+3, -3V, f = 5kHz.**

p = 1/f = $\frac{1}{5\times10^3}$ = 0.2ms

## 2

**Draw a cosine signal amplitude i+5, -5V, and f = 10kHz.**

p = $\frac{1}{10kHz}$ = 0.1ms

## 3

**Draw AM wave m = 0.5, 1, 1.5.**

Since m = Am/Ac = 0.5, therefore Am = 0.5 Ac

Let Ac = 2V, therefore Am = 1V. You can use any Ac

**Amplitude Modulated [Am]**: 

## 4

**Audio signal 20sin$\pi \times$ 500t, used to amplitude carrier of 80sin2$\pi \times 10^5$t**

1. **Modulation Index**
2. **Sideband frequency**
3. **Amplitude of each sideband frequency**
4. **Bandwidth required**
5. **Total power deliverd into a load of 600$\Omega$.****

m = 1 —> Am/Ac = 1. Let Am = Ac = 2V

Inner signal is arbitrary.

-------

Message m(t) = 20sin$\pi \times$ 500t = 20sin(2$\pi f_m$t) —> $f_m$ = 250Hz

Therefore Am = 20V

Carrier signal c(t) = 80sin(2$\pi \times 10^5$)t = 80sin(2$\pi f_c$t) 

Therefore $f_c = 1 \times 10^5$ Hz; Ac = 80V

1. Modulation index: m = Am/Ac = 20/80 = 0.25
2. Sideband frequency: fc + fm = 100 * 25kHz; fc - fm = 99.75kHz
3. Amplitude of each sideband frequency: fc, fm, fc, fc, fm $\frac{mA_c}{2} = \frac{0.25\times80}{2}$ = 10V
4. B/W required: B/V = 2fm = 2*250Hz = 500Hz
5. Total power: $p_{total} = \frac{A_c}{2R}(H\frac{m^2}{2}) = \frac{80^2}{2\times600}$ = 5.5W



## 5

**Calculate the percentage power saving when the carrier is suppressed in an AM wave mudlated to a depth of …**

### I)

Total power, Pt = Pc(H m^2/2)

if m = 1, Pt = Pc(1 + 1/2) = 1.5Pc

If m = 0.5, Pt = Pc(1 + 0.5^2/2) = 1.125Pc)

Therefore Power saving = 0.125 Pc

### II)

Pt = $\frac{m^2A_c^2}{8R} = \frac{A_c^2}{2R} (\frac{m^2}{4}) = P_c(\frac{m^2}{4})$

If m = 1 —> Pt = 0.25 Pc

If m = 0.5 —> Pt = 0.015625 Pc

Therefore Power saving = Pt2 - Pt1 = 0.234375 Pc

## 6

fc = $\frac{1}{2\pi \sqrt{LC}}$ = … = 229.720kHz

fm = 5kHz

LSB = fc - fm = 224.720kHz

USB = fc + fm = 234.720kHz

Therefore bandwidth: 2fm = 10kHz

## 7

$I_t = I_c\sqrt{H\frac{m^2}{2}} = I_c\sqrt{H\frac{0.6^2}{2}}$

It = 1.086Ic

Therefore Ic = It/1.086 = 5/1.086 = 4604A