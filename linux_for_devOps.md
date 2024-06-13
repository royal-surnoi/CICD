### access the instance with username and password

- set up password for root 
- enable password authentication in sshd configuration the file location /etc/ssh/
- restart sshd service

### passwordless authentication 
- master create sshkey 
  - ssh-keygen
  - we will get public and private keys
  - copy public key and paste it in target-server's 'authorized_keys' file and provide excutable permissions to
    files in target server 
  - then we can other server 
    ssh <username>@<public_IP>

### Labs
<img src="/home/lenovo/Desktop/Learning/Udemy/CICD/pictures/Screenshot from 2024-05-29 06-30-07.png">

end user connect remote servers by same name user , which is created on both the servers
- create user on both servers and connect with end user 
- for example if we create user on the server , we can't connect server based on created user initially, because public is not available in create users home directory , so that we need take public_key from default users (home directory .ssh folder) and paste it on created user home directory (.ssh/authorized_keys).then we can get connect.

- private is with us .pem 

provide passwordless authentication between remote servers
- create ssh keys and copy the public-key and paste it on remote server's authorized_keys file. similar process viseversa to the another remote server too 
- to create ssh keys by using command
  'ssh-keygen'