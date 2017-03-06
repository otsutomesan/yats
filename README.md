# yats
Yats - {HTML} Templates for Python

- Introduction
- Getting Started
- Licence

---
## Introduction
Yats is a simple python tool that is designed to split presentation from logic in dynamic web pages. It was primarily written to be used in conjunction with the modpython modpublisher module, but can equally be used in cgi scripts. It can also conceivably be applied to text and other markup languages other than HTML. It is based on HTMLgen's Template documents so usage is similar for users already familiar with that tool.  

The reasoning behind any HTML template tool is that it allows designers to focus on the presentation of the page, and programmers on the logic behind any dynamic data that is to be presented to the user. Advantages are readability and ease of testing, as code can be tested outside of the web page using tools such as pyunit.  

There are a number of template tools in use. For perl users there is HTML::TEMPLATE, and of course for Python there is the mother of all template systems, Zope. Yats takes a very simple approach in that it uses HTML comment tags for blocks of data, and braces { } for actual data symbols. All logic is applied in the python code.

---
## Getting Started

### Simple Usage
```
from yats import *

page=TemplateDocument('yats.html')
page.substitutions={'idle':'idle with eric'} 
page['eric']= 'spam and eggs'
page.write('yatsexample1.html')
#or to stdout
str(page)
```

### Conditional Insertions
```
from yats import *

page=TemplateDocument('yats.html')
page.extract('sometag')
page['sometag']='Block replaced'
page['eric']= 'spam and eggs'
page.write('yatsexample2.html')
```

### Inserting a row or rows of data (looping over data)
```
from yats import *

page=TemplateDocument('yats.html')
page['row'] = {'cheese':'cheddar','instock':'no','comment':'This is a cheese shop!'}
rows = ({'cheese':'blue vein','instock':'no','comment':'Over ripe'},{'cheese':'stilton','instock':'no'})
for rownum in range(0,len(rows),2): rows[rownum]['bgcolor']= 'bgcolor="#CCCCCC"'
page['rows'] = rows
page.write('yatsexample3.html')
```

---
## Licence
Copyright (c) 2001 Brett Haydon email:bbhaydon@bigpond.com  
 Permission to use, copy, modify, and distribute this software and
 its documentation for any purpose and without fee is hereby granted,
 provided that the above copyright notice appear in all copies and
 that both that copyright notice and this permission notice appear in
 supporting documentation.  
 THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS
 SOFTWARE, INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND
 FITNESS, IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY
 SPECIAL, INDIRECT OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER
 RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF
 CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN
 CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.  

 COPYRIGHT (C) 1996-9 ROBIN FRIEDRICH email:Robin.Friedrich@pdq.net  
 Permission to use, copy, modify, and distribute this software and
 its documentation for any purpose and without fee is hereby granted,
 provided that the above copyright notice appear in all copies and
 that both that copyright notice and this permission notice appear in
 supporting documentation.  
 THE AUTHOR DISCLAIMS ALL WARRANTIES WITH REGARD TO THIS
 SOFTWARE, INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND
 FITNESS, IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY
 SPECIAL, INDIRECT OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER
 RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF
 CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN
 CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
