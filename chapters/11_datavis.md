---
title: Field
subject: 
subtitle: A Primer on Effective Geospatial Data Visualization
short_title: 11. Data Visualization
exports:
    - format: typst
      template: lapreprint-typst
      output: export/11_datavis.pdf
---
> "Because the world around us is a complex one, it would be virtually impossible to simply place a small version of it on a map...Consequently all maps are abstractions of reality and form." @field

# 3. Visualization Principles
Maps as an abstraction of reality give their author a great deal of responsiblity and power. This can be abused, e.g., maps that lie or neglected, e.g., maps that suck or are very hard to decipher.

## FOSS Visualization
There are a lot of ways to visualize data, some of them quite expensive others expensive and propietary. Then there are free and open source software tools that are increasingly useful and sometimes on a par with paid or subscription software. 

Generally the biggest plus to using FOSS tools is they're free and flexible, keep you and in charge of the data and what it looks like, and your data doesn't have to go to a cloud server to be used by whatever AI company to train their models {numref}`pluses`. The biggest disadvantage is having to rely heavily on code and the terminal to run the tools. However, the latter is become less of a barrier with large language models (LLMs) such as Claude, script snippets, and other tricks we'll show you that make life easier in the FOSS world.

:::{table} Pros and cons of free and open source tools for data visualization.
:label: pluses
:align: center
| **PROS**    | **CONS**  |
|-------------------|-----------|
| 🟢 Free | 🔴 Code and CLI to use |
| 🟢 Open-source | 🔴 Can frequently fail |
| 🟢 Learning code is fun | 🔴 Some software not updated |
| 🟢 Flexible | 🔴 Unavailable tools |
:::

## Purpose & Audience
Define your message before you design. Every effective map or chart begins with a clear understanding of:

- **What is the story?** - What insight or finding do you want to communicate?
- **Who is the audience?** - What is their background and knowledge level?
- **What action or decision** will this visualization support?

According to cartographic design theory, a map or chart that cannot stand alone or fails to communicate a specific message to its intended audience has failed in its primary purpose—regardless of its aesthetic beauty or technical sophistication [@bertin; @tufte].

## Data Integrity
Represent data truthfully and avoid distortion. It is easy to lie with maps, although all maps distort the truth somewhat, you just need to decide which truth you're displaying. Distorted visualizations mislead audiences and undermine decision-making. This is not just an ethical issue—it destroys trust and credibility.

The most important rule in visualization is that your visualization must not lie. This means:

- **Accurate scaling** - Visual dimensions must be proportional to data values
- **Proper context** - Show data in appropriate context; don't cherry-pick ranges
- **No misleading effects** - Avoid visual tricks that exaggerate or minimize differences
- **Document your methods** - Clearly explain data sources, processing, and any transformations

Common distortions to avoid include

- Truncated axes that exaggerate small differences
- 3D effects that distort comparisons
- Area/volume charts that don't scale properly with data
- Cherry-picked time ranges or data subsets without context

According to @tufte the Lie Factor = Size of effect shown in graphic / Size of effect in data with a value of 1.0 indicating accurate data representation.

## Visual Encoding
The way you encode data visually determines how effectively viewers can extract information. Different visual variables work better for different types of data. Research in graphical perception shows that certain visual properties are processed pre-attentively (instantly, without conscious effort). Bertin's foundational work established that visual encoding must match the logical structure of the data being represented. This principle remains central to modern cartography and information design [@bertin]. Using the wrong encoding forces viewers to work harder to understand your data. These visual properties encode different types of information at different effectiveness levels {numref}`variables`.

:::{table} Visual variables [@bertin].
:label: variables
:align: center

| Visual Variable | Best For | Effectiveness |
|---|---|---|
| **Position** | Precise comparisons, continuous data | Highest |
| **Size** | Quantities, hierarchies | High |
| **Color (Hue)** | Categorical differences, qualitative data | High |
| **Value** (lightness) | Ordered sequences, quantitative ranges | High |
| **Texture/Pattern** | Categorical distinctions | Medium |
| **Orientation** | Directional data, flow | Medium |
| **Shape** | Category identification | Lower (hard to compare) |
:::

A key principle is to match the esncoding to your data type. These include:

- **Categorical data** → Use hue (distinct colors), shape, or texture
- **Ordinal data** (ranked) → Use value/lightness, size, or position
- **Quantitative data** (continuous) → Use position, size, or value (lightness)
- **Temporal data** → Use position (typically left to right) or animation

## Simplicity
Minimizing clutter and too many items in a map maximizes clarity and focuses the audience on your key messsages. Viewers have limited cognitive capacity. Every element competing for attention reduces the clarity of your message. Research in visual perception consistently shows that simplified, focused visualizations communicate more effectively than complex, decorated ones.Your visualization should communicate its message as efficiently as possible. Every element should earn its place.

Edward Tufte's foundational concept of the data-ink ratio advocates for maximizing the amount of ink devoted to representing data in any data visualization [@tufte]. Tufte argues that "non-data-ink" or decoration should be eliminated or minimized.

Some examples of items to eliminate:

- Chartjunk - Decorative elements that don't convey data (excessive text, north arrows, scale bars, 3D effects, background images, unnecessary grid lines)
- Redundant encoding - Showing the same data in multiple ways
- Competing visual elements - Elements that distract from the main message
- Excessive labeling - Text that clutters rather than clarifies

**For Maps:**
- Remove unnecessary boundary lines
- Use basemap details that provide context (not distraction)
- Simplify your color scheme
- Zoom to your area of interest
- Clear, minimal labeling

