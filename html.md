
##Document setup

* Include the HTML5 doctype at the start of every HTML page.
  ```html
  <!DOCTYPE html>
  ```

* Set the language attribute on the html element to the language of the content.
  ```html
  <html lang="en-GB" >
  ```

* Set the encoding - it should be UTF-8 and you should ensure that your editor is configured
  to use UTF-8.
  ```html
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  ```


##General guidelines

* Use HTML5 but provide fallbacks for new elements.
* Use semantic markup.
* Reduce markup wherever possible. Avoid superfluous parent elements.
* Avoid putting html directly into strings within javascript.  Consider using a templating system
  to cleanly separate html from javascript code.
* Don't use inline styles.


##Syntax

* Use lower case for tags and attributes.
```html
<!-- Bad -->
<H1>Hello, World!</h1>

<!-- Good -->
<h1>Hello, World!</h1>
```

* Don't omit optional closing tags.
```html
<!-- Bad -->
<p>One, two, buckle my shoe.
<p>Three, four, knock on the door.

<!-- Good -->
<p>One, two, buckle my shoe.</p>
<p>Three, four, knock on the door.</p>
```

* Include the trailing slash in self-closing elements.
```html
<!-- Bad -->
<img src="flower.jpg" alt="A yellow flower">

<!-- Good -->
<img src="flower.jpg" alt="A yellow flower" />
```

* Enclose attribute values in double quotes.
```html
<!-- Bad -->
<h1 class=hello-world>Hello, World!</h1>

<!-- Bad -->
<h1 class='hello-world'>Hello, World!</h1>

<!-- Good -->
<h1 class="hello-world">Hello, World!</h1>
```
* Don't put spaces around the equals sign when assigning attributes.
```html
<!-- Bad -->
<h1 class = "hello-world">Hello, World!</h1>

<!-- Good -->
<h1 class="hello-world">Hello, World!</h1>
```

* Don't use entity references except for HTML special characters.  There's no need provided the
  document is encoded as UTF-8.
```html
<!-- Bad -->
The currency symbol for sterling is &ldquo;&pound;&rdquo;.

<!-- Good -->
The currency symbol for sterling is "£".

<!-- This is fine -->
x &gt; y


##Formatting

* Use soft tabs, set to 4 spaces
* Indent nested elements once (four spaces).
* Try to avoid lines longer than 80 characters.  You may make an exception when splitting the line
  would make it less readable.


##Accessibility

* All images must have an alt attribute with appropriate alt text.  The alt attribute may
  be left empty when an image is purely decorative.
  ```html
  <!-- Bad -->
  <img src="andy.jpg" />

  <!-- Good -->
  <img src="andy.jpg" alt="Andy Murray hitting a tennis ball" />

  <!-- Good -->
  <img src="clip-art-fireworks.png" alt="" />
  ```

* Avoid using title attributes on links as this results in duplication of link text
  for screen reader users.
  ```html
  <!-- Bad -->
  <a href="/" title="home">Home</a>

  <!--- Good -->
  <a href="/">Home</a>
  ```


* Make sure that content appears in the document in the order it would be read on screen.
  This ensures screen readers will read content out in a logical order.
  ```html
    <!-- Bad -->

    <aside class="sidebar">
        <h2>You might also like these...</h2>
        <!-- ... -->
    </aside>
    <section class="main">
        <!-- ... -->
    </section>


    <!-- Good -->
    <section class="main">
        <!-- ... -->
    </section>
    <aside class="sidebar">
        <h2>You might also like these...</h2>
        <!-- ... -->
    </aside>

  ```

* Add labels for all input elements.

  ```html
    <!-- Bad -->
    <form>
        Telephone number: <input type="text" name="phone" id="phone" />
    </form>

    <!-- Good -->
    <form>
        <label for="phone">Telephone number:</label> <input type="text" name="phone" id="phone" />
    </form>

  ```

* Don't miss out heading levels.  Use classes if you want to change the visual appearance of some
  headings.
  ```html
  <!-- Bad -->
  <h1>News</h1>
  <h3>Kitten stuck up tree</h3>

  <!-- Good -->
  <h1>News</h1>
  <h2 class="headline">Kitten stuck up tree</h2>
  ```


* Mark up row and column headers in data tables with &lt;thead&gt; and &lt;th&gt;
```html

<!-- Bad -->
<table>
    <tr>
        <td>Badgers</td>
        <td>Foxes</td>
        <td>Wolves</td>
    </tr>
    <tr>
        <td>35</td>
        <td>94</td>
        <td>385</td>
    </tr>
</table>

<!-- Good -->
<table>
    <thead>
        <tr>
            <th>Badgers</th>
            <th>Foxes</th>
            <th>Wolves</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>35</td>
            <td>94</td>
            <td>385</td>
        </tr>
    </tbody>
</table>


* Clickable elements that refresh the page should be coded as links. Elements that update content
  within a page should be coded as buttons.
