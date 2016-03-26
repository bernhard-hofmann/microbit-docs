#uBit.accelerometer

##Overview

Onboard the micro:bit is an accelerometer. The accelerometer is linked to the
[i2c](ubit/i2c.md) bus, which is used to read data from the accelerometer.

When using the standard uBit presentation, the accelerometer is continuously updated
in the background using an idle thread, which is executed whenever the micro:bit
has no other tasks to perform..

If there is no scheduler running, the values are synchronously read on `get[X,Y,Z]()`
calls. Additionally, if you would like to drive accelerometer updates manually `updateSample()`
can be used.

The micro:bit uses the [NXP MMA8653 accelerometer](http://www.nxp.com/products/sensors/accelerometers/3-axis-accelerometers/2g-4g-8g-low-g-10-bit-digital-accelerometer:MMA8653FC).

##Message Bus ID

| Constant | Value |
| ------------- |-------------|
| MICROBIT_ID_ACCELEROMETER | 4 |

##Message Bus Events

| Constant | Value |
| ------------- |-------------|
| MICROBIT_ACCELEROMETER_EVT_TILT_UP | 1 |
| MICROBIT_ACCELEROMETER_EVT_TILT_DOWN | 2 |
| MICROBIT_ACCELEROMETER_EVT_TILT_LEFT | 3 |
| MICROBIT_ACCELEROMETER_EVT_TILT_RIGHT | 4 |
| MICROBIT_ACCELEROMETER_EVT_FACE_UP | 5 |
| MICROBIT_ACCELEROMETER_EVT_FACE_DOWN | 6 |
| MICROBIT_ACCELEROMETER_EVT_FREEFALL | 7 |
| MICROBIT_ACCELEROMETER_EVT_3G | 8 |
| MICROBIT_ACCELEROMETER_EVT_6G | 9 |
| MICROBIT_ACCELEROMETER_EVT_8G | 10 |
| MICROBIT_ACCELEROMETER_EVT_SHAKE | 11 |

##API
[comment]: <> ({"className":"MicroBitAccelerometer"})
##Constructor
<br/>
####MicroBitAccelerometer( <div style='color:#008080; display:inline-block'>uint16_t</div> id,  <div style='color:#008080; display:inline-block'>uint16_t</div> address)
#####Description
Constructor. Create an accelerometer representation with the given ID.
#####Parameters

>  <div style='color:#008080; display:inline-block'>uint16_t</div> *id* - the ID of the new object.

>  <div style='color:#008080; display:inline-block'>uint16_t</div> *address* - the default base address of the accelerometer.
#####Example
```c++
 accelerometer(MICROBIT_ID_ACCELEROMETER, MMA8653_DEFAULT_ADDR)

```
##configure
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> configure()
#####Description
Configures the accelerometer for G range and sample rate defined in this object. The nearest values are chosen to those defined that are supported by the hardware. The instance variables are then updated to reflect reality.
#####Returns
MICROBIT_OK on success, MICROBIT_I2C_ERROR if the accelerometer could not be configured.
##update
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> update()
#####Description
Reads the acceleration data from the accelerometer, and stores it in our buffer. This is called by the tick() member function, if the interrupt is set.
#####Returns
MICROBIT_OK on success, MICROBIT_I2C_ERROR is the read request fails.
##setPeriod
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> setPeriod( <div style='color:#008080; display:inline-block'>int</div> period)
#####Description
Attempts to set the sample rate of the accelerometer to the specified value (in ms). n.b. the requested rate may not be possible on the hardware. In this case, the nearest lower rate is chosen.
#####Parameters

>  <div style='color:#008080; display:inline-block'>int</div> *period* - the requested time between samples, in milliseconds.
#####Returns
MICROBIT_OK on success, MICROBIT_I2C_ERROR is the request fails.
##getPeriod
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> getPeriod()
#####Description
Reads the currently configured sample rate of the accelerometer.
#####Returns
The time between samples, in milliseconds.
##setRange
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> setRange( <div style='color:#008080; display:inline-block'>int</div> range)
#####Description
Attempts to set the sample range of the accelerometer to the specified value (in g). n.b. the requested range may not be possible on the hardware. In this case, the nearest lower rate is chosen.
#####Parameters

>  <div style='color:#008080; display:inline-block'>int</div> *range* - The requested sample range of samples, in g.
#####Returns
MICROBIT_OK on success, MICROBIT_I2C_ERROR is the request fails.
##getRange
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> getRange()
#####Description
Reads the currently configured sample range of the accelerometer.
#####Returns
The sample range, in g.
##whoAmI
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> whoAmI()
#####Description
Attempts to determine the 8 bit ID from the accelerometer.
#####Returns
the 8 bit ID returned by the accelerometer, or MICROBIT_I2C_ERROR if the request fails.
#####Example
```c++
 uBit.accelerometer.whoAmI();

```
##getX
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> getX()
#####Description
Reads the X axis value of the latest update from the accelerometer.
#####Returns
The force measured in the X axis, in milli-g.
#####Example
```c++
 uBit.accelerometer.getX();

```
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> getX( <div style='color:#008080; display:inline-block'>MicroBitCoordinateSystem</div> system)
#####Description
Reads the X axis value of the latest update from the accelerometer.
#####Parameters

>  <div style='color:#008080; display:inline-block'>MicroBitCoordinateSystem</div> *system* - The coordinate system to use. By default, a simple cartesian system is provided.
#####Returns
The force measured in the X axis, in milli-g.
#####Example
```c++
 uBit.accelerometer.getX();

```
##getY
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> getY()
#####Description
Reads the Y axis value of the latest update from the accelerometer.
#####Returns
The force measured in the Y axis, in milli-g.
#####Example
```c++
 uBit.accelerometer.getY();

```
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> getY( <div style='color:#008080; display:inline-block'>MicroBitCoordinateSystem</div> system)
#####Description
Reads the Y axis value of the latest update from the accelerometer.
#####Parameters

>  <div style='color:#008080; display:inline-block'>MicroBitCoordinateSystem</div> *system* - The coordinate system to use. By default, a simple cartesian system is provided.
#####Returns
The force measured in the Y axis, in milli-g.
#####Example
```c++
 uBit.accelerometer.getY();

```
##getZ
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> getZ()
#####Description
Reads the Z axis value of the latest update from the accelerometer.
#####Returns
The force measured in the Z axis, in milli-g.
#####Example
```c++
 uBit.accelerometer.getZ();

```
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> getZ( <div style='color:#008080; display:inline-block'>MicroBitCoordinateSystem</div> system)
#####Description
Reads the Z axis value of the latest update from the accelerometer.
#####Parameters

>  <div style='color:#008080; display:inline-block'>MicroBitCoordinateSystem</div> *system* - The coordinate system to use. By default, a simple cartesian system is provided.
#####Returns
The force measured in the Z axis, in milli-g.
#####Example
```c++
 uBit.accelerometer.getZ();

```
##getPitch
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> getPitch()
#####Description
Provides a rotation compensated pitch of the device, based on the latest update from the accelerometer.
#####Returns
The pitch of the device, in degrees.
#####Example
```c++
 uBit.accelerometer.getPitch();

```
##getPitchRadians
<br/>
####<div style='color:#FF69B4; display:inline-block'>float</div> getPitchRadians()
##getRoll
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> getRoll()
#####Description
Provides a rotation compensated roll of the device, based on the latest update from the accelerometer.
#####Returns
The roll of the device, in degrees.
#####Example
```c++
 uBit.accelerometer.getRoll();

```
##getRollRadians
<br/>
####<div style='color:#FF69B4; display:inline-block'>float</div> getRollRadians()
##getGesture
<br/>
####<div style='color:#FF69B4; display:inline-block'>BasicGesture</div> getGesture()
#####Description
Reads the last recorded gesture detected.
#####Returns
The last gesture detected.
#####Example
```c++
 if (uBit.accelerometer.getGesture() == SHAKE)

```
##isIdleCallbackNeeded
<br/>
####<div style='color:#FF69B4; display:inline-block'>int</div> isIdleCallbackNeeded()
#####Description
Returns 0 or 1. 1 indicates data is waiting to be read, zero means data is not ready to be read.
##~MicroBitAccelerometer
<br/>
####~MicroBitAccelerometer()
#####Description
Destructor for  MicroBitButton
____
[comment]: <> ({"end":"MicroBitAccelerometer"})