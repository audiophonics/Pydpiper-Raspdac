###PydPiper for RASPDAC

pages_raspdac_16x2.py is made to be used with WINSTAR 16x2 OLED used on the RASPDAC

Many Thanks to dhrone for the amazing work he done.
https://github.com/dhrone/pydPiper


##Download and Install Pydpiper

```
git clone https://github.com/dhrone/pydPiper.git
./install_docker.sh
```

##You can test display with this command :
```
docker run --network=host --privileged -v /var/log:/var/log:rw  -v /home/volumio/pydPiper:/app:rw dhrone/pydpiper:v0.31-alpha python /app/pydPiper.py --volumio --driver winstar_weg --width 80 --height 16 --rs 7 --e 8 --d4 25 --d5 24 --d6 23 --d7 27 --timezone 'Europe/Paris' --temperature celcius --pages pages_raspdac_16x2.py

```

##Service Installation :

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