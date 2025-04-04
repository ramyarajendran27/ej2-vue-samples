<template>
  <div class="control-section">
    <div align='center'>
      <ejs-chart style='display:block' :theme='theme' align='center' id='chartcontainer' :title='title'
        :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :width='width' :chartArea='chartArea'
        :legendSettings='legendSettings' :pointRender='pointRender'>
        <e-series-collection>
          <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' :marker='marker'> </e-series>
        </e-series-collection>
      </ejs-chart>
    </div>
    <div id="action-description">
      <p>
        This example shows multilevel labels in the chart axis. 
        We can add layers of labels to the axis using start and end range values.
      </p>
    </div>
    <div id="description">
      <p>
        In this example, you can see how to group axis labels based on ranges by using <code>ChartMultiLevelLabels</code>. 
        You can customize the text in each level by using <code>ChartAxisMultiLevelLabelBorder</code>, and <code>ChartAxisMultiLevelLabelTextStyle</code>.
      </p>
      <p>Axis labels in each level can be arranged smartly using the <code>Overflow</code> property. Its values and their behaviors are:
      </p>
      <ul>
        <li><code>Trim</code> - Trim the label when it intersect.</li>
        <li><code>Wrap</code> - Wrap the label when it intersect.</li>
        <li><code>None</code> - Shows all the labels.</li>
      </ul>
      <p>
        More information on the multi level labels can be found in this
        <a target="_blank"
          href="https://ej2.syncfusion.com/vue/documentation/chart/axis-labels/#multilevel-labels" aria-label="Navigate to the documentation for Multilevel Labels in Vue Chart component">documentation
          section</a>.
      </p>
    </div>
  </div>

</template>
<style scoped>
#control-container {
  padding: 0px !important;
}
</style>
<script>
import { Browser } from "@syncfusion/ej2-base";
import { ChartComponent, SeriesDirective, SeriesCollectionDirective, ColumnSeries, DataLabel, Category, MultiLevelLabel } from "@syncfusion/ej2-vue-charts";

import { loadChartTheme, pointRenderEvent } from "./theme-color";
let theme = loadChartTheme();

export default {
  components: {
    'ejs-chart': ChartComponent,
    'e-series-collection': SeriesCollectionDirective,
    'e-series': SeriesDirective
  },
  data: function () {
    return {
      theme: theme,
      seriesData: [
        { x: "Grapes", y: 28 },
        { x: "Apples", y: 87 },
        { x: "Pears", y: 42 },
        { x: "Grapes", y: 13 },
        { x: "Apples", y: 13 },
        { x: "Pears", y: 10 },
        { x: "Tomato", y: 31 },
        { x: "Potato", y: 96 },
        { x: "Cucumber", y: 41 },
        { x: "Onion", y: 59 }
      ],

      //Initializing Primary X Axis
      primaryXAxis: {
        valueType: "Category",
        labelRotation: 90,
        labelIntersectAction: Browser.isDevice ? 'Rotate90' : 'Trim',
        border: { width: 1, type: "Rectangle" },
        isIndexed: true,
        interval: 1,
        majorGridLines: { width: 0 },
        multiLevelLabels: Browser.isDevice
          ? [
            {
              border: { type: "Rectangle" },
              categories: [
                { start: -0.5, end: 2.5, text: "In Season" },
                { start: 2.5, end: 5.5, text: "Out of Season" },
                { start: 5.5, end: 7.5, text: "In Season" },
                { start: 7.5, end: 9.5, text: "Out of Season" }
              ]
            },
            {
              border: { type: "Rectangle" },
              textStyle: { fontWeight: "Bold" },
              categories: [
                { start: -0.5, end: 5.5, text: "Fruits" },
                { start: 5.5, end: 9.5, text: "Vegetables" }
              ]
            }
          ]
          : [
            {
              border: { type: "Rectangle" },
              categories: [
                { start: -0.5, end: 0.5, text: "Seedless" },
                { start: 0.5, end: 2.5, text: "Seeded" },
                { start: 2.5, end: 3.5, text: "Seedless" },
                { start: 3.5, end: 5.5, text: "Seeded" },
                { start: 5.5, end: 6.5, text: "Seedless" },
                { start: 6.5, end: 7.5, text: "Seeded" },
                { start: 7.5, end: 8.5, text: "Seedless" },
                { start: 8.5, end: 9.5, text: "Seeded" }
              ]
            },
            {
              border: { type: "Rectangle" },
              categories: [
                { start: -0.5, end: 2.5, text: "In Season" },
                { start: 2.5, end: 5.5, text: "Out of Season" },
                { start: 5.5, end: 7.5, text: "In Season" },
                { start: 7.5, end: 9.5, text: "Out of Season" }
              ]
            },
            {
              border: { type: "Rectangle" },
              textStyle: { fontWeight: "Bold" },
              categories: [
                { start: -0.5, end: 5.5, text: "Fruits" },
                { start: 5.5, end: 9.5, text: "Vegetables" }
              ]
            }
          ]
      },
      chartArea: {
        border: { width: 0 }
      },

      //Initializing Primary Y Axis
      primaryYAxis: {
        minimum: 0,
        maximum: 120,
        interval: 30,
        majorTickLines: { width: 0 },
        lineStyle: { width: 0 },
        labelStyle: { color: "transparent" }
      },

      legendSettings: { visible: false },

      marker: {
        dataLabel: {
          visible: true,
          position: "Outer"
        }
      },

      width: Browser.isDevice ? "100%" : "75%",
      title: "Fruits and Vegetables - Season"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, DataLabel, MultiLevelLabel]
  },
  methods: {
    pointRender: function (args) {
      pointRenderEvent(args);
    },
  }
};
</script>