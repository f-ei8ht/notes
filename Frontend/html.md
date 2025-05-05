HTML stands for hypertext markup language and hypertext means text that links to other text. 

markup language is way to tell browser how to display content A markup language is a [text-encoding system](https://www.bing.com/ck/a?!&&p=5c3ef0ea475ae757ebead83dd43dcd1e991ef8c13f23b09aa0d124c1554dd49dJmltdHM9MTc0NjMxNjgwMA&ptn=3&ver=2&hsh=4&fclid=34af192e-7b97-66dd-1e82-0c437a9167bd&u=a1L3NlYXJjaD9xPUVuY29kaW5nJTIwd2lraXBlZGlhJmZvcm09V0lLSVJF&ntb=1) which specifies the structure and formatting of a document and potentially the relationships among its parts. Markup can control the display of a document or enrich its content to facilitate automated processing.

Tim Berners lee
www => world wide web 
w3c => world wide web consortium
html

Ted nelson
hypertext
hypermedia

we use html5
because we have semantic tags

html element
```html
<!-- opening tag---> <h1> <!-- content ---> Hi </h1> <!-- closing tag--->

all these combine together and make html content
```

file extension .html or .htm

earlier in ms dos or windows only 3 letter for extension were used 

name must be index.html becuase it is treated as root file by default or default path of the homepage

```html
<!DOCTYPE html>
<!--- tells the browser about the version of html i.e., html5-->
<html lang="en">
  <!-- root element with lang attribute set to english-->
  <head>
    <meta charset="UTF-8" />
    <!-- character encoding-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <!--optimises layouts for different devices width=device-width makes widht of the screen to the devices width and initial scale zoom level of the page-->
    <meta name="description" content="This is a html page" />
    <!-- short description of the website -->
    <title>Document</title>
    <!-- title -->
  </head>
  <!--- what ever you write inside head contains info of the document -->
  <body>
    <h1>hi there</h1>
  </body>
  <!-- contains the content and displays it on the page-->
</html>
```


attributes can define the characteristic of element used along side them

## Headings
```html
<h1>hi there</h1> 2em
<h2>hi there</h2> 1.5em
<h3>hi there</h3> 1.17em
<h4>hi there</h4> 1em
<h5>hi there</h5> 0.83em
<h6>hi there</h6> 0.67em
```


<h1>hi there</h1>
  <h2>hi there</h2>
   <h3>hi there</h3>
   <h4>hi there</h4>
   <h5>hi there</h5>
   <h6>hi there</h6>

follow the hierarchy h1 to h6


## Paragraph
```html
<p> this is a para </p>
```

you can not nest block level elements inside p tag but can inline elements like em, strong
there is blank line or space above and below p tag by default i think

```html
<br /> line break
<hr /> horizontal line
```

<hr>

<p>this is a <br>para <p/>

no matter how much white space you use it will be rendered as one only

<!-- this is a comment--> 

## Text Formatting
```html
<strong> bold
<em> empahsis, italic
<u> underline
<s> strikethrough no longer relevant
<sub> subscript
<sup> superscript
<pre> content displayed as it is 
<abbr> add abbreviation to text
<kbd> keyboard style text ctrl  + s
<mark> highlight
<small> make font small
<del> delete the text 
```

never mismatch tag while nesting

### Anchor tag
<a> tag is used to define a hyperlink, connects or links one page to another