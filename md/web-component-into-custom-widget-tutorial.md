# How to include a Web Components inside a Custom Widget

Web components are changing the Web towards a standard way to encapsulate and distribute projects. The level of abstraction can vary by the context, however you can imagine importing a small stylized **button** inside your application just by importing
this button web component definition.

## Preface

The aims fo this tutorial is to create a [google-map](https://www.webcomponents.org/element/GoogleWebComponents/google-map)custom widget that imports 



## Include with external dependencies  

1) Create a custom-widget
2) Import polymer as asset. You can: 
    * Download polymer.min.js and import it as internal asset
    * Use cdnjs of [polymer.min.js](https://cdnjs.cloudflare.com/ajax/libs/polymer/0.5.6/polymer.min.js) as external asset
3) You need link at the top of your template the html file of google-map.
    
    `<link rel="import" href="https://raw-dot-custom-elements.appspot.com/GoogleWebComponents/google-map/1.2.0/google-map/google-map.html">`

4) Create 4 properties

            Name: apiKey
            Label: Api Key
            Treat as Dynamic value
            Type: text
            Default value: <insert your own key> 
             
            Name: draggable
            Label: Draggable
            Treat as Dynamic value
            Type: boolean
            Default value: true
             
            Name: latitude
            Label: latitude
            Treat as Bidirectional bond
             
            Name: longitude
            Label: longitude
            Treat as Bidirectional bond
    
Note: to generate your own key see [this documentation](https://developers.google.com/maps/documentation/javascript/get-api-key) 

5) In your template below your import, add  the following code:

        <style>
          google-map {
            height: 600px;
          }  
        </style>
        <google-map fit-to-marker api-key="{{properties.apiKey}}" latitude="{{properties.latitude}}" longitude="{{properties.longitude}}">
          <google-map-marker latitude="{{properties.latitude}}" longitude="{{properties.longitude}}" draggable="true" drag-events>
              <div>Latitude: {{properties.latitude}}</div>
              <div>Longitude: {{properties.longitude}}</div>      
          </google-map-marker>  
        </google-map>

6) In your controller, add the following code:

        var marker = document.querySelector('google-map-marker');
        
        marker.addEventListener('google-map-marker-dragend', function(e) {
            
             var latLng = e.detail.latLng;
             $scope.properties.latitude = latLng.lat();
             $scope.properties.longitude = latLng.lng();
        
             console.log('AFTER inside ', $scope.properties.latitude, $scope.properties.longitude);
             $scope.$apply();
           
         });
         
tl;dr; Link this custom-widget on custom-widget repositories on github 

## Include a bundled web component (without external link) 

### Install Bower

...

### Npm install dependencies
...

### Install Polymer Bundler
...

### Install Map component

bower install --save GoogleWebComponents/google-map

### Extract all the dependencies into a single file

polymer-bundler index.html > build-noscript.html --rewrite-urls-in-templates --strip-comments

➜  maps-component polymer-bundler index.html > build-complete.html --rewrite-urls-in-templates --inline-scripts --strip-comments


### Move all the scripts into a local asset

### Put the Polymer content inside the controller of the Custom Widget

### Add the Dom-Module and the Google Map tag into the Widget Template

### Success?
