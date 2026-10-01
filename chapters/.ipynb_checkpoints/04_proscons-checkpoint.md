---
title: Pros & Cons
subject: 
subtitle: Pluses and minuses of using open-source geospatial software
short_title: 4. Pros & Cons
exports:
    - format: typst
      template: lapreprint-typst
      output: export/04_proscons.pdf
---

## Open source vs. paid
Navigating the world of open-source and subscription-based geospatial tools is challenging. Paying for software, imagery, and technicians to conduct your analyses can also be costly. Increasingly, for-profit companies are monetizing software and imagery use that is proprietary to their products. Higher costs and limited access make it difficult for nonprofits, communities, and individuals to access important geospatial data, reducing the democratization and use of this information in a world where it needs to be freely available and accessible.

## False dichotomy
In truth, it's a false dichotomy to pit FOSS vs. paid geospatial tools. Your workflow may involve data analysis in GEE, then importing datasets into ArcGIS Pro for further analysis and creating layouts, web apps, or online maps. You may find that working with many government agencies requires the use of Arc products because it's what their employees know or the agency has a license (*Cf. the [Modern Geospatial](https://mapscaping.com/podcast/modern-geospatial/) Mapscaping Podcast on using FOSS with different clients*).  See Chapter 1: FOSS for more discussion on using multiple tools.

## Table
A non-exhaustive summary of the more commonly used geospatial software products is provided below (Table 1).

Table 1. Pros and cons of select geospatial software providers.

| SOFTWARE | PROS      | CONS            | PRICE |
| :------- | :------   | :-------        | ----: |
| ArcGIS Pro | Use, Support, Vis | Price, Credits, Notebooks | $100-6,000+/user/yr |
| CARTO | Use, Vis, Data | Haven't used | High |
| DuckDB | Use, Fast, Documentation | Vector data only | Free |
| Earth Blox | Use, Data, Solutions | Price | Unclear: >$1,500? |
| Felt | Use, Vis, QGIS integ | Price, Sharing, Long-term? | $360-1,080/user/yr |
| GEE  | Cloud, Support, Colab | Javascript, Cost | Free to mucho |
| Geemap | Use, Support, GEE/Colab integration | Setup in windows | Free |
| GeoLibre | Multiple formats, browser run, complex analyses | Minor bugs, doesn't (yet) save rasters | Free |
| Leafmap | Use, Feature-rich, one line code solutions | CLI, IDE setup in Windows | Free |
| Planet | Vis, Data | Haven't used | High |
| Post-GIS | Use, Fast, QGIS integration, Industry Standard | UI | Free |
| QGIS | Free, Community, Analysis | Vis, Crashing, Future? | Free |
| R, RStudio | Use, Plugins, Academic standard | Slow at times | Free |

## Discussion & Caveats
Comparing geospatial software and tool packages in Table 1 is somewhat unfair. For example, the new GeoLibre app is amazing, exceptionally fast, and works from desktop, browser, or phone apps, but as the authors state, it's like using a smartphone camera compared to a full-fledged SLR (QGIS or ArcGIS Pro) in terms of analysis and functionality. The term 'Use' signifies ease of use. Vis = visualization is very good and feature-rich. Support and documentation indicate whether support is good or bad. Typically, the software documentation and tutorials are very good, or the company or software provider quickly responds to bugs or questions. 

I didn't add many software packages I haven't used. I have limited knowledge of and experience with CARTO, Felt, and Earth Blox since I've only used them in free-to-test form. As a result, my pros and cons are limited for those packages. Midway through 2026, Carto started requiring key-based access for their excellent basemaps. This means adding them via XYZ tiles in QGIS or always using the key in GeoLibre. As a result, the QGIS plugin Quick Map Services just removed Carto as an option.

Evaluating pricing is difficult because several companies are opaque about pricing, ask you to submit information for a quote, or want you to join a call for bespoke pricing. For instance, Earth Blox doesn't list prices online and wouldn't tell me when I emailed them, but they offered to schedule a call to discuss the product. I've tried to add pricing information when I have an approximate or specific idea.

One common thread with the pros and cons of software cost is that paid means high quality and ample tech support. This is not necessarily true. Some open source software providers reply quickly or help with issues, partly because they're small. For well-loved free and open source software, communities, wikis, or forums often provide help or feedback to resolve issues. Several long-term providers, such as QGIS and Google Earth Engine (GEE), have very active communities, so getting help through forums for common bugs and errors is often easy. 

A major caveat for any software is a provider's long-term viability. You don't want to put all your assets, analysis, and projects into a proprietary system only to have the company go belly up later, making your data and analysis hard to access.
