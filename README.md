Breezeless
==========

[Breezeless](https://github.com/ccpalettes/breezeless) is a library that provides a set of
basic or advanced mixins for [LESS](http://lesscss.org)(a CSS pre-processor).

Features
--------

Breezeless focus on providing reusable LESS mixins and resolving complicated headaches in CSS
coding.

- **Easy to use**. All the mixins in Breezeless start with *bl-* prefix, and keep their names
the same as corresponding CSS properties as much as possible.

- **No CSS output**. All the mixins don’t output any CSS, thus, you can use these mixins inside
your own LESS mixins, but you can’t use the bl- prefixed names as CSS classes in HTML.

- **Cross-browser**. Breezeless generates vendor-prefixed versions of a CSS property. Breezeless
follows a rule to decide whether a vendor-prefixed CSS property should be added into a mixin.
If the market share of any version of any kind of the browsers that need a vendor-prefix to
support a specific CSS feature is equal to or greater than 0.02%, the vendor-prefix version CSS
property will be used.(All the market share data is get from [Can I use](http://caniuse.com/).)

- **Merged properties**. Breezeless solves special cases when a standard CSS property is supported
but another CSS property name that is used as a parameter of the former CSS property is maybe not
 supported(need add vendor-prefix) in a browser. For instance, Chrome 35 supports transition, but
doesn’t support transform(need add -webkit- vendor-prefix), with prue CSS, you need write
*transition: -webkit-transform 2s;* in Chrome 35 and write *transition: transform 2s;* in the
latest version of Chrome. Breezeless solves this problem in one line
*.bl-transition(transform 2s);*.

- **Helpes**. Breezeless also provides some useful helpers to deal with common browser compatibility
issues.

How to Use
----------

- Download the [breezeless.less](https://raw.githubusercontent.com/ccpalettes/breezeless/master/src/breezeless.less)
file and place it in your working LESS folder.

- Reference breezeless.less in the top of your LESS files.

```less
	@import (reference) "breezeless.less";

```

Documentation
-------------

### • border

**Description**

Set border style property of an element. A complete border style consists three properties, they
are width, style and color.

**Usage**

- When the length of arguments is less than or equral to 3, same style will be applied to all four
borders. You can pass border width, border style and border color into the arguments individually,
or passed a single value list combined of them to the mixin. The values of width style and color
are optional, the mixin will apply a default value if you leave any of them empty.

```less
	.bl-border(2px);
	.bl-border(2px; #999);
	.bl-border(0 dashed #A87);
```

- When the length of arguments is 4, the four arguments represent top border, right border, bottom
border and left border respectively, each argument is a value list which may consists border width,
border style and border color. If one argument’s value is set to null, then no style will be
applied to the relevant border.

```less
	.bl-border(6px; 3px; 1px; 2px);
	.bl-border(solid #FFF000; null; 3px dashed; 2px dotted #909090);
```

- Default values. By default, border width is set to 1px, border style is set to solid, and border
color is set to #000.

```less
	// equivalent to .bl-border(6px solid #000; 1px solid #FF0; 1px dashed #000; 1px solid blue);
	.bl-border(6px; #FF0; dashed; blue);
```

### • inline-block-fix

**Description**

The inline-block display fix. Fix to support inline-block display for IE6 and IE7.

**Usage**

```less
	.bl-inline-block-fix();
```

### • box-sizing

**Description**

Mixin for box-sizing CSS property.

**Usage**

```less
	.bl-box-sizing();  // default value: border-box
	.bl-box-sizing(border-box);
```

### • user-select

**Description**

Mixin for user-select CSS property.

**Usage**

```less
	.bl-user-select();  // default value: none
	.bl-user-select(text);
```

### • clearfix

**Description**

CLear an element itself which contains floated children.

**Usage**

```less
	.bl-clearfix();
```

### • box-shadow

**Description**

Set single or multiple shadows to one element.

**Usage**

```less
	//single shadow
	.bl-box-shadow(3px 3px 6px 2px rgba(0, 0, 0, 0.2));

	//multiple shadows
	.bl-box-shadow(1px 1px 2px 0 #F00; inset -1px -1px 2px 0 #00F);
```

### • border-radius

**Description**

Set border-radius property of an element.

**Usage**

```less
	.bl-border-radius(e("60px 20px / 30px"));
	.bl-border-radius(10px);
```

### • opacity

**Description**

Set opacity of an element, support IE6 and above.

**Usage**

- You can pass a number to the opacity argument.

```less
	.bl-opacity(0.5);
```

- A percentage number is also valid.

```less
	.bl-opacity(30%);
```

### • transition

**Description**

Set single or multiple transitions to one element.

**Usage**

- BreezeLess defined five transition mixins, one mixin is used to set the shorthand transition
property, and the other four are used to set specific transition CSS property. Each mixin accept
one or more arguments.

- When you need to pass “transform” as the transition-property value, you don’t need to add
vendor-prefixes before “transform”, BreezeLess will do it for you.

- bl-transition. Set the shorthand transition property.

```less
	.bl-transition(transform 1s);
	.bl-transition(width 2s; height 2s);
```

- bl-transition-property. Set transition-property property.

```less
	.bl-transition-property(transform; color);
```

- bl-transition-duration. Set transition-duration property.

```less
	.bl-transition-duration(1s; 2s);
```

- bl-transition-timing-function. Set transition-timing-function property.

```less
	.bl-transition-timing-function(ease);
```

- bl-transition-delay. Set transition-delay property.

```less
	.bl-transition-delay(1s);
```

### • animation

**Description**

Set single or multiple animations to one element.

**Usage**

- BreezeLess defined nine transition mixins, one mixin is used to set the shorthand animation
property, and the other eight mixins are used to set specific animation CSS property. Each mixin
accept one or more arguments.

- bl-animation. Set the shorthand animation property.

```less
	.bl-animation(swing 3s ease 1s 2 alternate both running);
	.bl-animation(bounce 5s; rotate 2s);
```

- bl-animation-name. Set animation-name property.

```less
	.bl-animation-name(swing);
```

- bl-animation-duration. Set animation-duration property.

```less
	.bl-animation-duration(3s; 5s);
```

- bl-animation-timing-function. Set animation-timing-function property.

```less
	.bl-animation-timing-function(ease-in; ease-out);
```

- bl-animation-delay. Set animation-delay property.

```less
	.bl-animation-delay(0s; 3s);
```

- bl-animation-iteration-count. Set animation-iteration-count property.

```less
	.bl-animation-iteration-count(2; infinite);
```

- bl-animation-direction. Set animation-direction property.

```less
	.bl-animation-direction(alternate; reverse; alternate-reverse);
```

- bl-animation-fill-mode. Set animation-fill-mode property.

```less
	.bl-animation-fill-mode(none);
```

- bl-animation-play-state. Set animation-play-state property.

```less
	.bl-animation-play-state(paused; running);
```

### • ellipsis

**Description**

Display an ellipsis (‘…’, U+2026 HORIZONTAL ELLIPSIS) for a clipped text.

**Usage**

```less
	.bl-ellipsis();
```

### • transform

**Description**

Set transform related CSS properties.

**Usage**

- bl-transform. Set the shorthand transform property.

```less
	.bl-transform(rotateX(60deg));
```

- bl-transform-origin. Set transform-origin property.

```less
	.bl-transform-origin(50px 100px);
```

- bl-transform-style. Set transform-style property.

```less
	.bl-transform-style(preserve-3d);
```

- bl-perspective. Set perspective property.

```less
	.bl-perspective(20px);
```

- bl-perspective-origin. Set perspective-origin property.

```less
	.bl-perspective-origin(0 50%);
```

- bl-backface-visibility. Set backface-visibility property.

```less
	.bl-backface-visibility(hidden);
```

More
----

To see more examples and references, you can check the [breezeless source code](https://github.com/ccpalettes/breezeless/blob/master/src/breezeless.less).

