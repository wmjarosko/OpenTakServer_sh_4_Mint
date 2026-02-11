# OpenTakServer_sh_4_Mint
OpenTakServer install modifications for Linux Mint 22.1

Download the script, make it executable;
chmod +x Mint_22.1_installer.sh

Execute the script
./Mint_22.1_installer.sh



Two issues I've found during testing;
1) If any packages complain about xia for whatever reason, exit the script and change the /etc/apt/sources.list.d/docker.list

"sudo nano /etc/apt/sources.list.d/docker.list"

 From;  https://download.docker.com/linux/ubuntu xia stable
 
 To; https://download.docker.com/linux/ubuntu noble stable
 
  crtl +O
  crtl +X
  
  rerun the script

2) If the script complains that the config.yml file already exists but it does not know what the 
ots user password is open a new terminal, set a password for the 'ots' user in postgress.  


  sudo -u postgres psql -c "\\du"   #verify the ots user role exists
  
  sudo -u postgres psql   #login to postgress to make changes
  
  ALTER ROLE ots WITH LOGIN PASSWORD 'your new password';
  
  \q  #quit sql session 

Then return to the script and use the same password you just set.

That's it.
  

