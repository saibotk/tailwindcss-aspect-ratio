# @tailwindcss/aspect-ratio

A plugin that provides a composable API for giving elements a fixed aspect ratio.


## Installation

Install the plugin from npm:

```sh
# Using npm
npm install @tailwindcss/aspect-ratio

# Using Yarn
yarn add @tailwindcss/aspect-ratio
```

Then add the plugin to your `tailwind.config.js` file:

```js
// tailwind.config.js
module.exports = {
  theme: {
    // ...
  },
  plugins: [
    require('@tailwindcss/aspect-ratio'),
    // ...
  ],
}
```

## Usage

Combine the `aspect-w-{n}` and `aspect-h-{n}` classes to specify the aspect ratio for an element:

```html
<div class="aspect-w-16 aspect-h-9">
  <iframe src="https://www.youtube.com/embed/dQw4w9WgXcQ" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
```

Use `aspect-none` to remove any aspect ratio behavior:

```html
<div class="aspect-w-16 aspect-h-9 lg:aspect-none">
  <!-- ... -->
</div>
```

When removing aspect ratio behavior, if nested elements have `w-{n}` or `h-{n}` classes, ensure they are re-declared with a matching breakpoint prefix:

```html
<div class="aspect-w-16 aspect-h-9 lg:aspect-none">
  <img src="..." alt="..." class="w-full h-full object-center object-cover lg:w-full lg:h-full" />
</div>
```

Note that due to the way this currently needs to be implemented ([the old padding-bottom trick](https://css-tricks.com/aspect-ratio-boxes/)) you need to assign the aspect ratio to a _parent_ element, and make the actual element you are trying to size the only child of that parent.

Once the [`aspect-ratio` property](https://developer.mozilla.org/en-US/docs/Web/CSS/aspect-ratio) is supported in modern browsers, we'll add official support to Tailwind CSS itself and deprecate this plugin.

Aspect ratio classes up to 16 are generated by default:

| Width | Height |
| --- | --- |
| `aspect-w-1` | `aspect-h-1` |
| `aspect-w-2` | `aspect-h-2` |
| `aspect-w-3` | `aspect-h-3` |
| `aspect-w-4` | `aspect-h-4` |
| `aspect-w-5` | `aspect-h-5` |
| `aspect-w-6` | `aspect-h-6` |
| `aspect-w-7` | `aspect-h-7` |
| `aspect-w-8` | `aspect-h-8` |
| `aspect-w-9` | `aspect-h-9` |
| `aspect-w-10` | `aspect-h-10` |
| `aspect-w-11` | `aspect-h-11` |
| `aspect-w-12` | `aspect-h-12` |
| `aspect-w-13` | `aspect-h-13` |
| `aspect-w-14` | `aspect-h-14` |
| `aspect-w-15` | `aspect-h-15` |
| `aspect-w-16` | `aspect-h-16` |

## Configuration

You can configure which values and variants are generated by this plugin under the `aspectRatio` key in your `tailwind.config.js` file:

```js
// tailwind.config.js
module.exports = {
  theme: {
    aspectRatio: {
      1: '1',
      2: '2',
      3: '3',
      4: '4',
    }
  },
  variants: {
    aspectRatio: ['responsive', 'hover']
  }
}
```
