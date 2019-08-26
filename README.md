# Soil Moisture Sensor Data

## Introduction 
Soil Moisture Sensor Data Collection Challenge. Continuously collect soil moisture samples every 5 seconds and display them using the lights on the micro:bit. 

## Step 1
``||basic: Continuously||`` ``||basic: show a number||``. 

```blocks
basic.forever(function () {
    basic.showNumber(0)
})
```

## Step 2
What ``||gatorSoil: number||`` do we want to be showing? What pin controls the power and what pin controls the data?

```blocks
basic.forever(function () {
    basic.showNumber(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1))
})
```

## Step 3
Since the ``||gatorSoil: soil moisture||`` ranges from 0 to 1, we want to map it to something that is easier to understand, 1 to 10. 
```blocks
basic.forever(function () {
    basic.showNumber(Math.map(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1), 0, 1, 1, 10))
})
```

## Step 4
We do not want a long list after the decimal point, so we ``||math: round||`` the ``||gatorSoil: soil moisture||`` to the closest whole number.

```blocks
basic.forever(function () {
    basic.showNumber(Math.round(Math.map(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1), 0, 1, 1, 10)))
})
```

## Step 5
We need to ``||basic: take a break||`` for 5 seconds in between each measurement.

```blocks
basic.forever(function () {
    basic.showNumber(Math.round(Math.map(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1), 0, 1, 1, 10)))
    basic.pause(5000)
})
```

## Step 6
``|Download|`` it and test it out. Once you have it working, click NEXT to move on to the next challenge

## Step 7
Now you will use the ``||radio: radio||`` to transfer data collected using the micro:bit to the chromebook. The radio channel is labeled on your receiver micro:bit box. Set the data collecting micro:bit to the same group as the data receiving micro:bit.

Make sure you have the micro:bit on the right group.
```blocks
radio.setGroup(21)
```

## Step 8 
Now instead of showing the ``||gatorSoil: soil moisture||`` value on the micro:bit, ``||radio:send||`` over the radio instead.
```blocks
radio.setGroup(14)
basic.forever(function () {
    radio.sendNumber(Math.round(Math.map(gatorSoil.moisture(AnalogPin.P2, GatorSoilType.Moisture, DigitalPin.P1), 0, 1, 1, 10)))
    basic.pause(5000)
})
```

## Step 9
``|Download|`` the code and test it out. 

```package
gatorSoil=github:sparkfun/pxt-gator-soil
```

