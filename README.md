# xpe

*Finally, a commandline xpath tool for linux that can actually handle real html.*

***What is this?***

xpe is a commandline xpath parser. It takes data from stdin, and then outputs the result of the xpath expression you supply it. For example:

    curl -sL github.com | xpe "//meta[@name='twitter:title']"
    GitHub: Where the world builds software

***How to install***

    sudo pip3 install xpe

