---
---

<div class="w-full h-full flex justify-center items-center pb-6">

<div>

# Table of content

<ol>
  <li>Typical Approaches of Writing CSS</li>
  <li>Atomic CSS and Tailwind CSS</li>
  <li class="opacity-30">Drawbacks and Benefits</li>
</ol>

</div>

</div>

---

<div class="h-full w-full flex items-center">
    <div class="max-w-2xl mx-auto">
        <div class="text-3xl leading-normal">
            Having some CSS classes that can be reused for specific UI component is nice
        </div>
        <div class="text-3xl leading-normal">
            What if, we don't limit to UI component and try to maximize CSS reuse?
        </div>
    </div>
</div>

---

<div class="max-w-2xl mx-auto">

If we able to maximize CSS reuse:

1. Our CSS will stop growing over time, as adding new features/pages does not requires adding new CSS rules.
1. We reduce the risk of breakage while adding CSS, which by design, is global scope.

</div>

<div class="max-w-xl mx-auto">
  <div class="text-3xl leading-relaxed text-center my-6">
    So how we maximize CSS reuse?
  </div>
  <div v-click class="text-3xl leading-relaxed text-center my-6">
    Answer: by keeping them small.
  </div>
</div>

---

# Atomic CSS - Maximizing CSS Reuse

1. Atomic CSS - the approach to CSS architecture that favors small, single-purpose classes with names based on visual function.
1. It was [firstly introduced in Yahoo](https://css-tricks.com/thierry-koblentz-atomic-css/) by Thierry Koblentz to avoid site maintenance requiring change of CSS, in order to reduce the risk of breakage.

---

# Tailwind CSS

1. Tailwind CSS - a CSS framework that is based on Atomic CSS. ([Demo](https://play.tailwindcss.com/r3fMxpjJjy))

<div class="grid grid-cols-2 gap-4">

```css
.text-left { text-align: left; }

.bg-primary-500 { background-color: #ef4444; }

.truncate {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

```html
<div class="bg-white border rounded shadow overflow-hidden">
  <img 
    alt="" 
    src="https://raw.githubusercontent.com/malcolm-kee/malcolm-kee/master/src/assets/malcolm-in-cpg.jpg" 
    class="block w-full h-auto" 
  />
  <div class="p-1">
    <h2 class="text-lg text-gray-800">Malcolm Kee</h2>
    <p class="text-gray-600">Malcolm is a guy that love coding and Harry Potter.</p>
  </div>
</div>
```

</div>

