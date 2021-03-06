<img align="center" width="450" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/white_balance/luciferingamma.jpg?raw=true">  
  
Thanks for the inspiration and for this article to [PlanetPixelEmporium.](http://planetpixelemporium.com/tutorialpages/light.html)

## Reproducing Real World Light
Occasionally the question arises as to how to reproduce the "real" color of light sources in a rendered environment. I set out to research this subject, and found a lot of very contradictory information. Some approaches try to categorize light sources by their color temperature. Some then try to come up with some meaningful way of converting that color temperature to RGB values to use in programs like Lightwave or Cinema 4D. Ultimately these approaches all fail to take into account several realities that work against trying to come up with a unified approach to light coloring and rendering.

The human visual system is very good at "white balancing" what we look at. As long as the scene we are viewing contains a continuous spectrum of colors, we interpret the light as "white". In reality, the incandescent light we light our homes with is quite orange. Daylight is very blue. Fluorescent lights vary from sickly greens to reddish purples. And yet, we see all these lighting situations as more or less neutrally colored.

In the real world, light consists of all visible colors, not just red, green, and blue wavelengths. The RGB color system that we use in computer graphics arose out of a peculiarity of human perception - we have structures in our eyes called "cones" that respond to red, green, and blue light sources. A monochromatic yellow light excites both the red and green cones in our eyes, and we see it as yellow. Such a yellow light in the real world would not allow a red object to appear red, or a green object to appear green. But in computer graphics a yellow light has both a red and green component, and so allows objects with those colors to appear fully colored. This is a limitation of many computer graphic programs at the moment.

Film cameras cannot compensate for the varying shades of light in the way that our visual sense can. Thus, we have daylight film which has heavy orange filtering to tone down the blue quality of outdoor light. We have indoor film which has a boosted blue response to even out the amber lighting. For fluorescent situations, we can use a combination of film type and filters to color balance the scene we are photographing. If we were to pick a particular color of light, say daylight, and say that it is "white" and photograph everything, indoors and out, with a film stock that renders daylight as white, all of our indoor shots would be shades of orange and amber, and outdoor shots under blue sky would be intensely blue. This would be undesirable.

Thus too it is undesirable to pick a similar approach with our 3D rendering of light. We have to be relative - and choose a light color to be "white" in our scene, with other types of light sources being colored relative to that one. In this way we can produce our synthetic "photos" to produce a pleasing result in our final renders. Of course, to understand how different types of light sources relate to each other, it is important to understand how these light sources work. To do this we are going to look at 3 basic types of light source.

## Black Body Illuminants
The first group of light sources are the black body illuminants. These are materials that produce light when they are heated. The sun is a black body illuminant, as is a candle flame. The color of light of these types of sources can be characterized by their Kelvin temperature. Note that this temperature has nothing to do with how "hot" a light source is - just with the color of its light. A light source with a low Kelvin temperature is very red. One with a high Kelvin temperature is very blue. More accurately, when we see two light sources side by side in a scene, the higher Kelvin light appears more blue, and the lower Kelvin light appears more red. Its all relative.

Black body illuminants produce a fairly even, continuous spectrum of colors, and so are perceived as "white" by our visual sense. Therefore, in the absence of comparative light sources in our scene, these should be rendered with warm, nearly white lights.

Below is a chart of some common Kelvin Light Source temperatures coupled with their RGB Equivalents. These equivalents were arrived arbitrarily - I eyeballed them. There were a couple of converters I found online, each taking a different approach. One of them colored the sources by reference - you input a Kelvin temperature that you want to be "white" and the temperature to convert into an RGB value. Visually, however, the results were disappointing. They were scientifically correct, but failed to take into account the adaptability of the human visual sense. The other converter did even worse, ending up with greenish shades in the 4500K range that black body illuminants are incapable of creating. So, the alternative was to use my eye and judgment to arrive at these values.
  
<img align="center" width="550" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/white_balance/1.jpg?raw=true">  

#### Samples  

<img align="center" width="550" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/white_balance/2.jpg?raw=true">  

## Fluorescent Lights
These light sources produce light by creating a large amount of UV light via high voltage electrical discharge through a tube filled with rare gasses. The UV light excites materials coating the tube to produce light through fluorescence. These lights have broad but sometimes disjointed spectra. Depending on the quality of the tube and its intended purpose, the color can vary in ways that cannot be described by black body illumination. In fact, the disjointed nature of fluorescent spectra begin to exceed the ability to characterize these colors accurately in RGB. These values and samples are again based on my personal observations of different source types.

<img align="center" width="550" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/white_balance/3.jpg?raw=true">  

#### Samples  

<img align="center" width="550" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/white_balance/4.jpg?raw=true"> 

## Gaseous Light Sources
This final type of light source usually involves a metallic gas under pressure being excited by a high voltage coil. They do not produce a continuous spectrum at all, but instead produce a series of monochromatic lines of light energy. This confounds our ability to accurately reproduce the full effect of how these lights look and interact with colors in a scene. For example, a standard mercury vapor lamp, such as found in older city street lights and parking lots, produces only a few lines of monochromatic light - a yellow, a green, a blue, and a purple. To the casual eye, the light looks somewhat "whitish" but in fact, red objects in such light lose their color and appear black - there is no red component to the light at all. But in RGB, you cannot produce a "purple-green" color without using red. Thus, red objects will still appear red under such a simulated light. Until the day that 3D programs such as Cinema 4D allow you to define light sources by their spectral output instead by RGB value, there isn't much we can do about it.

Again, the values in the following chart were eyeballed by myself, by looking at various night lights around my city.

<img align="center" width="550" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/white_balance/5.jpg?raw=true">  

#### Samples  

<img align="center" width="550" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/white_balance/6.jpg?raw=true">

## Gamma correction
The effect of gamma correction on an image: The original image was taken to varying powers, showing that powers larger than 1 make the shadows darker, while powers smaller than 1 make dark regions lighter.  

<img align="center" width="330" src="https://github.com/sblantipodi/firefly_luciferin/blob/master/data/img/white_balance/gamma.jpg?raw=true">  

You can find some basics on Gamma Correction [here.](https://en.wikipedia.org/wiki/Gamma_correction)

## Conclusion
Remember, the values in the charts in this article are merely a starting point for your own explorations and experiments. Particularly with the black body illuminants, the color of lighting is all relative, so remember to adjust your values accordingly. 