<template>
<div class="col-lg-12 control-section">
   <div id="action-description">
        <p>This sample demonstrates Dialog Editing
        </p>
    </div>
    <div>
        <ejs-treegrid :dataSource='data' childMapping='subtasks' :treeColumnIndex='1' height='380' :toolbar='toolbar'
        :editSettings  ='editSettings'>
            <e-columns>
               <e-column field='taskID' headerText='Task ID' width='80' textAlign='Right' isPrimaryKey='true' :edit='editparams' :validationRules='taskidrules'></e-column>
               <e-column field='taskName' headerText='Task Name' width='190'  editType= 'stringedit' :validationRules='tasknamerules'></e-column>
               <e-column field='startDate' headerText='Start Date' width='100' format="yMd"  editType='datepickeredit' textAlign='Right' :edit='editdataparam' :validationRules='startdaterules'></e-column>
               <e-column field='duration' headerText='Duration' width='85' textAlign='Right' :edit='editparams' editType='numericedit' :validationRules='durationrules'></e-column>
               <e-column field='progress' headerText='Progress' width='85' textAlign='Right' :edit='editparams'  editType= 'numericedit' :validationRules='progressrules'></e-column>
               <e-column field='approved' headerText='Approved' width='85' textAlign='Right'  editType= 'booleanedit' :displayAsCheckBox='true'></e-column>
            </e-columns>
        </ejs-treegrid>
    </div>

</div>
</template>
<script lang="ts">
import { TreeGridComponent, ColumnDirective, ColumnsDirective, Edit, Page, Toolbar } from "@syncfusion/ej2-vue-treegrid";
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
      editSettings: { allowEditing: true, allowAdding: true, allowDeleting: true, mode: 'Dialog' },
      toolbar: ['Add', 'Edit', 'Delete'],
      taskidrules: { required: true, number: true },
      tasknamerules: { required: true },
      startdaterules:  { date: ['M/d/yyyy', 'Please enter a valid date']},
      editdataparam : { params: { format:'M/d/yyyy'}},
      numberrules: { number: true, min: 0},
      durationrules : { number: true , min: 0},
      progressrules : { number: true , min: 0},
      editparams: { params: { format: 'n' }},
      pageSettings: { pageCount: 5}
    };
  },
   provide: {
      treegrid: [ Edit, Page, Toolbar]
    },
   methods:{
     
  }

}
</script>