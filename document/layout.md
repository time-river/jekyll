####TO INCLUDE A BASIC MDL LAYOUT COMPONENT:

 1. Code a <div> element. This is the "outer" div that holds the entire layout. Add MDL classes as indicated, separated by spaces, to the div using the class attribute.
```
<div class="mdl-layout mdl-js-layout">
</div>
```
 2. Inside the div, code a <header> element. This holds the header row with navigation links that is displayed on large screens, and the menu icon that opens the navigation drawer for smaller screens. Add the MDL class to the header using the class attribute.
```
<div class="mdl-layout mdl-js-layout">
  <header class="mdl-layout__header">
  </header>
</div>
```
 3. Inside the header, add a <div> to produce the menu icon, and include the MDL class as indicated. The div has no content of its own.
```
<div class="mdl-layout mdl-js-layout">
  <header class="mdl-layout__header">
    <div class="mdl-layout-icon"></div>
  </header>
</div>
```
 4. Still inside the header, add another <div> to hold the header row's content, and include the MDL class as indicated.
```
<div class="mdl-layout mdl-js-layout">
  <header class="mdl-layout__header">
    <div class="mdl-layout-icon"></div>
    <div class="mdl-layout__header-row">
    </div>
  </header>
</div>
```
 5. Inside the header row div, add a span containing the layout title, and include the MDL class as indicated.
```
<div class="mdl-layout mdl-js-layout">
  <header class="mdl-layout__header">
    <div class="mdl-layout-icon"></div>
    <div class="mdl-layout__header-row">
      <span class="mdl-layout__title">Simple Layout</span>
    </div>
  </header>
</div>
```
 6. Following the span, add a <div> to align the header's navigation links to the right, and include the MDL class as indicated.
```
<div class="mdl-layout mdl-js-layout">
  <header class="mdl-layout__header">
    <div class="mdl-layout-icon"></div>
    <div class="mdl-layout__header-row">
      <span class="mdl-layout__title">Simple Layout</span>
      <div class="mdl-layout-spacer"></div>
    </div>
  </header>
</div>
````
 7. Following the spacer div, add a <nav> element to contain the header's navigation links, and include the MDL class as indicated. Inside the nav, add one anchor <a> element for each header link, and include the MDL class as indicated. This completes the layout's header.
```
<div class="mdl-layout mdl-js-layout">
  <header class="mdl-layout__header">
    <div class="mdl-layout-icon"></div>
    <div class="mdl-layout__header-row">
      <span class="mdl-layout__title">Simple Layout</span>
      <div class="mdl-layout-spacer"></div>
      <nav class="mdl-navigation">
        <a class="mdl-navigation__link" href="#">Nav link 1</a>
        <a class="mdl-navigation__link" href="#">Nav link 2</a>
        <a class="mdl-navigation__link" href="#">Nav link 3</a>
      </nav>
    </div>
  </header>
</div>
```
 8. Following the header, add a <div> element to hold the slide-out drawer's content, and add the MDL class as indicated. The drawer appears automatically on smaller screens, and may be opened with the menu icon on any screen size.
```
<div class="mdl-layout mdl-js-layout">
  <header class="mdl-layout__header">
    <div class="mdl-layout-icon"></div>
    <div class="mdl-layout__header-row">
      <span class="mdl-layout__title">Simple Layout</span>
      <div class="mdl-layout-spacer"></div>
      <nav class="mdl-navigation">
        <a class="mdl-navigation__link" href="#">Nav link 1</a>
        <a class="mdl-navigation__link" href="#">Nav link 2</a>
        <a class="mdl-navigation__link" href="#">Nav link 3</a>
      </nav>
    </div>
  </header>
  <div class="mdl-layout__drawer">
  </div>
</div>
```
 9. Inside the drawer div, add a span containing the layout title (this should match the title in step 5), and include the MDL class as indicated.
```
<div class="mdl-layout mdl-js-layout">
  <header class="mdl-layout__header">
    <div class="mdl-layout-icon"></div>
    <div class="mdl-layout__header-row">
      <span class="mdl-layout__title">Simple Layout</span>
      <div class="mdl-layout-spacer"></div>
      <nav class="mdl-navigation">
        <a class="mdl-navigation__link" href="#">Nav link 1</a>
        <a class="mdl-navigation__link" href="#">Nav link 2</a>
        <a class="mdl-navigation__link" href="#">Nav link 3</a>
      </nav>
    </div>
  </header>
  <div class="mdl-layout__drawer">
    <span class="mdl-layout__title">Simple Layout</span>
  </div>
