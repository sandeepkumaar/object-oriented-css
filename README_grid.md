# Documentation for Grid CSS

## Terminology
As in normal grids, graph with equal interval units.
The CSS grid is similar to a graph except
  - grid *columns* can take variable *widths*
  - similar to grid columns, grid *rows* also take variable *heights*
  - grid items are placed inside the grid column/row
  - grid items can span more than one column/row also known as
  grid area.

### grid-container
container that holds the grid-items and flows them based on
the grid-template-columns/grid-template-rows

### grid-template-column / grid-template-row
Divided the grid-container into grid cells so that the item can
be placed on the grid-cell/ grid-area (group of cells form a grid area)

### grid-template-area
Groups the grid-cells into a grid-area.



## Single Row layout
This is the most widely used layout. Most frameworks have a 12 column grid system with a single row.

##### Flex Row Behaviour
The items are flown horizontally and when there is no space the items are flown to the next line.  
In other words, when container is shrinked the no.of columns
automatically changes/reduces and rows increases to accommodate the needed space

##### bootstrap grid behavior
The items are flown horizontally and when there is no space the items are **not** flown to the next line.  
Instead they rely on media queries to do the job  
CSS Grids is also in similar behaviour  


## Special features
Grid css is more powerful with media queries  
Changing the layout/the way item flows is really easy as we need to simple change the *container* definition.  
This can be done at media queries to achieve responsive layouts  
Dividing the containers width is flexible and easily modifiable


Very useful for responsive components where component elements needs to flow differently for different viewports

grid-template-area helps in abstraction
