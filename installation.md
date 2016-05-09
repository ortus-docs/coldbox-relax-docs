# Installation

Just drop into your **modules** folder or use CommandBox to install

`box install relax`

## System Requirements
- Lucee 4.5+
- Railo 4+
- ColdFusion 9+

## Settings
You will need to update the your `ColdBox.cfc` with a `relax` structure with your preferred settings for Relax.  
 
```
relax = {
    // The location of the relaxed APIs, defaults to models.resources
    APILocation = "models.resources",
    // Default API to load, name of the directory inside of resources
    defaultAPI = "myapi",
    // History stack size, the number of history items to track in the RelaxURL
    maxHistory = 10
};
```

## Modeling
You can look at the samples inside of this module under the `models/resources` directory.  To start you can copy the `Relax.cfc` into your own project folder and then start spicing up the API via the RelaxDSL methods.
