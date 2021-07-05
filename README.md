# audio
Vagrantfile to set up a quick and easy Kubuntu desktop environment with audio capabilities

## What is this for?

Suppose you are teaching students some kind of computing and you use VMs to ensure a reproducible environment. Normally you would interact with environment through SSH or maybe through browser-based admin portal. But maybe you decide some or all the students are better off starting with an interface that resembles a local desktop environment. 

In that case, you can install a lightweight desktop GUI (in this case KDE) and have Virtualbox run in GUI mode. This Vagrantfile helps you do that, creating an Ubuntu 18 machine and installing:

- KDE Desktop
- Chrome
- Visual Studio Code
- Audacity

## How to use it?

Download Vagrant and Virtualbox, using directions appropriate for your OS. Make sure to install the vagrant vbguest plugin to keep Guest Additions up to date. Then clone this repository and run. You need to reload for the desktop GUI to be available.

```bash
    > git clone https://github.com/garcias/audio.git audio
    > cd audio
    > vagrant up
```

## Other uses

The script will also install Wine. 
