# Automate-eGPU

Automate-eGPU provides Mac users with an easy way to setup their eGPU on macOS without a hastle. It has been tested with a large range of eGPUs and configurations. It is no longer maintained.

## Features

* Detects eGPU and graphics card
* Downloads and installs NVIDIA or AMD graphics drivers
* Automatically backup and restore built-in drivers

## Usage

### Installing Homebrew and Git
Before you begin, open Terminal and install [Homebrew](https://brew.sh/) and [Git](https://git-scm.com/) with the following commands:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
> Press Return
brew install git
```

Using Git, you can clone the repository with the following command:
```
git clone https://github.com/goalque/automate-eGPU.git
```

For more information on Git commands: https://education.github.com/git-cheat-sheet-education.pdf

### Running Automate-eGPU
Run the following command:
```
sudo ./automate-eGPU.sh [Options]
```

### Options
<table>
<tr>
<td>-a</td><td>Switch on automatic mode</td>
</tr>
<tr>
<td>-m</td><td>Switch off automatic mode (default)</td>
</tr>
<tr>
<td>-url</td><td>Downloads NVIDIA Driver package file from any valid web address</td>
</tr>
<tr>
<td>-clpeak</td><td>OpenCL performance test (http://github.com/krrishnarraj/clpeak)</td>
</tr>
<tr>
<td>-skip-web-driver</td><td>Skip NVIDIA Web Driver installation (for Kepler cards)</td>
</tr>
<tr>
<td>-skip-agdc</td><td>Skip AddBoardId() function</td>
</tr>
<tr>
<td>-uninstall</td><td>Restore original kexts, unload services and delete application support files</td>
</tr>
</table>

The manual [-m] mode does only the minimum initialization in order to use the eGPU and the advanced [-a] mode aims to configure everything automatically in the background.

To determine if your eGPU supports the Metal API:
```
curl -o ~/Desktop/metaltest.swift https://raw.githubusercontent.com/goalque/automate-eGPU/master/metaltest.swift
cd ~/Desktop
swiftc -sdk $(xcrun --show-sdk-path) -target x86_64-apple-macos10.13 -o metaltest metaltest.swift
./metaltest
```
