# PhotonDialog

### Overview

This library contains an Android DialogFragment for search-as-you-type via the photon geocoding API.
(see https://github.com/komoot/photon and https://photon.komoot.io/)
You can type an address and get the coordinates back.

This project is forked from Truiton / AutoSuggestTextViewAPICall (https://github.com/Truiton/AutoSuggestTextViewAPICall) which is licensed under Apache License 2.0

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
    implementation 'com.github.woheller69:PhotonDialog:-SNAPSHOT'
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
        photonDialog.show(fragmentManager, "");
        getSupportFragmentManager().executePendingTransactions();
        photonDialog.getDialog().getWindow().setSoftInputMode(WindowManager.LayoutParams.SOFT_INPUT_STATE_ALWAYS_VISIBLE);

```


