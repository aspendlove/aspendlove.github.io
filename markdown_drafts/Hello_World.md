## My journey creating this website

I created this website with a tool that was new to me, called Hugo. Here is a brief overview of my process.

### Finding Hugo
I found Hugo on [AlternativeTo](https://alternativeto.net/software/hugo/about/) as an alternative to WordPress. It looked like it would be much more interesting technically, while still being easy to build and deploy as you can use community themes instead of writing the entire interface yourself. I had never used a tool like WordPress or Hugo, but Hugo seemed like an interesting option and a good place to start. I had also heard good things about the tool from a web developer that I follow on YouTube.

### Getting Started
To get started, I first looked through the available community [themes](https://themes.gohugo.io/) and found a couple that caught the eye, namely "paper" and "terminal".

[Paper](https://themes.gohugo.io/themes/hugo-paper/), pictured above, is a very simple theme. It is clean and looks nice, but ultimately I decided that it lacked personality. It also had some design quirks regarding the profile picture that I found hard to edit without digging into the source code, which is not recommended as it would break compatibility with future updates to the theme. In general it is best to avoid modifying any of the theme files.

**Paper Theme image here**

[Terminal](https://themes.gohugo.io/themes/hugo-theme-terminal/#how-to-start), on the other hand, is nothing but personality. It emulates the design of a command line interface, or CLI, by using blocky text characters and a somewhat sparse design. Unlike other terminal themes, which lean heavily on the actual experience of using a terminal, this theme only portrays some of the look while still keeping in mind the user experience expected of a website. The only thing that I disliked, was the use of a monospace font for every part of the website. The font pulled the terminal design together, but provided a less than ideal reading experience for long bodies of text. I decided that it should be a design flare and not the main text for the website.

### Setting up the website with the Terminal theme

Using the Hugo [quick start guide](https://gohugo.io/getting-started/quick-start/) I was able to very easily setup my website with the Terminal theme. I had a bit of a hard time following the guide to install the Hugo package, but luckily it is included by default in the Fedora linux repositories, and I didn't have to install a separate homebrew package manager or compile from source.

Running a single command creates a Hugo website in the current working directory, and another two applies the community theme. After you've created the website, running the command "hugo server" in the root directory of the website starts a local live server, which automatically builds and updates based on changes you make in real time. Hugo's blazing fast build speeds are one of it's main accolades.

### Changing the main body font for the Terminal theme

Changing the font turned out to be a quite complex task, with me not knowing exactly what I was doing, but with some patience I figured it out in the end. In the Terminal theme [documentation](https://themes.gohugo.io/themes/hugo-theme-terminal/#how-to-safely-edit-the-theme-a-idhow-to-edit-), it gave a simple method to solving the issue of changing the theme without modifying any of it's files; creating another style.css file with higher specificity than the theme itself, allowing you to modify the CSS of the theme while only working with a single file separate from the theme. With this, and some time and patience, I was able to find a good serif font that fit the terminal theme but was still much more legible, add it to the CSS file, and apply it to the body of the blog posts I write. To do this I write my posts with a mixture of Markdown and HTML. I first write in Markdown to provide an easy writing experience that exchanges HTML's tag structure for special characters that create specific attributes such as headings and ordered lists. Instead of typing \<h1>Heading\</h1>, you can just type \# Heading. After I write the actual content in markdown, I can export to html, and add the necessary HTML classes to apply the correct CSS.

### Deploying the site

Unlike services such as WordPress, Hugo does not porovide hosting for the websites it creates. Luckily, however, free hosting is included by GitHub pages for anyone with a GitHub account. Deploying the website was as simple as running "hugo -D" to build the website to the public folder in the root directory of the website, and uploading it to your github pages repo. My website was then publicly accessible from [aspendlove.github.io](https://aspendlove.github.io)

## Closing thoughts

While making this site may have taken longer than a simple WordPress hosted template, I found the learning process of Hugo very enjoyable. I am one who would rather have complete control over my website's source code and deployment, rather than relying on a service to provide it for me, but locking me out of the details and low-level changes. While Hugo does allow you to create your own website, having the ability to use themes allowed me to make the personal decision to reliquish some control over the interface, in the interest of time spent on the project. However, it still allowed me to apply custom css and customize the options the theme makes available, such as changing the preset color themes. Hugo has been a great tool to work with, and I can see myself using it for future projects.