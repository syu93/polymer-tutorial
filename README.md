# Get started with polymer
 
*This document aim to bring a small comprehension to the Polymer library and all the elements which goes with.*

# Table of contents
* [Get started with polymer](#get-started-with-polymer)
* [Table of contents](#table-of-contents)
* [What is Polymer](#what-is-polymer)
    * [Web components](#web-components-?)
    * [Polyfill](#polyfill)
    * [Shadow DOM](#shadow-dom)
* [How to install Polymer](#how-to-install-polymer)
* [How to use Polymer (good way and learning way)](#how-to-use-polymer)

## What is Polymer
The Polymer __*library*__ *(because it's a library **not a framework**)* is designed to make it easier and faster for developers to create great, reusable components for the modern web....

__*Is it much clear now ...? Certainly not. Let's explain this in further details.*__

HTML provides a set of __built-in__ elements like `<button>`, `<form>` and `<table>` . Each element has its own API of attributes, properties, methods, and events. Each element has built-in styling, as well as style properties you can override using CSS.

Anyone can use these elements to build a simple web page. But they’re limited. To build something as simple as a set of tabs, you need HTML plus CSS and usually a script, too.

With __custom elements__, you can extend the vocabulary of HTML with your own elements. Elements that provide sophisticated UI. Elements that are as easy to use as `<select>` :

```html
<my-tabstrip>
  <my-tab> Home </my-tab>
  <my-tab> Services </my-tab>
  <my-tab> Contact Us </my-tab>
<my-tabstrip>
```
Polymer is built on top of the `web components` standards and it helps you build your own custom elements:

## Web components

**Web components**. These standards provide the primitives you 
    need to build new components such as `import html` or `custom tags`. You can build your own custom elements using these primitives, but it can be a lot of work.

**Note:** Not all browsers support these standards yet, so the web components `polyfill` fills the gaps, implementing the APIs in JavaScript.

## Polyfill ! Poly... what ?!
A **polyfill**, or **polyfiller**, is a piece of code (or plugin) that provides the technology that you, the developer, expect the browser to provide natively. Flattening the API landscape if you will.

**webcomponents.js** is a set of *polyfills* built on top of the Web Components specifications. It makes it possible for developers to use these standards today across all modern browsers.

As these technologies are implemented in browsers, the polyfills will shrink and you'll gain the benefits of native implementations. webcomponents.js automatically detects native support and switches to the fast path when available. Your elements seamlessly start relying on the native stuff--and get faster in the process.

## Shadow DOM
**`Shadow DOM`** provides encapsulation for the JavaScript, CSS, and templating in a *Web Component*. Shadow DOM makes it so these things remain separate from the DOM of the main document. You can also use Shadow DOM by itself, outside of a web component.

Why would you want to keep some code separate from the rest of the page? One reason is that on a large site, for example, if the CSS is not carefully organized, the styling for the navigation can "leak" into the main content area where it was not intended to go, or vice-versa. As a site or an app scales, this kind of thing becomes difficult to avoid

# How to install Polymer

## Installing with Bower

The recommended way to install **Polymer 1.0**
is through Bower. To install Bower, see the [Bower web site](http://bower.io/).

Bower removes the hassle of dependency management when developing or consuming
elements. When you install a component, Bower makes sure any dependencies are
installed as well.

## Project setup

If you haven't created a `bower.json` file for your application, run this
command from the root of your project:

    $ bower init
    
**Tip:** Use the `--allow-route` option if your are connected or execute command as __*root*__. The command will not work otherwise.

This generates a basic `bower.json` file. Some of the questions, like
"What kind of modules do you expose," can be ignored by pressing Enter.

The next step is to install Polymer:

    $ bower install --save Polymer/polymer#^1.2.0

Bower adds a `bower_components/` folder in the root of your project and
fills it with Polymer and its dependencies.

**Note:** You're able to change the bower dependency folder with the .bowerrc file

```
    {
        "directory": "vendor"
    }
```

**Tip:** `--save` adds the item as a dependency in *your* app's bower.json:
```
{
  "name": "my-project",
  "version": "0.0.0",
  "dependencies": {
    "polymer": "Polymer/polymer#^1.2.0"
  }
}
```

## Updating packages

When a new version of Polymer is available, run `bower update`
in your app directory to update your copy:

    $ bower update

This updates all packages in `bower_components/` to the latest stable version.

# How to use Polymer
Now that you have Polymer installed, it's time to create your app.

There is two ways of doing it:

**The first one**, by using the __Polymer Starter Kit *(PSK)*__ which you can download : [here](https://developers.google.com/web/tools/polymer-starter-kit/) 

**Note:** There is two PSK versions (choose the one that fit your needs).
For beginner I recommend using the light version that comes with all elements pre-installed.

It will provide you a complete application that you just have to hack and modify to match your needs.

**The seconde one** which I call *the learning way* :

Get your hands dirty and build your own application from the ground. It's really useful if you want to exactly understand what going on under the hood.

**Note:** I want to be very clear, I do not recommend to build your application from scratch because there is a great starter kit made by the Polymer developer theme-self.
        
        !!! Using the PSK will be more efficient if you're targeting the production ready application !!!
        
That being said, the best way to understand the way Polymer works is actually by using it. So let's do this.

### Let's take a look at a Polymer application architecture

Here is a sample of a very **simple** Polymer application.

**Note:** I my case the `bower_comonents` folder is renamed `vendor`.
```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="">
    <head>
        <meta charset="utf-8">
        <meta name="description" content="">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Polymer Application</title>

        <script src="vendor/webcomponentsjs/webcomponents.js"></script>
        <link rel="import" href="elements/elements.html">

        <!-- For the sake of the exemple css goes here -->
        <style type="text/css">
            html, body {
                margin: 0;
                padding: 0;
                height: 100%;
            }

            #cards {
                @apply(--layout-vertical);
                @apply(--center-justified);
                max-width: 400px;
                margin-left: auto;
                margin-right: auto;
            }
        </style>
        <link rel="stylesheet" type="text/css" href="css/style.css">
    </head>
    <body unresolved>
        <paper-toolbar>
          <paper-icon-button icon="menu" on-tap="menuAction"></paper-icon-button>
          <div class="title">Title</div>
          <paper-icon-button icon="more-vert" on-tap="moreAction"></paper-icon-button>
        </paper-toolbar>
        <div id="cards">
            <paper-card>
              <div class="card-content">
                <div>
                    Cards are a convenient means of displaying content composed of different types of 
                    objects.
                  <br><br>
                  <b>Hurray!</b>
                </div>
              </div>
            </paper-card>
        </div>
    </body>
</html>
```

Let's take a closer look of what going on the head or our html page.

```html
    <!-- index.html -->
    <meta charset="utf-8">
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Polymer Application</title>
```

        As it is a responsive application don't forget to specify all the meta needed. (you'll be 
        disappointed if it not working because of that)

Seriours stuff start here.

```html
    <!-- index.html -->
    ...
    <script src="vendor/webcomponentsjs/webcomponents-lite.js"></script>
    <link rel="import" href="elements/elements.html">
```

As I said before, to ensure that your application will be available on all modern browsers but also that the APIs will work the same way across browsers, you need to use the Polyfills *`webcomponents-lite.js`* that comes with Polymer.

__*And now you probably ask your-self : Ok cool but, Where is the polymer library ?*__

Here I come, you've noticed the `element.html` file. It's a part of the Polymer best practices. Instead of just throwing all the elements you need to import in your application in the index.html, use the **elements.html** as a "dependency container" that will import all the elements you need. It's more readable and this way you can manage easily all the elements you depend on.

For our simple application here it is :

```html
    <!-- elements.html -->
    <!-- Iron elements -->
    <link rel="import" href="../vendor/iron-icons/iron-icons.html">
    <!-- Paper elements -->
    <link rel="import" href="../vendor/paper-toolbar/paper-toolbar.html">
    <link rel="import" href="../vendor/paper-icon-button/paper-icon-button.html">
    <link rel="import" href="../vendor/paper-card/paper-card.html">
```

__*Well, I still not see the import of the polymer library, do we even need to include the library at all ?*__

In fact, you don't need to import your-self the polymer.html as the polymer library uses the native web compoent API *(with help of the Polyfill)*. The libray simply provide a set of tools that let you use this API to create your custom elements.

**Note:** As a matter of fact, the Polymer `custom elements` are including the Polymer library to use its API

Speaking of custom elements, let's dive into it.

```html
<link rel="import" href="../polymer/polymer.html">
<dom-module id="dom-element">
  <template>
    <p>I'm a DOM element. This is my local DOM!</p>
  </template>
  <script>
    Polymer({
      is: "dom-element"
    });
  </script>
</dom-module>
```

This is a very simple custom elements using Polymer.

**Note:** For more specification about how to create a powerfull custom element *[read this documentation](https://www.polymer-project.org/1.0/docs/devguide/properties.html)*.

After having import your custom element in the elements.html file.

```html
    <!-- elements.html -->
    ...
    <link rel="import" href="../dom-element/dom-element.html">
```

Start using it like any native element.

```html
    <!-- index.html -->
    ...
    <dom-element></dom-element>
```

**That all. I hope that now, Polymer is a bit less like black magic for you.**

**We have covered a lot of things here but if you want to go deeper here are some realy intersting links and very useful documentation.**

[What is a Polyfill?](https://remysharp.com/2010/10/08/what-is-a-polyfill)

[WebComponents.org](http://webcomponents.org/)

[Shadow DOM](https://developer.mozilla.org/fr/docs/Web/Web_Components/Shadow_DOM)

[Polymer-project.org](https://www.polymer-project.org/1.0/)

[Guides responsive material design layouts](https://elements.polymer-project.org/guides/responsive-material-design-layouts)

[Guides using elements](https://elements.polymer-project.org/guides/using-elements)

[Create custum element](https://www.polymer-project.org/1.0/docs/devguide/properties.html)

[Register a custom element](https://www.polymer-project.org/1.0/docs/devguide/registering-elements.html)

[Polymer Catalog](https://elements.polymer-project.org/)

[Custom Elements catalog (made by everyone)](https://customelements.io/)

**And great tutorial videos.**

[Polycast playlist](https://www.youtube.com/playlist?list=PLNYkxOF6rcIDdS7HWIC_BYRunV6MHs5xo)

[End to End with Polymer](https://youtu.be/1f_Tj_JnStA)

[Building Progressive Web Apps with Polymer](https://youtu.be/g7f1Az5fxgU)
