## Style elements in combination with another
ex: Want to style margin between h1 and p specifically (warning this selects and paragraphs after h1)
```css
/* Paragraphs that are siblings of and
   subsequent to any H1 */
h1 ~ p {
  color: red;
}
```

To style only direct descendent, use `+` instead of `~`
