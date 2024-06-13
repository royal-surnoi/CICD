```
# Setup Hostname
sudo hostnamectl set-hostname "jenkins.cloudbinary.io"

# Update the hostname part of Host File
echo "`hostname -I | awk '{ print $1 }'` `hostname`" >> /etc/hosts
```