</div>
```
 10. Following the span, add a <nav> element to contain the drawer's navigation links, and one anchor <a> element for each drawer link (these should match the links in step 7), and include the MDL classes as indicated. This completes the layout's drawer.
```
<div class="mdl-layout mdl-js-layout">
  <header class="mdl-layout__header">
    <div class="mdl-layout-icon"></div>
    <div class="mdl-layout__header-row">
      <span class="mdl-layout__title">Simple Layout</span>
      <div class="mdl-layout-spacer"></div>
      <nav class="mdl-navigation">
        <a class="mdl-navigation__link" href="#">Nav link 1</a>
        <a class="mdl-navigation__link" href="#">Nav link 2</a>
        <a class="mdl-navigation__link" href="#">Nav link 3</a>
      </nav>
    </div>
  </header>
  <div class="mdl-layout__drawer">
    <span class="mdl-layout__title">Simple Layout</span>
    <nav class="mdl-navigation">
      <a class="mdl-navigation__link" href="#">Nav link 2</a>
      <a class="mdl-navigation__link" href="#">Nav link 2</a>
      <a class="mdl-navigation__link" href="#">Nav link 3</a>
    </nav>
  </div>
</div>
```
 11. Finally, following the drawer div, add a <main> element to hold the layout's primary content, and include the MDL class as indicated. Inside that element, add your desired content.
```
<div class="mdl-layout mdl-js-layout">
  <header class="mdl-layout__header">
    <div class="mdl-layout-icon"></div>
    <div class="mdl-layout__header-row">
      <span class="mdl-layout__title">Simple Layout</span>
      <div class="mdl-layout-spacer"></div>
      <nav class="mdl-navigation">
        <a class="mdl-navigation__link" href="#">Nav link 1</a>
        <a class="mdl-navigation__link" href="#">Nav link 2</a>
        <a class="mdl-navigation__link" href="#">Nav link 3</a>
      </nav>
    </div>
  </header>
  <div class="mdl-layout__drawer">
    <span class="dml-layout__title">Simple Layout</span>
    <nav class="mdl-navigation">
      <a class="mdl-navigation__link" href="#">4</a>
      <a class="mdl-navigation__link" href="#">5</a>
      <a class="mdl-navigation__link" href="#">6</a>
    </nav>
  </div>
  <main class="mdl-layout__content">
    <p>Content</p>
    <p>Goes</p>
    <p>Here</p>
  </main>
</div>
```
The layout component is ready for use.

####
####CONFIGURATION OPTIONS
The MDL CSS classes apply various predefined visual enhancements to the footer. The table below lists the available classes and their effects.

MDL class | Effect | Remarks
--- | --- | ---
`mdl-mega-footer` | Defines container as an MDL mega-footer component | Required on footer element
`mdl-mega-footer__top-section` | Defines container as a footer top section | Required on top section "outer" div element
`mdl-mega-footer__left-section` | Defines container as a left section | Required on left section "inner" div element
`mdl-mega-footer__social-btn` | Defines a decorative square within mega-footer | Required on button dlement(if used)
`mdl-mega-footer__right-section` | Defines container as a right section | Required on right section "inner" div element
`mdl-mega-footer__middle-section` | Defines container as a footer middle section | Required on middle-section "outer" div element
`mdl-mega-footer__drop-down-section` | Defines container as a drop-down(vertical) content area | Required on drop-down "inner" div elements
`mdl-mega-footer__heading` | Defines a heading as a mega-footer heading | Required on h1 element inside drop-down section
`mdl-mega-footer__link-list` | Defines an unordered list as a drop-down(vertical) list | Required on ul element inside drop-down section
`mdl-mega-footer__bottom-section` | Defines container as a footer bottom section | Required on bottom section "outer" div element
`mdl-logo` | Defines a container as a styled section heading | Required on "inner" div element in mega-footer bottom-section or mini-footer left-section
`mdl-mini-footer` | Defines container as an MDL mini-footer component | Required on footer element
`mdl-mini-footer` | Defines container as a left section | Required on left section "inner" div element
`mdl-mini-footer__link-list` | Defines an unordered list as an inline(horizontal) list | Required on ul element sibling to "mdl-lgog" div element
`mdl-mini-footer__right-section` | Defines container as a right section | Required on right section "inner" div element
`mdl-mini-footer__social-btn` | Defines a decorative square within mini-footer | Required on button element(if used)
