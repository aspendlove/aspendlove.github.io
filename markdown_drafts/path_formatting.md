# Absolute vs. Relative Links

Most users won't have to think too much about the underlying parts of websites and operating systems, but only because others, such as web developers, do. Recently, while making my portfolio website at [https://aidanspendlove.dev](https://aidanspendlove.dev/), I had some issues with file paths causing issues when my site was hosted on different server configurations. I've had quite a bit of experience with file system paths, so I was able to figure out my issue, but if I had no experience, I would have been quite stumped. In this post, let me share what my problem was and how I fixed it.

## Basic syntax

This post assumes you already know how basic folder structures work, but here is a quick refresher on the syntax

-   / - Directory separator, signifies a folder. "/" is the root folder
-   . - Current directory
-   .. - Parent directory
-   ... - Parent of the Parent Directory
-   .... - continues on

## The problem and solution

This is the folder structure that I started with on my computer.

-   / 🗁
    -   project2 🗁
        -   images 🗁
            -   image.png 🖹
            -   thumbs 🗁
                -   thumb.png 🖹
        -   portfolio
            -   portfolio_page.html
        -   index.html 🖹
        -   style.css 🖹

This folder structure made it very easy to use Absolute links. **Absolute links** define every directory level explicitly, from the **root** folder. In my website, the root folder contained my full project2 folder, allowing me to explicitly define paths to images. To get to "image.png", I would use "/project2/images/image.png". Doing this made it so that there was no confusion with the links, they were perfectly explicit.

The problem was that when I uploaded it to the fine arts server, the directory structure changed to:

-   / 🗁
    -   ~aspendlove 🗁
        -   project2 🗁
            -   images 🗁
                -   image.png 🖹
                -   thumbs 🗁
                    -   thumb.png 🖹
            -   portfolio 🗁
                -   portfolio_page.html 🖹
            -   index.html 🖹
            -   style.css 🖹

Now when trying to use my links, they wouldn't work; "/project2/images/image.png" was no longer valid, the file had moved to "/~aspendlove/project2/images/image.png". This may seem like a small change, but it ruined all my links on the website. Images wouldn't load, pages wouldn't load, and all my styles were gone. I could have changed all the links accordingly, but then it wouldn't work on my computer. I would have to get creative.

I then thought of relative links. **Relative links** are a little trickier to manage, but they rely on the directory that the current file is already in. Let me show you an example.

If I am in the portfolio_page.html file, and I want to link to my style.css file, instead of doing "/project2/style.css" or "/~aspendlove/project2/style.css", I could use the . operator and it's siblings to base things on the **current** folder. So if portfolio_page.html is in the "portfolio" folder, which it is in both my computer and the fine arts server, I can use the idea that ".." goes back one directory. If I do "../style.css" the ".." will take me to the project2 folder, then will point to style.css. Because this only relies on the style.css file being one directory above of portfolio_page.html, this will work regardless of what / is, meaning you can move it between systems with no problem. This means that you have to be very careful to keep your links updated whenever you move a file in your localsite folder, but it makes up for it in its sheer portability. You can go pretty far with these relative links too, for example if I was in the thumbs folder, I could navigate to project 2 with "../../". On the fine arts server, I could get all the way to root with "../../../../". Relative links can also just be filenames like "style.css" if the place you are referencing it from is in the same directory as the file. For example, if I want to access style.css from index.html, I would just put in its name since they're both already in the same folder.

In the end, my solution was to use Relative links and to be careful about how I formatted them. Absolute links are helpful if you know exactly where your file is and how to get there, but if you plan on moving your folder around between computers and servers, it makes sense to spend the extra effort to use relative links.
