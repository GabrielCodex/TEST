# Creating a pin on location and zooming in on the map

### Step 1 

Apple "A CLLocation object represents the location data generated by a CLLocationManager object. This object incorporates the geographical coordinates and altitude of the device’s location along with values indicating the accuracy of the measurements and when those measurements were made."

So validLocation is the location data that comes from the CLLocationManager object(we called it location manager in this example) 

Line 21 zooms in on the location and we can set the coordiante


```swift
 func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
        print("Oh woah, locations updated")
        //    dump(locations)
        
        guard let validLocation: CLLocation = locations.last else { return }
        
       
        // this line zooms in on the actual location of the user 
        mapView.setRegion(MKCoordinateRegionMakeWithDistance(validLocation.coordinate, 500.0, 500.0), animated: true)
       
       // creates the pin 
       let pinAnnotation: MKPointAnnotation = MKPointAnnotation()
        pinAnnotation.title = "Hey, Title"
        pinAnnotation.subtitle = "Bring the rain"
        pinAnnotation.coordinate = validLocation.coordinate
        mapView.addAnnotation(pinAnnotation)
       
    }

```


