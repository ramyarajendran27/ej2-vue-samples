<template>
  <div class="control-section">
    <div>
      <ejs-stockchart
        style="display:block"
        id="stockchartcontainerstripline"
        :primaryXAxis="primaryXAxis"
        :primaryYAxis="primaryYAxis"
        :chartArea="chartArea"
        :title="title"
        :border="border"
        :theme="theme"
        :seriesType="series"
        :indicatorType="indicator"
        :trendlineType="trendlineType"
      >
        <e-stockchart-series-collection>
          <e-stockchart-series
            :dataSource="seriesData"
            type="Line"
            xName="x"
            yName="close"
          ></e-stockchart-series>
        </e-stockchart-series-collection>
      </ejs-stockchart>
    </div>

    <div id="action-description">
      <p>This sample visualizes stock chart with plot line on y axis.</p>
    </div>
    <div id="description">
      <p>
          In this example, you can see how to highlight a particular range in stock chart. Period and range selector help us to navigate different of data.
        <code>LineSeries</code> is used to represent selected data value.
      </p>
      <p>
      <p>
        Stock Chart provides support to 6 types of <a target="_blank" href="https://ej2.syncfusion.com/vue/documentation/stock-chart/trend-lines" aria-label="Navigate to the documentation for Trendlines in Vue Stock Chart component">trendlines</a> namely <code>Linear</code>, <code>Exponential</code>, <code>Logarithmic</code>, <code>Polynomial</code>, <code>Power</code>, <code>Moving Average</code>. By using trendline dropdown button, the required trendline type can be added or removed.
      </p>
      </p>
      
      <p style="font-weight: 500"><b>Injecting Module</b></p>
      <p>
        The Stock chart component features are segregated into individual feature-wise modules. To use date-time axis, inject
        the
        <code>DateTime</code> and <code>LineSeries</code> module using <code> provide: { stockchart: [ DateTime, LineSeries] },</code> method.
      </p>

    </div>
  </div>
</template>
  <style scoped>
</style>
<script>
import { Browser } from "@syncfusion/ej2-base";
import { amzn } from "./stock-data";
import {
  StockChartComponent,
  StockChartSeriesCollectionDirective,
  StockChartSeriesDirective,
  DateTime,
  Tooltip,
  RangeTooltip,
  Crosshair,
  StripLine,
  LineSeries,
  SplineSeries,
  CandleSeries,
  HiloOpenCloseSeries,
  HiloSeries,
  RangeAreaSeries,
  Trendlines,
  EmaIndicator,
  RsiIndicator,
  BollingerBands,
  TmaIndicator,
  MomentumIndicator,
  SmaIndicator,
  AtrIndicator,
  AccumulationDistributionIndicator,
  MacdIndicator,
  StochasticIndicator,
  Export
} from "@syncfusion/ej2-vue-charts";

import { loadStockChartTheme } from './theme-color';
let theme = loadStockChartTheme();

export default {
  components: {
    'ejs-stockchart': StockChartComponent,
    'e-stockchart-series-collection': StockChartSeriesCollectionDirective,
    'e-stockchart-series': StockChartSeriesDirective
  },
  data: function() {
    return {
      theme: theme,
      series: [],
      indicator: [],
      trendlineType: ['Linear', 'Exponential', 'Polynomial', 'Logarithmic', 'MovingAverage'],
      seriesData: amzn,
      //Initializing Primary X Axis
      primaryXAxis: {
        valueType: "DateTime",
        majorGridLines: { width: 0 }
      },

      //Initializing Primary Y Axis
      primaryYAxis: {
        lineStyle: { color: "transparent" },
        majorTickLines: { color: "transparent", width: 0 },
        stripLines: [{ start: 340, end: 380, color: "#3CB371", opacity: 0.1 }]
      },

      chartArea: {
        border: {
          width: 0
        }
      },
      border: {width: 1},
      title: "AAPL Historical"
    };
  },
  provide: {
    stockChart: [
      DateTime,
      Tooltip,
      StripLine,
      Crosshair,
      RangeTooltip,
      LineSeries,
      SplineSeries,
      CandleSeries,
      HiloOpenCloseSeries,
      HiloSeries,
      RangeAreaSeries,
      Trendlines,
      EmaIndicator,
      RsiIndicator,
      BollingerBands,
      TmaIndicator,
      MomentumIndicator,
      SmaIndicator,
      AtrIndicator,
      AccumulationDistributionIndicator,
      MacdIndicator,
      StochasticIndicator,
      Export
    ]
  },
  methods: {}
};
</script>