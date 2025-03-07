
# Next

* Allow destruction of deepscatter objects, freeing up associated GPU memory.
* Allow multiple plots on the same page by assigning ids: https://github.com/CreatingData/deepscatter/pull/47.
* Improved Typing for Aesthetics and Transforms. https://github.com/CreatingData/deepscatter/pull/46

# 2.4.1

Attempted bundle fixes.

# 2.4.0

FEATURES:

Preliminary ability to pass an arrow table directly to Deepscatter without tiling it using quadfeather. Each record batch is treated as a tile, and every batch will be drawn in most draw passes; this works well for up to a few million points.

DESIGN:

Extensive refactor to allow 'datasets' to be drawn, which provide an abstraction between individual tiles and the full renderer. This is currentoy used to draw arrow tables; I may also allow it to use duckdb soon. 

CODE QUALITY:

Thanks to Don Isaac, a number of improvements to linting and ts typing that should help increase code quality going forward. 

# 2.3.2

FEATURES: Clarify and cleanup the API around `tooltip_html` and `click_function`. Now both can be *either* by assigning a function to the base scatterplot object, or by passing a string that defines a function with an implied argument of `datum` to the JSON-based API.

BUGFIX: Fix problem breaking secondary filters.

CODE: Slightly simplify aesthetic code by removing 'label' attribute.

# 2.3.1 

Publication fix

# 2.3.0 

BREAKING API CHANGE: 'duration' argument is now in milliseconds, not seconds, for greater consistency with d3 tooling. 

Create new class of "plot settings" for aesthetics scaled at the plot level rather than the point level. This allows smooth updates to overall point size, target alpha, etc.

"Shufbow" scheme uses deterministic order. [commit](https://github.com/CreatingData/deepscatter/commit/a54fad1fcc2650b6fe5d08823be26e286e0e2edd)



# 2.2.5

Support int32 dates as floats (without null mask for now.)

# 2.2.3

Use of 'x0' and 'y0' positions produce smooth interpolation between two different points.

# 2.2.2

Hopefully fix issue with points of index zero breaking display size rules.

# 2.2.0

Switch to Arrow JS 7.0 backend, requiring substantial rewrite.

# 2.1.1

Restore some jitter types broken by ts conversion.

Remove some extraneous logging.

# 2.1.0

1. Major refactor to use typescript. This requires standardizing some of the approaches to API a bit more, and 
   likely will cause some short-term breakage until all changes are found. Most
   files renamed from `.js` to `.ts`. Not yet passing all typescript checks.

2. Shift texture strategy for lookups to minimize number of samplers; from 16 in the old version to two
   in the new one (one for one-d channels like filters, and the other for color schemes.) Introduces a new 
   class in AestheticSet.ts.

3. Start to build an API independent of the `plotAPI`, especially using Andromeda Yelton's code to programatically
   control the function responses on mouseover and click events. 

4. Some minor shifts in the shader code. I don't anticipate doing any more major webGL features, and instead am
   trying to prepare for a webGPU push that will be version 3.0.

5. Add UMD, IIFE, etc. modules builds.

# 2.0

Complete rewrite. Move from Canvas to WebGL and from csv tile storage to Apache Arrow.

# 1.0

First release.
