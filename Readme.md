# Klinkenberg Effect Permeability Calculator

This repository contains a Python implementation using the **Newton-Raphson iterative method** to calculate the absolute (liquid) permeability of a core sample from gas permeability measurements, accounting for the **Klinkenberg Effect**.

---

## Overview

When measuring core permeability in a laboratory, gas permeability ($k_g$) tends to be higher than liquid permeability ($k_L$). This discrepancy is caused by gas slippage along the pore walls at low pressures—a phenomenon known as the **Klinkenberg Effect**. 

To determine the true absolute permeability ($k_L$), multiple measurements at varying pressures are typically required. However, using empirical relationships, we can estimate $k_L$ from a single gas permeability measurement at a known mean pressure ($p_m$).



## Governing Equations

The relationship between gas permeability and absolute liquid permeability is expressed as:

$$k_g = k_L + \frac{c}{p_m}$$

Where an empirical correlation defines the slope $c$ as:

$$c = 6.9 \cdot k_L^{-0.36}$$

Substituting $c$ back into the first equation yields the non-linear objective function $f(k_L)$ that we need to solve for zero:

$$f(k_L) = p_m \cdot k_L + 6.9 \cdot k_L^{0.64} - p_m \cdot k_g = 0$$

To solve this using the **Newton-Raphson method**, we also define its first derivative with respect to $k_L$:

$$f'(k_L) = p_m + 4.416 \cdot k_L^{-0.36}$$

---

