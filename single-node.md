# Single Node Vagrantfile

This repository contains a basic `Vagrantfile` that provisions a single virtual machine named **node1**.  
It’s designed for easy modification and can be expanded to include multiple nodes.

---

## Features

- ✅ Preconfigured for a single node (`node1`)
- 🔄 Easily change CPU, RAM, box name, or provider settings
- 🌐 Choose between **public** or **private** network types

---

##  Vagrantfile Overview

```ruby
Vagrant.configure("2") do |config|
  # Disable default synced folder to avoid vboxsf mount error
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # ---------------- NODE 1 ----------------
  config.vm.define "node1" do |node|
    node.vm.box = "debian12-template" # or koalephant/debian12, bento/rockylinux-9.5
    node.vm.hostname = "node1"

    # Choose one of the following networks:
    # node.vm.network "public_network", ip: "192.168.1.180", bridge: "en0: Wi-Fi (Wireless)", auto_config: true
    # node.vm.network "private_network", ip: "192.168.56.180"

    node.vm.provider "virtualbox" do |vb|
      vb.name = "node1"
      vb.memory = 1024
      vb.cpus = 1
    end

    node.vm.provision "shell", inline: <<-SHELL
      echo "✅ node is up and running!"
    SHELL
  end

  # 💡 Copy & paste more nodes below using the same format

end
```

---

## 📌 License

This project is licensed under the MIT License.