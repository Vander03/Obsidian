
## CSS Class Selectors
Class selectors select the class attribute of an element. The selector is prefixed with a . (dot). One or more elements can be selected.

Some example class selectors:

| SELECTOR	| EXAMPLE |SELECTS |
| --- | --- | --- |
|.class	|.classname	|All elements with class="classname"|
|.class1.class2	|\<div class="cn1 cn2">...\</div>|All elements with both cn1 and cn2 classnames.
				|.class1 .class2|	\<div class="cn1"><br>  \<div class="cn2"> <br>...<br>\</div> <br>\</div>	| All elements with cn2 that are contained by an element with cn1. |


## CSS ID Selectors
Id selectors select the id attribute of an element. The selector is prefixed with a # (hash). Only one element can be selected because id values are unique on a page.

An id selector:

| SELECTOR| 	EXAMPLE	|SELECTS | 
| --- | --- | --- |
| \#id	|\#email|	The element with id="email"|


## Element Selectors
Element selectors select elements by tag name, i.e. type, such as div or ul. The style applies to all elements of that type.

Some element selectors:

|SELECTOR |	EXAMPLE|	SELECTS|
| --- | --- | --- |
|element	|ul	|All \<ul> elements|
|element1, element2	|div, ul	|All \<div> and \<ul> elements.|
|element1 element2	|div ul	|All \<ul> elements inside \<div> elements.|
|element1 > element2	|div > ul	|All child \<ul> elements of \<div> elements.|
|element1 + element2	|div + ul	|All \<ul> elements immediately preceded by a \<div> element.|
|element1 ~ element2	|div ~ ul	|All \<ul> elements preceded by a \<div> element.|


## Attribute Selectors
Attribute selectors select elements by attribute. The selectors are surrounded by square brackets, for example \[hidden]. The style applies to all elements with that attribute.

Some attribute selectors:

|SELECTOR|	EXAMPLE|	SELECTS|
| --- | --- | -- |
|\[attribute]	|\[for]	|All elements with a for attribute|
|\[attribute=value]|\[for="email"]	|All elements with a for="email" attribute|
|\[attribute^=value] |	button\[value^="Go"]	|All \<button> elements whose value attribute starts with "Go"|
|\[attribute\$=value]	|img\[src$=".png"]	|All <img> elements whose src attribute ends with ".jpg"|
|\[attribute*=value]	|img\[alt*="Van Gogh"]|	All \<a> elements whose alt attribute contains the substring "Van Gogh"|
|\[attribute~=value]	|\[title~=create]	|All elements whose title attribute contains the word "create", delimited by spaces.|
|\[attribute\|=value]	|\[lang\|=nl] | All elements whose lang attribute is a hyphen-separated list starting with "nl" or "nl-"|


## Pseudo-class Selectors
Pseudo-class selectors select elements by psuedo-class. It is commonly combined with element selectors, such as input:enabled.

Some pseudo class selectors:

