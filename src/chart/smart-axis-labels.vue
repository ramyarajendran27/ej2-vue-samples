<template>
  <div>
    <div class="col-md-8 control-section sb-property-border">
      <ejs-chart ref="chart" style='display:block' :theme='theme' align='center' id='chartcontainer' :title='title'
        :primaryXAxis='primaryXAxis' :primaryYAxis='primaryYAxis' :chartArea='chartArea' :pointRender='pointRender'
        :legendSettings='legendSettings' :tooltip='tooltip'>
        <e-series-collection>
          <e-series :dataSource='seriesData' type='Column' xName='x' yName='y' name='Users' width=2 :marker='marker'>
          </e-series>
        </e-series-collection>
      </ejs-chart>
    </div>
    <div>
      <div class="col-md-4 property-section">
        <table id="property" title="Properties" style="width: 100%">
          <tr style="height: 50px">
            <td>
              <div>Intersect Action
              </div>
            </td>
            <td>
              <div>
                <ejs-dropdownlist id='actionId' :change='actionChange' :dataSource='actiondata' index=0
                  :width='listwidth'></ejs-dropdownlist>
              </div>
            </td>
          </tr>
          <tr style="height: 50px">
            <td>
              <div>Edge Label Placement
              </div>
            </td>
            <td>
              <div>
                <ejs-dropdownlist id='labelId' :change='labelChange' :dataSource='labeldata' index=0
                  :width='listwidth'></ejs-dropdownlist>
              </div>
            </td>
          </tr>
          <tr style="height: 50px">
            <td>
              <div>Label Position
              </div>
            </td>
            <td>
              <div>
                <ejs-dropdownlist id='positionId' :change='positionChange' :dataSource='positiondata' index=0
                  :width='listwidth'></ejs-dropdownlist>
              </div>
            </td>
          </tr>
          <tr style="height: 50px">
            <td>
              <div id="trim">Enable Trim:
              </div>
            </td>
            <td>
              <div>
                <input type="checkbox" id="Trim" unchecked=true @change='trimChange' :width=120 aria-labelledby="Checkbox unchecked">
              </div>
            </td>
          </tr>
          <tr style="height: 50px">
            <td>
              <div id="labelWidth">Maximum Label Width: </div>
            </td>
            <td>
              <div>
                <ejs-numerictextbox value=34 :min="1" width=120 :change='widthChange'
                  id='labelWidth' aria-labelledby="Text"></ejs-numerictextbox>
              </div>
            </td>
          </tr>
        </table>
      </div>
    </div>
    <div id="action-description">
      <p>
        This example shows the smart label placement for the chart axis labels.
      </p>
    </div>
    <div id="description">
      <p>
        In this example, you can see how the axis labels are smartly arranged when they overlap with each other using the <code>LabelIntersectAction</code> property in the axis.</p>
        <p>The following are the <code>LabelIntersectAction</code> property values and their behaviors:
        <ul>
          <li><b>Hide</b> - Hide the label when it intersects.</li>
          <li><b>Trim</b> - Trim the label when it intersects.</li>
          <li><b>Wrap</b> - Wrap the label when it intersects.</li>
          <li><b>MultipleRows</b> - Arrange the label in multiple row when it intersect.</li>
          <li><b>Rotate45</b> - Rotate the label to 45 degree when it intersects.</li>
          <li><b>Rotate90</b> - Rotate the label to 90 degree when it intersects.</li>
          <li><b>None</b> - Shows all the labels.</li>
        </ul>
      </p>
      <p>
        Chart handles edge labels placement using the <code>EdgeLabelPlacement</code> property. Its values and their behaviors are:
        <ul>
          <li><code>None</code> - No action is performed.</li>
          <li><code>Hide</code> - Edge label is hidden.</li>
          <li><code>Shift</code> - Shifts the edge labels.</li>
        </ul>
      </p>
      <p style="font-weight: 500"><b>Injecting Module</b></p>
      <p>
        Chart component features are segregated into individual feature-wise modules. To use Category axis, we need to
        inject
        <code>Category</code> module using <code>provide: {chart: [Category]},</code> method.
      </p>
      <p>
        More information on the smart axis labels can be found in this
        <a target="_blank"
          href="https://ej2.syncfusion.com/vue/documentation/chart/axis-labels/#smart-axis-labels" aria-label="Navigate to the documentation for Smart Axis Labels in Vue Chart component">documentation
          section</a>.
      </p>
    </div>
  </div>

</template>
<style scoped>

