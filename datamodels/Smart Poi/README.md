## 1. Purpose: Data Model definition<br>
The definition of the data model for Smart POI into OMA NGSI data model from FIWARE
requires the following actions:

#### 1.1. Define “Smart Point of Interaction” data model: an interactive point in the city
which provides to citizens information, infotainment or co-creation points.

#### 1.2. Define “Smart Spot” data model: a set of resources related with the physical
device and the technology to provide a Smart Point of Interaction.

![alt text](https://drive.google.com/uc?id=0B5ZBzMDWQL6haGM0Nno1STJBeDg "Logo Title Text 1")

## 2.Define "Smart Point of Interaction" data model
Smart Spot Smart Spot Smart Spot
Device Device Device
DeviceModel DeviceModel DeviceModel
Define “Smart Point of Interaction” data model

| Field | Description |
|-------|-------------|
|"id" | Unique identifier|
|"type"| Entity type. It must be equal to “SmartPointOfInteraction”|
|"category"| Interaction type: “Information”, “Infotainment”, “Co-creation”, ...|
|"area"| Define the area covered by the Smart Point of Interaction using geoJSON format.|
|"availability"| Availability of the Smart functionality (ISO 8601 format).|
|"url"| Final URL announced by the smart spots. This is the real URL containing the solution/application.|
|"refLocationNGSIEntity”| Optional reference to an entity improved with this technology such as a “Parking”, “Point of Interest”, ..|
|"refSmartSpot"| Reference to the “Smart Spot” devices which are part of the Smart Point of Interaction.|


*_Example:_*
```json
{
"id": "SPOI-ES-4326",
"category": "SmartPointOfInteraction",
"type": "Infotainment",
"area": {                           
  "type": "Polygon",
  "coordinates": [[
    [100.0, 0.0], 
    [101.0, 0.0], 
    [101.0, 1.0], 
    [100.0, 1.0], 
    [100.0, 0.0] 
  ]]
},
"url": "www.siidi.eu",
"availability": [ "T09:00:00Z/T14:00:00Z", "T15:00:00Z/T19:00:00Z" ],
"refSmartSpot": [ "SSPOT-F94C58E29DD5", "SSPOT-F94C53E21DD2", "SSPOT-F94C51A295D9"]
}
```
*Tha *area* field is a example of geojson type

## 3.Define "Smart SPot" data model

| Field | Description |
|-------|-------------|
|id| Unique identifier|
|type| Entity type. It must be equal to "SmartSpot"|
|physicalURL| Physical URL broadcasted in "Eddystone URL" format.|
|signalStrengh| Signal strength to adjust the announcement range.|
|bluetoothChannel| Channels where to transmit the announcement.|
|area| Area radio covered by the spot in meters.|
|interval| Interval in milliseconds between announcements|
|availability| Availability of the service (physical web enabled) using ISO 8601 format.|
|refSmartPointOfInteraction| Reference to the Smart Point of Interaction of which it forms part.|
|refDevice| Reference to a "Device" entity, which is the representation of this same device for device management.|
```json

{
  "id": "SSPOT-F94C51A295D9",
  "type": "SmartSpot",
  "physicalUrl" : "https://hpoi.info/325531235437",
  "signalStrengh": "high",
  "bluetoothChannel": "37-38-39",
  "area": 30,
  "interval": 500,
  "availability": [ "T09:00:00Z/T14:00:00Z" , "T15:00:00Z/T19:00:00Z" ],  
  "refSmartPointOfInteraction": "SPOI-ES-4326",
  "refDevice": "HOP09aab934a8"
}

```
