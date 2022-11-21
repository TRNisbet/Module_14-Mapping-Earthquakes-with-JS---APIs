# Module 14 - Mapping

## Module Supplement

**NOTE:** In many parts of the module where they show you a code block, wait to copy and paste that code block into your files until you get to the step that refers to where to put it/how to use it. 

## 14.2.1 - Mapbox API Key

- Mapbox getting started link: https://www.mapbox.com/
- Once you have access to your API key, you will want to keep the key handy for section **14.2.4** where you will create a config.js file to paste your API key into.

## 14.2.4 - Create A Simple Map

- There is no .png in the url to remove
- You also need to remove the `zoomOffset` and `tileSize` attributes to match the expected solution code

## 14.3.4 - Merge Branch Into main Branch

- After merging and deleting the Simple_Leaflet_Map branch, when it says to open Terminal/GitBash - you need to be sure to navigate into the repository in order to `git checkout main`

- NOTE: Merge conflicts can occur, which would deter you from being able to properly merge one branch into another. The merging tool on GitHub would show you what conflicts occur and allow you to fix them through the UI or you can fix them from VSCode and commit any changes. If you run into a merge conflict, or simply want to see an example please be sure to ask your instructional staff during office hours for assistance.  

## 14.4.1 - Map A Single Point

- In `let map = L.map('mapid').setView([40.7, -94.5], 4);` you will not only change the Zoom from 4 to 14, but you also need to change the coordinates in `.setView()` to `[34.0522, -118.2437]` to change the center of the map to Los Angeles, California. 

### Skill Drill
- If you weren't able to get the correct map style, where it says to replace code - you are only replacing the first line of code of the TileLayer. So ultimately, your code should look like 
```js
// We create the tile layer that will be the background of our map.
let streets = L.tileLayer('https://api.mapbox.com/styles/v1/mapbox/dark-v10/tiles/{z}/{x}/{y}?access_token={accessToken}', {
    attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
    maxZoom: 18,
    accessToken: API_KEY
});
```

## 14.4.2 - Map Multiple Points

