# demo
# Features of drone
R C Controlled : 

1. Throttle
2. Pitch 
3. Yaw
4. Altitude hold
5. Hover
6. Geographical fence

<br>

> **1. Throttle**

<br>

Throttle is just a upward (or downward) movment of quadcopter which can be achived by increasing (or decreasing) all the propeller speeds by the same amount. It leads to a vertical force with respect to body-fixed frame which raises or lowers the quad-rotor.
```
 arm_and_takeoff(aTargetAltitude): #Arms vehicle and fly to aTargetAltitude.
    # Don't let the user try to arm until autopilot is ready
 print("Basic pre-arm checks")
 while not vehicle.is_armable:
  print(" Waiting for vehicle to initialise...")
  time.sleep(1)
 print("Arming motors")
    # Copter should arm in GUIDED mode
 vehicle.mode = VehicleMode("GUIDED")
 vehicle.armed = True
 
 while not vehicle.armed:      
   print(" Waiting for arming...")
   time.sleep(1)

 print("Taking off!")
   vehicle.simple_takeoff(aTargetAltitude) # Take off to target altitude

 while True:
   print(" Altitude: ", vehicle.location.global_relative_frame.alt)      
      if vehicle.location.global_relative_frame.alt>=aTargetAltitude*0.95: #Trigger just below target alt.
         print("Reached target altitude")
         break
   time.sleep(1)

```

<br>

<img src="https://cfdflowengineering.com/wp-content/uploads/2020/09/Drone_cove-page.png" height="250">

<br>

> **2. Pitch**

<br>

The second dimension an aircraft can move in is called “pitch.” The pitch means the drone tilts upwards or downwards based on its orientation and the location of its nose. A downwards tilt will move the aircraft (drone in this case) in a forwards motion, while an upwards tilt will move it backwards.


```
while(1):
 expt=get_expected_location_meter()
 covert_to_degree( get_from_gyroscope() )
 current=get_current()
 error=check_error(expt,current)
 if( get_distance(expt,current) <= 0 )
       break
 altitude_hold()
  
```

<br>

![pitch](https://images.squarespace-cdn.com/content/v1/5b1566faf407b4c2d4edc8e2/1528337221637-4YYWEN30OKV2OSGBIB4H/Pitch.png?format=750w)

<br>

> **3. Yaw**

<br>

“yaw” refers to the direction the front of your drone (or even a plane or car) is facing when rotating either clockwise or counterclockwise (or left and right if you prefer) on its vertical axis.


```
while(1):
 expt=get_expected_location() 
 current=get_from_magnetometer()
 error=check_error(expt,current)
 if(error==0):
    break
 rotate( get_fact_PID_controller(error) )

```

<br>

![yaw](https://images.squarespace-cdn.com/content/v1/5b1566faf407b4c2d4edc8e2/1528337146183-2JHYTR3POC14B5FQGWUT/image-asset.png?format=750w)

<br>

> **4. Altitude hold**

<br>

 the throttle is automatically controlled to maintain the current altitude.
 
 <br>
 
 > **5. Hover**

<br>

two of a drone's four rotors move clockwise, while the other two move counterclockwise, ensuring that the sideways momentum of the drone remains balanced.

<img src="https://hobbyhenry.com/wp-content/uploads/2020/03/Drone-Wont-Stay-Still.jpg?ezimgfmt=ng%3Awebp%2Fngcb1%2Frs%3Adevice%2Frscb1-1" height="250">

<br>

 > **6. Geographical fence**

<br>

This is the use of GPS to create a virtual boundary that triggers a predetermined response when the drone flies into — or out of — a particular area. If the drone flies towards a “fenced” or restricted area, it will stop mid-flight. If you try to take off from a restricted area, the drone will not start up at all. Geofences can be placed to keep drones out of certain fields, from flying over a particular building, and prevent them from entering into “no fly zones.”

<br>

<img src="https://dronebelow.com/wp-content/uploads/2018/06/3DR-geofencing.jpeg" height="250">

<br>
