<template>
<div>
    <div>
        <div class="col-lg-8 control-section">
            <div class="control-styles">
                <label class="h4">Selection Limit</label>
                <ejs-multiselect ref="multiselectInstance" cssClass="e-specific" id='multiselect-checkbox' :dataSource='countries' :placeholder='checkWaterMark' :fields='checkFields'
                    :mode='mode' :popupHeight='popHeight' :showDropDownIcon='true' :maximumSelectionLength='maxSelection'
                    :filterBarPlaceholder='filterPlaceholder'></ejs-multiselect>
            </div>
        </div>
        <div class="col-lg-4 property-section">
            <table id="property" class="property-panel-table" title="Properties">
                <tr>
                    <td style="width: 50%">
                        <div style="padding-top: 7px">
                            Selection Limit
                        </div>
                    </td>
                    <td style="width: 50%;">
                        <div>
                            <ejs-numerictextbox id="maxSel" aria-label="number"  value="3" :min="min"></ejs-numerictextbox>
                        </div>
                    </td>
                </tr>
                <tr>
                    <td></td>
                    <td>
                        <div>
                            <ejs-button cssClass="e-flat" v-on:click="btnClick">Apply</ejs-button>
                        </div>
                    </td>
                </tr>
            </table>
        </div>
    </div>
    <div id="action-description">
        <p>This sample demonstrates the maximum selection limit functionalities with checkbox of the MultiSelect. MultiSelect 
            value can set restrictions based on the maximum selection length that can be selected.</p>
    </div>
    <div id="description">
        <p>The MultiSelect has built-in support to limit the value selected in Multiselect component, when the <code>maximumSelectionLength</code>        property is set as <code>3</code>, maximum of only 3 value will be selected in the MultiSelect.</p>

        <p>The selection limit sample illustrates using the countries data.</p>

    </div>
</div>
</template>
<style scoped>
    .control-styles {
        margin: 0 auto; 
        width:300px; 
        padding-top: 25px
    }
    .e-specific.e-multiselect.e-input-group .e-ddl-icon::before {
        transform: translateY(1px);
    }
    .control-styles .h4 {
        font-size: 16px;
        margin: 0 0 10px;
        font-weight: bold;
    }

    .e-bigger .e-specific.e-multiselect.e-input-group .e-ddl-icon::before {
        transform: translateY(2px);
    }

    .property-panel-table div {
        padding: 10px 0;
    }

</style>
<script>
import { MultiSelectComponent, CheckBoxSelection } from "@syncfusion/ej2-vue-dropdowns";
import { NumericTextBoxComponent } from "@syncfusion/ej2-vue-inputs";
import { ButtonComponent } from "@syncfusion/ej2-vue-buttons";
import data from './dataSource.json';

export default {
    components: {
        'ejs-multiselect': MultiSelectComponent,
        'ejs-numerictextbox': NumericTextBoxComponent,
        'ejs-button': ButtonComponent
    },
    data: function() {
        return {
            checkFields: { text: 'Name', value: 'Code' },
            checkWaterMark: 'Select countries',
            popHeight: '350px',
            mode: 'CheckBox',
            filterPlaceholder: 'Search countries',
            maxSelection: 3,
            countries: data['countries'],
            min: 1
        };
    },
    methods: {
        btnClick: function() {
            var multiObj = this.$refs.multiselectInstance.ej2Instances;
            multiObj.value = null;
            this.maxSelection = parseFloat(document.getElementById('maxSel').value);
        }
    },
    provide: {
        multiselect: [CheckBoxSelection]
    }
}
</script>
