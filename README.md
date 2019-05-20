<h1 align="center">Google Places AutoComplete</h1>

May 19, 2019

Places SDK for Android - The autocomplete service in the Places SDK for Android returns place predictions in response to user search queries. As the user types, the autocomplete service returns suggestions for places such as businesses, addresses and points of interest.

PLACES_API_ACCESS_NOT_CONFIGURED -> solved


## Music to develop software [Spotify]

[Classics Soul Romantic by Eddy Escalante](https://open.spotify.com/user/12149682954/playlist/7qLC3tIjc1bWMhw5KeD2qN?si=rRzz_v2aR1KL9pivUYzQTw "Classics Soul Romantic by Eddy Escalante")

[Classic Soul Train by Eddy Escalante](https://open.spotify.com/user/12149682954/playlist/0730LTmBtBKgGBujChg3HS?si=0mhWtG-yRqe6gPbmEbdglw "Classic Soul Train by Eddy Escalante")

[Classics by Eddy Escalante](https://open.spotify.com/user/12149682954/playlist/6EjzxBbnBMr8NEenhuznPK?si=dOENe9hSTSaXAdEFFjb3Aw "Classics by Eddy Escalante")

## How to integrate into your app?
1. Place Autocomplete  [Place Autocomplete](https://developers.google.com/places/android-sdk/autocomplete)
2. Migración al nuevo cliente SDK de Places [Migración al nuevo cliente SDK de Places](https://developers.google.com/places/android-sdk/client-migration)
3. Presentamos nuevos y mejorados Places SDKs [Presentamos nuevos y mejorados Places SDKs](https://medium.com/@flutterhackserices/introducing-new-improved-places-sdks-1b60f876a2b)

#### Integrating the project is simple all you need to do is follow the below steps

### Step 1. Add the dependency

```java
dependencies {
    implementation 'com.google.android.libraries.places:places:1.1.0'
    implementation 'com.google.android.gms:play-services-maps:16.1.0'
    implementation 'com.google.android.gms:play-services-location:16.0.0'
}
```

### Step 2. Add permission

```xml
.....
    <!--
         The ACCESS_COARSE/FINE_LOCATION permissions are not required to use
         Google Maps Android API v2, but you must specify either coarse or fine
         location permissions for the 'MyLocation' functionality. 
    -->
    
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION"/>
    <uses-permission android:name="android.permission.INTERNET"/>
.....
```

### Step 3. Add Key

```xml
.....
<meta-data
            android:name="com.google.android.geo.API_KEY"
            android:value="YOUR-KEY" />
.....
```         

### Step 4. Code JAVA
```java
        String apiKey = getString(R.string.places_api_key);

        if (!Places.isInitialized()) {
            Places.initialize(getApplicationContext(), apiKey);
            PlacesClient placesClient = Places.createClient(this);
        }else{
            Toast.makeText(MainActivity.this, "-----initialize-----", Toast.LENGTH_LONG).show();
        }

        // Initialize the AutocompleteSupportFragment.
        AutocompleteSupportFragment autocompleteFragment = (AutocompleteSupportFragment)
                getSupportFragmentManager().findFragmentById(R.id.autocomplete_fragment);

        // PlaceFields
        autocompleteFragment.setPlaceFields(Arrays.asList(Place.Field.ID, Place.Field.NAME, Place.Field.LAT_LNG));

        try {
            autocompleteFragment.setOnPlaceSelectedListener(new PlaceSelectionListener() {
                @Override
                public void onPlaceSelected(@NonNull Place place) {
                    displayLocation(place.getLatLng().latitude,place.getLatLng().longitude,place.getName());
                    Toast.makeText(getApplicationContext(), "getName: " + place.getName() + " getLatLng: "+ place.getLatLng(), Toast.LENGTH_LONG).show();
                }

                @Override
                public void onError(@NonNull Status status) {
                    Toast.makeText(getApplicationContext(), "" + status.toString(), Toast.LENGTH_LONG).show();
                }
            });
        } catch (Exception e) {
            Toast.makeText(MainActivity.this, e.toString(), Toast.LENGTH_LONG).show();
        }
```   

## Youtube
[Google Place Autocomplete || PLACES_API_ACCESS_NOT_CONFIGURED](https://www.youtube.com/watch?v=0IWQ0xhrf7U&feature=youtu.be "by Eddy Escalante Ustariz")

[![Google Place Autocomplete || PLACES_API_ACCESS_NOT_CONFIGURED](https://img.youtube.com/vi/0IWQ0xhrf7U/0.jpg)](https://youtu.be/0IWQ0xhrf7U)

## Author
Maintained by [Eddy Escalante Ustariz](https://www.github.com/EddyEU)
 
 ## Contribution
[![GitHub contributors](https://img.shields.io/github/contributors/EddyEU/GooglePlaceAutocomplete.svg)](https://github.com/EddyEU/GooglePlaceAutocomplete/graphs/contributors)

* Bug reports and pull requests are welcome.            
          

## License
```
MIT License

Copyright (c) 2019 Eddy Escalante Ustariz

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```     
          
          
          
  

