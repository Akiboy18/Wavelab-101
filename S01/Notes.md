# S01 — Basic and Trigonometric Signals

---

## 🔹 1. Unit Step Signal

### 📌 Definition
A signal that turns ON at a specific time.

u(t) =
- 0, for t < 0  
- 1, for t ≥ 0  

### 🧠 Intuition
- OFF before t = 0  
- ON after t = 0  
- Acts like a switch  

### 💻 MATLAB
```matlab
t = -5:0.01:5;
u = t >= 0;

plot(t, u);
grid on;
title('Unit Step Signal');
