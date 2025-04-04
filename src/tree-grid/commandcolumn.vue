<template>
<div class="col-lg-12 control-section">
   <div id="action-description">
        <p>
            This sample demonstrates CRUD operations in Tree Grid using command column. You can perform CRUD operations as follows,
        </p>
        <ul>
            <li><code>Edit</code> - To edit record, double click a row or click Edit button from command column after selected a row.</li>
            <li><code>Delete</code> - To delete record, click Delete button from command column after selected a row.</li>
            <li><code>Update, Cancel</code> -You can save or discard changes by click Update and Cancel button from command column respectively.</li>
        </ul>
    </div>
    <div id="description">
        <p>
            The Tree Grid provides an option to render CRUD action buttons in a column by using the CommandColumn feature. The <code>columns->commands</code> property accepts array of CommandModel object. The predefined command button can be defined by using type property.
        </p>
        <p>
            The built-in command button are,
        </p>
        <ul>
            <li><code>Edit </code></li>
            <li><code>Delete</code></li>
            <li><code>Cancel</code></li>
            <li><code>Save</code></li>
        </ul>
        <p style="font-weight: 500">Injecting Module:</p>
        <p>
            Tree Grid features are segregated into individual feature-wise modules. To use CommandColumn feature, we need to inject
            <code>
            CommandColumn
            </code> module into the <code>provide</code> section.
        </p>
        <p>
        <br/> More information on the command column configuration can be found in this <a target="_blank" href="https://ej2.syncfusion.com/vue/documentation/treegrid/editing/command-column-editing">documentation section</a>.
        </p>
    </div>
    <div>
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height='380' :editSettings='editSettings'>
            <e-columns>
                <e-column field='taskID' headerText='Task ID' isPrimaryKey='true' textAlign='Right' width='90' :edit='editparams' editType='numericedit' :validationRules='taskIDrules'></e-column>
                <e-column field='taskName' headerText='Task Name' width='190' editType='stringedit' :validationRules='taskNamerules'></e-column>
                <e-column field='startDate' headerText=' Start Date' textAlign='Right' format='yMd' type='date' editType='datepickeredit' :edit='editdataparam' :validationRules='daterules' width='140'></e-column>
                <e-column field='duration' headerText='Duration' textAlign='Right'  width='130' :edit='editparams' editType='numericedit' :validationRules='numberrules'></e-column>
                <e-column field='progress' headerText='Progress' textAlign='Right' width='150' :edit='editparams' editType='numericedit' :validationRules='numberrules'></e-column>
                <e-column headerText='Manage Records' width='140' :commands='commands'></e-column>
            </e-columns>
        </ejs-treegrid>
    </div>

</div>
</template>
<script lang="ts">
import { TreeGridComponent, ColumnDirective, ColumnsDirective, Edit, Page, CommandColumn } from "@syncfusion/ej2-vue-treegrid";
import { sampleData } from "./data-source";

export default {
  components: {
    'ejs-treegrid': TreeGridComponent,
    'e-column': ColumnDirective,
    'e-columns': ColumnsDirective
  },  
  data: () => {
    return {
      data: sampleData.slice(0),
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Row', allowEditOnDblClick: false },
      taskIDrules: { required: true, number: true },
      taskNamerules: { required: true },
      editparams : { params: { format: 'n' } },
      daterules:  { date: ['M/d/yyyy', 'Please enter a valid date']},
      editdataparam : { params: { format:'M/d/yyyy'}},
      numberrules: { number: true, min: 0},
      commands: [{ type: 'Edit', buttonOption: { iconCss: ' e-icons e-edit', cssClass: 'e-flat' } },
        { type: 'Delete', buttonOption: { iconCss: 'e-icons e-delete', cssClass: 'e-flat' } },
        { type: 'Save', buttonOption: { iconCss: 'e-icons e-update', cssClass: 'e-flat' } },
        { type: 'Cancel', buttonOption: { iconCss: 'e-icons e-cancel-icon', cssClass: 'e-flat' } }]
    };
  },
   provide: {
      treegrid: [ Edit, Page, CommandColumn ]
    }

}
</script>