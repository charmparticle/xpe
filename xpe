#!/usr/bin/env python3

from sys import stdin, argv
from os import path

from lxml import etree
from chardet import detect


html = ""
i = 0


def show_help():
    helpstr = """
xpe takes data from stdin, and supplies the result of an xpath selection to stdout.
For example (assuming xpe is in your $PATH):

curl -s example.com | xpe '//title/text()'
(result should be 'Example Domain')

Alternatively, xpe can read a file supplied to it, ie:

xpe '//a/@href' somefile.html
or
xpe somefile.html '//a/@href'

xpe will print this help message if it is invoked improperly"""
    print(helpstr)
    exit(1)


if stdin.isatty():
    target = 'file'

    if len(argv[1:]) == 2:
        for n in range(1, 3):
            arg = argv[n]
            if path.exists(path.expanduser(arg)):
                target = path.expanduser(arg)
            else:
                xpath = arg

    if target == 'file':
        show_help()
else:
    target = 'stdin'

    if len(argv[1:]) == 0:
        show_help()

    xpath = argv[1]

xpr = xpath.strip("\"\'")
if len(xpr) == 0 or not xpr[0] in '/(':
    show_help()

if target == 'stdin':
    bytelines = stdin.buffer
else:
    bytelines = open(target, 'rb')

for bline in bytelines:
    if i == 0:
        try:
            if 'encoding=' in bline.decode():
                continue
        except Exception:
            pass

    # guess the encoding of the input so that I can use it
    guess = detect(bline)
    if guess['encoding'] is None:
        pass
    else:
        line = bline.decode(guess['encoding'], errors='ignore')
        html = html + line

    i = i + 1

bytelines.close()

htmlparser = etree.HTMLParser()
tree = etree.fromstring(html, htmlparser)

try:
    xpaths = tree.xpath(xpath)
except etree.XPathEvalError:
    show_help()

for xpath in xpaths:
    if type(xpath) == etree._ElementUnicodeResult:
        print(xpath)
    else:
        print(xpath.text)
