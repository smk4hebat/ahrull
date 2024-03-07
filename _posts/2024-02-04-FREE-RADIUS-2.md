# FREERADIUS 2

## update 

  sudo apt update 

## install aplikasi 

   sudo apt install freeradius 

## cek insalasi 

   sudo systemctl stop freeradius 

   sudo freeradius -X 

## hentikan proses control c

## jalankan servive lagi 

   systemctl enable --now freeradius 

## cek service 

    sudo systemctl start freeradius 

    sudo systemctl status freeradius

## menambah user 

   sudo nano /etc/freeradius/3.0/users

   john CLEARTEXT-password:= "coba1234"

   sudo systemctl start freeradius 

## mengetes

   radtest jophn coba1234 localhost 0 testing123

## menambah client nas mikrotik di freeradius 

   sudo nano /etc/freeradius/3.0/clients.conf

   client mikrotik {
     ipaddr = 192.168.200.1
     secret = testing123
     shortname = mikrotik_client
     nastype = mikrotik
}

## restart 

   sudo systemctl restart freeradius 

   ![allu](https://github.com/smk4hebat/ahrull/assets/156273663/d484b2a1-bdcd-4ad3-9e3b-7773c95d73a1)

   
     
