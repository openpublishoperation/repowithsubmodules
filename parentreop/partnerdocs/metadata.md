# Metadata #

There is a limited amount of metadata at the moment. 

Metadata can be specified at two places:

* In each topic, you can use YAML frontmatter to store metadata in Markdown file. This format is already widely used in github and will be rendered into a table in github markdown preview. Here is one example:

`---`
title: Get Started
toc_title: Get Started
`---

* Stored in [openpublishing.build.docset.config.json](repo-config.md) file within a docset.

- "ROBOTS": "NOINDEX, NOFOLLOW" - Indicates the search engines if the docset should be indexed by search engines.