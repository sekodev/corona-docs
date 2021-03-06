
# event.zRotation

> --------------------- ------------------------------------------------------------------------------------------
> __Type__              [Number][api.type.Number]
> __Event__             [gyroscope][api.event.gyroscope]
> __Revision__          [REVISION_LABEL](REVISION_URL)
> __Keywords__          gyroscope, zRotation
> __See also__			[event.xRotation][api.event.gyroscope.xRotation]
>						[event.yRotation][api.event.gyroscope.yRotation]
>						[event.deltaTime][api.event.gyroscope.deltaTime]
> --------------------- ------------------------------------------------------------------------------------------

## Overview

The rotation rate around the device's <nobr>__z__-axis</nobr> in radians per second.

## Gotchas

You can convert radians to degrees via the following formula:

<div class="code-indent">

_degrees = radians * (180 / pi)_

</div>

## Example
 
``````lua
-- Called when a new gyroscope measurement has been received
local function onGyroscopeDataReceived( event )
    -- Calculate approximate rotation traveled via delta time
    -- Remember that rotation rate is in radians per second
    local deltaRadians = event.zRotation * event.deltaTime
    local deltaDegrees = deltaRadians * (180/math.pi)
end
 
-- Set up the above function to receive gyroscope events if the sensor exists
if system.hasEventSource( "gyroscope" ) then
    Runtime:addEventListener( "gyroscope", onGyroscopeDataReceived )
end
``````
