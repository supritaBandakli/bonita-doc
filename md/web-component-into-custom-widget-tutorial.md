# How to include a Web Components inside a Custom Widget

Web components are changing the Web towards a standard way to encapsulate and distribute projects. The level of abstraction can vary by the context, however you can imagine importing a small stylized **button** inside your application just by importing
this button web component definition.

## Preface

The aims fo this tutorial is to create a custom widget that imports 


## Install Bower

...

## Npm install dependencies
...

## Install Polymer Bundler
...

## Install Map component

bower install --save GoogleWebComponents/google-map

## Extract all the dependencies into a single file

polymer-bundler index.html > build-noscript.html --rewrite-urls-in-templates --strip-comments

➜  maps-component polymer-bundler index.html > build-complete.html --rewrite-urls-in-templates --inline-scripts --strip-comments


## Move all the scripts into a local asset

## Put the Polymer content inside the controller of the Custom Widget

## Add the Dom-Module and the Google Map tag into the Widget Template

## Success?
