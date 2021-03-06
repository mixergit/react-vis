# LineSeries/LineMarkSeries

<!-- INJECT:"LineChart" -->

react-vis offers two different types of LineSeries, one that renders SVG and one that renders Canvas.
The SVG mode is accessed by using the normal `LineSeries`, just as above, while the Canvas mode is used by simply calling `LineSeriesCanvas` instead of `LineSeries`.

<!-- INJECT:"LineChartCanvas" -->
-**NOTE**: using the Canvas version of this layer disables animation

## Data format reference

#### x
Type: `number`  
Left-to-right position of marks in the series.

#### y
Type: `number`  
Top-to-bottom position of the top edge of the series.

## API Reference

#### color (optional)
Type: `string|number`  
Default: see [colors](colors.md)
Color of the line series. 
By default, you can pass a literal color to the series (i.e. "red" or "#f70"). You can also define a color scale at the top level, and pass a number which will be interpolated by the scale. If nothing is provided, lineSeries will be colored according to react-vis default scale.

#### curve (optional)
Type: `string|function`
Default: `null`
Apply the provided or named curve function from the D3 shape library to smooth the line series plot, see [the D3 documentation](https://github.com/d3/d3-shape#curves) for function names and instructions. Providing the function, not the name, will require importing the d3-shape package in order to configure it:

```javascript
// Setting up with only a name
const stringCurveProp = <LineSeries data={data} curve={'curveMonotoneX'} .../>;

const configuredCurve = d3Shape.curveCatmullRom.alpha(0.5);
const funcCurveProp = <LineSeries data={data} curve={configuredCurve} .../>;
```

#### data
Type: `Array<Object>`  
Array of data for the series. See above data format reference.

#### opacity (optional)
Type: `number`  
Default: 1  
Opacity of the area chart from 0 (transparent) to 1 (opaque).

#### stroke (optional)
Type: `string|number`  
Default: see [colors](colors.md)  
A color for the series. Will override color if both are provided.

##### strokeDasharray (optional)
Type: `string`
Specify a custom `stroke-dasharray` attribute which controls the pattern of dashes and gaps used to stroke paths.

##### strokeStyle (optional)
Type: `string`
If set to `dashed`, your series will use dashed lines. If set to `solid` or unspecified, your series will use solid lines. See `strokeDasharray` for specifying a custom stroke dash-array value.

##### strokeWidth (optional)
Type: `string|number`
Specifies the width of the line for the series. By default, this is determined by react-vis css (2px).

#### style (optional)
Type: `object`
An object which holds CSS properties that will be applied to the SVG element(s) rendered by the series. This allows you to style series beyond the other explicitly defined properties and without having to use CSS classnames and stylesheets. See [style](style.md)

```jsx
<LineSeries
  data={data}
  style={{strokeLinejoin: "round"}}
/>
```

### Interaction handlers

#### onNearestX (optional)
Type: `function(value, {event, innerX, index})`  
A callback function which is triggered each time the mouse pointer moves. It can access the datapoint of the mark whose x position is the closest to that of the cursor. 
Callback is triggered with two arguments. `value` is the data point, `info` object has following properties:
- `innerX` is the left position of the mark;
- `index` is the index of the data point in the array of data;
- `event` is the event object.
See [interaction](interaction.md)

#### onNearestXY (optional)
Type: `function(value, {event, innerX, innerY, index})`  
A callback function which is triggered each time the mouse pointer moves. It can access the datapoint of the mark whose position is the closest to that of the cursor. 
Callback is triggered with two arguments. `value` is the data point, `info` object has following properties:
- `innerX` is the left position of the mark;
- `innerY` is the top position of the mark;
- `index` is the index of the data point in the array of data;
- `event` is the event object.
See [interaction](interaction.md)

#### onSeriesClick
Type: `function`  
Default: none  
This handler fires when the user clicks somewhere on a LineSeries, and provides the corresponding event. See [interaction](interaction.nd)

```jsx
<LineSeries
...
  onSeriesClick={(event)=>{
  	// does something on click
  	// you can access the value of the event
  }}
```

#### onSeriesMouseOut
Type: `function`  
Default: none  
This handler fires when the user's mouse cursor leaves a LineSeries, and provides the corresponding event. See [interaction](interaction.nd)

```jsx
LineSeries
...
  onSeriesMouseOut={(event)=>{
  	// does something on mouse over
  	// you can access the value of the event
  }}
```

#### onSeriesMouseOver
Type: `function`
Default: none  
This handler fires when the user mouses over a LineSeries, and provides the corresponding event. See [interaction](interaction.nd)

```jsx
<LineSeries
...
  onSeriesMouseOver={(event)=>{
  	// does something on mouse over
  	// you can access the value of the event
  }}
```
