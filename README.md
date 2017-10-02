# Automate-eGPU

Automate-eGPU provides Mac users with an easy way to setup their eGPU on macOS without a hastle. It has been tested with a large range of eGPUs and configurations. It is no longer maintained.

## Features

* Detects eGPU and graphics card
* Downloads and installs NVIDIA or AMD graphics drivers
* Automatically backup and restore built-in drivers

## Usage

### Downloading Automate-eGPU

You can download Automate-eGPU with the following command:
```bash
cd ~/Desktop && curl -o automate-eGPU.sh  https://raw.githubusercontent.com/goalque/automate-eGPU/master/automate-eGPU.sh
```

Alternatively, you can download and install [Homebrew](https://brew.sh/) and [Git](https://git-scm.com/), then clone the repository with the following commands:
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
> Press Return
brew install git
git clone https://github.com/goalque/automate-eGPU.git
```

For more information on Git commands: https://education.github.com/git-cheat-sheet-education.pdf

### Running Automate-eGPU
For Mac OS X El Capitan 10.11 or higher, you need to disable [System Integrity Protection](https://support.apple.com/en-us/HT204899) with the following instructions:

1. Click the  menu. 
2. Select Restart... 
3. Hold down command-R to boot into the Recovery System. 
4. Click the Utilities menu and select Terminal. 
5. Type `csrutil disable` and press return. 
6. Close the Terminal app. 
7. Click the  menu and select Restart...

Run the following command to setup your eGPU:
```bash
chmod +x automate-eGPU.sh && sudo ./automate-eGPU.sh
```

### Options
Use any of the following options after
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

### To determine if your eGPU supports the Metal API:
```
curl -o ~/Desktop/metaltest.swift https://raw.githubusercontent.com/goalque/automate-eGPU/master/metaltest.swift
cd ~/Desktop
swiftc -sdk $(xcrun --show-sdk-path) -target x86_64-apple-macos10.13 -o metaltest metaltest.swift
./metaltest
```
