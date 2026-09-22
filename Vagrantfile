# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  ### NODO PROMETHEUS
  config.vm.define "prometheus" do |prom|
    prom.vm.box = "generic/rhel9"
    prom.vm.hostname = "prometheus-server"
    prom.vm.network "private_network", ip: "192.168.75.15"
    #Defino recursos del nodo
    prom.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 2
    end
  end
  ### NODO GRAFANA
  config.vm.define "grafana" do |graf|
    graf.vm.box = "generic/rhel9"
    graf.vm.hostname = "grafana-server"
    graf.vm.network "private_network", ip: "192.168.75.16"
    #Defino recursos del nodo
    graf.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus = 2
    end
  end
end
