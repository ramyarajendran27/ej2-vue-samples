<template>
    <div >
        <div class="col-lg-8 control-section tooltip-default" >
            <div id="control-wrapper">
                <div clas="tooltip-wrap">
                    <ejs-tooltip class="tooltipPosition" ref="tooltip" :position="tipposition" content="Let's go green to save the planet!!">
                        <!-- Button element -->
                        <ejs-button>Show Tooltip</ejs-button>
                    </ejs-tooltip>
                </div>
            </div>
        </div>
        <div class="col-lg-4 property-section tooltip-default">
            <table id="property"  title="Properties">
                <tbody>
                    <tr>
                        <td style="width: 30%">
                            <div>Position</div>
                        </td>
                        <td style="width: 70%;padding-right: 10px">
                            <div>
                                <select id="positions" @change="onChange" class="form-control" aria-label="positions">
                                    <option value="TopLeft">Top Left</option>
                                    <option value="TopCenter" selected>Top Center</option>
                                    <option value="TopRight">Top Right</option>
                                    <option value="BottomLeft">Bottom Left</option>
                                    <option value="BottomCenter">Bottom Center</option>
                                    <option value="BottomRight">Bottom Right</option>
                                    <option value="LeftTop">Left Top</option>
                                    <option value="LeftCenter">Left Center</option>
                                    <option value="LeftBottom">Left Bottom</option>
                                    <option value="RightTop">Right Top</option>
                                    <option value="RightCenter">Right Center</option>
                                    <option value="RightBottom">Right Bottom</option>
                                </select>
                            </div>
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div id="action-description">
             <p>This sample demonstrates the default functionalities of the Tooltip which will open
                by <b>hover</b> or <b>touch-hold</b> action on button and displayed in 12 different positions.
            </p>
        </div>
        <div id="description">
            <p>This sample illustrates a tooltip, that gets opened on hovering the target labelled <b>Show Tooltip</b>. The tooltip can be shown
                on 12 possible <a target="_blank" href="https://ej2.syncfusion.com/vue/documentation/api/tooltip/#position">positions</a>, by selecting the appropriate position values provided in the dropdown. The applicable tooltip
                positions are as follows:
            </p>
            <ul>
                <li><code>TopLeft</code></li>
                <li><code>TopCenter</code></li>
                <li><code>TopRight</code></li>
                <li><code>BottomLeft</code></li>
                <li><code>BottomCenter</code></li>
                <li><code>BottomRight</code></li>
                <li><code>LeftTop</code></li>
                <li><code>LeftCenter</code></li>
                <li><code>LeftBottom</code></li>
                <li><code>RightTop</code></li>
                <li><code>RightCenter</code></li>
                <li><code>RightBottom</code></li>
            </ul>
            <p>In case, if the tooltip needs to be opened on mobile devices, tap hold on the target labelled <b>Show Tooltip</b> instead of hovering
                and by default, it closes after 1.5 seconds on lift.</p>
            <p>More information on the Tooltip instantiation can be found in the
                <a href="https://ej2.syncfusion.com/vue/documentation/tooltip/getting-started/" target="_blank"> documentation section</a>.
            </p>
        </div>
    </div>
</template>
<style>
    .tooltip-default #property {
        padding-top: 200px;
    }
    .tooltipPosition {
        display:block;
        position:absolute;
        left:calc( 50% - 60px);
        top:35%;
    }
</style>

<script>
import { TooltipComponent } from "@syncfusion/ej2-vue-popups";
import { ButtonComponent } from "@syncfusion/ej2-vue-buttons";

export default {
   components: {
    'ejs-button': ButtonComponent,
    'ejs-tooltip': TooltipComponent
   },
   data: function(){
        return {
            tipposition : "TopCenter"
        }
   },
   methods: {
       onChange: function(args){
           this.tipposition = args.srcElement.value;
       }
   }
}
</script>
