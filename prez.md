class: center, middle

# WEB and Tango
![maxiv](image/maxiv.png)
# The MAX IV experimentation

Tango Meeting 2018, ELI Beamlines
 
By [Vincent Hardion](https://twitter.com/hardion) on the behalf of the [KITS team](https://github.com/orgs/MaxIV-KitsControls)


[Our MAX IV github repository](https://github.com/orgs/MaxIV-KitsControls)
---

# Agenda 

#- A long journey in Web Development
#- [TangoJS reviving](https://github.com/tangojs/tangojs-polymer)
#- [Tango REST Api in python](https://github.com/MaxIV-KitsControls/mtango-py)
#- More Web professional: GraphQL and WebSocket

---
# Context

##  Here today to make a presentation for developer or not end-user.
And especially for new comers to web development


## My personal journey in the web development
    - Me and my new passion: Javascript
    - Beginner: Javascript compares to Java like Dog compares to Hedgedog 
    - Amazed by the User Experience given by web

---
background-image: url(image/midlife.jpeg)
---
# Quite nice development that became abandonware
TangoJS, Mtango-py, Tango Web something, Elogy, Web Synoptic
.center[
<video style="width: 640px; height: 360px" autoplay loop>
    <source src="https://vimeo.com/maxiv/review/282663466/e19facceec" type="video/mp4">
    Your browser does not support playing this Video
</video>
]
---
# Elogy[*] saved at the last minute

.center[
<video style="width: 640px; height: 360px" autoplay loop>
    <source src="screencast/elogy.mov" type="video/mp4">
    Your browser does not support playing this Video
</video>
]


.footnote[* Compatible elog]
---
# TangoJS reviving

## Big push for the User eXperience 
Needed to push for web development in the team but why? Web development for Control software engineer is not mainstream but still we think is the way to go for the next year. 

## Not much motivation inside the team 
Where to start? We can revive the TangoJS and mtango-py projects... Great idea!!!

## Problem? TangoJS was using a prestandard version of web component
---
# Web component
**'''** 
*Web Components is a suite of different technologies allowing you to create reusable custom elements — with their functionality encapsulated away from the rest of your code — and utilize them in your web apps.*
**'''**

## Sounds the way I used to work on desktop development. So let's explore a bit more

.footnote[[MDN Reference](https://developer.mozilla.org/en-US/docs/Web/Web_Components)]
---
# Web component - Custom Element
## Usage
```html
<html lang="en">
  <head>  </head>
  <body>
    ...
    <tangojs-led model="sys/tg_test/1/State"></tangojs-led>
    ...
  </body>
</html>
```

## The inside
```html
<div id="root">
    <span>[[info.name]]</span>
    <span>[[attribute.value]]</span>
    <x-led on=true color='[[color]]'></x-led>
</div>
```

---
# Web component
## The idea is simply based on the ability to create new html tags.
## Desktop Developer: Look like qt and xml!!! Not that I like xml but let's continue

Others:
- Your component can keep its own style (Shadow DOM)
- Your component can be adaptable and dynamic (HTML templates)
- Your component can be easily reused by keeping it in a separate file (HTML Imports)

---
#TangoJS and Polymer
- TangoJS were out of date when started to get it running ;-)
- Started to upgrade it to the formal standard
- But found Polymer, basically a webcomponent library, not a framework.

---
#Polymer
**'''** *Polymer just builds on top of the Web Component standard adding some syntactical sugar* **'''**

- Javascript ES6 with class, inheritance, properties... Perfect for an OO developer
- Reactive when binding property and attribute... Perfect for Lucky Luke


---
#Polymer Example
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Polymer 3.0 example</title>
    <!-- Polyfills only needed for Firefox and Edge. -->
    <script src="./node_modules/@webcomponents/webcomponentsjs/webcomponents-loader.js"></script>
  </head>
<body>

  <!-- Define a new Custom Element by extending Polymer's base class  -->
  <script type="module">
    import {PolymerElement, html} from '@polymer/polymer';

    class MyElement extends PolymerElement {

      static get properties() { return { mood: String }}

      static get template() {
        return html`
          <style> .mood { color: green; } </style>
          Web Components are <span class="mood">[[mood]]</span>!
        `;
      }
    }

    customElements.define('my-element', MyElement);
  </script>

  <!--  Use element like any other HTML tag  -->
  <my-element mood="awesome"></my-element>
  
</body>
</html>
```

---
# Tangojs-polymer

Enhance any Polymer components with TangoJS capabilities (Mixins)
Extra properties you can bind with:
  - value: value of the Tangojs Attribute
  - unit: Unit of the Tangojs Attribute
  - setPoint: last set point
  - writable: True if the atriibute can be set 
  - qualityColor:  Quality factor of the current attribute
  - InputType: indicate which component is suitable for setting the value

---
# Tangojs-polymer
## Example for Label, an attribute component:
.center[![:scale 100%](image/tangojs-label.png)]

---
# Tangojs-polymer
## Example for Label, an attribute component:
### HTML:

```html
<template>
  <span id="name">[[info.label]]</span>
  <span id="value" style$="background-color: [[qualityColor]]">[[attribute.value]]</span>
  <span id="unit">[[unit]]</span>
</template>
```
### JavaScript:
```js
  class TangojsLabel extends Tangojs.withTangoAttribute(Polymer.Element) {
    static get is() { return 'tangojs-label'; }
  }
```

---
# Tangojs-polymer
.center[![:scale 50%](image/tangojs-button.png)]
.center[![:scale 50%](image/tangojs-input-string.png)]
.center[![:scale 50%](image/tangojs-input-boolean.png)]
---
# Tangojs-polymer
.center[![:scale 50%](image/tangojs-plotly.png)]
---
# Tangojs-polymer
.pull-left[
<video style="width: 640px; height: 360px" autoplay loop>
    <source src="screencast/tangojs-chart-scalar.mov" type="video/mp4">
    Your browser does not support playing this Video
</video>
]
.pull-right[
<video style="width: 640px; height: 360px" autoplay loop>
    <source src="screencast/tangojs-chart-spectrum.mov" type="video/mp4">
    Your browser does not support playing this Video
</video>
]

.foot-note[The problem is always the css]
---
# MTango-py
## Tango REST API in python
To continue the journey we had a look on the back end. MTango is nice but we cannot contribute much.

.center[![:scale 50%](image/mtango-py.png)]


.foot-note[Made by Grzegorz Kowalski during an intership]

---
# MTango-py

## [github.com/MaxIV-KitsControls/mtango-py](https://github.com/MaxIV-KitsControls/mtango-py/tree/develop)

##Run with Sanic (Flask+Asyncio)

##Easy install with conda environment and docker


---
# Tango GraphQL

##Experimental web backend for TANGO

This is an attempt at using "modern" - perhaps too modern - web standards to make a TANGO web service. It provides websocket communication for subscribing to attributes, and an (incomplete) GraphQL interface to the TANGO database.

## Examples
````graphql

query{
	devices(pattern: "sys/tg_test/1"){
	   name,
	   attributes {
	     name,
	     datatype,
           }
        }
   }

```
.foot-note[Made by Mikel Eguiraun, Johan Forsberg]
---
# GraphQL in Live with Jiweb
.pull-left[
<video style="width: 640px; height: 360px" autoplay loop>
    <source src="screencast/graphql.mov" type="video/mp4">
    Your browser does not support playing this Video
</video>
]
.pull-right[
<video style="width: 640px; height: 360px" autoplay loop>
    <source src="screencast/jiweb.mov" type="video/mp4">
    Your browser does not support playing this Video
</video>
]

.foot-note[The problem is still the css]
.footnote[Credits Fredrick Bolsten, Hannes Petri, Mikel Eguiraun]
---
# One more thing
## Thinking of User Autonomy

.left[
<video style="width: 640px; height: 360px" autoplay loop>
    <source src="screencast/design.mov" type="video/mp4">
    Your browser does not support playing this Video
</video>
]
Largely inspired by Taurus ecosystem

.footnote[Credits Hannes Petri]
---
# Conclusion

## CSS is hard

## Need Websocket standard for Tango
## Interested by Tango/graphQL
## True web developer prefers React

## Web is still the future

