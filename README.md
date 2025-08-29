# Linux
Vagrant_Linux서버_구성
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "lu.mzclab.kr" do |cfg|
    cfg.vm.box="generic/ubuntu2004"
    cfg.vm.provider "vmware_desktop" do |v|
      v.gui = true
      v.linked_clone = false
      v.whitelist_verified = true 
      v.vmx["memsize"] = "4096"
      v.vmx["memvcpus"] = "2"
    end
    cfg.vm.host_name = "lu.mzclab.kr"
    cfg.vm.network "private_network", ip: "192.168.65.99"
    cfg.vm.network "forwarded_port", guest:22, host:60010, auto_correct:true, id:"ssh"
  end
  config.vm.define "lr.mzclab.kr" do |cfg|
    cfg.vm.box="generic/rocky9"
    cfg.vm.provider "vmware_desktop" do |v|
      v.gui = true
      v.linked_clone = false
      v.whitelist_verified = true 
      v.vmx["memsize"] = "4096"
      v.vmx["memvcpus"] = "2"
    end
    cfg.vm.host_name = "lr.mzclab.kr"
    cfg.vm.network "private_network", ip: "192.168.65.98"
    cfg.vm.network "forwarded_port", guest:22, host:60011, auto_correct:true, id:"ssh"
  end
end
