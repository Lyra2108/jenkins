Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "public_network"

  config.vm.provider "virtualbox" do |v|
    v.name = "Jenkins"
    v.memory = 4096
    v.cpus = 2
  end

  config.vm.provision "docker" do |d|
    d.build_image "/vagrant/Jenkins",
      args: "-t jenkins:local"
    d.run "jenkins", 
      image: "jenkins:local",
      args: "-v jenkins_home:/var/jenkins_home -p 8080:8080 -p 50000:50000"
  end
end
