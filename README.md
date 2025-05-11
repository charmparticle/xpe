# xpe

*Finally, a commandline xpath tool that is easy to use.*

***What is this?***

xpe is a commandline xpath parser. Pipe in some textual data, supply it with an xpath expression, and it will dump the result to stdout. Perfect for shellscripting. For example:
    
    curl -s example.com | xpe "//h1/text()"

    Example Domain
    
Alternatively, xpe can query a file for xpath expressions like so:

    xpe '//a/@href' somefile.htm

The order doesn't matter, so the following is also valid:

    xpe somefile.htm '//a/@href'

**Lately, I've been using xidel instead because it is faster. I created a gist for how to get xidel to act like xpe**

https://gist.github.com/charmparticle/3253f75880d8daf546e5fb2dd4437213

***How to install***

    sudo pip3 install xpe

***How to upgrade***

    sudo pip3 install -U xpe
