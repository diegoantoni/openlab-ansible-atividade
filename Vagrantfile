# -*- mode: ruby -*-
# vi: set ft=ruby :

vms = {
    'wordpress' => {'memory' => '1024', 'cpus' => 2, 'ip' => '50', 'box' => 'almalinux/8', 'provision' => 'provisionamento/wordpress.yaml'}
    #'wordpress' => {'memory' => '1024', 'cpus' => 2, 'ip' => '60', 'box' => 'almalinux/8','provision' => 'provisionamento/worpress.yaml'}
  }
  
  Vagrant.configure('2') do |config|
  
    config.vm.box_check_update = false
  
          if !(File.exists?('id_rsa'))
            system("ssh-keygen -b 2048 -t rsa -f id_rsa -q -N ''")
         end
  
    vms.each do |name, conf|
      config.vm.define "#{name}" do |k|
        k.vm.box = "#{conf['box']}"
        k.vm.hostname = "#{name}.atividade.example"
        k.vm.network 'private_network', ip: "192.168.56.#{conf['ip']}"
        k.vm.provider 'virtualbox' do |vb|
          vb.customize ["modifyvm", :id, "--groups", "/Ansible"]
          vb.name = conf["name"]
          vb.memory = conf['memory']
          vb.cpus = conf['cpus']
          
        end
        k.vm.provision "ansible_local" do |ansible|
          ansible.playbook = "#{conf['provision']}"
        end
    end
  
    config.vm.provision "shell", inline: <<-SHELL
    sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
    systemctl restart sshd
    mkdir -p /root/.ssh
    cp /vagrant/keys/id_rsa /root/.ssh/id_rsa
    cp /vagrant/keys/id_rsa.pub /root/.ssh/authorized_keys
    chmod 600 /root/.ssh/id_rsa
    dnf -y install epel-release
    dnf -y install ansible-core
    SHELL
  
    end
  end
