Creating private key pair | git bash

1. Generate a public key
   => ssh-keygen -t rsa
2. To copy the public ssh key
   => cat ~/.ssh/id_rsa.pub
3. To push the ssh key to the server
   => ssh-copy-id root@ipAddress