**For Charts:**
- Remove decorative gridlines (or make them subtle)
- Use only the necessary axes
- Choose bar charts or dot plots over pie charts (when comparing values)
- Consistent, limited color palettes
- One insight per chart

:::{important} A word about north arrows & scale bars 🧭
:class: dropdown
North arrows are nice, but add clutter to maps and often are not needed when it's understood that up is north on the page. North arrows are only really necessary if you've rotated the map and north is a different direction. Scale bars also add to the clutter and are not necessary, particularly if your audience is familiar with the map's region or you have an inset map showing the location of the area. There are always exceptions to layout cleanup, but it's usually better to leave these out. Your map will be easier to read and cleaner as a result. Don't add these items for dogmatic reasons, ask if they really add value and only add if needed.
:::

## Visual Hierarchy
Guide viewer attention and integrate all elements intentionally. Don't add items such as north arrows and scale bars just because everyone else does. A well-designed visualization controls the order and emphasis of information, guiding viewers from the most important insights to supporting details. Modern visualization experts including @few emphasize the importance of visual hierarchy in directing attention and improving comprehension.

Use these techniques to emphasize importance:

- **Size** - Important elements larger than supporting elements
- **Color** - Highlight key data with contrasting colors; use muted tones for context
- **Position** - Place primary insights prominently (top-left for readers of left-to-right languages)
- **Contrast** - Use white space and contrast to separate important information
- **Saturation** - More saturated colors draw attention; desaturated colors recede

All elements of a map should work together:

- **Title** - Clear, specific (not "US Population" but "US Population Growth, 2010-2020")
- **Legend** - Essential but not intrusive; only show what's necessary. Sometimes the legend can be part of the explanatory text.
- **Data Sources** - Always cite your data sources
- **Annotations** - Use strategically to highlight key insights without overwhelming
- **Color scheme** - Consider colorblind-friendly palettes

A reminder of some basic design principles

- **Consistency** - Use the same colors and symbols throughout a series of maps/charts
- **Balance** - Distribute visual weight; avoid one-sided emphasis
- **Rhythm** - Repetitive patterns (when intentional) can emphasize patterns in data
- **Gestalt Principles** - Humans group similar elements together; use this intentionally

Viewers naturally scan visualizations with a specific eye pattern. By understanding this, you can guide them to your key insights first, then let them explore details. This makes your visualization more persuasive and memorable.

:::{figure} /figures/datavis/uk.png
:label: terrible
:width: 350px
:align: center
A map showing absolutely nothing. From  Twitter's terriblemaps.
:::

# Bad Map Lessons
Let's look at some examples. There are lot of heinous maps out there that are cluttered, trying to convey too much information, take too long to interpret, or don't interpret anything ({numref}`terrible`). 

## Principles (MOVE THIS TO SECTION ABOVE)
Although the ArcGIS pro layout interface is easier to use than QGIS, let's ignore that and just borrow some great layout suggestions from [John Nelson](https://www.youtube.com/@JohnNelsonMaps) ({numref}`principle-table`).

:::{table} Principles of sound map layouts. Adapted from John Nelson's [ArcGIS Pro Layout Makeover](https://www.youtube.com/watch?v=q93ZAFoS_bc&t=10s).
:label: principle-table
:align: center

| Principle | Details |
|-----------|---------|
| Composition | - Overall, balance the composition <br>- Prioritize map size<br>- Area of interest best fit = layout orientation<br>- Use surrounds as balancing agents<br>- Use layout guides |
| Text | - Only key words as title<br>- Secondary context as sub-title<br>- Eliminate, distill, or defer paragraphs<br>- Integrate annotation <br>- Include attribution |
| Surrounds | - Remove unnecessary borders, backgrounds, and neatlines<br>- Simplify the legend and  overview<br>- Remove the north arrow, scalebar, and photographs |
:::

## Examples
Let's explore some of the details of these principles and suggestions with an example. {numref}`bad` shows many things wrong you can do with a map from too many colors, excessive text, hard to read legend, and confusing data layers, among other things. Overall, it's just trying to show too many layers and combining data that may or may not be related and certainly not viewable, understandable in a static map. There are random labels of fires, some text that overlaps and unless you know the area, it's hard to tell where the map is located. The only thing this map gets kudos for is 80's ski clothing color styling!

:::{figure} /figures/datavis/superbad.png
:label: bad
:width: 700px
:align: center
A terrible map!
:::

Let's see if we can simplify it to make it a little more readable. In the new map, we've simplified in a lot of different ways {numref}`better`. First we removed the north arrow, scale bar, much of the purple text, and background colors. We also removed the credits, something we normally would not recommend, but the credits were quite long and it was easier to remove them, unclutter the map and move to the figure caption. We added an inset map showing location of the area of interest that is highlighted with a clearer border and a simplified base map, focusing the reader on the area where the action is. We clarified the title as well. Legend entries are simplified and fewer. We used guides to align the legend and inset map as well as the legend and text to help balance the overall items in the map. It's not perfect (yet) but it is much easier to interpret.

:::{figure} /figures/datavis/super.png
:label: better
:width: 700px
:align: center
A map of fire impacts on disadvantaged communities. Credits: ESRI, Tiger Lines, USGS, NASA, TomTom, Garmin, OSM, GIS user community.
:::

In this example, the base map could be cleaned up a bit more and the labels could use a little better detail or removed and added back in with key towns or places highlighted