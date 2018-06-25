# unit-no-unknown

Disallow unknown units.

```css
a { width: 100pixels; }
/**           ↑
 *  These units */
```

This rule considers units defined in the CSS Specifications, up to and including Editor's Drafts, to be known.

## Options

### `true`

The following patterns are considered violations:

```css
a {
  width: 10pixels;
}
```

```css
a {
  width: calc(10px + 10pixels);
}
```

The following patterns are *not* considered violations:

```css
a {
  width: 10px;
}  
```

```css
a {
  width: 10Px;
}  
```

```css
a {
  width: 10pX;
}  
```

```css
a {
  width: calc(10px + 10px);
}
```

## Optional secondary options

### `ignoreUnits: ["/regex/", "string"]`

Given:

```js
["/^my-/", "custom"]
```

The following patterns are *not* considered violations:

```css
a {
  width: 10custom;
}
```

```css
a {
  width: 10my-unit;
}
```

```css
a {
  width: 10my-other-unit;
}
```
### `ignoreValue: ["/regex/", "string"]`

Given:

```js
["/[0-9]x/", "10custom"]
```

The following patterns are *not* considered violations:

```css
div {
  background-image: image-set(
	     '/images/some-image-1x.jpg' 1x,
	     '/images/some-image-2x.jpg' 2x,
	     '/images/some-image-3x.jpg' 3x,
	);
}

```css
div {
  width: 10custom;
}
```

