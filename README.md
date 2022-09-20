# Design & Prototype

From the first week of sketching and defining the concept, the next is to design hi-fidelity design visualization interface for one of the concepts I came up last week. Due to the time limitation, [concept #1](https://github.com/Chayanitoey/MajorStudio1/tree/main/Quant%20Project/Concept%201) would be the best option to execute and leaning more on different JS libraries i.e. [three.js](https://threejs.org) and [webGL](https://webglfundamentals.org/webgl/lessons/webgl-fundamentals.html#toc) in which I aim to explore. 

## Inspiration 

The theme is the emotion in between pessimism and optimism in a hyper-surrealism state -with the information about the global waste percentage, the audience may feel hopeless or discouraging after the facts unveiled, in order to lift up the mood, light shapes and form appear to show that there is still hope. 

Here is the mood board : 
![image](https://github.com/Chayanitoey/MajorStudio1/blob/7fa2c9900c5133f003fe953203b1afda23c59cec/Assets/Mood%20&%20Tone%20board.png)


## Style guide 
- **Color** : There are 4 main colors and each represents different meanings- however, they all match in the space of wireframes. ![image](https://github.com/Chayanitoey/MajorStudio1/blob/7fa2c9900c5133f003fe953203b1afda23c59cec/Assets/Colors.png)

- **Typography** : Two font  families will be used for this project 'Libre Franklin' and 'Lato'- both can be accessible using font cdn ![image](https://github.com/Chayanitoey/MajorStudio1/blob/7fa2c9900c5133f003fe953203b1afda23c59cec/Assets/Typography.png)

## Wireframing 

Designed on Figma, screen size 1920 * 1080, horizontal screen. First step before designing the UI, I started with outlining components & interactions i.e. what the landing page looks like, how does animation would play in different scenarios, etc. 

Here is an example of what that process looks likes :  
![image](https://github.com/Chayanitoey/MajorStudio1/blob/43cd1c30b7adb9c8c77a15c1b79dcec2487ff150/Assets/Figma%20BrainStorm.jpg)

- **Hi-fidelity design** : 2 frames ( landing page and clicking state frame)

![image](https://github.com/Chayanitoey/MajorStudio1/blob/7fa2c9900c5133f003fe953203b1afda23c59cec/Assets/Overview.png)

![image](https://github.com/Chayanitoey/MajorStudio1/blob/7fa2c9900c5133f003fe953203b1afda23c59cec/Assets/Country%20Focus.png)

## Prototyping 

At this stage - about 40% of the microsite is completed, however, polishing tasks will still take a big portion of the process. Here is the 
[link](https://chayanitoey.github.io/MajorStudio1/) to the prototype 

## Debugging 

For this week, I'll work on the data label (hovering) which is based on globe.gl framework and will move on to country card which relies on another data set(showing different categories of waste generated in details) 


## Globe.gl snippet

```javascript

//using d3 library for the colors 

                        const weightColor = d3.scaleSequentialSqrt()
                          .interpolator(d3.interpolateLab("purple","orange")) 
                          .domain([1, 10])
                          .range([0,300]);
                       
//get dom id and set up function from globe.GL
                        const world = Globe()
                          (document.getElementById('globeViz'))
                          .globeImageUrl('//unpkg.com/three-globe/example/img/earth-dark.jpg')
                          .bumpImageUrl('//unpkg.com/three-globe/example/img/earth-topology.png')
                          .backgroundImageUrl('https://media1.giphy.com/headers/anthonyantonellis/SqsFmi8lZMtI.gif')
                          .hexBinPointWeight('Total')
                          // .hexAltitude(d => d.sumWeight * 6e-8)
                          .hexBinPointLat( 'lat')
                          .hexBinPointLng( 'lng')
                          .hexAltitude(d => d.sumWeight * 6e-4)
                          .hexBinResolution(4)
                          .hexTopColor(d => weightColor(d.sumWeight))
                          .hexSideColor(d => weightColor(d.sumWeight))
                          .hexBinMerge(false)

//hex label is still under debugging, will need to return d.GeoAreaName
                          .hexLabel(d => `
                           <div style ="font-size:400%;font-family:'Lato', sans-serif">
                         Country : 
                            </div>
                          ` 
                          )

```

## Link to data and related repositories : 
- [Major Studio 1 by Richard The](https://github.com/visualizedata/major-studio-1)
- [Last Week Progress](https://github.com/Chayanitoey/MajorStudio1/tree/main/Quant%20Project)
- [Data sets](https://github.com/Chayanitoey/MajorStudio1/tree/Design%26Prototype/Data)


