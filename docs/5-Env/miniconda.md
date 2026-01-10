# Miniconda

## 1. What Is Miniconda?

**Miniconda** is a **lightweight distribution of Conda**, a popular package and environment manager for Python (and other languages).

Think of it like this:

-   **Anaconda** = Python + Conda + *hundreds of preinstalled packages*
-   **Miniconda** = Python + Conda + *almost nothing else*

You install **only what you need**, when you need it.

### Why Miniconda?

✅ Small installation size

✅ Clean environment

✅ Full control over packages

✅ Ideal for learning, servers, and developers

## 2. What Is Conda?

Before continuing, it helps to understand **Conda**.

Conda is:

-   A **package manager** (like `pip`)
-   An **environment manager**

With Conda, you can:

-   Install packages
-   Create isolated Python environments
-   Switch between Python versions easily

## 3. Miniconda vs Anaconda

| Feature               | Miniconda | Anaconda |
| --------------------- | --------- | -------- |
| Installer **size**    | ~50 MB    | ~500+ MB |
| Preinstalled packages | Very few  | Hundreds |
| Environment control   | Full      | Full     |
| Beginner friendly     | ✅ Yes     | ✅ Yes    |
| Recommended           | ⭐⭐⭐⭐⭐     | ⭐⭐⭐      |

👉 **For beginners who want to learn cleanly, Miniconda is recommended.**

## 4. Installing Miniconda

### 4.1 Download Miniconda

Go to the official website:

👉 https://docs.conda.io/en/latest/miniconda.html

Choose:

-   **Python 3.x**
-   Your operating system:
    -   Windows (x86_64)
    -   macOS (Intel / Apple Silicon)
    -   Linux (x86_64)

### 4.2 Install on macOS / Linux

Example (macOS / Linux):

```bash
bash Miniconda3-latest-MacOSX-x86_64.sh
```

During installation:

-   Press `Enter` to read the license

-   Type `yes` to accept

-   Choose the install location (default is fine)

-   When asked:

    ```
    Do you wish the installer to initialize Miniconda3 by running conda init?
    ```

    👉 Type **yes**

Restart your terminal after installation.

### 4.3 Install on Windows

1.  Double-click the installer `.exe`
2.  Choose:
    -   Just Me
    -   Add Miniconda to PATH ❌ (recommended to leave unchecked)
3.  Finish installation
4.  Open **Anaconda Prompt**

## 5. Verify Installation

Open a terminal and run:

```bash
conda --version
```

Example output:

```
conda 24.x.x
```

Check Python:

```bash
python --version
```

## 6. Understanding Conda Environments

### What Is an Environment?

A **Conda environment** is an isolated Python workspace:

-   Independent Python version
-   Independent packages
-   No conflicts with other projects

Example:

-   Project A → Python 3.8
-   Project B → Python 3.11

## 7. Basic Conda Commands

### 7.1 Update Conda

```bash
conda update conda
```

### 7.2 Create an Environment

```bash
conda create -n myenv python=3.11
```

-   `-n` - **n**ame
-   `myenv` → environment name
-   `python=3.11` → Python version

### 7.3 Activate an Environment

```bash
conda activate myenv
```

Your prompt will change:

```text
(myenv) $
```

### 7.4 Deactivate an Environment

```bash
conda deactivate
```

### 7.5 List Environments

```bash
conda env list
```

## 8. Installing Packages

### 8.1 Install a Package

```bash
conda install numpy
```

Conda will automatically resolve dependencies.

### 8.2 Install Multiple Packages

```bash
conda install numpy pandas matplotlib
```

### 8.3 Use pip inside Conda (when needed)

```bash
pip install requests
```

👉 Best practice:

-   Prefer `conda install`
-   Use `pip` only if Conda does not have the package

## 9. Removing Packages and Environments

### Remove a Package

```bash
conda remove numpy
```

### Remove an Environment

```bash
conda remove -n myenv --all
```

## 10. Common Beginner Tips

### 10.1 Do NOT Work in `base` Environment

The `base` environment is for Conda itself.

❌ Bad:

```bash
(base) pip install something
```

✅ Good:

```bash
conda create -n project1 python=3.11
conda activate project1
```

### 10.2 Disable Auto-Activation of `base`

```bash
conda config --set auto_activate_base false
```

Restart terminal.

### 10.3 Check Installed Packages

```bash
conda list
```

## 11. Typical Workflow Example

```bash
# create environment
conda create -n data python=3.10

# activate
conda activate data

# install packages
conda install numpy pandas matplotlib

# work on project
python

# leave environment
conda deactivate
```

## 12. When Should You Use Miniconda?

Miniconda is perfect if you:

-   Want clean Python environments
-   Use multiple projects
-   Care about dependency conflicts
-   Work on servers or Raspberry Pi
-   Prefer minimal setups

## 13. Summary

-   Miniconda = lightweight Conda + Python
-   Conda manages packages and environments
-   Always create environments
-   Avoid using `base`
-   Install only what you need