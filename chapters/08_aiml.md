---
title: AIML
subject: 
subtitle: Can artificial intelligence revolutionize the geospatial world? 
short_title: 8. AIML
exports:
    - format: typst
      template: lapreprint-typst
      output: export/08_aiml.pdf
---

:::{image} /figures/ai.png
:alt: Brave image of ai
:align: center
:::

# Jury (sorta) Still Out
Two years ago in 2024 I concluded that AI wasn't really there for geospatial data analysis and visualization. It still seems that many LLMs don't entirely understand geospatial data or geodetic formulas, mostly because they have been trained on text and not geospatial data like coordinates and projections. But in the past two years there has been much progress and there are more examples where entering language into a prompt will produce accurate maps. 

In an example of research bridging the gap of where things are located spatially, researchers tested LLMs using applied world knowledge of specific coordinates vs. 'pure gps', such as geometric math, e.g., calculating distances [@truong]. They found that models are better at the applied track to guess locations but could not do pure gps. They also found that LLMs are very good at pinpointing places for a given coordinate, but accuracy declines when asked to locate a specific city. For more accurate models that do what you need, it's likely you'll need to build and adapt your own.

Whether AI can revolutionize the geospatial world is a good question. @aiscan concluded that AI will lead to beneficial outcomes, however, it is not a panacea, and measures must be put into place for equitable access and deployment. In a review of the same paper, Frank van der Most points out that only two of the 21 applications cited as significant are focused on implementing solutions [@fvdm].

There have been many attempts and big claims in the geospatial world, but as of 2024, I have to conclude it isn't quite ready for primetime (although this is rapidly changing)! Machine learning (ML) is well developed in the free and open source (cf. chapters or tutorials from Leafmap and the R geocomputation book). ML is often conflated with AI, but it's not the same. Artificial intelligence for geospatial is at the gee-whiz stage, but it's not amazing. One recent example showed prompt engineering with GeoGPT to produce some ok chloropleth maps that would take the same amount of time to assemble using the appropriate dataset and software highlighted in this book. Plus, taking a little time to run the code and do exploratory data analysis always allows you to know the data, which is something that doesn't happen when you ask a question and get a map. Also, GeoGPT is not free, nor is it open source!

## Exceptions
An exception to the usefulness side I've seen with AI is [Bunting Lab's](https://buntinglabs.com/) autocomplete for map digitization, which installs as a QGIS plugin. This isn't a free tool, but it seems like it would certainly be worth its weight in gold if you needed to do a lot of map digitizing, taking much of the tedious manual labor out of this task. Another exception is where AI generates cut-and-paste codeblocks that throw fewer errors than the nonsense generated from prompts a few months ago or get you unstuck when an approach is not working.

Another recent except is GeoAgent, a QGIS plugin, allows users to input requests, queries, and analyses by typing or voice [@wu]. The plugin design and UI are excellent and easy to use, although I've found entering the secret keys to start to have some errors. The documentation has links to a video [tutorial](https://www.youtube.com/watch?v=5zkXQlHUsu8) on YouTube that will get you up and running quickly.

Overall, AI still has a ways to go with geospatial analysis. AI could help democratize geospatial analysis by lowering the cost of entry to both data and coding, but it seems like many of the companies involved are going down for profit routes rather than free and open source.

## Resources
- NASA/Microsoft VEDA dashboard and earth copilot
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
