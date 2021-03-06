<div class="printonly">This is a print-version of a paper first written for the Web. The Web-version is available at <a href="https://brechtvdv.github.io/Article-Using-an-existing-website-as-a-queryable-low-cost-LOD-publishing-interface/">https://brechtvdv.github.io/Article-Using-an-existing-website-as-a-queryable-low-cost-LOD-publishing-interface/</a>.</div>

## Introduction
{:#introduction}

The [Flemish Institute for Audiovisual Archiving](https://viaa.be) (VIAA) is a non-profit organization that preserves petabytes of valuable image, audio or video files. These files and accompanying metadata are covered by distinct [licenses](https://viaa.be/nl/portaal/support-category/item/viaa-licenties-in-het-archiefsysteem), but some can be made accessible under an Open Data [license](https://creativecommons.org/publicdomain/zero/1.0/). One initiative is opening up historical newspapers of the first World War with the open platform [hetarchief.be](https://hetarchief.be). In 2017, the raw data of these newspapers have been published as a [Linked Open Data](cite:cites 5stars) (LOD) dataset using the low-cost [Triple Pattern Fragments](cite:cites tpf) (TPF) interface. Although this interface is still accessable ([http://linkeddatafragments-qas.viaa.be/](http://linkeddatafragments-qas.viaa.be/)), no updates from the website have been exported to the TPF interface due to absence of automatisation.

<figure id="wiperstimes">
<center>
<img src="img/wiperstimes.PNG">
</center>
<figcaption markdown="block">
The famous newspaper 'Wipers Times' published on 26th February 1916 (source: hetarchief.be).
</figcaption>
</figure>

Maintaining an up-to-date LOD interface brings besides technical resources also an organizational challenge. Content editors often work in a seperate environment such as a [Content Management System](https://en.wikipedia.org/wiki/Content_management_system) (CMS) to update a website. The raw data gets exported from that system and published in a dedicated environment leaving the source of truth to the CMS. The question rises whether the data can be published closer to the authorative source in a more sustainable way.

Website maintainers are currently using [JSON-LD](https://json-ld.org/spec/latest/json-ld/) structured data snippets to attain better search result ranking and visualisation with search engines. These snippets are script tags inside a HTML webpage containing Linked Data in JSON format (JSON-LD) compliant with the [Schema.org](cite:cites 7131410) datamodel. Not only [search engine optimization](https://support.google.com/webmasters/answer/3069489?hl=en) (SEO), but also standard LOD publishing is possible. The data should be representative with the main content of the subject page, such as newspaper metadata, to be aligned with the structured data [guidelines](https://developers.google.com/search/docs/guides/sd-policies) of search engines. In order that Linked Data user agents such as [Comunica](cite:cites taelman_iswc_2018) can query a website as a dataset, the webpages should be linked together through hypermedia [controls](cite:cites fielding2000architectural).

First we give a short background of the Comunica tool and the Hydra partial collection views.
We then describe how hetarchief.be is enriched with JSON-LD snippets. Next, we explain how we allow Comunica to query over this and other sources by adding two building blocks.
After this, we demonstrate how a custom data dump can be created by an end-user that wants to further analyze this data, for instance in spreadsheet software.
The online version of this paper embeds this demo and can be tested live.
Finally, we conclude the demonstrator with a discussion and perspective on future work.