- You'll want to change your `map` variable back to the original coordinates and zoom level from when you created a simple map. `let map = L.map('mapid').setView([40.7, -94.5], 4);`
- If you still have the dark tile layer leftover from the skill drill, make sure to change the url in your tileLayer back to the streets url `'https://api.mapbox.com/styles/v1/mapbox/streets-v11/tiles/{z}/{x}/{y}?access_token={accessToken}'` in order to match the output photos from the module.
- **RESOURCE:** `.tolocalestring()` function documentation (https://www.w3schools.com/jsref/jsref_tolocalestring_number.asp)

### Skill Drill
- When the instructions say "a radius where the population number is decreased by 200,000", they mean to divide the population by 200,000 rather than 100,000 like was done in the module step above. 

## 14.4.3 - Map Lines

- If you copied over the logic.js code from what you changed in your skill drill, you will need to remove the lines of code where you created the `cityData` variable and the `cityData.forEach()` method. You will also need to change your tile layer back to the Streets tile. 
- Make sure to remove the link in your `index.html` for the `cities.js` from the previous activity since it will not be used. 

## 14.5.5 - Map GeoJSON LineStrings

1. For question #1, you can refer to the MapBox documentation - https://docs.mapbox.com/api/maps/styles/ 
    - The correct answer is correct on the module according to the documentation; however, you may notice if you've played around on MapBox's site and came across the sample Light style page (https://api.mapbox.com/styles/v1/mapbox/light-v11.html?title=true&access_token=pk.eyJ1IjoibWFwYm94IiwiYSI6ImNpejY4M29iazA2Z2gycXA4N2pmbDZmangifQ.-g_vE53SD2WrJ6tFX7QHmA#1.68/3.5/9.6) if you look in the URL there is in fact a v11 available that does work. So if you tested each solution (minus the typo mentioned below), `...light-v11...` would work as well in the URL. I would assume in this case that internally they have upgraded to v11 but have not chosen to update their api documentation to use that version yet.
    - There is also a typo at the end of the option with `light-v11` where the end of the string has an extra `<` that shouldn't be there. 

## 14.6.x

**NOTE:** As you go through each step, changing the name of your `logicStep#.js` file, make sure to change the reference name to that file in your `index.html` page

**NOTE:** The given images may look slightly different simply because you are calling an API, which means the data may have looked slightly different at the time of the screenshot for the module example. 

## 14.6.4 - Add Color and Popup for Each Earthquake

- In the `getColor()` function, although the solution is looking for what is given in the code snippet, and the code works - a better practice would be to turn those individual `if`'s into `else if`
```js
function getColor(magnitude) {
      if (magnitude > 5) {
        return "#ea2c2c";
      }
      else if (magnitude > 4) {
        return "#ea822c";
      }
      else if (magnitude > 3) {
        return "#ee9c00";
      }
      else if (magnitude > 2) {
        return "#eecc00";
      }
      else if (magnitude > 1) {
        return "#d4ee00";
      }
      else{return "#98ee00";}
    }
```



- - -

## Class Material Reviews

### Class 1
- Creating a Mapbox account and generating an API key was covered in Lesson **14.2.1**
- Creating and editing an HTML page and a CSS file was covered in Lesson **14.2.3**
- Adding the Leaflet CSS and JavaScript libraries links was covered in Lesson **14.2.3**
- Adding the API key to the `config.js` file was covered in Lesson **14.2.4**
- Creating a `logic.js` file was covered in Lesson **14.2.4**
- Adding a map object and tile layer was covered in Lesson **14.2.4**
- Creating a basic map was covered in Lesson **14.2.4**
- Creating a map with circle markers was covered in Lesson **14.4.2**

### Class 2
- Mapping GeoJSON data was covered in Lessons **14.5.1 through 14.5.6**
- Mapping earthquake data was covered in Lesson **14.6.1**
- Adding a style to the map was covered in Lesson **14.6.2**
- Adding color to the map was covered in Lesson **14.6.3**
- Adding an additional overlay was covered in Lesson **14.6.4**

- - -

## Challenge Instruction Supplement

### Deliverable 1

**NOTE:** I would recommend right clicking on the javascript files in VSCode and selecting `Format Document` - this will help you better see where code is aligned within other methods/functions.

**Step 1** 
- Create a second layer group variable specifically for the tectonic plates

**Step 2**
- Add a reference attribute to the overlays object for the tectonic plate layer group you created in step 1.

**Step 3**
- You will want to be sure to use the raw file source for `GeoJSON/PB2002_boundaries.json` from GitHub. (https://raw.githubusercontent.com/fraxen/tectonicplates/master/GeoJSON/PB2002_boundaries.json)

### Deliverable 2

**NOTE:** I would recommend utilizing VSCode's split screen in order to have your `challenge_logic.js` file open next to the `major_eq_starter_logic.js` file to reference where each step should be in your code.

**Step 1**
- This corresponds to the same place that Deliverable 1 Step 1 was in your tectonic_plate starter code that you are using for `challenge_logic.js`

**Step 2**
- This corresponds to the same place that Deliverable 1 Step 2 was in your tectonic_plate starter code that you are using for `challenge_logic.js`

**Steps 3-9**
- Copy lines 111-132 from `major_eq_starer_logic.js` and paste them into your `challenge_logic.js` file after the line `allEarthquakes.addTo(map);` and before the creation of the `legend` variable.

**Steps 4-6**
- Below where I say to "reuse" these functions, the solution expects you to just define the same functions used earlier in the code with the same name; however, I would just remember that best practice is to not reuse function names. In this case as well, the two functions that are not changed (styleInfo and getRadius) could just be called and do not need to be redefined. Because Step 5 asks you to change the logic used in the previous getColor function, better practice would be to name this function something different since it's performing different logic. [If you have questions about what is expected for Steps 4-6, please be sure to speak to your instructional staff during office hours]

**Step 4**
- Reuse the same `styleInfo()` function from the d3 call earlier in the file

**Step 5**
- Reuse the same `getColor()` function from the d3 call earlier in the file, but change it according to the directions

**Step 6**
- Reuse the same `getRadius()` function from the d3 call earlier in the file

**Step 7**
- This geoJson layer will look almost identical to the one used on line 92 of `tectonic_plate_starter_logic.js`, the difference being that you need to add this layer to the correct layer group

### Deliverable 3

*At this point, hopefully you have become familiar enough with your `challenge_logic.js` file enough to know where these steps should be inserted into.*

- You are adding a 3rd tile layer option. You can pick any from the resource linked in the module to add to your Streets and Satellite options.


