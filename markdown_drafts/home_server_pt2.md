This is part two of my home server post. Read part 1 before this post.

# Moving to PC

I left off last post talking about the new mini PC that I bought. It was turning out to be a considerable update over the raspberry pi, but all the software I was used to running on my raspberry pi was either incompatible, or simple enough that I wanted to go beyond. The biggest thing I wanted to change was to move away from nextcloudPi as an operating system, and move to a general purpose server operating system.

## Choosing an Operating System

For as long as I've used a computer, I've used some flavor of Linux, therefore I am very familiar with the base that powers a large majority of servers in production today. In my work most of our clients used Windows Server, but for my use case it offers no benefits over Linux, and actually would be much worse. Running Windows Server would be expensive, slow, difficult to use, and inflexible. The only reason that companies use Windows Server for their internal business use is because it integrates well with their windows workstations with Active Directory.

So I decided to use Linux, but that doesn't narrow it down much. There are many different flavors of Linux out there, and a lot of it comes down to personal preference. Luckily I have had a long time to try almost all of them, so I knew what I wanted almost immediately. Here's how I narrowed it down. For reference a distro, or distribution, refers to a specific implementation of an operating system based on the Linux kernel and surrounding tools.

-   Debian
    -   Pros
        -   Debian is what powers nextcloudPi, and makes a good server operating system because feature updates are very slow to roll out, meaning big changes that may mess up your applications does not happen as often. Security updates are still pushed out regularly
        -   Debian is very basic compared to other Linux flavors, and is very simple to use and flexible because of that.
        -   Debian has a large support base and has been around for a long time
    -   Cons
        -   Debian uses the apt package manager. This is mostly personal preference, but I find it to be less stable and overall buggier
        -   Debian does not offer advanced niceties that some of the other distros
        -   Very hard to install
-   Ubuntu
    -   Pros
        -   Ubuntu has a very large support base, and is based on Debian, so it can also make use of Debian's support base
        -   Ubuntu has some advanced features, such as support for the snap packaging format by default.
        -   Ubuntu offers long term support releases that are supported for 5 years
        -   Easy to install
    -   Cons
        -   I have found Ubuntu to be less than stable
        -   The apt package manager is also used
        -   Ubuntu still lacks many advanced features
-   Red Hat Enterprise Linux
    -   Pros
        -   RHEL based systems are independent projects from Debian.
        -   RHEL offers long term releases for 10 years as opposed to Ubuntu's 5
        -   RHEL offers many advanced features, such as
            -   Cockpit, which provides a web interface to remotely manage your server
            -   Toolbox, which creates containers to isolate certain operations on your system
            -   Immutable Filesystems, which on the editions that it is included in disallows the system from being modified and only allowing changes to be made through containerization.
            -   Firewalld, a new advanced firewall and network routing backend
            -   Support for snap server packages
            -   Podman, for running OCI containers
        -   RHEL uses the DNF package manager which I have found to be much more stable and reliable over APT
        -   RHEL is backed by the resources at Red Hat and IBM
    -   Cons
        -   DNF is slightly slower than APT in most operations
        -   RHEL is harder to install than Ubuntu, but easier than Debian
        -   Depending on the version you may have to pay for RHEL

I ended up going with Fedora, which is a faster updating free version of RHEL. I use Fedora Workstation on my desktop and laptop, so it makes sense to use Fedora Server as well.

## Next up

Didn't realize this would need a part 3, next I'll talk about setting fedora server up with services.

