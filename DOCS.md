## Docs

### Files

To use LineScript for your webpage, you will need four files: the base.html file, links to compiler.js and gate.js, and a .osls file that you create yourself. Besides this, you may have your own CSS files, your own JavaScript files, and links to external CSS and JavaScript files.

- **base.html**: this is the HTML baseplate that the compiler will render your webpage on. You can copy the code below, or from [this link](https://raw.githubusercontent.com/ntrupin/LineScript/master/src/base.html).

```html
<html id="whole">
 <body onload="build('MY_FILE')" id="line">
  <script src="https://raw.githubusercontent.com/ntrupin/LineScript/master/src/compiler.js"></script>
  <script src="https://raw.githubusercontent.com/ntrupin/LineScript/master/src/gate.js"></script>
 <body>
</html>
```

You can rename the file anything you wish; It only matters that you keep the contents of the file the exact same. You can replace MY_FILE with the name of your .osls file (excluding the extension. That means you would write index.osls as index).

- **compiler.js**: this script automatically executes on runtime (see how in the gate.js section), and compiles your .osls script into a valid HTML document to be displayed on the webpage.

- **gate.js**: this script bridges the gap between document and compiler. It requests and splits the .osls file and passes the contents to be parsed by the compiler. Once the compiler finished running, gate.js also renders the HTML on the webpage. Calling build('MY_FILE') from base.html is calling the default function from gate.js, telling it to start rendering the webpage.

- **MY_FILE.osls**: this is the file that you wrote, containing the LineScript code. You point to it from base.html (explained earlier) in order for it to be parsed and displayed. The .osls extension stands for *Open Source LineScript*, and is the identifier for LineScript files.

### Writing

LineScript has a syntax inspired by Elm and Haskell, and the syntax only allows one tag to be placed on a line.

All commands are broken up into two or three parts, using -> (to break tag->argument) or :: (to break tag::text or tag->argument::text

#### Positive Tags

Positive Tags, or Positives, are basic tag::text combinations. Common Positives include

**Basic Paragraph Elements**

```html
p :: Hello, world!
```

and **Basic Header Element**

```html
h1 :: I'm a Title!
```

#### Negative Tags

Negative Tags, or Negatives, are tag->argument combinations that lack a text component. Common Negatives include 

**Negative Div Elements**

```html
div -> style="background-color:yellow" ::
```

**Meta Tags**

```html
meta -> charset="utf-8" ::
```

#### Neutral Tags

Neutral Tags, or Neutrals, are tag->argument::text combinations that contain all parts of the available spectrum. Common Neutrals include

**Styled Paragraph Elements**

```html
p -> style="color:red" :: Hello, world!
```

**JavaScript Div Elements**

```html
div -> onclick="alert('Click!')" :: Hello, world!
end :: div
```

#### Nestable Tags

Nestable Tags are tags that can have other tags nested inside of them. The most common Nestable likely is

**Div-Title Combination**

```html
div :: 
 h1 :: I'm a Title!
 p :: And a Pretty Good One, Too
end :: div
```

Nestable tags must always be closed by end :: TAG_NAME.

### Scripts and Stylesheets

For styling documents in LineScript, you can link to external style sheets (such as [Bootstrap](https://getbootstrap.com) or [Skeleton](https://getskeleton.com)), use inline CSS, or use your own custom style sheet. All function of CSS3 is allowed, and extensions such as WebKit are able to be used.

JavaScript can be embedded inline in LineScript to interact with storage, the parsed HTML, servers, and more. LineScript also includes the ability to use JavaScript libraries such as [jQuery](https://jquery.com).

However, LineScript does not support embedded style sheets or scripts. All CSS or JavaScript must be written inline or in a separate document.

### Code

Coming Soon.
