## Flexbox Explained

### Flex Container (Parent) Properties

    .flex-container { 
      display: flex; 
    }

  **_display: flex_** creates a flexible box along the Y (row) axis. This is the default behavior

  ===============

    .flex-container {
      display: flex;
      flex-direction: row || row-reverse || column || column-reverse
    }

   **_flex-direction_** can equal row, row-reverse, column, column-reverse This takes the child elements and organizes them in single row or a single column either in normal or reverse order. This defines our main axis.

  ===============

    .flex-container {
      display: flex;
      flex-direction: see above ^;
      flex-wrap: wrap || wrap-reverse || nowrap
    }

   **_flex-wrap_** can equal wrap, wrap-reverse, or nowrap flex-direction orders the individual items. flex-wrap orders the rows/columns created

  ===============

    .flex-container {
      display: flex;
      flex-flow: row wrap || column nowrap || etc
    }

  **_flex-flow_** is shorthand for flex-direction and flex-wrap It takes two arguments, just like the individual properties.

  ===============

    .flex-container {
      display: flex;
      flex-flow: row wrap;
      justify-content: flex-start || flex-end || center || space-between || space-around;
    }

   **_justify-content_** can be flex-start, flex-end, center, space-between, space-around. Justify-content determines the distribution of the flex-items (children) within the flex-container on the main axis. If flex-direction is row, then horizontal is the main axis. When flex-direction is column, then column is the main axis.

  ===============

    .flex-container {
      display: flex;
      flex-flow: row wrap;
      justify-content: center;
      height: 400px;
    }

  Give our flexbox a set **height** property so we can mess with spacing in the next property...

  ===============

    .flex-container {
      display: flex;
      flex-flow: row wrap;
      justify-content: center;
      height: 800px;
      align-items: flex-start, flex-end, center, baseline, stretch
    }

  **_align-items_** can be flex-start, flex-end, center, baseline, stretch. This aligns our items on the cross axis. If it's a row, it'll align items vertically. If it's a column, it'll align items horizontally.

  ^^THIS ALLOWS US TO FINALLY ALIGN THINGS VERTICALLY!!!!!^^

### Flexbox Item (Child) Properties

    .flex-item1 { 
      order: 1 || 2 || 3 || etc;
    }

  **_order_** can be an integer. 1 will move the .flex-item1 boxes to the end of the list, while -1 will move them to the start of the list. 0 is neutral.

  ===============

    .flex-item1 {
      flex-basis: 25%;
    }

  **_flex-basis_** is kind of like width, but not quite the same thing. Width is an absolute measurement — an element is that wide, all the time. We can measure width in relative units (say 50% instead of 600px), but in the end, the measurement itself never changes. For flex-basis, we try to achieve a given width with the space available. It could be smaller than this width, or it could be wider, depending on the extra space and how that’s supposed to be distributed. Distribution of extra space is controlled by flex-grow and flex-shrink (below).

  ===============

    .flex-item1 {
      flex-grow: 1;
    }

    .flex-item2 {
      flex-grow: 2
    }

  **_flex-grow_** can be 0 or a positive integer. Flex-grow, like flex-shrink (below), distributes extra space once each element is displayed on the page. 
  
  In this example, we are telling `.flex-item2` to grow at a 2:1 ratio to `.flex-item1`

  By assigning a value to flex-grow, any extra space will be assigned in greater proportion to this element, making it larger relative to the other items. This just an integer to represent a proportion to the other items.

===============

    .flex-item1 {
      flex-shrink: 1;
    }

    .flex-item2 {
      flex-shrink 2;
    }
  
  **_flex-shrink_** can be 0 or a positive integer. Flex-shrink controls what happens to extra space as elements shrink. By assigning a value to flex-shrink, as elements get smaller on the page, this element will get smaller faster than the others. This just an integer to represent a proportion to the other items.

    .flex-item1 {
      flex: flex-grow flex-shrink flex-basis;
    }

 This is shorthand for defining **_flex-grow_**, **_flex-shrink_** and **_flex-basis_** properties

