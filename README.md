# PhotonDialog

### Overview

This library contains an Android DialogFragment for search-as-you-type via the photon geocoding API.
(see https://github.com/komoot/photon and https://photon.komoot.io/)
You can type an address and get the coordinates back.

### Installation

Add the JitPack repository to your root build.gradle at the end of repositories:

```gradle
allprojects {
  repositories {
    ...
    maven { url 'https://jitpack.io' }
  }
}
```

Add the library dependency to your build.gradle file.

```gradle
dependencies {
    implementation 'com.github.woheller69:PhotonDialog:V1.0'
}
```

### Usage

Let your activity implement PhotonDialog.PhotonDialogResult

```
        public class MainActivity extends AppCompatActivity implements PhotonDialog.PhotonDialogResult

```

and override onPhotonDialogResult, where you define what to do with the result 

```
    @Override
    public void onPhotonDialogResult(City city) {

    String cityName = city.getCityName();
    String countryCode = city.getCountryCode();
    float lon = city.getLongitude();
    float lat = city.getLatitude();
    
    // do what you need to do
    
    }
```

Open a search dialog:

```
        FragmentManager fragmentManager = getSupportFragmentManager();
        PhotonDialog photonDialog = new PhotonDialog();
        photonDialog.setTitle("Search");
        photonDialog.setNegativeButtonText("Cancel");
        photonDialog.setPositiveButtonText("Select");
        
        //Optional: Define countries. Otherwise locations in all countries are shown
        ArrayList<String> countryList = new ArrayList<>();
        countryList.add("DE");
        countryList.add("AT");
        photonDialog.setCountryList(countryList);
        
        photonDialog.show(fragmentManager, "");
        getSupportFragmentManager().executePendingTransactions();
        photonDialog.getDialog().getWindow().setSoftInputMode(WindowManager.LayoutParams.SOFT_INPUT_STATE_ALWAYS_VISIBLE);

```

### License

This library is licensed under the GPLv3.

The library uses:
- Leaflet which is licensed under the very permissive <a href='https://github.com/Leaflet/Leaflet/blob/master/FAQ.md'>2-clause BSD License</a>
- Map data from OpenStreetMap, licensed under the Open Data Commons Open Database License (ODbL) by the OpenStreetMap Foundation (OSMF) (https://www.openstreetmap.org/copyright)
- Search-as-you-type location search is provided by [photon API](https://photon.komoot.io), based on OpenStreetMap. See also (https://github.com/komoot/photon)
- Android Volley (com.android.volley) (https://github.com/google/volley) which is licensed under <a href='https://github.com/google/volley/blob/master/LICENSE'>Apache License Version 2.0</a>
- AndroidX libraries (https://github.com/androidx/androidx) which is licensed under <a href='https://github.com/androidx/androidx/blob/androidx-main/LICENSE.txt'>Apache License Version 2.0</a>
- AutoSuggestTextViewAPICall (https://github.com/Truiton/AutoSuggestTextViewAPICall) which is licensed under <a href='https://github.com/Truiton/AutoSuggestTextViewAPICall/blob/master/LICENSE'>Apache License Version 2.0</a>

