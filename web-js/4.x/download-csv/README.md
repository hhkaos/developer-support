## Download Client Side CSV
I have seen a lot of questions about how to save data from an ArcGIS JavaScript application. There are a few ways built in, such as applyEdits and using a Geoprocessing service. Both of those options are server side operations, so I thought adding a client side option may help some people. In this sample the user can add points to a map. When they click the download button, the points along with queried feature layer attributes are downloaded as a CSV.

[Live Demo](https://esri.github.io/developer-support/web-js/4.x/download-csv/index.html)