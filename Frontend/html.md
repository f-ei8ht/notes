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
`<a>` tag is used to define a hyperlink, connects or links one page to another
attributes:
href - hypertext reference

```html
<a href="obisidian.md">Visit</a>
```
download - suggest to download when clicked
rel - relation between the current page and target page
tabindex - control tab order when using keyboard
accesskey - using keyboard shortcut
aria-* label, hidden 
mailto:
tel:

Always use quotes for differentiating attributes if one then no problem if more than one a lot of problem

[Character Entity Reference Chart - W3cubTools](https://tools.w3cub.com/html-entities)
&trade;

## Image tag
```html
<p>This is img tag demo</p>
    <img
      src="/html/5247889.jpg"
      alt="Vegeta"
      title="Vegeta"
      width="100%"
      height="auto"
      usemap="#map"
      loading="lazy"
    />
    <map name="map">
	    <area
        shape="rect"
        coords="0,0,100,500"
        href="https://f-8.me"
        alt="Website"
	     />
    </map>
```

what i learned is you can add a map to image to create it a link with area for shape like circle rectangle poly

Void elements are those that do not have closing tag they are also called empty elements
```html
<hr/>
<area/>
<br/>
<img/>
<input/>
<meta/>
```

## picture tag

the picture element contains zero ore more source elements and one img element to offer alternative versions of image for different display/devices scenarios

```html
<picture>
      <source srcset="/html/5247889.jpg" />
      <img src="/html/5247889.jpg" alt="Vegeta" />
</picture>
```

figure tag can be used to write the image caption using figcaption

## HTML lists

ordered and unordered 

specific order in ordered list like numbers alphabets and style = list-type:
also type attribute in ordered list and start will start from what you specify

nested list inlcuded
```html
   <p>List</p>

    <strong>ordered</strong>

    <ol style="list-style: lower-alpha">

      <li>item 1</li>

      <li>item 2</li>

      <li>item 3</li>

      <li>item 3</li>

    </ol>

    <ol style="list-style: lower-roman">

      <li>item 1</li>

      <li>item 2</li>

      <li>item 3</li>

      <li>item 3</li>

    </ol>

    <ol style="list-style: decimal">

      <li>item 1</li>

      <li>item 2</li>

      <li>item 3</li>

      <li>item 3</li>

    </ol>

    <ol type="A">

      <li>item 1</li>

      <li>item 2</li>

      <li>item 3</li>

      <li>item 3</li>

    </ol>

    <strong>unordered</strong>

    <ul style="list-style: square">

      <li>item 1</li>

      <li>item 2</li>

      <li>item 3</li>

      <li>item 4</li>

    </ul>

    <ul style="list-style: circle">

      <li>item 1</li>

      <li>item 2</li>

      <li>item 3</li>

      <li>item 4</li>

    </ul>

    <ul style="list-style: disc">

      <li>item 1</li>

      <li>item 2</li>

      <li>item 3</li>

      <li>item 4</li>

    </ul>

    <hr />

    <p>nested list</p>

    <ul>

      <li>

        Fruit

        <ol type="1">

          <li>Mango</li>

          <li>

            Apple

            <ul>

              <li>Green</li>

              <li>Red</li>

            </ul>

          </li>

          <li>Pears</li>

        </ol>

      </li>

      <li>vegetable</li>

      <li>Meat</li>

    </ul>

    <hr />

    <ul style="list-style: none; display: flex; gap: 15px">

      <li>home</li>

      <li>about</li>

      <li>service</li>

      <li>contact</li>

    </ul>
```

## HTML TABLES

table tag - defines tables => use row and column to maintain data
tbody - groups the main content of an html table
thead - header title
th - header cell within a table 
td - data cell with a table
tr  - define a row
rowspan
colspan

```html
<!DOCTYPE html>

<html lang="en">

  <head>

    <meta charset="UTF-8" />

    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <title>Tables</title>

    <style>

      table,

      tr,

      td,

      th {

        border: 2px solid black;

        border-collapse: collapse;

        padding: 10px;

        text-align: center;

      }

      th {

        font-size: x-large;

      }

      tr,

      td {

        font-size: large;

      }

      .yellow {

        background: rgb(255, 255, 174);

      }

      .green {

        background: rgb(180, 255, 180);

      }

      .blue {

        background: rgb(176, 235, 255);

      }

    </style>

  </head>

  <body>

    <h1>Tables in html</h1>

    <hr />

    <br />

    <table>

      <thead>

        <tr>

          <th colspan="7">TIME TABLE</th>

        </tr>

      </thead>

      <tbody>

        <tr style="font-weight: bold">

          <td rowspan="7">Hours</td>

          <td>Monday</td>

          <td>Tuesday</td>

          <td>Wednesday</td>

          <td>Thursday</td>

          <td>Friday</td>

          <td>Saturday</td>

        </tr>

        <tr>

          <td>Science</td>

          <td>Science</td>

          <td>Science</td>

          <td>Science</td>

          <td>Science</td>

          <td>Science</td>

        </tr>

        <tr>

          <td>Maths</td>

          <td>Maths</td>

          <td>Maths</td>

          <td>Maths</td>

          <td>Maths</td>

          <td>Maths</td>

        </tr>

        <tr style="font-weight: bold">

          <td colspan="6">Lunch</td>

        </tr>

        <tr>

          <td>English</td>

          <td>English</td>

          <td>English</td>

          <td>English</td>

          <td>English</td>

          <td rowspan="2">Games</td>

        </tr>

        <tr>

          <td>Computer</td>

          <td>Computer</td>

          <td>Computer</td>

          <td>Computer</td>

          <td>Computer</td>

        </tr>

      </tbody>

    </table>

    <br />

    <hr />

    <h1>Another Table</h1>

    <br />

    <table>

      <tr>

        <th rowspan="3">Day</th>

        <th colspan="3">Seminar</th>

      </tr>

      <tr>

        <th colspan="2">Schedule</th>

        <th rowspan="2">Topic</th>

      </tr>

      <tr>

        <th>Begin</th>

        <th>End</th>

      </tr>

  

      <tr>

        <td rowspan="2">Monday</td>

        <td class="yellow" rowspan="2">8:00 a.m.</td>

        <td class="blue" rowspan="2">5:00 p.m.</td>

        <td>Introduction to XML</td>

      </tr>

      <tr>

        <td>Validity: DTD and Relax NG</td>

      </tr>

  

      <tr>

        <td rowspan="3">Tuesday</td>

        <td class="yellow">8:00 a.m.</td>

        <td class="green">11:00 a.m.</td>

        <td rowspan="1">XPath</td>

      </tr>

      <tr>

        <td class="green">11:00 a.m.</td>

        <td class="green">2:00 p.m.</td>

      </tr>

      <tr>

        <td class="green">2:00 p.m.</td>

        <td class="blue">5:00 p.m.</td>

        <td rowspan="1">XSL Transformations</td>

      </tr>

  

      <tr>

        <td>Wednesday</td>

        <td class="yellow">8:00 a.m.</td>

        <td class="green">12:00 p.m.</td>

        <td>XSL Formatting Objects</td>

      </tr>

    </table>

  </body>

</html>
```

iframe tag nested browsing context display another html page in the current page 
everywebsite or everything cannot be added using iframe or we can say embedded

```html
<iframe

      width="1510"

      height="790"

      src="https://f-8.me"

      title="My Personal Portfolio"

      frameborder="0"

      allowfullscreen

    ></iframe>
```

audio tag and video tag 

```html
<audio controls loop muted autoplay>

      <source src="/html/audio.mp3" type="audio/mpeg" />

      your browser does not supports this audio

    </audio>

    <hr />

    <br />

    <video

      controls

      width="500"

      height="250"

      loop

      muted

      poster="/html/5247889.jpg"

      autoplay

    >

      <source src="/html/video.mp4" type="video/mp4" />

    </video>
```

## Forms in html