| SELECTOR             | EXAMPLE                   | SELECTS                                                                                                          |
| -------------------- | ------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| :active              | a:active                  | All active links                                                                                                 |
| :visited             | a:visited                 | All visited links                                                                                                |
| :link                | a:link                    | All unvisited links                                                                                              |
| ::after              | ul::after                 | Add cosmetic content after each                                                                                  |
| ::before             | ul::before                | Add cosmetic content before each                                                                                 |
| :checked             | input:checked             | All elements that are checked                                                                                    |
| :default             | input:default             | All elements that are specified as default                                                                       |
| :enabled             | input:enabled             | All elements that are enabled                                                                                    |
| :disabled            | input:disabled            | All elements that are disabled                                                                                   |
| :valid               | input:valid               | All input elements with a valid value                                                                            |
| :invalid             | input:invalid             | All elements with an invalid value                                                                               |
| :in-range            | input:in-range            | All elements with a value that is within a specified range                                                       |
| :out-of-range        | input:out-of-range        | All elements with a value outside the specified range                                                            |
| :indeterminate       | input:indeterminate       | All elements that are in an indeterminate state                                                                  |
| :required            | input:required            | All elements with a "required" attribute                                                                         |
| :optional            | input:optional            | All elements with no "required" attribute                                                                        |
| :read-only           | input:read-only           | All elements with a "readonly" attribute                                                                         |
| :read-write          | input:read-write          | All elements WITHOUT a "readonly" attribute                                                                      |
| ::placeholder        | input::placeholder        | All elements with placeholder text                                                                               |
| :hover               | input:hover               | The element that currently being hovered                                                                         |
| :focus               | input:focus               | The element that currently has focus                                                                             |
| :empty               | ol:empty                  | All element without child elements                                                                               |
| :first-child         | li:first-child            | All elements that are the first child of their parent                                                            |
| :last-child          | li:last-child             | All elements that are the last child of their parent                                                             |
| :nth-child(n)        | li:nth-child(2)           | All elements that are second child of their parent                                                               |
| :nth-last-child(n)   | li:nth-last-child(2)      | All elements that are second to last child of their parent                                                       |
| :only-child          | li:only-child             | All elements that are the only child of its parent                                                               |
| :first-of-type       | label:first-of-type       | All elements that are the first label of their parent                                                            |
| :last-of-type        | label:last-of-type        | All elements that are the last label of their parent                                                             |
| :nth-of-type(n)      | label:nth-of-type(2)      | All elements that are the second label of their parent                                                           |
| :nth-last-of-type(n) | label:nth-last-of-type(2) | All elements that are the second to last label of their parent                                                   |
| :only-of-type        | label:only-of-type        | All elements that are the only label element of their parent                                                     |
| ::first-letter       | p::first-letter           | The first letter of every element                                                                                |
| ::first-line         | p::first-line             | The first line of every element                                                                                  |
| :lang(language)      | p:lang(fr)                | All French elements                                                                                              |
| :not(selector)       | :not(table)               | All elements that are not a element                                                                              |
| :root                | :root                     | The document's root element                                                                                      |
| ::selection          | ::selection               | Parts of an element that is selected (highlighted) by the user -- usually text                                   |
| :target              | :target                   | The element that matches the url fragment, <br> e.g. element with id="list" when the url is www.mysite.com#list. |


# CSS Properties

