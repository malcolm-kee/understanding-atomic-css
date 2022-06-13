---
---

<div class="w-full h-full flex justify-center items-center pb-6">

<div>

# Table of content

<ol>
  <li>Typical Approaches of Writing CSS</li>
  <li class="opacity-30">Atomic CSS and Tailwind CSS</li>
  <li class="opacity-30">Drawbacks and Benefits</li>
</ol>

</div>

</div>

---

# Approach 1: Semantic CSS

Separation of Concern: HTML is for content, CSS is for styling.

<div class="grid grid-cols-2 gap-4">

<div>

<div class="relative">

```html
<h1 class="text-center">Welcome</h1>
```

<emojione-v1-cross-mark class="absolute bottom-0 right-0" />

</div>

</div>

<div class="relative">

```html
<style>
  .greeting {
    text-align: center;
  }
</style>
<h1 class="greeting">Welcome</h1>
```

<emojione-v1-left-check-mark class="absolute bottom-0 right-0" />

</div>

</div>

The poster child example that illustrates this approach is [CSS Zen Garden](http://www.csszengarden.com/).

---

# Semantic CSS Workflow

<div class="grid grid-cols-2 gap-4">

<div>

1. Write the markup.

```html
<div>
  <img alt="" src="https://raw.githubusercontent.com/malcolm-kee/malcolm-kee/master/src/assets/malcolm-in-cpg.jpg" />
  <div>
    <h2>Malcolm Kee</h2>
    <p>Malcolm is a guy that love coding and Harry Potter.</p>
  </div>
</div>
```

</div>

<div v-click>

2. Add descriptive class based on content

```html {1}
<div class="author-bio">
  <img alt="" src="https://raw.githubusercontent.com/malcolm-kee/malcolm-kee/master/src/assets/malcolm-in-cpg.jpg" />
  <div>
    <h2>Malcolm Kee</h2>
    <p>Malcolm is a guy that love coding and Harry Potter.</p>
  </div>
</div>
```

</div>

</div>

<div v-click>

3. Use the class as "hook" in CSS/SCSS to style the markup.

```scss
.author-bio {
  background-color: white;
  border: 1px solid hsl(0,0%,85%);
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  overflow: hidden;
  > img {
    display: block;
    width: 100%;
    height: auto;
  }
  > div {
    padding: 1rem;
    > h2 {
      font-size: 1.25rem;
      color: rgba(0,0,0,0.8);
    }
    > p {
      font-size: 1rem;
      color: rgba(0,0,0,0.75);
      line-height: 1.5;
    }
  }
}
```

</div>

---

<div class="w-60 mx-auto">
  <div class="author-bio">
    <img alt="" src="https://raw.githubusercontent.com/malcolm-kee/malcolm-kee/master/src/assets/malcolm-in-cpg.jpg" />
    <div>
      <h2>Malcolm Kee</h2>
      <p>Malcolm is a guy that love coding and Harry Potter.</p>
    </div>
  </div>
</div>

<link href="/author-bio.css" rel="stylesheet" />

---

<div class="flex items-center h-full max-w-xl mx-auto pb-6">

1. Although its goal is to "separate the concerns", but there is still coupling between the CSS and the HTML.
1. The markup isn't concerned with styling, but the CSS is very concerned with the markup structure.

</div>

---

# Approach 1 Improved: Decoupling Styles from Structure

1. Adding classes to each markup so styles can target them directly.
1. Most well known methodology: Block Element Modifier (BEM).

---

<div class="grid grid-cols-2 gap-4">

<div>

The markup:

```html
<div class="author-bio">
  <img class="author-bio__image" alt="" src="https://raw.githubusercontent.com/malcolm-kee/malcolm-kee/master/src/assets/malcolm-in-cpg.jpg" />
  <div class="author-bio__content">
    <h2 class="author-bio__name">Malcolm Kee</h2>
    <p class="author-bio__body">Malcolm is a guy that love coding and Harry Potter.</p>
  </div>
</div>
```

</div>

<div>

The style:

```css
.author-bio {
  background-color: white;
  border: 1px solid hsl(0,0%,85%);
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  overflow: hidden;
}

.author-bio__image {
  display: block;
  width: 100%;
  height: auto;
}

.author-bio__content {
  padding: 1rem;
}

.author-bio__name {
  font-size: 1.25rem;
  color: rgba(0,0,0,0.8);
}

.author-bio__body {
  font-size: 1rem;
  color: rgba(0,0,0,0.75);
  line-height: 1.5;
}
```

</div>

</div>

---

<div class="grid grid-cols-2 gap-4">

<div>

## Improvements:

1. selector specificity is low
1. CSS is less dependent on markup structure.

</div>
<div v-click>

## Drawbacks:

1. very verbose class names
1. every element that you need to apply style needs its own class name (naming is hard!)

</div>

</div>

---

## Then, one day...

<div class="max-w-xl mx-auto flex items-start gap-4 py-6">
  <div class="w-[600px]">
    <h3 class="!text-base font-extrabold mb-1">Author Bio</h3>
    <div class="author-bio">
      <img alt="" src="https://raw.githubusercontent.com/malcolm-kee/malcolm-kee/master/src/assets/malcolm-in-cpg.jpg" />
      <div>
        <h2>Malcolm Kee</h2>
        <p>Malcolm is a guy that love coding and Harry Potter.</p>
      </div>
    </div>
  </div>
  <div>
    <h3 class="!text-base font-extrabold mb-1">Article Preview</h3>
    <div class="article-preview">
      <img alt="" src="https://images.unsplash.com/photo-1555066931-4365d14bab8c?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=700&h=400&q=80" />
      <div>
        <h2>Setting Up Your Machine for Development</h2>
        <p>Setting up your machine properly for development is important to maximize your productivity as a software engineer. Learn how to do that.</p>
      </div>
    </div>
  </div>
</div>

<link href="/author-bio.css" rel="stylesheet" />
<link href="/article-preview.css" rel="stylesheet" />

---

<div class="flex gap-5">

<div>
  <img src="/components.jpg" alt="" class="w-[500px]" />
</div>

<div>

1. We can't use `.author-bio` CSS class.
1. If we create its own classes for the markup (`.article-preview`, `.article-preview__image` etc), how should we handle the CSS?

<div class="flex gap-4 my-6">
  <div class="flex-1 shadow p-3" v-click>
    <div class="font-bold">Option 1: Duplicate the Styles</div>
    <p class="text-sm">Copy/paste the <code>.article-preview</code> classes</p>
    <p class="text-sm">... and violates DRY principle.</p>
  </div>
  <div class="flex-1 shadow p-3" v-click>
    <div class="font-bold">Option 2: Use <code>@extend</code></div>
    <p class="text-sm">Use <code>@extend</code> directive supported by most CSS preprocessors</p>
    <p class="text-sm">... which is <a href="https://csswizardry.com/2014/11/when-to-use-extend-when-to-use-a-mixin/" target="_BLANK" rel="noopener noreferrer">not recommended in general</a>.</p>
  </div>
</div>

<p class="text-3xl text-center my-6" v-click>OR...</p>

</div>

</div>

---


<div class="flex items-start gap-4">

<div>

# Approach 2: Content agnostic component

1. Author Bio and Article Preview components have _**nothing in common from a semantic perspective**_, but they have _**a lot in common from a design perspective**_.
1. Let's create a component based on the design perspective, a `.media-card`.

</div>

<div v-click>

```css
.media-card {
  background-color: white;
  border: 1px solid hsl(0,0%,85%);
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  overflow: hidden;
}

.media-card__image {
  display: block;
  width: 100%;
  height: auto;
}

.media-card__content {
  padding: 1rem;
}

.media-card__name {
  font-size: 1.25rem;
  color: rgba(0,0,0,0.8);
}

.media-card__body {
  font-size: 1rem;
  color: rgba(0,0,0,0.75);
  line-height: 1.5;
}
```

</div>

</div>

---

<div class="w-full h-full flex items-center max-w-xl pb-12">

1. We remove the duplication from CSS, but looking closer, we've actually "mixing concern" now, as the HTML includes the visual decision (`.media-card`).
1. If we need to change how the Author Bio or Article Preview looks like, we need to update the HTML file. With previous approach, we just need to update the CSS without touching the HTML.

</div>

---

<p class="text-3xl">But think about this:</p>

What if we needed to add a new type of content that also needed the same styling?

<div v-click>

1. With "semantic" approach, we need to create a new sets of HTML and CSS.
1. With this content-agnostic approach, we just need to write the new HTML with the classes, without adding new CSS.

<blockquote class="mt-6">
  <div class="text-xl p-3">
    If adding new UI always requires change of markup and CSS, are they a single concern or separate concerns? Which approach (semantic or content-agnostic) is a better abstraction?
  </div>
</blockquote>

</div>

<div v-click>
  <div class="text-3xl text-center my-6 max-w-lg mx-auto">
    Maybe, separation of concern is not the right way to look at this.
  </div>
</div>

---

## It is about choosing the dependency direction.

<div class="mt-10">

| "Semantic" Approach          | Content Agnostic Approach    |
| ---------------------------- | ---------------------------- |
| CSS depends on HTML          | HTML depends on CSS          |
| HTML does not care how it look. <br /> CSS cares what structure/class of HTML | CSS does not care what is the HTML. <br /> HTML care what CSS are available |
| HTML is restyleable, but CSS is not reusable | CSS is reusable, HTML is not restyleable |
| Examples: CSS Zen Garden     | Examples: Bootstrap |

</div>

<div v-click>
  <div class="text-3xl leading-relaxed text-center my-6 max-w-xl mx-auto">
    Which one is more common requirement? <br />Restylable HTML or reusable CSS?
  </div>
</div>

---

<div class="h-full w-full flex items-center">

<div class="text-5xl leading-normal">The popularity of Bootstrap tells us having reusable CSS by sacrificing restyleable HTML is a worthy tradeoff in most projects.</div>

</div>