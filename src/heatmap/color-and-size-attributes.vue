<template>
<main><div>
<div class="control-section">
    <div class="content-wrapper">
        <ejs-heatmap id='container' :tooltipSettings='tooltipSettings' :titleSettings='titleSettings' :xAxis='xAxis' :yAxis='yAxis' :dataSource='dataSource' :dataSourceSettings='dataSourceSettings' :cellSettings='cellSettings' :legendSettings='legendSettings' :paletteSettings='paletteSettings' :load='load' :tooltipRender='tooltipRender'></ejs-heatmap>
    </div>
    <div style="float: right; margin-right: 10px;">Source:
        <a href="https://en.wikipedia.org" target='_blank'>https://en.wikipedia.org/</a>
    </div>
</div>
</div>
<section id="action-description" aria-label="Description of HeatMap sample">
    <p>
        This sample illustrates the number of commercial air craft accidents and the fatalities across the world between 2012 and 2017. Each data point interprets the accident count and the fatality associated with the accident, the size of the bubble depicts the accident count and the shade of the bubble depicts the fatality count.
    </p>
</section>
<section id="description" aria-label="Description of the HeatMap features demonstrated in this sample">
    <p>
        In this example, you can see how to map more than one data for each data point or cell of the bubble heatmap. The <code>size</code> and <code>shade</code> parameters of the bubble is used to depict the data source values. The legend will be displayed only for the shade parameter of the bubble. For JSON data, you can specify which data source value should be mapped to either size or shade of the bubble parameters using the <a target='_blank' href="https://ej2.syncfusion.com/vue/documentation/api/heatmap/dataModel/#bubbledatamapping">bubbleDataMapping</a> property. The data source field should be mapped to the <a target='_blank' href="https://ej2.syncfusion.com/vue/documentation/api/heatmap/bubbleDataModel/#size">size</a> and <a target='_blank' href="https://ej2.syncfusion.com/javascript/documentation/api/heatmap/bubbleDataModel/#color">color</a> properties of the <code>bubbleDataMapping</code> property.
    </p>
    <p>The tooltip is enabled in this example. To see the tooltip in action, hover the mouse over an item or tap an item on touch-enabled devices.</p>
    <br>
    <p><b>Injecting Module</b></p>
    <p>
      Heatmap component features are separated into discrete feature-based modules. To use a tooltip, legend and data adaptor, inject the <a target="_blank"
      href="https://ej2.syncfusion.com/vue/documentation/heatmap-chart/tooltip">Tooltip</a>, <a target="_blank" href="https://ej2.syncfusion.com/vue/documentation/heatmap-chart/legend">Legend</a> and 
      <a href="https://ej2.syncfusion.com/vue/documentation/api/heatmap/adaptorType/" target='_blank'>Adaptor</a> modules using the <code>provide:{ heatmap:[Tooltip, Legend, Adaptor] }</code> method.
    </p>
</section>
</main>
</template>
<script>
import { HeatMapComponent, Tooltip, Legend, Adaptor } from "@syncfusion/ej2-vue-heatmap";

