# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"

  config.vm.network "forwarded_port", guest: 8080, host:80

  config.vm.network "private_network", ip: "192.168.33.21"

  config.vm.synced_folder "./", "/vagrant"

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
 
    vb.memory = "4096"

    vb.customize [
      "modifyvm", :id,
      "--vram", "256", #ビデオメモリ確保（フルスクリーンモードにするため）
      "--clipboard", "bidirectional", #クリップボードの共有
      "--draganddrop", "bidirectional", #ドラッグアンドドロップ可能に
      "--cpus", "2", #CPUは２つ
      "--ioapic", "on" #I/O APICを有効化
    ]
  end

  config.vm.provision :docker, run: "always"
end
