ion-google-autocomplete
================
[![GitHub version](https://badge.fury.io/gh/Hobbule%2Fion-google-autocomplete.svg)](https://badge.fury.io/gh/Hobbule%2Fion-google-autocomplete)
[![Bower version](https://badge.fury.io/bo/ion-google-autocomplete.svg)](https://badge.fury.io/bo/ion-google-autocomplete.svg)

This is a simple directive for Ionic 1 that allows you to add an input text element that enables user to select a place from Google Places with its details in a convenient Ionic Modal

# Changes in this fork

 Add attribute directives:
  - closeButtonIconClass: the icon to use for the close button
  - placeHolderText: self explainatory
  - containerClassName: prefix all the css classes you want to change by the name set in this attribute. Use !important if needed.
    - Example: to change the bar-header height, set containerClassName to address-input (for instance) and use the css rule:
  
  ```
     .address-input.bar-header { height: 80px!important; }
  ```
Change:  
  - Replace button text by an icon

To install run
```
 bower install https://github.com/powowbox/ion-google-autocomplete.git --save
```
# Demo
<img src="https://s3.amazonaws.com/ionic-marketplace/ion-google-autocomplete/screenshot_4.gif" />

See the codepen here: http://codepen.io/sebrojas14/pen/QERQyj

# Installation
You can use bower:
`bower i ion-google-autocomplete`

# Usage
1. Include the library and Google Places in your index.html (remember to replace your_api_key by your Google API Key:
    ```html
    <script src="lib/ion-google-autocomplete/dist/ion-google-autocomplete.js"></script>
    <script src="http://maps.googleapis.com/maps/api/js?key=your_api_key&libraries=places"></script>
```
2. Add the `ion-google-autocomplete` module to your app module dependencies
3. In your controller initialize data and options
    ```javascript
    $scope.data = {};
    
    //Optional
    $scope.countryCode = 'US';
    
    //Optional
    $scope.onAddressSelection = function (location) {
    
        //Do something
        var a = location.address_components;
    };
    ```
4. Add the google-autocomplete-suggestion attribute to your text input field
    ```html
    <input type="text" placeholder="Change address" google-autocomplete-suggestion location="data.location" country-code="{{countryCode}}" on-selection="onAddressSelection(location)" ng-model="data.location.formatted_address" readonly required>
    ```

## Configurable options

### The `location`
Required
A object property where place details returned by Google are stored. For example, you can use `$scope.data.location.geometry.location.lat()` to get latitude of the selected place

### The `country-code`
Optional
Use as componentRestrictions, see https://developers.google.com/places/web-service/autocomplete
"components — A grouping of places to which you would like to restrict your results. Currently, you can use components to filter by country. The country must be passed as a two character, ISO 3166-1 Alpha-2 compatible country code. For example: components=country:fr would restrict your results to places within France."

### The `on-selection`
Optional
This option receives a function called when a place is selected using the modal. Receives a paramter location with the places details returned by Google.
```javascript
$scope.onAddressSelection = function (location) {

    //Do something
    var a = location.address_components;
};
```

## Release Notes

v1.0.0
- Now is using Ionic Modal service and can be used inside another Ionic Modal