export default {
components: {
    'ejs-heatmap': HeatMapComponent
},
data:function(){
return{
        titleSettings: {
            text: 'Commercial Aviation Accidents and Fatalities by year 2012 - 2017',
            textStyle: {
                size: '15px',
                fontWeight: '500',
                fontStyle: 'Normal',
                fontFamily:'inherit'
            }
        },
         xAxis: {
            labels: ['2017', '2016', '2015', '2014', '2013', '2012'],
            textStyle: {
                fontFamily: 'inherit'
            }
        },
        yAxis: {
            labels:  ['Jan-Feb', 'Mar-Apr', 'May-Jun', 'Jul-Aug', 'Sep-Oct', 'Nov-Dec'],
            textStyle: {
                fontFamily: 'inherit'
            }
        },
        dataSource: [
            { Year: '2017', Months: 'Jan-Feb', Accidents: 4, Fatalities: 39 },
            { Year: '2017', Months: 'Mar-Apr', Accidents: 3, Fatalities: 8 },
            { Year: '2017', Months: 'May-Jun', Accidents: 1, Fatalities: 3 },
            { Year: '2017', Months: 'Jul-Aug', Accidents: 1, Fatalities: 0 },
            { Year: '2017', Months: 'Sep-Oct', Accidents: 4, Fatalities: 4 },
            { Year: '2017', Months: 'Nov-Dec', Accidents: 2, Fatalities: 15 },
            { Year: '2016', Months: 'Jan-Feb', Accidents: 4, Fatalities: 28 },
            { Year: '2016', Months: 'Mar-Apr', Accidents: 5, Fatalities: 92 },
            { Year: '2016', Months: 'May-Jun', Accidents: 5, Fatalities: 73 },
            { Year: '2016', Months: 'Jul-Aug', Accidents: 3, Fatalities: 1 },
            { Year: '2016', Months: 'Sep-Oct', Accidents: 3, Fatalities: 4 },
            { Year: '2016', Months: 'Nov-Dec', Accidents: 4, Fatalities: 126 },
            { Year: '2015', Months: 'Jan-Feb', Accidents: 1, Fatalities: 45 },
            { Year: '2015', Months: 'Mar-Apr', Accidents: 5, Fatalities: 152 },
            { Year: '2015', Months: 'May-Jun', Accidents: 0, Fatalities: 0 },
            { Year: '2015', Months: 'Jul-Aug', Accidents: 4, Fatalities: 54 },
            { Year: '2015', Months: 'Sep-Oct', Accidents: 5, Fatalities: 243 },
            { Year: '2015', Months: 'Nov-Dec', Accidents: 2, Fatalities: 45 },
            { Year: '2014', Months: 'Jan-Feb', Accidents: 2, Fatalities: 18 },
            { Year: '2014', Months: 'Mar-Apr', Accidents: 3, Fatalities: 239 },
            { Year: '2014', Months: 'May-Jun', Accidents: 0, Fatalities: 0 },
            { Year: '2014', Months: 'Jul-Aug', Accidents: 4, Fatalities: 501 },
            { Year: '2014', Months: 'Sep-Oct', Accidents: 1, Fatalities: 2 },
            { Year: '2014', Months: 'Nov-Dec', Accidents: 4, Fatalities: 162 },
            { Year: '2013', Months: 'Jan-Feb', Accidents: 2, Fatalities: 68 },
            { Year: '2013', Months: 'Mar-Apr', Accidents: 3, Fatalities: 7 },
            { Year: '2013', Months: 'May-Jun', Accidents: 2, Fatalities: 12 },
            { Year: '2013', Months: 'Jul-Aug', Accidents: 4, Fatalities: 15 },
            { Year: '2013', Months: 'Sep-Oct', Accidents: 2, Fatalities: 64 },
            { Year: '2013', Months: 'Nov-Dec', Accidents: 3, Fatalities: 83 },
            { Year: '2012', Months: 'Jan-Feb', Accidents: 0, Fatalities: 0 },
            { Year: '2012', Months: 'Mar-Apr', Accidents: 2, Fatalities: 158 },
            { Year: '2012', Months: 'May-Jun', Accidents: 5, Fatalities: 90 },
            { Year: '2012', Months: 'Jul-Aug', Accidents: 0, Fatalities: 0 },
            { Year: '2012', Months: 'Sep-Oct', Accidents: 3, Fatalities: 33 },
            { Year: '2012', Months: 'Nov-Dec', Accidents: 4, Fatalities: 42 }
        ],
        dataSourceSettings:  {
            isJsonData: true,
            adaptorType: 'Cell',
            xDataMapping: 'Year',
            yDataMapping: 'Months',
            bubbleDataMapping: { size: 'Accidents', color: 'Fatalities' }
        },
        cellSettings: {
           border: {
                width: 0
            },
            showLabel: false,
            tileType: 'Bubble',
            bubbleType: 'SizeAndColor',
            textStyle: {
                fontFamily: 'inherit'
            }
        },
        paletteSettings: {
            palette: [{ color: '#C06C84' },
            { color: '#355C7D' }
            ],
            type: 'Gradient'
        },
        legendSettings: {
            visible: true,
            textStyle: {
                fontFamily: 'inherit'
            }
        },
        tooltipSettings:{
            textStyle: {
                fontFamily: 'inherit'
            }
        },
        height:'200px'
}
},
provide:{
    heatmap:[Tooltip, Legend, Adaptor]
},
methods: {
    load: function(args) {
    /* custom code start */
      let selectedTheme = location.hash.split("/")[1];
      selectedTheme = selectedTheme ? selectedTheme : "Material";
      args.heatmap.theme =
        (selectedTheme.charAt(0).toUpperCase() + selectedTheme.slice(1)).replace(/-dark/i, "Dark").replace(/-high/i, 'High').replace(/contrast/i, 'Contrast').replace(/5.3/i, '5');
    /* custom code end */
    },
    tooltipRender:function(args)
    {
        args.content = ['Year ' + ' : ' + args.xLabel + '<br/>' + 'Months ' + ' : ' + args.yLabel + '<br/>'
                + 'Accidents ' + ' : ' + args.value[0].bubbleData + '<br/>' + 'Fatalities ' + ' : '
                + args.value[1].bubbleData];
    },
  }
}
</script>