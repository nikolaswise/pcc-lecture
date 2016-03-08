# CSS: Rules to Style By

> Presentation for Esri Developer Summit 2016
> Paul C Pederson

CSS can quickly become an unmanageable nightmare of important rules and overly-specific selectors, don't let it.

Below is the content of the presentation in `README` format, with links! You can also check out the slide version at [css-rules.surge.sh](http://css-rules.surge.sh).

## Who is this guy?

## @paulcpederson
- front end developer + designer at Esri
- half a decade working with CSS at scale
- currently working on Calcite Web

## What's the problem with CSS?
CSS is naturally drawn towards chaos, disorder, and complexity.

From this:

```css
.right {
  float: right;
}
```

to this:

```css
.right,
.rtl .left,
.rtl #top .site-brand,
.rtl #top .site nav,
.rtl #top .site nav li,
.rtl .cui-carousel-item,
.rtl .case-study-group .block,
.rtl fieldset label,
.rtl .feature .feature-text,
.rtl .feature .feature-block,
.rtl .header .header-inner,
.rtl .navigation-bar header,
.rtl .navigation-bar nav,
.rtl dl.inline dt,
.rtl .toolbar .btn,
.rtl .toolbar .dropdown-wrapper,
.rtl .btn-group a,
.rtl .input-list li label,
.rtl input[type="checkbox"],
.rtl input[type="radio"],
.rtl .navigation-bar header h1,
.rtl .navigation-bar-nav ul li,
.rtl .tab-group .tab-nav .tab {
  float: right !important !important !important;
}
```

## CSS has a tendency to get:
1. Larger
2. More Complex
3. Harder to change
4. Harder to maintain

![](buggy.gif)

## It doesn't have to be terrible!

## Lots of smart systems:
- BEM
- SMACSS
- OOCSS

## Preprocessors can help, too!
- Stylus
- Sass
- LESS
- PostCSS
- Myth

### But you don't need any of those to have better CSS...

Below are some simple ways to make CSS easier to work with down the road.

## 1. Use low-specificity selectors

```css
.sidebar {}               /* less specific */
#page .sidebar div > a {} /* waaay more specific */
```

## 2. Don't use ID or element selectors

bad:

```css
#banner {
  background-color: blue;
}

#banner h1 {
  color: white;
}
```

good:

```css
.banner {
  background-color: blue;
}

.banner-title {
  color: white;
}
```

## 3. Don't depend on a certain markup structure

bad:

```css
.header ul li a {
  margin-right: 20px;
}
```

good:

```css
.header-link {
  margin-right: 20px;
}
```

## 4. Don't use inline styles

bad:

```html
<div style="background-color: red; color: white; border: 1px solid black;">
  Alert!
</div>
```

good:

```html
<div class="alert">
  Alert
</div>
```

```css
.alert {
  background-color: red;
  color: white;
  border: 1px solid black;
}
```

## 5. Don't use !important

Seriously! Don't do it!

## 6. Prefix modifier classes

bad:

```css
.btn {
  padding: .25em;
  background-color: blue;
  color: white;
}

.btn.red {
  background-color: red;
}
```

good:

```css
.btn {
  padding: .25em;
  background-color: blue;
  color: white;
}

.btn-red {
  background-color: red;
}
```

## 7. Write Small Rules

bad:

```css
.widget {
  border: 1px solid #ddd;
  padding: 4em;
  background-color: #efefef;
  font-size: 4rem;
  margin-top: 24px;
  margin-bottom: 24px;
}

.gadget {
  border: 1px solid #ddd;
  padding: 4em;
  background-color: #efefef;
  font-size: 4rem;
  margin-top: 16px;
  margin-bottom: 24px;
}
```

good:

```css
.panel {
  border: 1px solid #ddd;
  padding: 4em;
  background-color: #efefef;
}

.font-large { font-size: 4rem; }

.leader-1 { margin-top: 16px; }
.leader-2 { margin-top: 24px; }

.trailer-2 { margin-bottom: 24px; }
```

## 8. Use a prefix for JavaScript hooks

bad:

```html
<a href="#" class="btn">Click Me!</a>
```

good:

```html
<a href="#" class="btn js-btn">Click Me!</a>
```