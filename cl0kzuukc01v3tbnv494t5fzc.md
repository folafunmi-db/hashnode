## Tailwind vs Sass/SCSS: Structure and Consistency over Style and Comfort

## Introduction

For this article, I choose the totally non-controversial and completely innocent topic of CSS frameworks, particularly placing the growing Tailwind library and the dominant Sass/SCSS. 

Why? I just love violence 😈. But actually, having read several [opinions](#heading-resources) on both sides of the aisle, I choose to air my views as a contribution to the ongoing debate regarding CSS frameworks. Who knows, someone might just find it useful 🤷🏾‍♂️

It’s difficult to miss the appeal of Sass (Syntactically Awesome Style Sheets), which is an extension of CSS that provides features that seem to have been left out of CSS itself. It preserves the natural feel of writing CSS, but at what cost? 🤔

Alternatively, Tailwind proposes a utility-first approach to CSS where styles pre-exist with classes that can be added to any HTML element. While this has developer experience (DX) benefits, it’s an unnatural way of writing CSS because you don’t actually write CSS, it’s already been written! Aren’t we just writing HTML then? Doesn’t this violate separations of concerns? 🤔

It’s apparent that both Sass and Tailwind recognize that plain CSS needs help. Judging by the widespread adoption of both frameworks, the developer community seems to agree with this premise. As at the time of writing this, Sass has 7.3M+ [weekly downloads](https://www.npmjs.com/package/sass) while TailwindCSS has garnered 2.4M+ [weekly downloads](https://www.npmjs.com/package/tailwindcss) on NPM. In reality, these numbers represent the lower bound of their uses. 

>Both aim to increase the quality of life around writing CSS but their approach however differs.


## What is Sass?

Released in 2006, Sass (Syntactically Awesome Style Sheets) is a mature stylesheet language that’s compiled to CSS (Cascading Style Sheets). Essentially, Sass makes you write CSS more efficiently. It provides features with a fully CSS-compatible syntax.

Sass is preprocessed into CSS. The Sass preprocessor (written in Dart or Ruby) takes input data in Sass or SCSS format and converts it to an output that's pure CSS. This is necessary because browsers can only read CSS code.

This means when you run Sass/SCSS code, you're actually converting your code to CSS. That CSS code output is then used directly by a browser.


### What is SCSS?

To clear up the confusion between Sass and SCSS, SCSS stands for “Sassy CSS” and is a more natural feel to CSS compared to the original Sass syntax. 

The initial Sass syntax uses indentation for nesting and provides a visual hierarchy in the code, its appearance is similar to Python or Ruby but unlike CSS. It uses the `.sass` extension. 

SCSS on the other hand uses curly braces that better resemble regular CSS. It uses the `.scss` extension.

An example of indented Sass syntax from the official docs.

```scss
@mixin button-base()
  @include typography(button)
  @include ripple-surface
  @include ripple-radius-bounded

  display: inline-flex
  position: relative
  height: $button-height
  border: none
  vertical-align: middle

  &:hover
    cursor: pointer

  &:disabled
    color: $mdc-button-disabled-ink-color
    cursor: default
    pointer-events: none

```

An example of SCSS syntax from the official docs.

```scss
@mixin button-base() {
  @include typography(button);
  @include ripple-surface;
  @include ripple-radius-bounded;

  display: inline-flex;
  position: relative;
  height: $button-height;
  border: none;
  vertical-align: middle;

  &:hover { cursor: pointer; }

  &:disabled {
    color: $mdc-button-disabled-ink-color;
    cursor: default;
    pointer-events: none;
  }
}

```

Both perform the same function and have the same capabilities. However, SCSS syntax is more appealing, easier to learn, and personally, it’s the only one I’ve ever used.


## Benefits of Sass

Sass provides features that enable developers to move faster when working on a project. Some benefits include:

- Variables: Facilitates the DRY (Don’t Repeat Yourself) approach. Although regular CSS has this feature at the time of writing albeit with a different syntax.
- Mixins: Even DRY-er approach. This encapsulates certain rules into one.
- Functions: Useful for some folks, but not me 😅 🤷🏾‍♂️.

Read more [here](https://sass-lang.com/guide).

Sass/SCSS makes CSS feel more like a programming language, giving developers flexibility and ease. Typically, for none trivial cases Sass is more maintainable than native CSS as it's easier to collocate by nesting rules for hover and focus selectors.

For example, this is the Sass/SCSS equivalent,

```scss
$button-height: 1rem;
$mdc-button-disabled-ink-color: #e4e4e4;

.button {
  display: inline-flex;
  position: relative;
  height: $button-height;
  border: none;
  vertical-align: middle;

  &:hover {
    cursor: pointer;
  }

  &:focus {
    background: $mdc-button-disabled-ink-color;
  }

  &:disabled {
    color: $mdc-button-disabled-ink-color;
    cursor: default;
    pointer-events: none;
  }
}
```

Of this CSS,

```css
.button {
  display: inline-flex;
  position: relative;
  height: 1rem;
  border: none;
  vertical-align: middle;
}
.button:hover {
  cursor: pointer;
}
.button:focus {
  background: #e4e4e4;
}
.button:disabled {
  color: #e4e4e4;
  cursor: default;
  pointer-events: none;
}

```
## What is Tailwind?

Contrary to Sass/SCSS, Tailwind adopts the atomic CSS style, using the term utility-classes to define a subset of the much broader term. 

Utility classes here mean classes that do one thing well.

### What is Atomic CSS?

Atomic CSS is more of an architectural philosophy rather than one particular library or framework. Notably, Tailwind wasn’t the first on the atomic CSS scene. There are other libraries that adopt the atomic CSS pattern like [Tachyons](http://tachyons.io/).

According to [John Polacek](https://css-tricks.com/author/johnpolacek/) in his [article](https://css-tricks.com/lets-define-exactly-atomic-css/),

>Atomic CSS is the approach to CSS architecture that favors small, single-purpose classes with names based on visual function.

Please note that Tailwind classes aren’t the same inline styles. The differences have best been captured elaborately in [this article](https://frontstuff.io/in-defense-of-utility-first-css) by [Sarah Dayan](https://twitter.com/frontstuff_io). Rather than go through the reasons outlining differences, I’ll just give a scenario instead.

Say you want a card profile component that appears in landscape on a widescreen with left-aligned text but portrait on a smaller screen with center-aligned text, and it also changes the background color, shadows, and opacity when hovered or focused. 

Can inline styles help you out there? Yeah, I didn’t think so.

## My comparison

As the title implies, the essence of this article is to give my take on the two frameworks and explain my thought process behind them.

There are undeniable advantages for both Tailwind and Sass. Based on your preferences you’d place more weight on one over the other in certain instances. 

In all honesty, I initially started out with Sass. I loved it, it saved me from repetitive and cumbersome native CSS. But per my experience with both as well as recent updates, Tailwind has evolved to become my go-to CSS framework on most new projects. Here are my reasons:

 ### 1. Composability & Modularity

With Sass, there has to be extra effort on the part of the developer to achieve a modular system in order to make CSS more manageable and robust. This can be done using different modular CSS methodologies like Object Oriented CSS (OOCSS) or Block, Element, and Modifier (BEM), etc. More on those [here](https://snipcart.com/blog/organize-css-modular-architecture).

This however is a given with Tailwind. Tailwind classes by their atomic nature are able to effectively build composable isolated components.

 ### 2. Naming

I’m sure there are developers out there who pride themselves on being able to come up with clever and suitable names for CSS classes. I am not one of those people.

Let’s say you want to name classes for a card that holds the ads for a site. You might come up with,
```scss
.car--card {...}
.car--card .img {...}
.car--card .img img{...}
.other {...}
```
Further down the line, you discover the same design is used for other ads on your app. This can become,
```scss
.ad--card {...}
.ad--card .img {...}
.ad--card .img img{...}
.other {...}
```
Then later you discover that the same design is used for the card that show your app services. This it becomes,
```scss
.media--card {...}
.media--card .img {...}
.media--card .img img{...}
.other {...}
```
🤦🏾‍♂️ Not the best of examples, but do you see my point?

Tailwind takes the burden of naming off my shoulders by providing suitably named classes(according to function rather than form) which are well-documented classes and can always be looked up whenever needed. The utility classes mean the same things wherever, whenever.

 ### 3. Responsiveness

Tailwind pushes you to use best practices when developing. Notable it enforces the mobile-first approach, thereby forcing the developer to think of responsiveness right from the get-go. 

It encourages a robust approach that takes into consideration different screen sizes and orientations. This can also be easily extended in the tailwind config file.

 ### 4. Onboarding new developers

It takes developers some time to get accustomed to any new codebase, even ones that are in familiar language. Specific design decisions have to be understood enough to be followed. Essentially, newer developers have to interpret what someone else meant and whether their decisions were deliberate and contextual, or arbitrary and habitual.

According to Daniel Terhorst-North in writing about [CUPID](https://dannorth.net/2022/02/10/cupid-for-joyful-coding),

>The greatest programming trait is empathy; empathy for your users; empathy for support folks; empathy for future developers; any of whom may be future you. Writing “code that humans can understand” means writing code for someone else. This is what idiomatic code means.

New developers can get accustomed to Tailwind classes in a short time and this knowledge is transferable across projects. Although this would still be more than the time to learn Sass since, it is in appearance, still CSS.

Sass provides more freedom in development however, this can lead to a problem of clarity. 

 ### 5. Clarity

The flexibility and freedom provided by Sass can serve as a blessing and a curse. Nesting selectors and media queries can hasten development for the author of a codebase but not so much for a maintainer that'd come in later.

It's quite easy to create confusion due to nesting in Sass where elements can be selected from (almost) wherever. Granted, this is also possible with native CSS and isn't peculiar to Sass however it's an issue solved by atomic CSS. So, this is more of an architectural issue rather than an intrinsic one.

I once wrote mixins using Sass like: 

```scss
@mixin font-face($weight: 500, $style: normal) {
  font-weight: $weight;
  font-style: $style;
  font-family: Poppins, BR Firma;
}

@mixin font-look($font-size, $line-height) {
  font-size: $font-size;
  line-height: $line-height;
}

@mixin font-look-mediaQuery($font-size, $line-height, $screen-width: 600px) {
  @media only screen and (max-width: $screen-width) {
    font-size: $font-size;
    line-height: $line-height;
  }
}

.p-bigbold {
  /* Paragraph Big Bold */
  @include font-face(500);
  @include font-look(1.125rem, 1.4375rem);
  @include font-look-mediaQuery(0.875rem, 1.125rem);
}

```

When I wrote this only God and I understood it, now only God does 😂

 ### 6. Resilience

Here I ask the question, How easy is it to mess up?

For Tailwind making changes feels safer. Sass/SCSS can be global(depends though, there’s such a thing as scoped CSS) and you never know what you might break when you make a change. Classes in your HTML are local, so you can change them without worrying about something else breaking.

 ### 7. Predictability & Consistency

Tailwind is fully deterministic. It does the same thing everywhere. Compared to Sass a component can be copied and pasted in a different and there’s a better chance it looks the same. With Sass, it really depends on the architecture. 

No need to fight specificity battles, I prefer the consistency of Tailwind.

 ### 8. Constraints

Being able to follow a design system is one of the hallmarks of a good frontend developer but in cases where there isn't a clear design, system Tailwind provides sane defaults that are invaluable.

Tailwind's utility classes help you work within the constraints of a system instead of littering your stylesheets with arbitrary values. 

In practice, one way(my preferred way) of sticking to a design system is to define constants that hold the values of all different sizes, colours, fonts, and all that a design system entails. Then apply those constants wherever needed in the codebase.

This is possible in both Sass, with the use of variables, and also tailwind with the use of custom classes. But without a doubt, Tailwind's tooling takes the cake.

 ### 9. Tooling

On VScode (my IDE of choice) the IntelliSense provided when styling with Tailwind is second to none.

I found Tailwind's syntax intuitive yet the tooling makes writing Tailwind even easier. In fact, I only got to know some CSS rules when I began writing Tailwind.

Yes, I'm looking at you `whitespace-nowrap`.


## Concerns

As with all things, there are demerits and trade-offs. Some of the ones I list here are per my use as at the time of writing. 

Notably, there are other concerns with Tailwind that have been handled by subsequent upgrades. I won't dwell much on those in the section below.

 ### 1. Breaking Constraints

Tailwind is utility-first, not utility-only. Asides from the practice of just adding regular CSS or Sass styles alongside Tailwind classes, the maintainers of Tailwind provided a way to add in custom sizes, colours, etc directly in the Tailwind classes.

This is possible thanks to the Tailwind JIT (Just In Time) compiler. Just like Sass's nesting feature, this is also a blessing and a curse.

It helps in cases where the developer wants one-off dimensions that are not available in the default Tailwind classes and isn't worth creating custom classes for. But then it provides an avenue to keep using custom values all over the app.

Although this is unlikely, you'd be surprised what you'd find in some codebases 😬


 ### 2. Size

Although Tailwind utilizes PostCSS to remove all unused styles, it's still larger in production than if Sass had been used. 

This actually isn't much of an issue since if your CSS is in the range of kilobytes there are far better ways to improve performance on your site. So, this isn't so serious but it was worth mentioning for the sake of being thorough.

Also, keep in mind that Tailwind used to be massive in development but in recent upgrades, the JIT compiler has deployed in response to this. However, this has created a different problem which I elaborate on below.


 ### 3. Debugging

Recent upgrades of the JIT compiler to Tailwind development have made debugging using the browser dev tools more difficult in some cases.

This is due to the JIT compiler creating classes on the fly, therefore, removing the need to purge unused CSS classes since they were never created in the first place. 

However, because the classes are created on the fly any class not specified somewhere in the code doesn't exist and cannot be added ad hoc in the dev tools. This is needed sometimes to quickly see how a certain class affects the styles.

This can become especially burdensome if there are several custom tailwind classes added to the config.

>There are tools to help with this though like Devtools for [Tailwind](https://devtoolsfortailwind.com/).

 ### 4. Theming

This might be more of a personal preference but I’m not for the `bg-white dark:bg-black` syntax which is the default way of theming in Tailwind. Why have classes that do nothing half the time? What if I want more than two themes?

I’d rather have variables that I can switch out at will. Another approach is to use custom classes that are toggled like the approach that [Next-themes](https://github.com/pacocoursey/next-themes) takes. However, this is specific to NextJS.


## Conclusion

As a note, it’s not the tool but the craftsman that does good work. Tailwind provides benefits out of the box, but these can be opted out of following bad usage of the library.

>Everything rises and falls on architecture.

In summary, I’ll advise choosing Tailwind in a new project as it presents sane defaults which help provide structure to an application.

There are other alternatives to just Tailwind or Sass. The option of Styled-components is also a good one, which enables the use of Sass/SCSS syntax within its tagged templates. You can also use Tailwind in conjunction with Styled-components using a library like [Twin.macro](https://github.com/ben-rogerson/twin.macro) or [Twind](https://twind.dev/).

For a holistic view of the opposition to Tailwind, you can read a different point of view [here](https://www.aleksandrhovhannisyan.com/blog/why-i-dont-like-tailwind-css/#4-tailwind-is-bloated).

I hope this article helps. 

Please share your thoughts and opinions in the comments section below.

## Resources

1. https://frontstuff.io/no-utility-classes-arent-the-same-as-inline-styles
2. https://frontstuff.io/in-defense-of-utility-first-css
3. https://johnpolacek.github.io/the-case-for-atomic-css/
4. https://www.codecademy.com/resources/blog/what-is-sass/
5. https://snipcart.com/blog/organize-css-modular-architecture
6. https://www.swyx.io/why-tailwind/?ck_subscriber_id=1095223109
7. https://css-tricks.com/lets-define-exactly-atomic-css/
