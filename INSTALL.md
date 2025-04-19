# 🚀 Setting Up Manim

Welcome to **Manim Bootcamp 2025**! This guide helps you install and configure **Manim**, a Python-based animation engine, across different platforms. We’ll also ensure LaTeX support is properly installed so your math equations look sharp in animations.

---

## 🧠 What You Need

- Python ≥ 3.9  
- Pip (Python package manager)  
- Git (optional but useful)  
- A code editor (VS Code recommended)  
- LaTeX environment for rendering math  
- Manim (installed via pip)  

---

## ☁️ Option 1: Running Manim Online (Google Colab)

1. Open [Google Colab](https://colab.research.google.com)  
2. Create a new Python 3 notebook  
3. Run the following setup in a cell:

    ```python
    !sudo apt update
    !sudo apt install libcairo2-dev \
        texlive texlive-latex-extra texlive-fonts-extra \
        texlive-latex-recommended texlive-science \
        tipa libpango1.0-dev
    !pip install manim
    !pip install IPython==8.21.0  # Fixes cell magic compatibility
    ```

4. Now paste and run your Manim code using the `%%manim` magic:

    ```python
    from manim import *

    %%manim -qm -v WARNING HelloManim

    class HelloManim(Scene):
        def construct(self):
            text = Text("Hello, Manim!").scale(1.5)
            self.play(Write(text))
            self.wait(1)
    ```

---

## 💻 Option 2: Local Setup

### 🪟 Windows (with VS Code)

#### 1. Install Python (≥ 3.9)

- Download from [python.org](https://www.python.org/downloads/)  
- Make sure to check **“Add Python to PATH”** during installation

#### 2. Install VS Code

- Get it from [code.visualstudio.com](https://code.visualstudio.com)  
- Install the following VS Code extensions:
  - Python
  - Jupyter
  - LaTeX Workshop (optional for editing `.tex` files)

#### 3. Install Git (Optional)

- From [git-scm.com](https://git-scm.com)

#### 4. Install LaTeX (Full Setup)

Manim needs a LaTeX system to render math. On Windows, install:

- **MiKTeX**: [miktex.org](https://miktex.org)  
- **Strawberry Perl**: [strawberryperl.com](https://strawberryperl.com) (required by MiKTeX for updates)

> 📌 After installing, open MiKTeX Console → Settings → Check “Install missing packages on the fly”

#### 5. Install Manim

Open a terminal (CMD, PowerShell, or VS Code terminal):

```bash
pip install manim
```

To test, create a Python file (`hello.py`) with a Manim scene and run:

```bash
manim -pql hello.py HelloManim
```

---

### 🐧 Ubuntu / Linux

#### 1. Install Python and system dependencies

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
sudo apt install libcairo2-dev libpango1.0-dev ffmpeg
```

#### 2. Install LaTeX

```bash
sudo apt install texlive texlive-latex-extra texlive-fonts-extra texlive-science
```

#### 3. Install Manim

```bash
pip install manim
```

To test, create a `.py` file with a scene and run:

```bash
manim -pql your_script.py SceneName
```

---

### 🍎 macOS

#### 1. Install Homebrew (if not installed)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### 2. Install Python and dependencies

```bash
brew install python
brew install cairo pango ffmpeg
```

#### 3. Install LaTeX

```bash
brew install --cask mactex
```

> 📌 After install: open Terminal and run `sudo tlmgr update --self && sudo tlmgr install standalone` if needed.

#### 4. Install Manim

```bash
pip install manim
```

---

## ✅ Verifying Installation

Run this command to see if Manim is installed:

```bash
manim --version
```

You should see the installed version of Manim, Python, and dependencies.

---

## 🧪 Sample Test

Save this to `hello.py`:

```python
from manim import *

class Hello(Scene):
    def construct(self):
        self.play(Write(Text("It works! 🎉")))
```

Then run:

```bash
manim -pql hello.py Hello
```

You should see a preview window with the animation.

---

## 🧵 Need Help?

Check the [TROUBLESHOOTING.md](./TROUBLESHOOTING.md) for common issues or reach out on PaCODEah Community.