| PROPERTY | DESCRIPTION |
|---|---|
|[align-content](https://www.dofactory.com/css/align-content)|Aligns items in a flex container along flex lines.|
|[align-items](https://www.dofactory.com/css/align-items)|Aligns evenly spaced items in a flex container.|
|[align-self](https://www.dofactory.com/css/align-self)|Aligns an item inside a flex container.|
|[all](https://www.dofactory.com/css/all)|Resets all element properties to its default or inherited values.|
|[animation](https://www.dofactory.com/css/animation)|Creates an animating element.|
|[animation-delay](https://www.dofactory.com/css/animation-delay)|Sets a delay before an animation begins.|
|[animation-direction](https://www.dofactory.com/css/animation-direction)|Sets how, in which direction, an animation is played.|
|[animation-duration](https://www.dofactory.com/css/animation-duration)|Defines the duration of an animation cycle.|
|[animation-fill-mode](https://www.dofactory.com/css/animation-fill-mode)|Defines how styles are applied before and after animation.|
|[animation-iteration-count](https://www.dofactory.com/css/animation-iteration-count)|Sets the number of times an animation is played.|
|[animation-name](https://www.dofactory.com/css/animation-name)|Defines a name for the animation.|
|[animation-play-state](https://www.dofactory.com/css/animation-play-state)|Sets the animation play state to running or paused.|
|[animation-timing-function](https://www.dofactory.com/css/animation-timing-function)|Specifies the animation speed curve.|
|[backface-visibility](https://www.dofactory.com/css/backface-visibility)|Shows or hides the backface visibility of an element.|
|[background](https://www.dofactory.com/css/background)|Sets the background of an element.|
|[background-attachment](https://www.dofactory.com/css/background-attachment)|Defines how the background is attached to an element.|
|[background-blend-mode](https://www.dofactory.com/css/background-blend-mode)|Defines the background layer blending mode.|
|[background-clip](https://www.dofactory.com/css/background-clip)|Defines how background extends beyond the element.|
|[background-color](https://www.dofactory.com/css/background-color)|Sets the background color of the element.|
|[background-image](https://www.dofactory.com/css/background-image)|Specifies a background image for an element.|
|[background-origin](https://www.dofactory.com/css/background-origin)|Specifies the background image origin position.|
|[background-position](https://www.dofactory.com/css/background-position)|Sets the position of a background image.|
|[background-repeat](https://www.dofactory.com/css/background-repeat)|Specifies how the background image is repeated.|
|[background-size](https://www.dofactory.com/css/background-size)|Sets the size of the background image.|
|[border](https://www.dofactory.com/css/border)|Specifies a border for an element|
|[border-bottom](https://www.dofactory.com/css/border-bottom)|Specifies a bottom border for an element.|
|[border-bottom-color](https://www.dofactory.com/css/border-bottom-color)|Sets the color of a bottom border .|
|[border-bottom-left-radius](https://www.dofactory.com/css/border-bottom-left-radius)|Sets the border radius of the bottom left corner.|
|[border-bottom-right-radius](https://www.dofactory.com/css/border-bottom-right-radius)|Sets the border radius of the bottom right corner|
|[border-bottom-style](https://www.dofactory.com/css/border-bottom-style)|Sets the style of the bottom border.|
|[border-bottom-width](https://www.dofactory.com/css/border-bottom-width)|Sets the width of the bottom border|
|[border-collapse](https://www.dofactory.com/css/border-collapse)|Sets table borders to single collapsed line or separated.|
|[border-color](https://www.dofactory.com/css/border-color)|Sets the color of the border.|
|[border-image](https://www.dofactory.com/css/border-image)|Defines an image as border, instead of a color.|
|[border-image-outset](https://www.dofactory.com/css/border-image-outset)|Sets how far a border image extends beyond the border.|
|[border-image-repeat](https://www.dofactory.com/css/border-image-repeat)|Defines if and how the border image is repeated.|
|[border-image-slice](https://www.dofactory.com/css/border-image-slice)|Defines how the border image will be sliced.|
|[border-image-source](https://www.dofactory.com/css/border-image-source)|Specifies the url of the border image file.|
|[border-image-width](https://www.dofactory.com/css/border-image-width)|Sets the width of the image border.|
|[border-left](https://www.dofactory.com/css/border-left)|Sets the left border of the element.|
|[border-left-color](https://www.dofactory.com/css/border-left-color)|Sets the color of the left border.|
|[border-left-style](https://www.dofactory.com/css/border-left-style)|Sets the style of the left border.|
|[border-left-width](https://www.dofactory.com/css/border-left-width)|Sets the width of the left border.|
|[border-radius](https://www.dofactory.com/css/border-radius)|Sets the radius of the border.|
|[border-right](https://www.dofactory.com/css/border-right)|Sets the right border of the element.|
|[border-right-color](https://www.dofactory.com/css/border-right-color)|Sets the color of the right border.|
|[border-right-style](https://www.dofactory.com/css/border-right-style)|Sets the style of the right border.|
|[border-right-width](https://www.dofactory.com/css/border-right-width)|Sets the width of the right border.|
|[border-spacing](https://www.dofactory.com/css/border-spacing)|Sets the adjacent table cell distance.|
|[border-style](https://www.dofactory.com/css/border-style)|Defines the style of the border|
|[border-top](https://www.dofactory.com/css/border-top)|Sets the top border of the element.|
|[border-top-color](https://www.dofactory.com/css/border-top-color)|Sets the color of the top border.|
|[border-top-left-radius](https://www.dofactory.com/css/border-top-left-radius)|Sets the border radius of the top left corner.|
|[border-top-right-radius](https://www.dofactory.com/css/border-top-right-radius)|Sets the border radius of the top right corner.|
|[border-top-style](https://www.dofactory.com/css/border-top-style)|Sets the style of the top border.|
|[border-top-width](https://www.dofactory.com/css/border-top-width)|Sets the width of the top border.|
|[border-width](https://www.dofactory.com/css/border-width)|Sets the border width of the element.|
|[bottom](https://www.dofactory.com/css/bottom)|Positions the element from the bottom of the relative container.|
|[box-shadow](https://www.dofactory.com/css/box-shadow)|Adds a shadow effect to an element.|
|[box-sizing](https://www.dofactory.com/css/box-sizing)|Sets how element height and width are calculated.|
|[caption-side](https://www.dofactory.com/css/caption-side)|Defines on which side of the table a caption is placed.|
|[caret-color](https://www.dofactory.com/css/caret-color)|Sets the color of the blinking mouse caret.|
|[@charset](https://www.dofactory.com/css/charset)|Specifies the character encoding of the stylesheet.|
|[clear](https://www.dofactory.com/css/clear)|Sets the element side that does not allow floating elements.|
|[clip](https://www.dofactory.com/css/clip)|Sets how an image is cropped or clipped inside a container.|
|[clip-path](https://www.dofactory.com/css/clip-path)|Clips an element inside a specific shape or SVG.|
|[color](https://www.dofactory.com/css/color)|Specifies the color of text in an element.|
|[column-count](https://www.dofactory.com/css/column-count)|Divides an element into the specified number of columns.|
|[column-fill](https://www.dofactory.com/css/column-fill)|Specifies how divided columns are filled.|
|[column-gap](https://www.dofactory.com/css/column-gap)|Specifies the space between divided columns.|
|[column-rule](https://www.dofactory.com/css/column-rule)|Sets the style, width, and color of a column divider.|
|[column-rule-color](https://www.dofactory.com/css/column-rule-color)|Sets the color of a column divider.|
|[column-rule-style](https://www.dofactory.com/css/column-rule-style)|Sets the style of a column divider.|
|[column-rule-width](https://www.dofactory.com/css/column-rule-width)|Sets the width of a column divider.|
|[column-span](https://www.dofactory.com/css/column-span)|Sets number of divided columns an element should span.|
|[column-width](https://www.dofactory.com/css/column-width)|Specifies the width of a divided column.|
|[columns](https://www.dofactory.com/css/columns)|Divide an element into columns of a certain width.|
|[content](https://www.dofactory.com/css/content)|Used to insert content before or after an element.|
|[counter-increment](https://www.dofactory.com/css/counter-increment)|Increase or decrease a CSS counter.|
|[counter-reset](https://www.dofactory.com/css/counter-reset)|Initialize or reset CSS counter.|
|[cursor](https://www.dofactory.com/css/cursor)|Specifies the shape of the mouse cursor.|
|[direction](https://www.dofactory.com/css/direction)|Specifies the text writing direction of a block-level element.|
|[display](https://www.dofactory.com/css/display)|Specify an element's display behavior.|
|[empty-cells](https://www.dofactory.com/css/empty-cells)|Specifies whether empty table cell borders will be displayed.|
|[filter](https://www.dofactory.com/css/filter)|Adds an image enhancing effect to an image.|
|[flex](https://www.dofactory.com/css/flex)|Specifies the width of the flexible items.|
|[flex-basis](https://www.dofactory.com/css/flex-basis)|Specifies the initial width of a flex item.|
|[flex-direction](https://www.dofactory.com/css/flex-direction)|Specifies the direction for the flex item to align.|
|[flex-flow](https://www.dofactory.com/css/flex-flow)|Controls the direction and wrapping of flexible items.|
|[flex-grow](https://www.dofactory.com/css/flex-grow)|Specifies how a flex item can grow inside the container.|
|[flex-shrink](https://www.dofactory.com/css/flex-shrink)|Specifies how a flex item can shrink inside the container.|
|[flex-wrap](https://www.dofactory.com/css/flex-wrap)|Specifies how flexible items wrap inside the container.|
|[float](https://www.dofactory.com/css/float)|Sets how an element is positioned relative to other elements.|
|[font](https://www.dofactory.com/css/font)|Sets font family, variant, weight, height, and size for an element.|
|[@font-face](https://www.dofactory.com/css/font-face)|Embeds a custom font inside a web page|
|[font-family](https://www.dofactory.com/css/font-family)|Sets the font family for an element.|
|[font-kerning](https://www.dofactory.com/css/font-kerning)|Sets the spacing between the font's characters.|
|[font-size](https://www.dofactory.com/css/font-size)|Sets the size of the font for an element.|
|[font-size-adjust](https://www.dofactory.com/css/font-size-adjust)|Specifies a fall-back font size.|
|[font-stretch](https://www.dofactory.com/css/font-stretch)|Sets the text characters to a wider or narrower variant.|
|[font-style](https://www.dofactory.com/css/font-style)|Set the font style to normal, italic, or oblique.|
|[font-variant](https://www.dofactory.com/css/font-variant)|Specifies that text is displayed in a small-caps font.|
|[font-weight](https://www.dofactory.com/css/font-weight)|Sets the weight or thickness of the font.|
|[grid](https://www.dofactory.com/css/grid)|Defines a grid layout with responsive rows and columns.|
|[grid-area](https://www.dofactory.com/css/grid-area)|Sets the size and location of grid items in a grid container.|
|[grid-auto-columns](https://www.dofactory.com/css/grid-auto-columns)|Specifies the size of the columns in a grid container.|
|[grid-auto-flow](https://www.dofactory.com/css/grid-auto-flow)|Specifies the initial placement of items in a grid container.|
|[grid-auto-rows](https://www.dofactory.com/css/grid-auto-rows)|Specifies the initial size of the items in a grid container.|
|[grid-column](https://www.dofactory.com/css/grid-column)|Specifies the size and location of a grid item in a grid container.|
|[grid-column-end](https://www.dofactory.com/css/grid-column-end)|Specifies in which column-line the grid item will end.|
|[grid-column-gap](https://www.dofactory.com/css/grid-column-gap)|Specifies the gap size between columns in a grid container.|
|[grid-column-start](https://www.dofactory.com/css/grid-column-start)|Specifies in which column line the grid item will start.|
|[grid-gap](https://www.dofactory.com/css/grid-gap)|Specifies the gap size between grid rows and columns.|
|[grid-row](https://www.dofactory.com/css/grid-row)|Specifies the grid item size and location in a grid container.|
|[grid-row-end](https://www.dofactory.com/css/grid-row-end)|Specifies in which row-line the grid item will end.|
|[grid-row-gap](https://www.dofactory.com/css/grid-row-gap)|Specifies the gap size between rows in a grid container.|
|[grid-row-start](https://www.dofactory.com/css/grid-row-start)|Specifies in which row line the grid item will start|
|[grid-template](https://www.dofactory.com/css/grid-template)|Divides a page into sections with a size, position, and layer.|
|[grid-template-areas](https://www.dofactory.com/css/grid-template-areas)|Specifies area in a grid container.|
|[grid-template-columns](https://www.dofactory.com/css/grid-template-columns)|Sets the number and width of columns in a grid container.|
|[grid-template-rows](https://www.dofactory.com/css/grid-template-rows)|Sets the number and height of rows in a grid container.|
|[height](https://www.dofactory.com/css/height)|Sets the height of an element.|
|[hyphens](https://www.dofactory.com/css/hyphens)|Specifies hyphenation with wrap opportunities in a line of text.|
|[@import](https://www.dofactory.com/css/import)|Imports a style sheet inside another style sheet.|
|[justify-content](https://www.dofactory.com/css/justify-content)|Defines the alignment of items in a flex container.|
|[@keyframes](https://www.dofactory.com/css/keyframes)|Defines the CSS style to animate.|
|[left](https://www.dofactory.com/css/left)|Positions the element from the left of the relative container.|
|[letter-spacing](https://www.dofactory.com/css/letter-spacing)|Sets the spacing between characters.|
|[line-height](https://www.dofactory.com/css/line-height)|Sets the vertical spacing between lines of text.|
|[list-style](https://www.dofactory.com/css/list-style)|Defines the markers (bullet points) for items in a list.|
|[list-style-image](https://www.dofactory.com/css/list-style-image)|Defines an image markers (bullet points) for items in a list.|
|[list-style-position](https://www.dofactory.com/css/list-style-position)|Sets the marker (bullet point) positions for items in a list|
|[list-style-type](https://www.dofactory.com/css/list-style-type)|Defines the marker types (bullet points) for items in a list|
|[margin](https://www.dofactory.com/css/margin)|Sets the margin (outside spacing) for an element.|
|[margin-bottom](https://www.dofactory.com/css/margin-bottom)|Sets the bottom margin (outside spacing) for an element.|
|[margin-left](https://www.dofactory.com/css/margin-left)|Sets the left margin (outside spacing) for an element.|
|[margin-right](https://www.dofactory.com/css/margin-right)|Sets the right margin (outside spacing) for an element.|
|[margin-top](https://www.dofactory.com/css/margin-top)|Sets the top margin (outside spacing) for an element.|
|[max-height](https://www.dofactory.com/css/max-height)|Sets the maximumn height for an element.|
|[max-width](https://www.dofactory.com/css/max-width)|Sets the maximum width for an element.|
|[@media](https://www.dofactory.com/css/media)|Applies media queries to a page.|
|[min-height](https://www.dofactory.com/css/min-height)|Sets the minimum height for an element.|
|[min-width](https://www.dofactory.com/css/min-width)|Sets the minimum width for an element.|
|[object-fit](https://www.dofactory.com/css/object-fit)|Specifies how an image or video fits inside a container.|
|[object-position](https://www.dofactory.com/css/object-position)|Specifies the image or video position inside a container.|
|[opacity](https://www.dofactory.com/css/opacity)|Sets the opacity (transparency) of the element.|
|[order](https://www.dofactory.com/css/order)|Specifies the order of an item in a flex container.|
|[outline](https://www.dofactory.com/css/outline)|Adds an outline (highlighted border) to an element.|
|[outline-color](https://www.dofactory.com/css/outline-color)|Sets the color of an outline.|
|[outline-offset](https://www.dofactory.com/css/outline-offset)|Sets the space between the outline and border.|
|[outline-style](https://www.dofactory.com/css/outline-style)|Sets the style of an outline.|
|[outline-width](https://www.dofactory.com/css/outline-width)|Sets the width of an outline.|
|[overflow](https://www.dofactory.com/css/overflow)|Specifies the flow of content that exceeds the container.|
|[overflow-x](https://www.dofactory.com/css/overflow-x)|Specifies the flow of content that exceeds the container width.|
|[overflow-y](https://www.dofactory.com/css/overflow-y)|Specifies the flow of content that exceeds the container height.|
|[padding](https://www.dofactory.com/css/padding)|Sets the spacing between content and element border.|
|[padding-bottom](https://www.dofactory.com/css/padding-bottom)|Sets the spacing between content and bottom element border.|
|[padding-left](https://www.dofactory.com/css/padding-left)|Sets the spacing between content and left element border.|
|[padding-right](https://www.dofactory.com/css/padding-right)|Sets the spacing between content and right element border.|
|[padding-top](https://www.dofactory.com/css/padding-top)|Sets the spacing between content and top element border.|
|[page-break-after](https://www.dofactory.com/css/page-break-after)|Adds a print page-break after an element.|
|[page-break-before](https://www.dofactory.com/css/page-break-before)|Adds a print page-break before an element.|
|[page-break-inside](https://www.dofactory.com/css/page-break-inside)|Specifies if print page-break is allowed inside an element.|
|[perspective](https://www.dofactory.com/css/perspective)|Adds perspective to a 3D-positioned element.|
|[perspective-origin](https://www.dofactory.com/css/perspective-origin)|Sets the origin of the perspective for a 3D-positioned element.|
|[pointer-events](https://www.dofactory.com/css/pointer-events)|Specifies whether element reacts to pointer events or not.|
|[position](https://www.dofactory.com/css/position)|Sets the element's positioning method.|
|[quotes](https://www.dofactory.com/css/quotes)|Defines the quotation marks to be used on text.|
|[right](https://www.dofactory.com/css/right)|Positions the element from the right of the relative container.|
|[scroll-behavior](https://www.dofactory.com/css/scroll-behavior)|Specifies the scrolling behavior of an element|
|[table-layout](https://www.dofactory.com/css/table-layout)|Aligns elements according to a table with rows and columns.|
|[text-align](https://www.dofactory.com/css/text-align)|Sets the alignment of text inside an element.|
|[text-align-last](https://www.dofactory.com/css/text-align-last)|Sets the alignment for the last line of text.|
|[text-decoration](https://www.dofactory.com/css/text-decoration)|Defines the style and color of underlined text.|
|[text-decoration-color](https://www.dofactory.com/css/text-decoration-color)|Defines the color of underlined text.|
|[text-decoration-line](https://www.dofactory.com/css/text-decoration-line)|Defines the kind of line to use with text.|
|[text-decoration-style](https://www.dofactory.com/css/text-decoration-style)|Defines the style of underlined text.|
|[text-indent](https://www.dofactory.com/css/text-indent)|Sets the indentation to the beginning of text.|
|[text-justify](https://www.dofactory.com/css/text-justify)|Defines the text justification inside a container.|
|[text-overflow](https://www.dofactory.com/css/text-overflow)|Sets the display behavior of text that overflows a container.|
|[text-shadow](https://www.dofactory.com/css/text-shadow)|Adds a shadow effect to text.|
|[text-transform](https://www.dofactory.com/css/text-transform)|Defines text capitalization or casing.|
|[top](https://www.dofactory.com/css/top)|Positions the element from the top of the relative container|
|[transform](https://www.dofactory.com/css/transform)|Applies a 2D or 3D transformation to an element.|
|[transform-origin](https://www.dofactory.com/css/transform-origin)|Sets the origin for the transformation of the element.|
|[transform-style](https://www.dofactory.com/css/transform-style)|Specifies the display behavior of 3D space nested elements.|
|[transition](https://www.dofactory.com/css/transition)|Creates transitions from one property value to another.|
|[transition-delay](https://www.dofactory.com/css/transition-delay)|Creates a delay before the transition effect starts.|
|[transition-duration](https://www.dofactory.com/css/transition-duration)|Specifies the time the transition will take.|
|[transition-property](https://www.dofactory.com/css/transition-property)|Specifies the CSS property that will transition.|
|[transition-timing-function](https://www.dofactory.com/css/transition-timing-function)|Defines the speed curve function of the transition.|
|[user-select](https://www.dofactory.com/css/user-select)|Specifies how text can be selected (highlighted)|
|[vertical-align](https://www.dofactory.com/css/vertical-align)|Specifies vertical alignment of an element.|
|[visibility](https://www.dofactory.com/css/visibility)|Specifies the visibility of an element.|
|[white-space](https://www.dofactory.com/css/white-space)|Specifies how white-space is handled inside an element.|
|[width](https://www.dofactory.com/css/width)|Sets the width of an element.|
|[word-break](https://www.dofactory.com/css/word-break)|Specifies how line breaks take place.|
|[word-spacing](https://www.dofactory.com/css/word-spacing)|Sets the spacing between words.|
|[word-wrap](https://www.dofactory.com/css/word-wrap)|Specifies how long words can be wrapped.|
|[writing-mode](https://www.dofactory.com/css/writing-mode)|Sets the text reading orientation: top to bottom, etc.|
|[z-index](https://www.dofactory.com/css/z-index)|Sets the vertical stacking order relative to other elements.|