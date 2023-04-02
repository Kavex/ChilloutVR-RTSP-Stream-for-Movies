### Running your own RTSP server

Running a RTSP server with digital ocean ocean is fairly easy but you will need to have some knowledge of [Putty](https://www.putty.org/) and [OBS](https://obsproject.com/download).

These instructions can work on any docker setup but we will be using digtalocean server because they are cheap and easy to setup. 

### Setting up a DigitalOcean server

 1.    Create an account at  [https://www.digitalocean.com/](https://www.digitalocean.com/)
    
 2.   Create a droplet
 - Reference the how to create a droplet guide for more detail
   [https://docs.digitalocean.com/products/droplets/how-to/create/](https://docs.digitalocean.com/products/droplets/how-to/create/)
 - Under the  _Choose an image_  section, choose the  _Marketplace_  tab and select the Docker on Ubuntu option. If that option does not exist search for the "Docker" keyword.
- Under  _Choose a plan_  you will need to choose appropriate specs for the PC. If you're just streaming to couple of people, a basic shared CPU can work. If you're streaming to more people I'd recommend choosing the cheapest CPU Optimized instance.
- Choose a datacenter that is close to your location
- For authentication if you don't know what SSH Keys are then just use a password
- Click create droplet and you're done creating the droplet

    
 3.    Connect using Putty
 - Follow [Connect using Putty](https://docs.digitalocean.com/products/droplets/how-to/connect-with-ssh/putty/) and skip the SSH key section if you're using a password. Your username is  `root`  by default.
  - Click Open to connect and put your password in
  - You should now be connected to your server

### Setting up  [RtspSimpleServer](https://github.com/aler9/rtsp-simple-server)

Paste this command in to Putty to start a basic Rtsp server. You can do more secure setup if you like but you'll have to read the main page for the rtsp simple server.
```
docker run --rm -it -e RTSP_PROTOCOLS=tcp -p 8554:8554 -p 1935:1935 aler9/rtsp-simple-server
```
In OBS you will set the streaming server to custom and in the server type: rtmp://YourDigitalOceansIP with they Key being anything you want.

![enter image description here](https://i.imgur.com/HekiBVj.png)

Once you start streaming your desktop then in the Video Player in ChilloutVR you can using rtsp url which will looks something like this.

**rtsp://YourDigitalOceansIP:8554/MyKey**
