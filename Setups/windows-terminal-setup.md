# Installasjon av div for Windows Terminal

1. **Install PowerShell with winget (set to default in settings)**
    ```
        winget install --id Microsoft.Powershell --source winget
    ```



2. **Install Oh My Posh**
    ```
        winget install JanDeDobbeleer.OhMyPosh -s winget
    ```
    - Generate a profile file for PowerShell:
    ```powershell
        New-Item -Path $PROFILE -Type File -Force
    ```
    - Open profile file with VSCode: `code .PROFILE` 
    - Set the theme and remember to change the name in the following snippet (example is using montys): 
    ```powershell
        # Initialize Oh-My-Posh with custom theme config
        oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\montys.omp.json" | Invoke-Expression
    ```
    
3. **Set Nerd Font**
    - Download CascadiaCove Nerd Font using `winget`:
    ```powershell
        wget "https://github.com/ryanoasis/nerd-fonts/releases/download/v3.2.1/CascadiaCode.zip" -O "CascadiaCode.zip"
    ```
    - Set the font in **Windows Terminal** in the `settings.json`:
    ```json
        "profiles": 
        {
            "defaults": 
            {
                "colorScheme": "Dark+",
                "font": 
                {
                    "face": "CaskaydiaCove Nerd Font",
                    "size": 12
                }
            },
    ```
    - For **Visual Studio Code** set the following in settings.json:
    Open settings.json by using `CTRL + SHIFT + P` => "Open User Settings (JSON)"
    ```json
        {
            "security.workspace.trust.untrustedFiles": "open",
            "terminal.integrated.fontFamily": "CaskaydiaCove Nerd Font",
            "terminal.integrated.fontSize": 14,
            "editor.fontFamily": "CaskaydiaCove Nerd Font, 'Courier New', monospace"
        }
    ```

4. **Install folder icons**
   Run this in the terminal:
   ```PowerShell
    Install-Module -Name Terminal-Icons -Repository PSGallery
   ```

   Set this line in the PROFILE:
   ```powershell
    Import-Module -Name Terminal-Icons
   ```

   Reload the PROFILE: 
   `. $PROFILE`
   <br>

5. **Install ZLocation**
    ```powershell
        Install-Module ZLocation -Scope CurrentUser; Import-Module ZLocation; Add-Content -Value "`r`n`r`nImport-Module ZLocation`r`n" -Encoding utf8 -Path $PROFILE.CurrentUserAllHosts
    ```

6. **Install Chocolatey** 
    - Start Terminal as **Admin**
    - Check restriction policy: `Set-ExecutionPolicy AllSigned` and change if necessary: `Set-ExecutionPolicy AllSigned`  
    - Install Chocolatey: 
        ```powershell
        Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
        ```