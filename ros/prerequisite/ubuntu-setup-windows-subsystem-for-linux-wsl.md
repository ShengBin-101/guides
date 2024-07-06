---
description: In this guide, we are going to setup WSL2 for Ubuntu 22.04 on Windows 11.
---

# 💻 Ubuntu Setup - Windows Subsystem for Linux (WSL)

1. Search on Windows: "Turn Windows Features on or off" and Enable "Windows Subsystem for Linux"

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

2. Restart your Computer
3. Open Powershell and start installing WSL and Ubuntu Distribution of Choice

```
wsl --install
```

To use WSL2 instead of WSL1,

```
wsl --set-default-version 2
```

Since I am using Ubuntu 22.04, for WSL, run the following to set up Ubuntu 22.04 in WSL2,

```
wsl --install Ubuntu-22.04
```

To set Ubuntu 22.04 as the default distribution for WSL2,

```
wsl --set-default Ubuntu-22.04
```

For more info, look here

{% embed url="https://learn.microsoft.com/en-us/windows/wsl/install" %}
