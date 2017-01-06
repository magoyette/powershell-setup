# powershell-setup

My personal PowerShell setup. Used with Windows 7.

PowerShell is executed with ConEmu as a console emulator.

## Requirements

- Git must be on the Windows path for posh-git
- PowerShell version 3 or greater. The version can be checked with $PSVersionTable.PSVersion
- Windows 7 SP 1 or greater
- [Chocolatey](https://chocolatey.org) is used to install Jump-Location, since the installation fails with PowerShellGet

## Set the Execution Policy

Open a PowerShell prompt as an administrator and run the following command.

``` powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Confirm
```

## PowerShellGet

Install [PowerShellGet](https://www.microsoft.com/en-us/download/details.aspx?id=49186). It will be used to install PSReadLine and posh-git.

PowerShellGet is included by default in Windows 10.

## PSReadLine

[PSReadLine](https://github.com/lzybkr/PSReadLine) improves a lot PowerShell.

PSReadLine is included by default in Windows 10.

``` powershell
Install-Module PSReadline
```

Add to the PowerShell profile the following lines.

``` powershell
if ($host.Name -eq 'ConsoleHost')
{
    Import-Module PSReadline
}
```

## posh-git

[posh-git](https://github.com/dahlbyk/posh-git) add Git integration to PowerShell.

``` powershell
Install-Module posh-git -Scope CurrentUser
```

Add to the PowerShell profile the following line.

``` powershell
Import-Module $PSScriptRoot\Modules\posh-git\profile.example.ps1
```

## Chocolatey

Install [Chocolatey](https://chocolatey.org). Chocolatey is used to install Jump-Location, since its installation with PowerShellGet fails with an error.

## Jump-Location

[Jump-Location](https://github.com/tkellogg/Jump-Location) adds a j command that works like a cd that memorize previously visited folders.

``` powershell
choco install Jump-Location
```

The Chocolatey installation will add the Import-Module line in the PowerShell profile.

## ConEmu

ConEmu is a console emulator that has a lot of features not supported by the PowerShell console.

### Install ConEmu

- Download the [ConEmu](https://conemu.github.io/) portable application.
- Unzip the ConEmu archive in C:\dev\apps
- Start ConEmu64.exe
- On the ConEmu fast configuration window:
    - Set statup task to {Shells::PowerShell}.
    - Set preferred color scheme to "<Solarized>". The theme will be changed later, but the theme change is necessary to generate a node in the XML.
    - Check "Quake-style slide down from the top of the screen" and set the keybinding to "Win+Alt+Z". That global keybinding allows to display/hide ConEmu with a slide down animation.
- Maximize the ConEmu window

### Configure ConEmu Settings

Open ConEmu Settings.

#### Main

- Set the "Main console font" to "DejaVu Sans Mono" with a "Size" of 16.
- Set the "Alternative font" to "DejaVu Sans Mono".

#### Startup > Tasks

- Select {Shells::PowerShell}
    - Click on the "Startup dir..." button and select "C:\"

#### Features > Colors

- Install the "Solarized Dark" theme from [ConEmu-Color-Themes](https://github.com/joonro/ConEmu-Color-Themes/blob/master/solarized-dark.xml). That "Solarized Dark" theme uses grey for regular text instead of white, unlike the Solarized themes bundled with ConEmu.
- Select in "Schemes" the "Solarized Dark" theme.
