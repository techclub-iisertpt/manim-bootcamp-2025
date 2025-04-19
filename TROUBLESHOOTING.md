# 🛠️ Manim Bootcamp 2025 – Troubleshooting Guide

This document provides solutions to common issues faced while setting up or running Manim animations in Google Colab or on your local machine.

---

## 📦 Setup Issues

### ✅ Required Setup Commands (Ubuntu / Colab)

Make sure you run this block before using Manim in Google Colab:

```bash
!sudo apt update
!sudo apt install libcairo2-dev \
    texlive texlive-latex-extra texlive-fonts-extra \
    texlive-latex-recommended texlive-science \
    tipa libpango1.0-dev
!pip install manim
!pip install IPython==8.21.0
```

> ⚠️ Skipping these installations may lead to rendering or LaTeX-related errors.

---

## 🧪 Runtime Errors & Fixes

### ❌ `manim` command not found or nothing renders

**Cause**: Not using IPython magic (`%%manim`) in Colab.

**Fix**: Use this format:

```python
%%manim -qm -v WARNING SceneName
```

### ❌ `RuntimeError: cairo returned CAIRO_STATUS_WRITE_ERROR`

**Cause**: Cairo (graphics engine) is not properly configured.

**Fix**: Ensure `libcairo2-dev` is installed.

### ❌ `OSError: Cannot find a usable font configuration`

**Cause**: Missing or misconfigured fonts.

**Fix**:

- Use default fonts: `Text("Hello")`
- Or specify: `Text("Hello", font="Arial")`

### ❌ LaTeX not rendering in `MathTex`

**Cause**: Missing LaTeX dependencies.

**Fix**: Install all relevant texlive packages:

```bash
texlive texlive-latex-extra texlive-fonts-extra texlive-latex-recommended texlive-science
```

**Example**:

```python
MathTex(r"\\frac{a}{b}")
```

### ❌ `NameError`, `TypeError`, or Empty Output

**Causes**:

- Not inheriting from `Scene`
- Missing `construct()`
- Using wrong animation syntax

**Checklist**:

- ✅ Class inherits from `Scene`
- ✅ `construct()` method exists
- ✅ Use `self.play(...)`, `self.add(...)`
- ✅ Use `%%manim` at top of cell

---

## 🐍 Version & Dependency Conflicts

### ❌ `AttributeError` or IPython Magic Failure

**Fix**:

```bash
!pip install IPython==8.21.0
```

### ❌ `ImportError` for `numpy`, `scipy`, or `odeint`

**Fix**:

```bash
!pip install numpy scipy
```

---

## 📊 Graphs & Math Scenes

### ❌ Graphs not showing or axes missing

**Fix**:

```python
axes = Axes(...)
self.play(Create(axes))
```

### ❌ MathTex not displaying or cut off

**Fix**:

- Avoid unsupported LaTeX commands (e.g., `\text{}`)
- Use pure math: `MathTex(r"\\sum x_i")`

---

## 🌀 Lorenz Attractor & Custom Plots

### ❌ `odeint` fails or plot crashes

**Fix**:

- Import `numpy`, `scipy.integrate`
- Avoid too many points (`t_vals = np.linspace(0, 40, 10000)` is reasonable)

---

## ⚖️ Riemann Rectangles / Animations

### ❌ Rectangles not showing or slow

**Fix**:

- Ensure all rectangles are added as `VGroup`
- Use `Transform(...)` for animation refinements

---

## 🔍 Debug Tips

- 🤝 Print inside `construct()` to debug logic
- 🔎 Use `.shift(...)`, `.scale(...)` to locate misplaced objects
- ✅ Restart runtime if rendering gets stuck in Colab

---

## 🚪 Still Stuck?

1. Share the exact **code snippet**
2. Include the **full error message**
3. Mention your **platform** (Google Colab / local OS)

Feel free to reach out to @Santhosh-Sathyamurthy and @techclub-iisertpt.

---

Happy Animating! 🎥️
