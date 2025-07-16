# slides_with_reveal_js

**reveal.js** is an open source `HTML presentation framework`. It's a tool that enables anyone with a web browser 
to create fully-featured and beautiful presentations for free.

The official site can be found [here](https://revealjs.com/installation/).

In this tutorial, I will try to use reveal js to create my first HTML slides.

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
				plugins: [ RevealMarkdown, RevealHighlight, RevealNotes ]
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
						<img src="images/casd.svg" alt="casd logo" style="height: 180px; margin: 0 auto 4rem auto; background: transparent;" class="demo-logo">
					</a>
					<h2>Pengfei's Reveal Slides</h2>
					<p><small>Created by <a href="https://github.com/pengfei99">Pengfei Liu</a></small> </p>
                    <p><small>04/08/2025</small> </p>
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


## 4. Pdf export

## 5. Presenter view


