# xp

*Finally, a commandline xpath tool for linux that doesn't suck.*

***What is this?***

xp is a commandline xpath parser. It takes data from stdin, and then outputs the result of the xpath expression you supply it. For example:

    curl -sL github.com | xp "//meta[@name='twitter:title']"
    GitHub: Where the world builds software
    
***How to use:***

 * Install lxml and chardet: `sudo pip3 install lxml chardet`
 
 * Download xp from this repo

 * move xp to somewhere in your `$PATH`, like maybe `/usr/local/bin`
 
 * have fun!
    
