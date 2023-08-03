<!---
// SPDX-License-Identifier: CC-BY-4.0
// Copyright Contributors to the SMTPE RIS OSVP Metadata Project
-->

# Camera and Lens Metadata Parameters for VFX

DRAFT - April 7, 2003

This initial set of parameters should be considered a work in progress and are being published here for community use and feedback. Work is underway on a similar set of parameters for use in in-camera VFX (ICVFX), which more directly addresses the goals of the RIS OSVP project. The initial set of parameters are those that the group deemed most essential to VFX work, with clear and well-understood methods for using them. The focus was on those parameters that impact the images as captured by the camera sensor or the original primary captured output of the camera. The parameters are listed in 5 tables:

* [Camera parameters with a defined format in CAMDKIT](#camera-parameters-with-a-defined-format-in-camdkit)<br>
* [Lens parameters with a defined format in CAMDKIT](#lens-parameters-with-a-defined-format-in-camdkit)<br>
* [Parameters without a defined format](#parameters-without-a-defined-format)<br>
* [Parameters requiring further study including use cases](#parameters-requiring-further-study-including-use-cases)<br>
* [Image characteristics already present in essence formats](#image-characteristics-already-present-in-essence-formats)<br>

A backlog of parameters needing additional work is included in the tables below.

## Camera parameters with a defined format in CAMDKIT

These parameters were determined to be important for use in traditional post-VFX and having sufficiently clear definitions and practices to include in the CAMDKIT JSON format. Most are available in the captured outputs of cameras. When available from a camera manufacturer's tools, CAMDKIT ingests and normalizes them to the listed format. In addition CAMDKIT outputs the duration of the clip so that the sampling rate can be computed from the number of samples.

|Parameter|Need<br>vs. Like<br>to Have|Static vs.<br>Dynamic|Description|Units|Constraints|
|---------|------|------|--------------------------|-----|--------|
|Active Sensor Physical Dimensions|Need|Static|Height and width of the active area of the camera sensor|micron|The height and width shall be each be an integer in the range [0..2,147,483,647].|
|Camera Firmware Version|Need|Static|Version identifier for the firmware of the camera|n/a|Unicode string betwee 0 and 1023 codepoints.|
|Camera Make|Need|Static|Make of the camera|n/a|Unicode string betwee 0 and 1023 codepoints.|
|Camera Model|Need|Static|Model of the camera|n/a|Unicode string betwee 0 and 1023 codepoints.|
|Camera Serial Number|Need|Static|Unique identifier of the camera|n/a|Unicode string betwee 0 and 1023 codepoints. Uniqueness is scoped to the camera make and camera model.|
|Capture Rate|Need|Static|Capture frame frate of the camera|hertz|Rational number whose numerator and denominator are in the range (0..2,147,483,647].|
|FDL Link|Need|Static|Unique identifier of the FDL used by the camera|n/a|UUID URN as specified in IETF RFC 4122. Only lowercase characters shall be used. Example: urn:uuid:f81d4fae-7dec-11d0-a765-00a0c91e6bf6|
|ISO Speed|Need|Static|Arithmetic ISO scale as defined in ISO 12232|unit|Integer in the range (0..2,147,483,647].|
|Shutter Angle|Need|Static|Shutter speed as a fraction of the capture frame rate|**0.01** degrees (angular)|Integer in the range (0..360000].|


## Lens parameters with a defined format in CAMDKIT

These lens parameters were determined to be important for use in traditional post-VFX and having sufficiently clear definitions and practices to include in the CAMDKIT JSON format. Most are available in the captured outputs of cameras ands lenses. When available from a manufacturer's tools, CAMDKIT ingests and normalizes them to the listed format.

|Parameter|Need<br>vs. Like<br>to Have|Static vs.<br>Dynamic|Description|Units|Constraints|
|--------|-------------|--------------------------|--------------|---------------|-----|
|Anamorphic Squeeze|Need|Static|Nominal ratio of height to width of the image of an axis-aligned square captured by the camera sensor|0.01 unit|Integer in the range (0..2,147,483,647].|
|Entrance Pupil Position|Need|Dynamic|Entrance pupil position of the lens|millimeter|Rational number whose numerator and denominator are in the range (0..2,147,483,647].|
|F Stop|Need|Dynamic|The linear f-number of the lens, equal to the focal length divided by the diameter of the entrance pupil|0.001 unit|Integer in the range (0..2,147,483,647].|
|Nominal Focal Length|Need|Dynamic|Nominal focal length of the lens|millimeter|Integer in the range (0..2,147,483,647].|
|Focus Position|Need|Dynamic|Focus distance/position of the lens|millimeter|Integer in the range (0..2,147,483,647].|
|Lens Firmware Version|Need|Static|Version identifier for the firmware of the lens|n/a|Unicode string betwee 0 and 1023 codepoints.|
|Lens Make|Need|Static|Make of the lens|n/a|Unicode string betwee 0 and 1023 codepoints.|
|Lens Model|Need|Static|Model of the lens|n/a|Unicode string betwee 0 and 1023 codepoints.|
|Lens Serial Number|Need|Static|Unique identifier of the lens|n/a|Unicode string betwee 0 and 1023 codepoints. Uniqueness is scoped to the lens make and lens model.|
|T Stop|Need|Dynamic|The linear t-number of the lens, equal to the F-number of the lens divided by the square root of the transmittance of the lens|0.001 unit|Integer in the range (0..2,147,483,647].|

## Parameters without a defined format

These parameters were deemed important but with varying meanings or mechanisms for extracting them. They are not implemented in CAMDKIT.

|Parameter|Need<br>vs. Like<br>to Have|Static vs.<br>Dynamic|Notes|
|--------|-------------|-------------|--------------|
|Distortion Characteristics|Like|Dynamic|Usually computed by forumla or by software based on other parameters|
|Exposure Falloff Characteristics|Like|Dynamic|Based on iris position|
|Tint Value|Like|Static||

## Parameters requiring further study including use cases
These parameters were deemed potentially useful, but more clarity is needed on their definitions or the use cases for them.

|Parameter|Need<br>vs. Like<br>to Have|Static vs.<br>Dynamic|Notes|
|--------|-------------|-------------|--------------|
|Active Sensor Dimensions in Photosites|TBD|Static|Useful to estimate Moire in ICVFX. Need post-VFX use case.|
|Capture Color Space|TBD|Static|Log, Lin, ACES, 709, 2020, etc.|
|Circle of Confusion|TBD||Used to compute depth of field based on entrance pupil position, iris position, focus, and focal length.  Multiple definitions, e.g., optical vs. VFX (pixel depth-based). Need clear definition.|
|Depth of Field|TBD|Dynamic|Near and far plane distance. Essential or derived from other parameters?|
|Debayered Output Resolution|TBD|Static|Not always known at capture time. Present in image characteristics?|
|Monitoring Encoding Curve|TBD|Static|Need use case|
|Pinhole Focal Length|TBD|Dynamic|Need use case. Derivable from other data?|
|LUT|TBD|Static|Which LUTs matter?|
|CDL Data|TBD||Need use case.|
|White Balance|TBD|Static|Usually expressed as color temperature. Different curves. Effect on image varies by maker.|


## Image characteristics already present in essence formats

These are metadata items that may be needed that are commonly present in essence formats (images or video) and are therefore not covered in this work.

|Parameter|Notes|
|-------------|--------------|
|Image Frame Dimensions|Height and width of image in pixels|
|Colorimetry|Mapping of component signals to red, green and blue tristimulus values|
|Quantization|Quantization of component signals, including the bit depth|
|Sampling|Spatial sampling/sub-sampling of components|

<sub>Licensed under a Creative Commons Attribution 4.0 license<br></sub>

