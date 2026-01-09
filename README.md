# LazyVimInstall

To set up **LazyVim** on Windows 11, follow these steps using PowerShell. This process will install Neovim, the LazyVim starter template, necessary compilers, and required fonts.

---

### 1. Install Neovim and Prerequisites

First, install the Neovim editor and the Git client (if not already installed) to handle the configuration files.

```powershell
winget install Neovim

```

### 2. Clone the LazyVim Starter Template

Navigate to your local app data folder and clone the official starter configuration.

```powershell
cd $env:LOCALAPPDATA
git clone https://github.com/LazyVim/starter nvim

```

### 3. Install NerdFonts

LazyVim requires a NerdFont to display icons correctly. We will use Oh My Posh to manage the font installation.

```powershell
winget install JanDeDobbeleer.OhMyPosh
oh-my-posh font install

```

*> **Note:** After running the command above, select a font like "JetBrainsMono" from the list and update your Terminal settings to use it.*

### 4. Install Compilers and Tools

Install the Zig compiler and the WinLibs environment to ensure plugins like Treesitter can compile parsers.

```powershell
winget install zig.zig
winget install --id=BrechtSanders.WinLibs.POSIX.UCRT -e

```

### 5. Clean Up and Initialize

Remove existing data folders to prevent configuration conflicts and delete the `.git` folder from the starter template so you can initialize your own repository later.

```powershell
rm -Recurse -Force $env:LOCALAPPDATA\nvim-data
cd $env:LOCALAPPDATA\nvim
Remove-Item $env:LOCALAPPDATA\nvim\.git -Recurse -Force

```

### 6. Install Scoop and Helper Utilities

Finally, install [Scoop](https://scoop.sh/) to easily manage CLI utilities like `fd` (for file finding) and `tree-sitter`.

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
scoop install tree-sitter fd

```

---

### Next Steps

Once finished, simply type `nvim` in your terminal. LazyVim will automatically start downloading the rest of its plugins.

Add -command "nvim" to your Powershell desktop shortcut target e.g. C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe -command "nvim" and set the 'Start in' folder to your desired location.
