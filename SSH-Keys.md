# SSH Keys

###1. Create RSA encrypted SSH Keys

    ssh-keygen -t rsa 

(hit Return three times to accept location and to not add a key passphrase)

###2. (If you have ssh-copy-id installed) Copy Public Key File To Each Server To Which The User Will Connect

    ssh-copy-id <userpid>@<servername>

###2. (If you don't have ssh-copy-id installed) Copy Public Key File To Each Server To Which The User Will Connect

    cat ~/.ssh/id_rsa.pub | ssh <userpid>@servername "mkdir -p ~/.ssh && cat >>  ~/.ssh/authorized_keys"

//At this point the user will be able to ssh to the server without a password (e.g. “ssh aschroed@snowmane.vbi.vt.edu”)//

###3. Logoff of the Server

    exit

###4. Create/Edit user SSH config file

    nano ~/.ssh/config

with content:

    host snowmane
    HostName snowmane.vbi.vt.edu
    User <userpid>
    IdentityFile ~/.ssh/id_rsa
   
    host gimli
    HostName gimli.vbi.vt.edu
    User <userpid>
    IdentityFile ~/.ssh/id_rsa

//At this point the user will be able to ssh to a server without needing to enter a password or the full name of the server (e.g. “ssh snowmane”)//