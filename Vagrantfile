# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/bionic64"
  config.vm.provider :virtualbox do |v|
    v.name = "kubuntu"
    v.memory = 4096
    v.gui = true
    v.customize ["modifyvm", :id, '--audio', 'coreaudio', '--audiocontroller', 'hda', '--audioout', 'on', "--vram", "64"]
    v.customize ["storageattach", :id, "--storagectl", "IDE", "--port", "0", "--device", "1", "--type", "dvddrive", "--medium", "emptydrive"]
  end
  
  # On host, install guest additions manager before provisioning: 
  #   vagrant plugin install vagrant-vbguest
  #   vagrant vbguest --do install

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    sudo apt-get update -qq
    sudo apt-get install -y dkms
    # Install audio drivers
    wget -O oem-audio.deb http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu/pool/main/o/oem-audio-hda-daily-dkms/oem-audio-hda-daily-dkms_0.201905191531~ubuntu18.04.1_all.deb
    sudo dpkg -i oem-audio.deb
    sudo apt install -y alsa-utils
    # Install desktop
    sudo apt install -y kde-standard
    # Add Chrome and VS Code to APT sources
    wget -q -O - https://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
    sudo sh -c 'echo "deb https://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
    curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
    sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
    sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
    # Install applications
    sudo apt update -qq
    sudo apt install -y -f google-chrome-stable code 
    
    # afterward use change password used for installing new software
    #   sudo passwd ubuntu
    SHELL
    
end

# References;
# https://github.com/naomiaro/vagrant-alsa-audio
