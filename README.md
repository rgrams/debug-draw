# Debug-Draw
A set of convenience functions to draw lines, shapes, and text with the "draw_line" and "draw_debug_text" render messages. This is not intended to be used for final game graphics. Most of the functions only draw on a 2D plane at z=0, though the `ray` function can draw 3D lines.

__Dependency Link:__
>https://github.com/rgrams/debug-draw/archive/master.zip

*Don't know what to do with this link? Read the manual: https://www.defold.com/manuals/libraries/*

## Settings:

### debugdraw.COLORS
<kbd>table</kbd>

A table of colors that you can use for drawing lines and shapes. You can modify this at runtime if you want.

The list of built-in colors:
* white
* black
* red
* cyan
* yellow
* orange
* green
* blue
* pink
* magenta

### debugdraw.default_color
<kbd>vector4 | string</kbd>

The default color that will be used if you don't specify one. The default value is __*yellow*__. You can set it to a new vector4 or a string name from the `COLORS` list.

### debugdraw.default_circle_segments
<kbd>number</kbd>

The default number of segments for drawing circles used if you don't specify it. The default value is __*16*__.

## Functions:
> NOTE: Unless you mess with your render script, all coordinates are in world space.

### debugdraw.ray(v1, v2, [color])
Draw a line from `v1` to `v2`. The line can be 3D.

*PARAMETERS*
* __v1__ <kbd>number</kbd> - Line start point.
* __v2__ <kbd>number</kbd> - Line end point.
* __color__ <kbd>nil | string | vector4</kbd> - Line color. Can be a vector4 or a string name from the COLORS list.
	* *Optional - `debugdraw.default_color` (yellow) by default.*

### debugdraw.line(x1, y1, x2, y2, [color])
Draw a 2D line from (x1, y1) to (x2, y2).

*PARAMETERS*
* __x1, y1__ <kbd>number</kbd> - Line start point X and Y.
* __x2, y2__ <kbd>number</kbd> - Line end point X and Y.
* __color__ <kbd>nil | string | vector4</kbd> - Line color. Can be a vector4 or a string name from the COLORS list.
	* *Optional - `debugdraw.default_color` (yellow) by default.*

### debugdraw.rect(lt, rt, top, bot, [color])
Draw a rectangle from it's left, right, top, and bottom coordinates.

*PARAMETERS*
* __lt, rt, top, bot__ <kbd>number</kbd> - Left, right, top, and bottom coordinates of the rectangle.
* __color__ <kbd>nil | string | vector4</kbd> - Line color. Can be a vector4 or a string
name from the COLORS list.
	* *Optional - `debugdraw.default_color` (yellow) by default.*

### debugdraw.box(cx, cy, w, h, [color], [rot])
Draw a rectangle from a center point, width, and height, with optional rotation.

*PARAMETERS*
* __cx, cy__ <kbd>number</kbd> - X and Y of the center of the box.
* __w, h__ <kbd>number</kbd> - Width and height of the box.
* __color__ <kbd>nil | string | vector4</kbd> - Line color. Can be a vector4 or a string name from the COLORS list.
	* *Optional - `debugdraw.default_color` (yellow) by default.*
* __rot__ <kbd>nil | number</kbd> - Rotation angle (in radians) of the box.
	* *Optional - `0` by default.*

### debugdraw.cross(cx, cy, radiusX, radiusY, [color], [rot])
Draw a cross or X from a center point and two radii, with optional rotation.

*PARAMETERS*
* __cx, cy__ <kbd>number</kbd> - X and Y of the center of the cross.
* __radiusX__ <kbd>number</kbd> - The radius (half of the length) of the horizontal (before rotation) line  of the cross.
* __radiusY__ <kbd>number</kbd> - The radius (half of the length) of the vertical (before rotation) line of the cross.
* __color__ <kbd>nil | string | vector4</kbd> - Line color. Can be a vector4 or a string name from the COLORS list.
	* *Optional - `debugdraw.default_color` (yellow) by default.*
* __rot__ <kbd>nil | number</kbd> - Rotation angle (in radians) of the cross.
	* *Optional - `0` by default.*

### debugdraw.circle(cx, cy, radius, [color], [segments], [baseAngle])
Draw a circle from a center point and a radius, with optional segment count and base angle. If you reduce the number of segments, you can use this to draw equilateral triangles, squares, pentagons, hexagons, heptagons, etc., or even single lines. If you do, you may want to supply a `baseAngle` to orient your shape the way you want.

*PARAMETERS*
* __cx, cy__ <kbd>number</kbd> - X and Y of the center of the circle.
* __radius__ <kbd>number</kbd> - The radius of the circle.
* __color__ <kbd>nil | string | vector4</kbd> - Line color. Can be a vector4 or a string name from the COLORS list.
	* *Optional - `debugdraw.default_color` (yellow) by default.*
* __segments__ <kbd>nil | number</kbd> - The number of line segments to draw the circle/shape with. If you use a non-integer number you'll get a space at the end of your circle instead of a closing line. Setting this to `2` will draw one line across the center of the would-be circle, rotated at `baseAngle`. Setting it to less than 2 will draw a line across only part of the circle, and setting it to 1 or less will draw nothing.
	* *Optional - `debugdraw.default_circle_segments` (16) by default.*
* __baseAngle__ <kbd>nil | number</kbd> - The angle in radians of the first vertex of the circle. Measured counter-clockwise from the positive X-axis. This only really matters if you're using a very low number of segments.
	* *Optional - `0` by default.*

### debugdraw.text(text, x, y, [color])
Draws some text. Unlike the other functions, this one's X and Y are in *screen space* (starting from (0,0) at the bottom left of the screen).

*PARAMETERS*
* __text__ <kbd>string</kbd> - The text to draw.
* __x, y__ <kbd>number</kbd> - X and Y of the top left corner of the text's bounding box, in *screen space*.
* __color__ <kbd>nil | string | vector4</kbd> - Line color. Can be a vector4 or a string name from the COLORS list.
	* *Optional - `debugdraw.default_color` (yellow) by default.*
