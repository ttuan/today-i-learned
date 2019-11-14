# Scoped CSS

When a <style> tag has `scoped` attribute, its CSS will apply to elements of the
current file only. This is similar to the style encapsulation found in Shadow
DOM.

The <style scoped> will overwrite the global styles generally found in the head,
but only on the sibling/descendent element inside the same parent.

```html
<div>
  <style scoped>
    h1 { color: FireBrick;   }
    p  { color: SaddleBrown; }
  </style>
  <h1>This is an H1 in a scoped div. Regardless of global styles the text should be "FireBrick".</h1>
  <p>This is a paragraph in a scoped div. The text should be "SaddleBrown".</p>
</div>

<p>This is another paragraph, that will unaffected by the scoped style and remain black.</p>
```

[Css-trick: Saving the day with scoped css](https://css-tricks.com/saving-the-day-with-scoped-css/)
