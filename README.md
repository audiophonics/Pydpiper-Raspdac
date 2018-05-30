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
wget https://raw.githubusercontent.com/audiophonics/Pydpiper-Raspdac/master/pydPiper.cfg
wget https://raw.githubusercontent.com/audiophonics/Pydpiper-Raspdac/master/pages_raspdac_16x2.py
```

## You can test display with this command :

Take care to replace directory with the one where PydPiper is located
```
sudo docker run --network=host --privileged -v /var/log:/var/log:rw -v /home/volumio/pydPiper:/app:rw dhrone/pydpiper:v0.31-alpha python /app/pydPiper.py
```

## Service Installation :

```
wget https://raw.githubusercontent.com/audiophonics/Pydpiper-Raspdac/master/pydpiper.service
```

Then activate service :
```
sudo cp pydpiper.service /etc/systemd/system
sudo systemctl enable pydpiper
sudo systemctl start pydpiper
```


For other software than Volumio, you will have to run the ./install_volumio.sh that launch configure.py script.
It's allowing to use LMS, Moode, Rune, or MPD music info sources.
