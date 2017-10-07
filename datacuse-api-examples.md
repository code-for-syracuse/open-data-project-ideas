# Overview

The City of Syracuse's open data portal uses GeoServices to provide access to city data. GeoServices are RESTful services that can be queried using a SQL-like syntax. More information on using [GeoServices](http://geoservices.github.io/) here.

# Examples

## Query the city's parcel data set for specific feastures of a property:

```bash
~$ curl -s "https://services6.arcgis.com/bdPqSfflsdgFRVVM/arcgis/rest/services/parcel_data_august_2017/FeatureServer/0/query?where=StNum%3D%27127%27+AND+FullAdd+LIKE+%27%25hancock%25%27&outFields=Nhood,LandUse,YearBuilt&f=pjson"
```

Response:

```json
{
  "objectIdFieldName": "OBJECTID_1",
  "globalIdFieldName": "",
  "geometryProperties": {
    "shapeAreaFieldName": "Shape__Area",
    "shapeLengthFieldName": "Shape__Length",
    "units": "esriFeet"
  },
  "geometryType": "esriGeometryPolygon",
  "spatialReference": {
    "wkid": 102716,
    "latestWkid": 2261
  },
  "fields": [
    {
      "name": "Nhood",
      "type": "esriFieldTypeString",
      "alias": "Nhood",
      "sqlType": "sqlTypeOther",
      "length": 254,
      "domain": null,
      "defaultValue": null
    },
    {
      "name": "LandUse",
      "type": "esriFieldTypeString",
      "alias": "LandUse",
      "sqlType": "sqlTypeOther",
      "length": 254,
      "domain": null,
      "defaultValue": null
    },
    {
      "name": "YearBuilt",
      "type": "esriFieldTypeString",
      "alias": "YearBuilt",
      "sqlType": "sqlTypeOther",
      "length": 254,
      "domain": null,
      "defaultValue": null
    }
  ],
  "features": [
    {
      "attributes": {
        "Nhood": "Strathmore",
        "LandUse": "Single Family",
        "YearBuilt": "1955"
      },
      "geometry": {
        "rings": [
          [
            [
              928598.206898917,
              1102421.597689
            ],
            [
              928441.872894,
              1102341.63393817
            ],
            [
              928414.586531252,
              1102395.07149534
            ],
            [
              928573.197106417,
              1102476.199942
            ],
            [
              928598.206898917,
              1102421.597689
            ]
          ]
        ]
      }
    }
  ]
}
```

## Look up the trash pickup day for a property

```bash
~$ curl -s "https://services6.arcgis.com/bdPqSfflsdgFRVVM/arcgis/rest/services/Trash_Pickup_Day/FeatureServer/0/query?where=number%3D%27127%27+AND+address+LIKE+%27%25hancock+dr%25%27&outFields=number%2Caddress%2CTrash_Pickup_Day&f=pjson"
```

Response:

```json
{
  "objectIdFieldName": "FID",
  "globalIdFieldName": "",
  "geometryType": "esriGeometryPoint",
  "spatialReference": {
    "wkid": 102100,
    "latestWkid": 3857
  },
  "fields": [
    {
      "name": "number",
      "type": "esriFieldTypeString",
      "alias": "number",
      "sqlType": "sqlTypeNVarchar",
      "length": 256,
      "domain": null,
      "defaultValue": null
    },
    {
      "name": "address",
      "type": "esriFieldTypeString",
      "alias": "address",
      "sqlType": "sqlTypeNVarchar",
      "length": 256,
      "domain": null,
      "defaultValue": null
    },
    {
      "name": "Trash_Pickup_Day",
      "type": "esriFieldTypeString",
      "alias": "Trash_Pickup_Day",
      "sqlType": "sqlTypeNVarchar",
      "length": 256,
      "domain": null,
      "defaultValue": null
    }
  ],
  "features": [
    {
      "attributes": {
        "number": "127",
        "address": "Hancock Dr",
        "Trash_Pickup_Day": "Thursday"
      },
      "geometry": {
        "x": -8480216.2996,
        "y": 5315819.977399997
      }
    }
  ]
}
```
