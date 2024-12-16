# Tp Linux 

```
sudo apt install nginx
````
## Mettre a jour le système
```
sudo apt update && sudo apt upgrade -y
````
## Configurer le pare feu
### installer iptable afin de pouvoir modifier les droits  
```
sudo apt update 
sudo apt install iptable
````
### cette suite de commandes afin de configurer le pare feu 
````
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

sudo iptables -P INPUT DROP (le réactiver si on doit installer qqch j'ai eu le prblm)

sudo iptables -P FORWARD DROP 

sudo iptables -P OUTPUT ACCEPT
````
## Ensuite configurer SSH 
### Changer le port par défaut :
 ### Désactiver l'accès à root par SSH :
###  Activer l'authentification avec une clée publique : 


## Modifier le fichier de configuration SSH :

````
sudo nano /etc/ssh/sshd_config
````
### Une fois dedans modifier ces lignes qui on pour effet 
```
Port 22                        
PermitRootLogin no / yes pour se log en ssh               
PasswordAuthentication no / yes si on veut se log en ssh encore une fois 
```

## installation et configuration de Fail2Ban
```
suo apt install fail2ban -y
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
```
### Configurer fail2ban
```
sudo nano /etc/fail2ban/jail.local
```
## Ensuite modifier le fichier 
````
[sshd]
enabled = true
port = 22
maxretry = 5
bantime = 3600
````
### Ensuite on redémarre fail2ban pour le rendre effectif 
```
sudo systemctl restart fail2ban

(si fail2ban n'est pas actif lors du restart on installe rsyslog puis on redémarre fail2ban)

sudo apt install rsyslog (commande pour install rsyslog)
````
## Configuration de AppArmor 

````
sudo apt install apparmor-utils -y
````
### Ensuite vérfier si il est bien actif 
```
sudo aa-status 
```