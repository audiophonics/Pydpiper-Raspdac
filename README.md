### PydPiper for RASPDAC

pages_raspdac_16x2.py is made to be used with WINSTAR 16x2 OLED used on the RASPDAC and Volumio2

Many Thanks to Dhrone for the amazing work he done.

https://github.com/dhrone/pydPiper


## Download and Install Pydpiper

```
cd /home/volumio (for example)
git clone https://github.com/dhrone/pydPiper.git
cd pydPiper
./install_docker.sh
wget https://raw.githubusercontent.com/audiophonics/Pydpiper-Raspdac/master/pages_raspdac_16x2.py
```

## You can test display with this command :

Take care to replace directory with the one where PydPiper is located
```
docker run --network=host --privileged -v /var/log:/var/log:rw  -v /home/volumio/pydPiper:/app:rw dhrone/pydpiper:v0.31-alpha python /app/pydPiper.py --volumio --driver winstar_weg --width 80 --height 16 --rs 7 --e 8 --d4 25 --d5 24 --d6 23 --d7 27 --timezone 'Europe/Paris' --temperature celcius --pages pages_raspdac_16x2.py

```

## Service Installation :

```
nano pydpiper.service
```

Add this line :
```
ExecStart=/usr/bin/docker run --network=host --privileged -v /var/log:/var/log:rw  -v /home/volumio/pydPiper:/app:rw dhrone/pydpiper:v0.31-alpha python /app/pydPiper.py --volumio --driver winstar_weg --width 80 --height 16 --rs 7 --e 8 --d4 25 --d5 24 --d6 23 --d7 27 --timezone 'Europe/Paris' --temperature celcius --pages pages_raspdac_16x2.py
```

Then activate service :
```
sudo cp pydpiper.service /etc/systemd/system
sudo systemctl enable pydpiper
sudo systemctl start pydpiper
```


Pour afficher les infos depuis un serveur LMS la ligne de commande du service serait : 
```
docker run --network=host --privileged -v /var/log:/var/log:rw  -v /home/volumio/pydPiper:/app:rw dhrone/pydpiper:v0.31-alpha python /app/pydPiper.py --lms --lmsplayer b8:27:eb:e4:52:6d --driver winstar_weg --width 80 --height 16 --rs 7 --e 8 --d4 25 --d5 24 --d6 23 --d7 27 --timezone 'Europe/Paris' --temperature celcius --pages pages_raspdac_16x2.py
```

En remplacant l'adresse MAC par celle de votre platine (--lmsplayer)
