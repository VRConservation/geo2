---
title: AIML
subject: 
subtitle: Can artificial intelligence revolutionize the geospatial world? 
short_title: 8. AIML
exports:
    - format: typst
      template: lapreprint-typst
      output: export/08_aiml.pdf
# updated October 1, 2026      
---

:::{image} /figures/ai.png
:alt: Brave image of ai
:align: center
:::

# Jury (sorta) Still Out
Two years ago, in 2024, I concluded that AI wasn't really there for geospatial data analysis and visualization. Many LLMs still don't fully understand geospatial data or geodetic formulas, mostly because they were trained on text rather than geospatial data like coordinates and projections. But over the past two years, progress has increased, and more examples show that entering language into a prompt can produce accurate maps. 

In an example of research bridging the gap of where things are located spatially, researchers tested LLMs using applied world knowledge of specific coordinates vs. 'pure gps', such as geometric math, e.g., calculating distances [@truong]. They found that models perform better at the applied task of guessing locations but cannot do pure GPS. They also found that LLMs are very good at pinpointing places for a given coordinate, but accuracy declines when asked to locate a specific city. For more accurate models that do what you need, it's likely you'll need to build and adapt your own.

Whether AI can revolutionize the geospatial world is a good question. @aiscan concluded that AI will lead to beneficial outcomes; however, it is not a panacea, and measures must be put into place for equitable access and deployment. In a review of the same paper, Frank van der Most points out that only two of the 21 applications cited as significant are focused on implementing solutions [@fvdm].

The geospatial world has seen many attempts and big claims. In 2024, I concluded that AI was not ready for primetime. On the other hand, machine learning (ML) is well developed in the free and open source (cf. chapters or tutorials from Leafmap and the R geocomputation book). ML is often conflated with AI, but it's not the same. However, at a basic level it now works and pretty well (see Using AI box).

:::{caution} Using AI in GeoLibre Works, but...
:class:dropdown
In initial tests with GeoLibre and Claude, I added two vector datasets, a raster dataset, and ran two simple SQL queries. Once connected with the API key, it worked quickly and smoothly, and Claude could find the datasets online, clip or query them to an AOI, and run summary statistics on tessellated hexagons. That does come at some cost. The simple analysis/data additions cost $2.90, not much, but that would add up with a little more analysis. It felt like if you needed AI to do that kind of geospatial analysis, you might be better off paying someone to do it for you.

Setting it up through Ollama with local models took some time, and only works with models that have tools. I eventually tried adding free models such as qwen2.5:7b and llama3.2:3b. I was able to connect the qwen and llama models to GeoLibre, but they were exceptionally slow and only gave answers on how to run Python code to add two simple vector sets. Claude, on the other hand, just added the layers.

QGIS has a model context protocol plugin that allows you to communicate between a model and QGIS. I have not tried it, but the setup documentation doesn't look very low friction.
:::

Artificial intelligence for geospatial is at the gee-whiz stage, but it's not amazing. One recent example showed prompt engineering with GeoGPT to produce some ok chloropleth maps that would take the same amount of time to assemble using the appropriate dataset and software highlighted in this book. Plus, taking a little time to run the code and do exploratory data analysis always allows you to know the data, which is something that doesn't happen when you ask a question and get a map. Also, GeoGPT is not free, nor is it open source!

## Exceptions
One notable exception is [GeoLibre](https://geolibre.app) a geospatial app that runs on the desktop, browser or phone and has an AI panel that can also be used with spoken words in addition to written [@wu-geolibre]. This arose in part from Geemap and Leafma, mentioned in earlier chapters as well as GeoAgent, a QGIS plugin, allows users to input requests, queries, and analyses by typing or voice [@wu]. The plugin design and UI are excellent and easy to use, although I've found entering the secret keys to start to have some errors. The documentation has links to a video [tutorial](https://www.youtube.com/watch?v=5zkXQlHUsu8) on YouTube that will get you up and running quickly.

Another useful exception is [Bunting Lab's](https://buntinglabs.com/) autocomplete for map digitization, which installs as a QGIS plugin. This isn't a free tool, but it seems like it would certainly be worth its weight in gold if you needed to do a lot of map digitizing, taking much of the tedious manual labor out of this task. Another exception is where AI generates cut-and-paste codeblocks that throw fewer errors than the nonsense generated from prompts a few months ago or get you unstuck when an approach is not working.

Overall, AI still has a ways to go with geospatial analysis. AI could help democratize geospatial analysis by lowering the cost of entry to both data and coding, but it seems like many of the companies involved are going down for profit routes rather than free and open source.

## Resources
- [GeoLibre](https://geolibre.app/) is a free and open source cloud-native GIS platform available on multiple platforms. It's AI panel works well when you connect with paid models, but I found setting it up with local free models in Ollama to be problematic and didn't work (yet). 
- [QGIS-mcp plugin](https://plugins.qgis.org/plugins/qgis_mcp_plugin/) is a socket server plugin that connects QGIS to LLMs through the model context protocol. It works, but has a fair bit of friction in setup difficulty.
- NASA/Microsoft VEDA dashboard and earth copilot.
- [Autonomous GIS](https://github.com/gladcolor/LLM-Geo). This repo and LLM are pretty cool and hopefully will receive further development over time. Unfortunately, there was a lot of activity from commits when it came out, but not much since.
- [Jupyter generative AI](https://blog.jupyter.org/generative-ai-in-jupyter-3f7174824862). Generative AI coding in Jupyter notebooks.
- [human brain edge over ai article](https://www.linkedin.com/pulse/where-human-brain-still-has-edge-over-ai-fast-company-j2jpe/)
- [A Beginner's Guide to Prompt Engineering with GitHub Copilot](https://dev.to/github/a-beginners-guide-to-prompt-engineering-with-github-copilot-3ibp). This is an extensive guide on how to engineer your prompts to code better and best use AI. It is also applicable to prompts in other platforms such as Gemini or ChatGPT.
- [Open source MLOps: Platforms, frameworks, and tools](https://neptune.ai/blog/best-open-source-mlops-tools). Thoughtful piece on pros and cons of open source machine learning tools.
- [Awesome Machine Learning](https://github.com/josephmisiti/awesome-machine-learning). A curated list of resources, tools, frameworks, articles, and projects related to Machine Learning Operations (MLOps).
- [GeoGPT: An assistant for understanding and processing geospatial tasks](https://doi.org/10.1016/j.jag.2024.103976). Paper by Zhang et al (2024) on the GeoGPT model that can conduct geospatial data collection, processing, and analysis in an autonomous manner.
- [Aino AI plugin](https://plugins.qgis.org/plugins/aino-qgis-plugin-main/). QGIS plugin Aino converts natural language prompts such as "parks in Barcelona" into vector layers containing relevant OSM data.
- [Clay Foundation Model](https://clay-foundation.github.io/model/index.html). Does it only work on Linux devices with CUDA GPUs? What the?




<!-- 

 It could be that AI helps to democratize geospatial analysis by lowering the cost of entry to geospatial data and software. Democratization of data medium article 
 
From Josep Ferrer (@rfeers on twitter): In multiple linear regression, imagine you're baking. You've got different ingredients or variables. You need the perfect recipe (model) for your cake (prediction). Each ingredient's quantity (coefficient) affects the taste (outcome).
-->
