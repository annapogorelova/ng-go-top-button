# ng-go-top-button
A simple customizable go-top button component for Angular projects.

## Versions

This is the new version of the original [ng2-go-top-button](https://www.npmjs.com/package/ng2-go-top-button). This version was re-created according to the new Angular library format to support Angular v9 and higher. For previous Angular versions refer to the original version.

## Installation
```
npm install ng-go-top-button --save
```

## Usage
Import statement in the app module:
```typescript
import {GoTopButtonModule} from 'ng-go-top-button';
import {BrowserAnimationsModule} from '@angular/platform-browser/animations';

...

@NgModule({
    ...
    imports: [..., GoTopButtonModule, BrowserAnimationsModule],
    ...
```

In the target app component:
```typescript
import { Component, ViewEncapsulation } from '@angular/core';

@Component({
  ...
  encapsulation: ViewEncapsulation.None // for animations and custom styling to work
})
export class AppComponent {
...
}
```

On your template paste the `<ng-go-top-button></ng-go-top-button>` html. This will add a simple button with default styles and without animated scroll. By default go-top-button will appear on the right side, 50% top and bottom and without any icons or text. You can then customize its styles and behaviour.

Example of customization:
```angular2html
<ng-go-top-button 
                 [animate]="true"
                 [speed]="50"
                 [acceleration]="2"
                 [scrollDistance]="300"
                 [classNames]="'custom-class'"
                 [styles]="{
                    'border-radius': '20px 20px 20px 20px',
                    'right': '5px',
                    'color': 'green',
                    'border': '5px solid',
                    'line-height': '20px'
                 }">
        <i class=\'fa fa-arrow-up\'></i>
  </ng-go-top-button>
```
Custom CSS class declaration (if needed):
```css
.custom-class {
    position: fixed;
    background-color: pink;
    border-color: green;
    height: 30px;
    width: 30px;
}
```

## API
| Property | Type | Description |
| ------ | ------ | ------ |
| scrollDistance | *number* | Number of pixels to be scrolled Y for button to be shown. Defaults to 200px. Must be greater than zero. |
| styles | *object* | User-defined styles config for the button. |
| classNames | *string* | Custom class names in the following format 'class1 class2 class3'. *Note*: this attribute completely overrides the default '.go-top-button' class attributes, so one should specify all style properties manually.|
| animate | *boolean* | If true, scrolling will be animated. False by default. |
| speed | *number* | Speed of animated scroll. Must be greater than 1. 80 by default. |
| acceleration  | *number* | Number of pixels to speed up when scrolling is animated. 0 by default - this way page will be scrolled top with the constant speed. |
| tabIndex  | *number*  |   Custom tabindex button attribute value, by default 0.


## IE-specific issues:

IE does not support web animations. If you would like to enable them, install and import the corresponding polyfill to your polyfills.js file:

In your project's directory:
```
npm install --save web-animations-js
```

In polyfills.js:
```
import 'web-animations-js';
```

## Example project

You can find example project that uses `ng-go-top-button` in `projects/example-app/` directory of this repository. To run the example project execute the following commands from the root directory of the project:

```
ng build --project=example-app
cd projects/example-app
ng serve
```
