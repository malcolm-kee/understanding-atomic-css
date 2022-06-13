---
---

<div class="w-full h-full flex justify-center items-center pb-6">

<div>

# Table of content

<ol>
  <li>Typical Approaches of Writing CSS</li>
  <li>Atomic CSS and Tailwind CSS</li>
  <li>Drawbacks and Benefits</li>
</ol>

</div>

</div>

---

### Drawbacks of Tailwind CSS:

1. Learning curve to get familiar with the class name
1. Very long class name when viewing HTML directly

---

### Drawbacks of Tailwind CSS:

1. Learning curve to get familiar with the class name -> cost of any CSS framework.
1. Very long class name when viewing HTML directly -> abstracted with UI framework component.

---

### Benefits of Tailwind CSS:

1. Better developer experience - no context switching and no selector naming
1. Promote use of design token - intellisense encourages developer to use predefined scales instead of write custom rule.
1. Reduce scope of CSS - make markup copy pastable
1. Reduce redundancy - smaller CSS file sizes

---

# Questions?

Some FAQ for inspirations:

1. Why isn't this just inline style?
1. Does it means that we should not have CSS component, like `.button`?
1. CSS file size is smaller, but isn't that just cause the HTML/JS size bigger?
1. But what about complex CSS, like `grid-template-columns`?
1. What type of projects is not fit for Tailwind CSS?

---

Q: Why isn't this just inline style?

A:

<img src="/atomic-css.png" class="block w-[500px] mx-auto" alt="" />

---

Q: CSS file size is smaller, but isn't that just cause the HTML/JS size bigger?

A:

<img src="/class-size.png" class="block w-[500px] mx-auto" alt="" />

And Gzip like Atomic CSS because repetitions means a better compression ratio.

---

Q: Does it means that we should not have CSS component, like `.button`?

A:

With React, we usually abstract CSS component with components, so it is fine to not have that `.button` class. However, if there is use case that you want to create some reusable class outside React (e.g. in HTML directly), Tailwind make it straightforward as well.

<div class="grid grid-cols-2 gap-4">

```html
<div class="bg-white shadow px-6 py-6 sm:px-8"></div>
```

```html
<div class="card"></div>
<style>
  .card {
    @apply bg-white shadow px-6 py-6 sm:px-8;
  }
</style>
```

</div>

The workflow is: utility first, abstract later.

---

Q: But what about complex CSS, like `grid-template-columns`?

A:

If you need that, just write custom CSS.

The point is not that Tailwind will be the workflow that cover ALL of your CSS code, but most of them to make you productive.

As a metaphor, React doesn't need to covers every part of UI to be a good tool to improve your development workflow.

---

Q: What type of projects is not fit for Tailwind CSS?

A:

I can think of few projects that should not use Tailwind CSS:

- projects that want a single CSS stylesheet to be used in multiple platforms (like used in CMS or multiple frameworks)
- projects that does not use frontend framework
- UI libraries that allows some customization, e.g. Ant Design
