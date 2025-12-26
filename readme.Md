### Jenkins Setup

Partition the disk  
<!-- Increase the disk size for both master and agents , 3rd extend is not required for node or agent-->
...
growpart /dev/nvme0n1 4

lvextend -L +10G /dev/mapper/RootVG-varVol
lvextend -L +10G /dev/mapper/RootVG-rootVol
lvextend -l +100%FREE /dev/mapper/RootVG-homeVol

xfs_growfs /
xfs_growfs /var
xfs_growfs /home
...


Installation commands from Jenkins official doc
Below is for master , for agent java is enough to install
...
sudo curl -o /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
# Add required dependencies for the jenkins package
sudo yum install fontconfig java-21-openjdk -y
sudo yum install jenkins -y
sudo systemctl daemon-reload
sudo systemctl start jenkins
sudo systemctl enable jenkins
...

### Install Plugins
...
stage view plugin
...