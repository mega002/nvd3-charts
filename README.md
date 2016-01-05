# nvd3-charts
Custom responsive charts for nvd3 (gauge, bubble, radar).

## Gauge chart
Simple gauge, wants a single value as data. Use a CSS width of 190px to keep it together (not responsive).

![](https://raw.githubusercontent.com/enplore/nvd3-charts/master/gauge.png)

```
nv.addGraph(function() {
    var chart = nv.models.gaugeChart()
        .title('Gauge')
        .min(0)
        .max(1);

    d3.select('#gauge-chart-1 svg')
        .datum([Math.random()])
        .call(chart);

    nv.utils.windowResize(chart.update);
    return chart;
});
```

## Packed bubble chart
Based on http://bl.ocks.org/mbostock/4063269. Accepts the same data structure. Responsive. Will reveal child node when clicked.

```
nv.addGraph(function() {
    var chart = nv.models.packedBubbleChart()
        .title('Bubbles')
        .valueFormat(function(d) { return d.index.toFixed(2); })
        .color(d3.scale.linear()
              .domain([0, 0.25, 0.5])
              .range(['#88ac67', "#f78f20", "#db4e4e"]));

    d3.select('#bubble-chart svg')
        .datum(bubbleData))
        .call(chart);

    nv.utils.windowResize(chart.update);
    return chart;
});
```

## Radar chart
Based on http://bl.ocks.org/nbremer/6506614. Accepts the same data structure. Nodes are linked if the data point's "link" property is set.

```
nv.addGraph(function() {
    var chart = nv.models.radarChart()
        .valueFormat(function (d) { return d.toFixed(2); })
        .min(min)
        .max(max)
        .margin({ top: 10 })
        .color(d3.scale.linear()
            .range(['#88ac67', "#f78f20", "#db4e4e"]));

    d3.select('#radar-chart svg')
        .datum(radarData)
        .call(chart);

    nv.utils.windowResize(chart.update);
    return chart;
});
```