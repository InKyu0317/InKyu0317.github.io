---
layout: page
title: HERE SDK note
---

### SDK & API products

* Javascript API
* REST API
* Mobile SDK <Starter, Premium> (Android, iOS), Premium version provides vector based map
* Automotive

### Android SDK system requirement

* Minimum API: Android 4.1 (API level 16)
* RAM: 60MB
* SDK library space: 25MB
* Map Data space: 50MB
* Internet Connection
* 256MB cached memory
* Android SDK documentation [link](https://developer.here.com/documentation/android-premium/topics/introduction.html)
* SDK & API pdf downloads [link](https://developer.here.com/documentation/versions)
* Github Example code [link](https://github.com/heremaps/here-android-sdk-examples)

### Main features
  
* Maps (Multiple Layers)
* Positioning (Driver's position)
* Directions (Finds multiple routes from starting position to destination)
* Turn by turn navigations

### Map
  
* MVC pattern: MapFragment (View) + Controller (implemented by developer) + Map (Model)
* MapFragment: Gesture (Finger), Map Scheme(Explore, Overlays, Navigation mode)
* MapEngine: creates a Map instance for MapFragment
* MapInstance: it can be used for applying more options to Map
* Offline maps (always need to check the updates) in persistent cached data storage
  * Headless Fetch
    * use Bounding Box/Route object to pre fetch data before use navigation. It stores data to Cached Memory (256MB) 
    * if the cached memory is not enough, it download while the navigation updates driver's position (it will remove old data)    
  * MapLoader
    * MapEngine makes MapLoader object and using Listener to get fetching opertion result
    * MapPackage is element of MapData, they are classified according to Regions

### Positioning
  
* Basic
  * GPS, GPS_NETWORK, WI-FI
* Advanced
  * Cellular, LTE, CDMA, WCDMA, GSM
  * Offline, Turnnel (MapMatching, RadioPositioning) with WI-FI or Bluetooth
  * Satellite-based (GNSS)

### Directions (car & pedestrian)
  
* Route calculation classes
  * CoreRouter: calculate route
  * RoutePlan: waypoint container
  * Route Waypoint: starting point to destination
  * Route Options: # of route suggestion, direction, 
  route type (fastest, shortest ..), departure time
* RouteResult & Route Class
  * RouteResult: route calculation result
  * RouteClass ViolatedOption 
  (User added avoid toll option, if the route has to pass at least one toll, there will be a violated option)
* MapRoute & Map object 
  * MapRoute display the route on the map, Map object are view object on Map
* Dynamic Routing Penalty
  * create a policy of roads and area restriction factors that are applied during routing calculations
* Traffic Updater
  * Traffic Information live updater
* Offline Routing
  * MapLoader & MapPackages
* Route Consumption
  * calvulate gas(Energy) consumption
* Route Serialization
  * converts to binary

### Turn by turn navigation

* Navigation Manager Class 
  * simulate, navigation, tracking mode
  * Background navigation: no map data stream, using map loader
  * Headless Navigation: using map engine
  * Natural Guidance: voice instruction (Multilingual)
  * NavigationManager Listener: monitoring navigation status
* Manuver Class
  * provides information from one segment to the next (current road -> next road) 
* Rerouting (Basic, dynamic(skip), manual(skip))
  * Basic recalculation: it checks if the driver goes further from destination
* Lane information
  * before the exit or turn left/right, it helps the driver to change lane (if road has more than 3 lanes)
* Traffic Aware Navigation mode
  * based on current traffic situation, it change the route
* Realistic views