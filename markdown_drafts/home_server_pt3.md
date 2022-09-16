This is part two of my home server post. Read the other parts before this post.

# Setting up services

After I had my operating system picked out and installed, I had to set up the actual software I would run on the server. I'll quickly go over some of the process for each service I run.

## Nextcloud

To make installing Nextcloud easy, I looked for something between a dedicated OS like NextcloudPI, and setting it up from scratch with nginx, sqlite, and php. I settled on running the [Nextcloud snap](https://github.com/nextcloud-snap/nextcloud-snap), which only took a couple of commands to get up and running. Because it is a snap, it is completely self contained and trivial to setup. After initial setup I had to allow it access to external drives, setup https, and configure Nextcloud through the web interface.

## Yacht

To install my other services, I turned to a technology I had not used before; [Docker](https://www.docker.com/). Docker is a way to run applications in their own confined environments, making setup and running multiple services easier than trying to install everything manually where they can interfere with each other. Because I had no experience with Docker, I used [Yacht](https://yacht.sh/) to easily manage my applications in a nice graphical user interface.

## Jellyfin

Jellyfin is a self hosted media streaming platform. It allows you to stream your music and movie files anywhere. I find it handy to listen to my music library from wherever I happen to be, and watch select videos I ripped from DVD's. It also has some nice features, including a watch party option to watch movies with friends remotely.

To set it up I followed the instructions on the website to setup a new docker container. I wanted to share media between Jellyfin and Nextcloud without needing to create duplicate files in different places, so I created shared central folder for my media which I gave access to Jellyfin to through Docker volume configuration, and Nextcloud through the external media addon. Now I view and manage my files in Nextcloud, and stream them through Jellyfin.

## Pi-Hole

Despite the name, [Pi-Hole](https://pi-hole.net/) does not have to be run on a Raspberry Pi. Pi-Hole is a DNS server that filters DNS traffic before forwarding it to a public upstream provider. DNS is the service that translates human readable domain names, such as https://google.com, to computer routable IP addresses. When Pi-Hole acts as your DNS server, it can be configured to block certain connections to websites by simply redirecting the domain names to an empty IP address. This allows Pi-Hole to block ads, trackers, and any other website connections that you desire. I also use it to create my own DNS entry locally, allowing me to access my server on my local network and Tailscale network as octo.pi instead of the full IP address.

Pi-Hole was also just a docker container, but it has some more setup that I'll talk about shortly.

## Cockpit

Cockpit is remote management software built into Fedora Server. It allows you to manage firewall settings, running processes, systemd services, monitor system performance and resources, and even create a remote terminal connection. It is an incredibly useful tool, and comes setup out of the box. You simply need to access it from a web browser.

## Flame Dashboard

All of these services, and some more that I did not talk about, each run on their own network port. To access a service running at port 678, you would need to type octo.pi:678. It can get hard to remember all these arbitrary numbers as the ports in use start building up. This is where [Flame Dashboard ](https://github.com/pawelmalak/flame)comes in. Installed via a Docker container, Flame provides a simple dashboard which you can use to link to all the other services that you run. It acts as a singular place to access the entirety of your server, only requiring you to remember one port number (port 80 for http or 443 for https are used by default in browsers, so if you chose either of those ports you won't have to specify the port at all).

**Insert flame dashboard photo**

## Tailscale

All of these services by default are only confined to your local network for security reasons. You don't want to expose services to the open network if at all avoidable. Doing so can create security risks for even the most secure servers. To avoid allowing public access to all of these services, I found a tool named [Tailscale](https://tailscale.com/) to provide a different solution. Tailscale contains elements of a VPN, but contains differences too. VPN's have been popularized lately as a privacy tool, but that ability is actually a small part of what a VPN actually is. 

VPN stands for Virtual Private Network, and does exactly what it says. It allows you to securely connect to a private network without exposing it to the public internet. It works by creating an encrypted tunnel from your device on the internet, to a local network. Anyone on the internet cannot access this secure tunnel. It has many uses, including some privacy uses. By sending your data through a tunnel in this way, you prevent others from viewing your data. The thing that VPN companies leave out, however, is that the end of the tunnel ends at their servers by necessity, so you are essentially entrusting one company with all your data in order to keep any other random person from accessing it. VPN's only even prevent metadata, (essentially data about your data such as sender, recipient, time, etc.) from being transmitted publicly. As long as you are using a website with https, your traffic is already encrypted as it travels over the internet.

That aside, the reason I would want to use a VPN, is to securely access my server at home, without exposing it to the internet. This is a very secure method to do so, and is actually the standard practice used by businesses when employees need remote access to the company's servers. When I started looking for VPN's, however I found an interesting new technology called Tailscale.

Tailscale is an interesting new take on a VPN. It is a service that uses traditional VPN technologies to create a new way to access remote resources securely. It creates a system of computers, and facilitates direct communication between them. Instead of connecting your computer to a whole central network, you can create connections between multiple computers on different networks, and access them as if they were a part of a single local network. Direct connections provide lower latency connections between devices, and it has many advanced features that make it appealing. First of all, unlike most VPN's, which need to be publicly exposed to the internet to allow the encrypted tunnels to be established, Tailscale does not; It can interact with devices through firewalls. Tailscale also provides advanced DNS settings for the devices on the network, allowing me to use Pi-Hole running on my server at home, to provide DNS to my phone wherever I go. It also allows any device I connect to my Tailscale network to access my server quickly and securely. It differs from a traditional VPN, however, because not all traffic is routed through some central network. Tailscale only connects devices together when specifically requested, like when you type in the URL to your server at home. This means that all your other connections go through the internet, which does make it less of a technology for complete privacy by routing all of your data through a single point.

Tailscale has a generous free plan, and works great connecting my devices to my server wherever I go.

## Closing Thoughts

It has taken me a long time to get my server to where it is now, and even now I am still continuing to improve it. But as of right now it has been stable for multiple months now, and will be for many to come. It has been very handy for me, allows me to have more control over the services I use, and has been a fun project for me to learn from. If you have the time and desire to learn from a project like this, I'd definitely recommend you pick up a raspberry pi or old computer, and start exploring what you can do running your own server.