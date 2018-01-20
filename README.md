# Ti.WFS
Client for  Web Feature Service (Open Geospatial) for Axway Titanium

With this module you can use WFS services.

### Usage

```
var Wfs = require("ti.wfs");
Wfs.setEndpoint("https://geodienste.hamburg.de/HH_WFS_Strassenbaumkataster");
Wfs.setVersion("2.0.0");
Wfs.requestFeature({
   region : region,
   typeNames : "app:Strassenbaumnkataster"
},onload: function(e){
  console.log(e.data)
});
```

