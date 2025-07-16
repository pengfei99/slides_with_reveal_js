# slides_with_reveal_js

**reveal.js** is an open source `HTML presentation framework`. It's a tool that enables anyone with a web browser
to create fully-featured and beautiful presentations for free.

The official site can be found [here](https://revealjs.com/installation/).

In this tutorial, I will try to use reveal js to create my first HTML slides.

The index.html is the dev page of our slides, we will update it during this tutorial.

The demo.html is the default demo page of `reveal.js`.

## 1. Install the reveal js

You can find the official installation doc [here](https://revealjs.com/installation/)

I choose the simplest way:

- Download the latest reveal.js version https://github.com/hakimel/reveal.js/archive/master.zip
- Unzip and replace the example contents in index.html with your own
- Open index.html in a browser to view it

## 2. Customize index.html

You can notice, the default `index.html` file has three import parts:

- import slides style: For example, the main style is `dist/reveal.css`, theme style is `dist/theme/black.css`,
- content of the slides: All slides are in a div with class="reveal".
- import js scripts for slides animation: For example `<script src="dist/reveal.js"></script>` import `dist/reveal.js`

```html

<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">

    <title>Pengfei reveal slides</title>

    <link rel="stylesheet" href="dist/reset.css">
    <link rel="stylesheet" href="dist/reveal.css">
    <link rel="stylesheet" href="dist/theme/black.css">

    <!-- Theme used for syntax highlighted code -->
    <link rel="stylesheet" href="plugin/highlight/monokai.css">
</head>
<body>
<div class="reveal">
    <div class="slides">
        <section>Slide 1</section>
        <section>Slide 2</section>
    </div>
</div>

<script src="dist/reveal.js"></script>
<script src="plugin/notes/notes.js"></script>
<script src="plugin/markdown/markdown.js"></script>
<script src="plugin/highlight/highlight.js"></script>
<script>
    // More info about initialization & config:
    // - https://revealjs.com/initialization/
    // - https://revealjs.com/config/
    Reveal.initialize({
        hash: true,

        // Learn about plugins: https://revealjs.com/plugins/
        plugins: [RevealMarkdown, RevealHighlight, RevealNotes]
    });
</script>
</body>
</html>

```

### 2.1 Change theme

The default theme is `<link rel="stylesheet" href="dist/theme/black.css">`. Now let's use `dracula.css`.

```html
<!--replace the old black.css by darcula.css-->
<link rel="stylesheet" href="dist/theme/dracula.css">
```

You can find all available themes [here]()

## 3 Add slides contents

In this section, I will show how to edit the slide content

### 3.1 Edit the cover page

Let's create the first cover page. Below is the default content. Each slide page is hosted inside a section.

```html

<div class="reveal">
    <div class="slides">
        <section>Slide 1</section>
        <section>Slide 2</section>
    </div>
</div>
```

The first page, I will show the logo of the organization, the title of the presentation and the name of the author and
the date of the presentation.

```html

<div class="reveal">
    <div class="slides">
        <!--Each slide is inside a section-->
        <!-- section for slide 1-->
        <section>
            <a href="https://casd.eu">
                <img src="images/casd.svg" alt="casd logo"
                     style="height: 180px; margin: 0 auto 4rem auto; background: transparent;" class="demo-logo">
            </a>
            <h2>Pengfei's Reveal Slides</h2>
            <p><small>Created by <a href="https://github.com/pengfei99">Pengfei Liu</a></small></p>
            <p><small>04/08/2025</small></p>
        </section>
        <section>Slide 2</section>
    </div>
</div>
```

### 3.2 Sub slides

**Reveal.js** allows us to have sub slides with `<section>...</section>` inside another `<section>...</section>`.

```html

<!-- section for slide 1-->
<section>
    <a href="https://casd.eu">
        <img src="images/casd.svg" alt="casd logo"
             style="height: 180px; margin: 0 auto 4rem auto; background: transparent;" class="demo-logo">
    </a>
    <h2>Pengfei's Reveal Slides</h2>
    <p><small>Created by <a href="https://github.com/pengfei99">Pengfei Liu</a></small></p>
    <p><small>04/08/2025</small></p>
</section>
<!-- section for slide 2-->
<section>
    <section>
        <h1>1st Page of slide-2</h1>
    </section>

    <section>
        <h2>2nd Page of slide-2</h2>
    </section>
</section>
```

With the above example, slide 2 has two pages; you can use the down arrow to display the second page of slide-2.

### 3.3 Lists

To show a list of slides is really simple. Below are two examples, slide 3 shows a not ordered list. slide 4 shows an
ordered list.

```html
<!-- section for slide 3-->
<section>
    <h2>No order List</h2>
    <ul>
        <li>Item 1: some long text</li>
        <li>Item 2: some other text</li>
        <li>Item 3: some other texts</li>
        <li>Item 4: some other texts</li>
    </ul>
</section>

<!-- section for slide 4-->
<section>
    <h2>Fantastic Ordered List</h2>
    <ol>
        <li>One is smaller than...</li>
        <li>Two is smaller than...</li>
        <li>Three!</li>
    </ol>
</section>
```

### 3.4 Code

Slide 5 shows an example of how to include code in your presentations.

The start of the code is `<pre><code class="hljs powershell" data-trim data-line-numbers="2,4"><script type="text/template">`
- `hljs powershell`: use `Highlight.js` for syntax highlighting, and the code is `powershell`.
- `data-trim`: ignore the space before and after the code
- `data-line-numbers="2,4"`: highlight line 2, 4 in the code
```html
<!-- section for slide 5-->
<section>
    <h2>Create a Conda Environment</h2>
    <pre><code class="hljs powershell" data-trim data-line-numbers="2,4"><script type="text/template">
      # create a conda environment with python 3.10
      conda create -n myenv python=3.10
      # activate the environment
      conda activate myenv
      # check the version of python in the virtual environment
      python --version
  </script></code></pre>
    <p><small><em>Lines 2 and 4 are essential to create and activate the environment.</em></small></p>
</section>
```

We can also add actions in the code display. In the below example, we use `data-line-numbers="|1|3-4|5|"` to add
highlight actions. When we use the right arrow to move slides, the action will be triggered. The line 1 will be highlighted
with the first action, then line 3-4, then 5.


```html
<!-- section for slide 6-->
<section data-auto-animate>
    <h2 data-id="code-title">Code with animations</h2>
    <pre data-id="code-animation">
        <code class="hljs python" data-trim data-line-numbers="|1|3-4|5|">
        <script type="text/template">
            import matplotlib.pyplot as plt

            plt.plot([1,2,3], [4,5,6])
            plt.title("Basic Plot")
            plt.show()
        </script>
        </code>
    </pre>
</section>
```

## 4. Pdf export

To do a pdf export, you need to add a `print-pdf` style.
```html
 <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js/plugin/print-pdf/print-pdf.css" media="print">
```

In the browser, after index.html url add a query `index.html?print-pdf`, you should see the print-pdf mode
Then use `ctrl+p` to trigger the print dialog of your browser.

If you want to add slide numbers, you need to add a config section `Reveal.configure({ slideNumber: true })`.
Below shows a complete example.

```html
<script>
    // More info about initialization & config:
    // - https://revealjs.com/initialization/
    // - https://revealjs.com/config/
    Reveal.initialize({
        hash: true,

        // Learn about plugins: https://revealjs.com/plugins/
        plugins: [RevealMarkdown, RevealHighlight, RevealNotes]
    });
    Reveal.configure({ slideNumber: true })
</script>
```

## 5. Presenter view

In the import js package section, we have imported `<script src="plugin/notes/notes.js"></script>`, and in the 
plugin section, we have `RevealNotes`. This means we have already included the presenter view plugin.

To show the `presenter view`, you need to press the **s** on the keyboard.

There will be a pop-up window in your browser that displays the presenter view.


