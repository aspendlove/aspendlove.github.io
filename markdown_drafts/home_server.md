I have run a small home server for a couple years now. I'd like to go over how it has evolved and how it is setup now. This is part 1 of a 2 part post.

## Raspberry Pi

My server ambitions started out with a raspberry pi 3B+. I had had it for years, and had even used it as my main computer for a while at the start of high school. It was outdated when I put it to work as my server, with the raspberry pi 4 already out, but I was ambitious to find a use for the small computer and to learn more about running a server.

I had attempted to run Nextcloud on a raspberry pi before, but I always had issues. The guides I followed used a base version of Raspbian Lite that they used as a base to install all the software and configurations needed for Nextcloud manually. Weary of trying this method again and failing, I searched for another way, and found [NextcloudPi](https://Nextcloudpi.com/), a pre-configured operating system already setup with Nextcloud and many tools designed to make managing it easier. It gave me the ability to get my server up and running easily, while still giving me a taste of the details of server deployment.

My little raspberry pi server was in use for about 2 years, running NextcloudPi.

## Nextcloud

My main reason for running a server is Nextcloud. It is a all in one dashboard that contains many services in one place. My main uses for it are:

- Notes
- Contacts
- Calendar
- File storage and file sharing

It is a very useful all in one solution that has replaced:

- Google Drive
- Google Contacts
- Google Calendar
- Google Keep

Hosting my own data away from the prying eyes of large companies is one of the reasons that I enjoy running my own server. I strive for privacy, as it is continuously compromised to large tech companies. I also enjoy the technical aspect of learning about server management. I work summers at an IT company, and this hobby project has made me better able to service the servers of my clients.

## Upgrading

After a couple years my raspberry pi server was growing quite sluggish. The nextcloud interface became very hard to navigate. I decided it was time to upgrade from an old raspberry pi to something newer.

I didn't want to spend very much money on this venture, as I didn't think I had to in order to make a good server for myself. I capped my budget around $200 and got looking. Many people think that servers have to be very specialized equipment, and most depictions of a server are large rack mounted behemoths that look nothing like the computers we interact with day to day. The reality is, however, that almost any computer can be a server. All that is required to make a server is server software, such as nginx, nextcloud, apache2, and Plex, and a network connection. What dedicated enterprise servers bring to the table is certain specialized features that make them better tailored to be used at scale. They have redundant power supplies, so that if one fails the server does not lose power. They have large banks of specialized error correcting ram in order to ensure absolute stability. Their storage is also redundant, with large pools of hard drives being managed so that a number of drives can completely fail before data is lost. These niceties, along with others such as easy remote management, are what make these specialized servers useful. 

For a personal server, however, I don't need any of that. If my server has downtime, the only person that will be affected is me. I don't have to worry about a company full of people losing precious work time waiting for server issues to resolve (I only have to worry about that in my IT job 😅). I don't need data redundancy because I can deal with the downtime of having to restore a backup. Because I didn't need the features of a business oriented server, I could get creative in what I used. I settled on a mini PC made by Lenovo around 2014. It is a small black box containing an old 4th gen Intel i5, 8 gigs of ram, and 256 gb of ssd storage. I bought it second hand from a work colleague and it set me back around $200. 

## Next up

In my next post I'm going to go through the deployment of my new server, and frustrating process that finally led me to it's current working state.