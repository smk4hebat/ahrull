## INSTALL FREERADIUS

1.      sudo apt update


   
2.      sudo apt install freeradius

   
3.      sudo service freeradius start

 
4.      sudo service freeradius status

   
5.      sudo nano /etc/freeradius/users

  
6.      username cleartext-password := "password"

    
7.      radtest username password localhost O testing123

    
8.      radclient -x localhost auth testing123

 
![radius](https://github.com/smk4hebat/ahrull/assets/156273663/268279fc-a8d8-46e1-9147-136ff1b235e1)