</style>
<script>
import { extend } from '@syncfusion/ej2-base';
import { Browser } from "@syncfusion/ej2-base";
import { NumericTextBoxComponent } from '@syncfusion/ej2-vue-inputs';
import { DropDownListComponent } from "@syncfusion/ej2-vue-dropdowns";
import { ChartComponent, SeriesDirective, SeriesCollectionDirective, ColumnSeries, Tooltip, DataLabel, Category } from "@syncfusion/ej2-vue-charts";
import { pointMaterialColors, pointMaterialDarkColors, pointFabricColors, pointBootstrapColors, pointHighContrastColors, pointBootstrap5Colors, pointBootstrap5DarkColors, pointFluentColors, pointFluentDarkColors, pointTailwindColors, pointTailwindDarkColors, pointFluent2Colors, pointFluent2HighContrastColors, pointTailwind3Colors, pointTailwind3DarkColors } from './theme-color';

import { loadChartTheme,  pointRenderEvent } from "./theme-color";
let theme = loadChartTheme();

export default {
  components: {
    'ejs-chart': ChartComponent,
    'e-series-collection': SeriesCollectionDirective,
    'e-series': SeriesDirective,
    'ejs-dropdownlist': DropDownListComponent,
    'ejs-numerictextbox': NumericTextBoxComponent
  },
  data: function () {
    return {
      theme: theme,
      seriesData: [
        { x: 'South Korea', y: 39, DataLabelMappingName: "39M" }, { x: 'India', y: 61, DataLabelMappingName: "61M" },
        { x: 'Pakistan', y: 20, DataLabelMappingName: "20M" }, { x: 'Germany', y: 65, DataLabelMappingName: "65M" },
        { x: 'Australia', y: 16, DataLabelMappingName: "16M" }, { x: 'Italy', y: 29, DataLabelMappingName: "29M" },
        { x: 'France', y: 45, DataLabelMappingName: "45M" }, { x: 'United Arab Emitrates', y: 10, DataLabelMappingName: "10M" },
        { x: 'Russia', y: 41, DataLabelMappingName: "41M" }, { x: 'Mexico', y: 31, DataLabelMappingName: "31M" },
        { x: 'Brazil', y: 76, DataLabelMappingName: "76M" }, { x: 'China', y: 51, DataLabelMappingName: "51M" }
      ],

      //Initializing Primary X Axis
      primaryXAxis: {
        valueType: 'Category',
        interval: 1,
        majorGridLines: { width: 0 },
        labelIntersectAction: 'Hide',
        majorTickLines: { width: 0 },
        minorTickLines: { width: 0 }
      },
      chartArea: {
        border: {
          width: 0
        }
      },

      //Initializing Primary Y Axis
      primaryYAxis:
      {
        labelStyle: { size: '0px' },
        majorTickLines: { width: 0 },
        majorGridLines: { width: 0 },
        lineStyle: { width: 0 },
      },
      actiondata: ['Hide', 'Trim', 'Wrap', 'MultipleRows', 'Rotate45', 'Rotate90', 'None'],
      labeldata: ['None', 'Hide', 'Shift'],
      positiondata: ['Outside', 'Inside'],
      listwidth: 120,
      marker: {
        dataLabel: {
          visible: true,
          name: 'DataLabelMappingName',
          position: 'Top',
          angle: -90,
          enableRotation: Browser.isDevice ? true : false,
          font: { fontWeight: '600' }
        }
      },

      tooltip: { enable: true, header: '', format: '<b>${point.x}</b> <br> Internet Users : <b>${point.y}M</b>' },

      legendSettings: {
        visible: false
      },

      pointRender: function (args) {
        pointRenderEvent(args);
      },
      title: "Internet Users in Millions"
    };
  },
  provide: {
    chart: [ColumnSeries, Category, DataLabel, Tooltip]
  },
  updated: function () {
    this.$nextTick(function () {
      this.$refs.chart.ej2Instances.dataBind();
    });
  },

  methods: {
    actionChange: function (args) {
      let axis = document.getElementById('actionId').value;
      let primaryXAxis = extend({}, this.primaryXAxis);
      primaryXAxis.labelIntersectAction = axis;
      this.primaryXAxis = primaryXAxis;
    },
    labelChange: function (args) {
      let label = document.getElementById('labelId').value;
      let primaryXAxis = extend({}, this.primaryXAxis);
      primaryXAxis.edgeLabelPlacement = label;
      this.primaryXAxis = primaryXAxis;
    },
    positionChange: function (args) {
      let position = document.getElementById('positionId').value;
      let primaryXAxis = extend({}, this.primaryXAxis);
      primaryXAxis.labelPosition = position;
      this.primaryXAxis = primaryXAxis;
    },
    widthChange: function (e) {
      let width = document.getElementById('labelWidth').value;
      let primaryXAxis = extend({}, this.primaryXAxis);
      primaryXAxis.maximumLabelWidth = width;
      this.primaryXAxis = primaryXAxis;
    },
    trimChange: function (args) {
      let trim = document.getElementById("Trim");
      let primaryXAxis = extend({}, this.primaryXAxis);
      primaryXAxis.enableTrim = trim.checked;
      this.primaryXAxis = primaryXAxis;
    }
  }
};
</script>