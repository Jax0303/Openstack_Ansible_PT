Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  
  config.vm.define "tnode1" do |node|
    node.vm.network "private_network", ip: "172.31.232.211"
    
    # SSH 설정
    node.vm.provision "shell", inline: <<-SHELL
      sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/' /etc/ssh/sshd_config
      systemctl restart sshd
    SHELL
  end
end 