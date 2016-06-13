# -*- mode: ruby -*-
# vi: set ft=ruby :


# Testado em um host Ubuntu 16.04 x64.

## Versão minima requerida do Vagrant instalado em seu sistema para o correto funcionamento desta VM.
Vagrant.require_version ">= 1.8.1"

## Inicia a configuração usando a versão 2 do Vagrantfile.
Vagrant.configure("2") do |config|
    
	## Nome da Box a ser usada.
	config.vm.box = "e-cogni/xenial64"
	## URL para download da Box.
	config.vm.box_url = "https://github.com/e-cogni/vagrant-ubuntu/releases/download/16.04/ubuntu-xenial64-pt_br.box"
	## Intervalo de portas para redirecionamentos.
	config.vm.usable_port_range = 2800..2900 
	## Tempo limite para estabelecer uma conexão SSH com a VM.
	config.vm.boot_timeout = 600
	## Hostname da VM.
	config.vm.hostname = "xenial64.local"
	## Compartilhamentos via NFS têm um melhor desempenho. Antes de ativar, certifique-se de ter o servidor NFS instalado em seu sistema.
	#config.vm.synced_folder ".", "/vagrant", type: "nfs"
	## Exemplos de configuração de rede
	### Rede publica (bridge). Use apenas se extremamente necessario, pois VMs Vagrant são normalmente inseguras.
	#config.vm.network :public_network, ip: "192.168.0.100", :netmask => "255.255.255.0", bridge: "wlan0", auto_config: true
	### Rede interna (intnet). 
	#config.vm.network :private_network, virtualbox__intnet: "rede_interna", ip: "10.100.0.100", :netmask => "255.255.0.0"
	### Rede apenas para o host (host-only).
	#config.vm.network :private_network, ip: "172.16.0.100", :netmask => "255.255.255.0" 

	## Configurações no SO da VM. Caso seja necessário realizar alguma alteração.
	### Neste exemplo será executado um shell na VM.
	#config.vm.provision "shell",
	### Toda vez que a VM carregar.
    	#run: "always",
	### Pode ser um comando, ou um conjunto de comandos.
	#inline: "(ip route del 0/0 && ip route add 0/0 via 192.168.0.1 dev eth1) || exit 0;"
	### Ou um shell script.
    	#path: "./config-vm.sh"
	### Também é possível usar Ansible, Puppet, etc. para essas configurações.

	## O plugin vagrant-cachier faz cache local da VM e de pacotes do SO, acelerando assim o provisionamento de multiplas VMs.
	#if Vagrant.has_plugin?("vagrant-cachier")
	#	config.cache.scope = :box
	#	config.cache.enable :apt
	#else
	#	puts "[-] ALERTA: O provisionamento de novas VMs ocorrerá mais rápido se você primeiro executar: 'vagrant plugin install vagrant-cachier' "
	#end

	## Exemplos de configurações específicas para o VirtualBox.
	config.vm.provider :virtualbox do |vbox|
		### Define o nome de exibição da VM no VirtualBox.
		vbox.customize ["modifyvm", :id, "--name", "Ubuntu Server 16.04 LTS x64 - pt_BR"]
		### Insere a VM em um grupo.
		vbox.customize ["modifyvm", :id, "--groups", "/Boxes"]
		### Redefine a memória disponível para a VM.
		#vbox.customize ["modifyvm", :id, "--memory", 1024]
		### Redefine a quantidade de CPUs visíveis para a VM.
		#vbox.customize ["modifyvm", :id, "--cpus", 1]
		### Ativa o modo promíscuo para a interface de rede 4.
		#vbox.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
	end
end
