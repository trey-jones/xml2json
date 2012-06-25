XML2JSON
========

Python script converts XML to JSON or the other way around

Usage
-----
Make this executable

    $ chmod u+x xml2json3

Then invoke it from the command line like this

    $ xml2json3 file.xml file.json

Or the other way around

    $ xml2json3 -m json file.json file.xml

You can also output to stdout

    $ xml2json3 -m json file.json console

Possibly more info in help:

	$ xml2json3 -h

Consider putting the script on your path!  I have it in ~/bin

More info
---------

Rewritten to a command line utility by Hay Kranen: http://www.haykranen.nl
Fork it on Github: http://github.com/hay/xml2json
Rewritten by Trey Jones for Python3 with a goal of parsing huge (many Gigs) XML files, namely osm data.

@ and # prefixes for attributes and text/tail respectively removed
We can correctly parse json to xml without them.

<pre>
XML                              JSON
<e/>                             "e": null
<e>text</e>                      "e": "text"
<e name="value" />               "e": { "name": "value" }
<e name="value">text</e>         "e": { "name": "value", "text": "text" }
<e> <a>text</a><b>text</b> </e> "e": { "a": "text", "b": "text" }
<e> <a>text</a> <a>text</a> </e> "e": { "a": ["text", "text"] }
<e> text <a>text</a> </e>        "e": { "text": "text", "a": "text" }
</pre>