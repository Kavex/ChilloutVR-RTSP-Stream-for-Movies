### Running your own RTSP server

Running a RTSP server with digital ocean ocean is fairly easy but you will need to have some knowledge of [Putty](https://www.putty.org/) and [OBS](https://obsproject.com/download).

These instructions can work on any docker setup but we will be using digtalocean server because they are cheap and easy to setup. 

### Setting up a DigitalOcean server

 1.    Create an account at  [https://www.digitalocean.com/](https://www.digitalocean.com/)
    
 2.   Create a droplet

 - Reference the how to create a droplet guide for more detail [https://docs.digitalocean.com/products/droplets/how-to/create/](https://docs.digitalocean.com/products/droplets/how-to/create/)
   
 - Under the  _Choose an image_  section, choose the  _Marketplace_  tab and select the Docker on Ubuntu option. If that option does not exist search for the "Docker" keyword.
 
 ![enter image description here](https://i.imgur.com/LvzFOlr.png)
![enter image description here](https://i.imgur.com/D1TxiQn.png)

- Under  _Choose a plan_ just choose the cheapest one. If you find yourself streaming to a lot of people then bumping up the plan can't hurt. 

![enter image description here](https://i.imgur.com/87oEByy.png)
- Choose the datecenter closest to yourself. I normally just choose San Francisco.

![enter image description here](https://i.imgur.com/0upPox0.png)
- For authentication if you don't know what SSH Keys are then just use a password

![enter image description here](https://i.imgur.com/kGcE4h4.png)

- Click create droplet and you're done creating the droplet

![enter image description here](https://i.imgur.com/2yXcehm.png)

 3.    Connect using Putty
 - Follow [Connect using Putty](https://docs.digitalocean.com/products/droplets/how-to/connect-with-ssh/putty/) and skip the SSH key section if you're using a password. Your username is  `root`  by default.
  - Click Open to connect and put your password in
  - You should now be connected to your server

### Setting up  [RtspSimpleServer](https://github.com/aler9/rtsp-simple-server)

Paste this command in to Putty to start a basic Rtsp server. You can do more secure setup if you like but you'll have to read the main page for the rtsp simple server.
```
docker run --rm -it -e RTSP_PROTOCOLS=tcp -p 8554:8554 -p 1935:1935 aler9/rtsp-simple-server
```
In OBS you will set the streaming server to custom and in the server type: rtmp://YourDigitalOceansIP with the Key being anything you want.

![enter image description here](https://i.imgur.com/HekiBVj.png)

Once you start streaming your desktop then in the Video Player in ChilloutVR you can using rtsp url which will looks something like this.

**rtsp://YourDigitalOceansIP:8554/MyKey**
