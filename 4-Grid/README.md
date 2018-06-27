## Grid Properties Cheatsheet

### Grid Container (Parent) Properties

#### grid-template-columns, grid-template-rows

    .grid-container {
      grid-template-columns: [optional: line name, in square brackets] <track-size> | <repeat>;
      grid-template-rows: [optional: line name, in square brackets] <track-size> | <repeat>;
    }

  **_grid-template-columns_** and **_grid-template-rows_** define the number of columns/rows and how wide/tall they are. Typically you'll be setting the columns explicitely and the rows will auto create as needed

  `track-size:` length, %, fr, auto

  `line name:` an arbitrary name for this item. If no name assigned, a number is used. Names must come between `[ ]`.

  Examples:

    .grid-container {
      grid-template-columns: [col1] 40px [col2] 3fr;
  	  grid-template-rows: 50% 25vh auto;
  	}

  	.grid-container-2 {
  	  grid-template-rows: repeat(2, 350px [name]) 10%;
  	}

  	translates to

  	.grid-container-2 {
  	  grid-template-rows: 350px [name] 350px [name] 10%;
  	}

  ===============

  #### grid-template-areas 

  List of names of areas. First, name areas via selector. Then specify layout via this property. Area name must be specified for each column/row. A `.` (dot) indicates no content in this row/column.

  Examples:

    .grid-container {
      grid-template-columns: 1fr 3fr;
      grid-template-rows: auto;
      grid-template-areas: 
        "header header header header"
        "aside . article article";
    }

    .grid-header {
      grid-area: header;
    }

    .grid-article {
      grid-area: article;
    }

    .grid-aside {
      grid-area: aside;
    }


  **_grid-template_** is shorthand for grid-template-rows, grid-template-columns, and grid-template-areas in a single declaration. This is good if you need a perfectly even grid (i.e. 12 x 12)
  
  ===============

  #### grid-gap, grid-column-gap, grid-row-gap

    .grid-container {
      grid-column-gap: 20px;
      grid-row-gap: 20px;
      grid-gap: 20px(row) 10px(column);
    }

   **_grid-column-gap_**, **_grid-row-gap_**, or simply **_grid-gap_** creates space between rows and/or columns. (I believe only pixels are allowed for measurement currently, please correct me if I'm mistaken)

===============

#### justify-items, align-items, justify-content, align-content

    .grid-container {
      justify-items: start;
      align-items: end;
      justify-content: space-around;
      align-content: space-evenly;
    }

  **_justify-items_** can have values of `start | end | center | stretch` to align grid items on row axis. Stretch is default value.

  **_align-items_** can have values of `start | end | center | stretch` to align grid items on column axis. Stretch is default value.

  **_justify-content_** can have values of `start | end | center | stretch | space-around | space-between | space-evenly`. If size of grid container is bigger than total of grid items, you can align grid items within the container (like flexbox). This works on row axis.

  **_align-content_** can have values of `start | end | center | stretch | space-around | space-between | space-evenly`. If size of grid container is bigger than total of grid items, you can align grid items within the container (like flexbox). This works on column axis.

  ===============

  #### grid-auto-rows, grid-auto-columns

    .grid-container {
      grid-auto-rows: 20px;
      grid-auto-column: 1fr;
    }

  If you create grid cells beyond those specified in grid-template-columns and grid-template-rows, these specifies how big these extra rows/columns should be.

------

### Grid Item (Child) Properties

#### grid-column-start/end, grid-row-start/end

    grid-column-start
    grid-column-end
    grid-row-start
    grid-row-end: <number> | <name> | span <number> | span <name> | auto;


This is the longhand for declaring individual values for start and end points for rows and columns.

Example: This grid item will start at column 1 and span 4 columns and it will start on the 3rd row and span until the end of the grid-area-template named "footer-end" (see grid-area-template above)

    .grid-item-1 {
      grid-column-start: 1;
      grid-column-end: span 4;
      grid-row-start: 3;
      grid-row-end: span footer-end;
    }

===============

#### grid-column, grid-row

    grid-column
    grid-row: <start-line> / <end-line> | <start-line> / span <value>;

  Combines start and end values with a `/` between the values

  Example:

    .grid-item-1 {
      grid-column: 1 / span 4;
      grid-row: 3 / span footer-end;
    }	

===============

#### grid-area

    grid-area: <name> | <row-start> / <column-start> / <row-end> / <column-end>;

  Setting dimensions by `grid-area` is tricky, as we have two ways to approach it:

  * Assign a name for the grid-template-areas property (see above examples). I recommend using this method while getting acclimated.

  * Assign a name AND the dimensions for a grid-template-areas property. If you use this method, you would not necessarily need a grid-template-rows and grid-template-columns declaration. This can get confusing easily, so I don't recommend messing with this until you feel comfortable.

  Example:
    
    .grid-item-1 {
      grid-area: 1 / name3 / namedline / 4;
    }

===============

    justify-self: start | end | center | stretch;
    
  Aligns content in a grid item on the row axis. Overrides justify-items. 

===============

    align-self: start | end | center | stretch;

  Aligns content in a grid item on the column axis. Overrides align-items.