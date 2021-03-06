---
page_title: Plugin development
page_description: Plugin development for Grafana
page_keywords: grafana, plugins, documentation, development
---

# Plugin development

From grafana 3.0 it's very easy to develop your own plugins and share them with other grafana users.

## Short version

1. [Setup grafana](https://github.com/grafana/grafana/blob/master/DEVELOPMENT.md)
2. Clone an example plugin into ```data/plugins```
3. Code away!

## What languages?

Since everything turns into javascript it's up to you to choose which language you want. That said it's probably a good idea to choose es6 or typescript since we use es6 classes in Grafana. So it's easier to get inspiration from the Grafana repo is you choose one of those languages.

## Buildscript

You can use any build system you like that support systemjs. All the built content should end up in a folder named ```dist``` and committed to the repository.By committing the dist folder the person who installs your plugin does not have to run any buildscript.

All our example plugins have build scripted configured.

## module.(js|ts)

This is the entry point for every plugin. This is the place where you should export your plugin implementation. Depending on what kind of plugin you are developing you will be expected to export different things. You can find whats expected for [datasource](http://docs.grafana.org/v3.0/plugins/datasources/), [panels](http://docs.grafana.org/v3.0/plugins/panels/) and [apps](http://docs.grafana.org/v3.0/plugins/app/)
plugins in the documentation.

## Start developing your plugin
There are two ways that you can start developing a Grafana plugin.
1. Setup a Grafana development environment. [(described here)](https://github.com/grafana/grafana/blob/master/DEVELOPMENT.md)  and place your plugin in the ```data/plugins``` folder.
2. Install Grafana and place your plugin the plugins directory which is set in your [config file](http://docs.grafana.org/installation/configuration/)

We encourage people to setup the full Grafana environment so that you can get inspiration from the rest of grafana code base.

When Grafana starts it will scan the plugin folders and mount every folder that contains a plugin.json file unless the folder contains a subfolder named dist. In that case grafana will mount the dist folder instead.
This makes it possible to have both built and src content in the same plugin folder.

## Boilerplate
We currently have three different examples that you can fork/download to get started developing your grafana plugin.

 - [simple-json-datasource](https://github.com/grafana/simple-json-datasource) (small datasource plugin for querying json data from backends)
 - [piechart-panel](https://github.com/grafana/piechart-panel)
 - [example-app](https://github.com/grafana/example-app)
