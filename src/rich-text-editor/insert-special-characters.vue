<template>
<div>
<div class="control-section">
    <div class="sample-container">
        <div class="default-section" id="rteSection">
        <ejs-richtexteditor ref="rteObj" :toolbarSettings="toolbarSettings" :created="onCreate"  :actionComplete='actionComplete'>
        <p style="margin-right:10px">The custom command "insert special character" is configured as the last item of the toolbar. Click on the command and choose the special character you want to include from the popup.</p></ejs-richtexteditor>
        <ejs-dialog id='rteDialog' :buttons='dlgButtons' :header='header' ref="dialogObj" :overlayClick='dialogOverlay' :visible='visible' height='340px' width='43%' :showCloseIcon='showCloseIcon' :isModal='modal'  :target='target' :created="dialogCreate">
        </ejs-dialog>
        <div id="customTbarDialog" style="display: none">
                <div id="rteSpecial_char" ref="rteSpecialCharEle">
                   <div class="char_block" title="&#94;">&#94;</div>
                    <div class="char_block" title="&#95;">&#95;</div>
                    <div class="char_block" title="&#96;">&#96;</div>
                    <div class="char_block" title="&#123;">&#123;</div>
                    <div class="char_block" title="&#124;">&#124;</div>
                    <div class="char_block" title="&#125;">&#125;</div>
                    <div class="char_block" title="&#126;">&#126;</div>
                    <div class="char_block" title="&#160;">&#160;</div>
                    <div class="char_block" title="&#161;">&#161;</div>
                    <div class="char_block" title="&#162;">&#162;</div>
                    <div class="char_block" title="&#163;">&#163;</div>
                    <div class="char_block" title="&#164;">&#164;</div>
                    <div class="char_block" title="&#165;">&#165;</div>
                    <div class="char_block" title="&#x20B9;">&#x20B9;</div>
                    <div class="char_block" title="&#166;">&#166;</div>
                    <div class="char_block" title="&#167;">&#167;</div>
                    <div class="char_block" title="&#168;">&#168;</div>
                    <div class="char_block" title="&#169;">&#169;</div>
                    <div class="char_block" title="&#170;">&#170;</div>
                    <div class="char_block" title="&#171;">&#171;</div>
                    <div class="char_block" title="&#172;">&#45;</div>
                    <div class="char_block" title="&#173;">&#173;</div>
                    <div class="char_block" title="&#174;">&#174;</div>
                    <div class="char_block" title="&#175;">&#175;</div>
                    <div class="char_block" title="&#176;">&#176;</div>
                    <div class="char_block" title="&#177;">&#177;</div>
                    <div class="char_block" title="&#178;">&#178;</div>
                    <div class="char_block" title="&#179;">&#179;</div>
                    <div class="char_block" title="&#180;">&#180;</div>
                    <div class="char_block" title="&#181;">&#181;</div>
                    <div class="char_block" title="&#182;">&#182;</div>
                    <div class="char_block" title="&#183;">&#183;</div>
                    <div class="char_block" title="&#184;">&#184;</div>
                    <div class="char_block" title="&#185;">&#185;</div>
                    <div class="char_block" title="&#186;">&#186;</div>
                    <div class="char_block" title="&#187;">&#187;</div>
                    <div class="char_block" title="&#188;">&#188;</div>
                    <div class="char_block" title="&#189;">&#189;</div>
                    <div class="char_block" title="&#190;">&#190;</div>
                    <div class="char_block" title="&#191;">&#191;</div>
                    <div class="char_block" title="&#192;">&#192;</div>
                    <div class="char_block" title="&#193;">&#193;</div>
                    <div class="char_block" title="&#194;">&#194;</div>
                    <div class="char_block" title="&#195;">&#195;</div>
                </div>
            </div>
        </div>
    </div>
</div>
<div id="action-description">
    <p>
        This sample shows how to add your own commands to toolbar of the Rich Text Editor. The <code>“Ω” </code> command
        is added to insert special characters in the editor. Click the “Ω” command to show the special characters list, and
        then choose the character to be inserted in the editor.
    </p>
</div>

<div id="description">
    <p>The Rich Text Editor allows you to configure your own commands to its toolbar using <code>toolbarSettings</code> property. 
        The command can be plain text, icon, or HTML template. 
        You can also define the order and group where the command should be included. 
        Bind the action to the command by getting its instance. </p>
    <p><b>Injecting Module</b></p>
    <p>The above features built as modules have to be included in your application. For example, to use image and link, we need to inject <code>Toolbar, Link, Image, HtmlEditor, QuickToolbar, PasteCleanup</code> into the <code>provide</code> section.</p>
</div>

</div>
</template>
<style scoped>
    #rteSpecial_char .char_block {
        display: inline-block;
    }

    #custom_tbar,
    #custom_tbar div{
        cursor: pointer;
        font-size: 16px;
    }

    .e-bigger #custom_tbar div {
        font-size: 18px;
    }

    #rteSection {
        height: 350px;
    }

    #rteSpecial_char {
        padding: 15px 0 15px 0;
    }

    .material #rteSpecial_char .char_block.e-active {
        outline: 1px solid #e3165b;
        border-color: #e3165b;
    }

    .material-dark #rteSpecial_char .char_block.e-active {
        outline: 1px solid #56a4fd;
        border-color: #56a4fd;
    }

    .fabric #rteSpecial_char .char_block.e-active,
    .fabric-dark #rteSpecial_char .char_block.e-active {
        outline: 1px solid #0078d6;
        border-color: #0078d6;
    }

    .bootstrap4 #rteSpecial_char .char_block.e-active {
        outline: 1px solid #007bff;
        border-color: #007bff;
    }

    .bootstrap #rteSpecial_char .char_block.e-active,
    .bootstrap-dark #rteSpecial_char .char_block.e-active {
        outline: 1px solid #317ab9;
        border-color: #317ab9;
    }

    .highcontrast #rteSpecial_char .char_block.e-active {
        outline: 1px solid #ffd939;
        border-color: #ffd939;
    }

    .tailwind #rteSpecial_char .char_block.e-active,
    .tailwind3 #rteSpecial_char .char_block.e-active {
        outline: 1px solid #3730a3;
        border-color: #3730a3;
    }

    .tailwind-dark #rteSpecial_char .char_block.e-active,
    .tailwind3-dark #rteSpecial_char .char_block.e-active {
        outline: 1px solid #22d3ee;
        border-color: #22d3ee;
    }

    .bootstrap5 #rteSpecial_char .char_block.e-active,
    .bootstrap5\.3 #rteSpecial_char .char_block.e-active,
    .bootstrap5\.3-dark #rteSpecial_char .char_block.e-active,
    .bootstrap5-dark #rteSpecial_char .char_block.e-active {
        outline: 1px solid #0D6EFD;
        border-color: #0D6EFD;
    }

    .bootstrap5 #rteSpecial_char .char_block.e-active,
    .bootstrap5-dark #rteSpecial_char .char_block.e-active {
        outline: 1px solid #0D6EFD;
        border-color: #0D6EFD;
    }

    .fuent2-highcontrast #rteSpecial_char .char_block.e-active {
    outline: 1px solid #22d3ee;
    border-color: #22d3ee;
    }

    .fluent #rteSpecial_char .char_block.e-active,
    .fluent-dark #rteSpecial_char .char_block.e-active {
        outline: 1px solid #0078DE;
        border-color: #0078DE;
    }

    .fluent2 #rteSpecial_char .char_block.e-active,
    .fluent2-dark #rteSpecial_char .char_block.e-active {
        outline: 1px solid #0f6cbd;
        border-color: #0f6cbd;
    }

    .material3 #rteSpecial_char .char_block.e-active,
    .material3-dark #rteSpecial_char .char_block.e-active {
        outline: 1px solid #7D69B1;
        border-color: #7D69B1;
    }
    .fabric.e-bigger .e-toolbar .e-toolbar-items .e-toolbar-item .e-tbar-btn.e-btn .e-tbar-btn-text,
    .highcontrast.e-bigger .e-toolbar .e-toolbar-items .e-toolbar-item .e-tbar-btn.e-btn .e-tbar-btn-text {
        padding-right: 10px;
    }

    .bootstrap.e-bigger .e-toolbar .e-toolbar-items .e-toolbar-item .e-tbar-btn.e-btn .e-tbar-btn-text,
    .bootstrap .e-toolbar .e-toolbar-items .e-toolbar-item .e-tbar-btn.e-btn .e-tbar-btn-text {
        padding-right: 6px;
    }

    .fabric .e-toolbar .e-toolbar-items .e-toolbar-item .e-tbar-btn.e-btn .e-tbar-btn-text,
    .highcontrast .e-toolbar .e-toolbar-items .e-toolbar-item .e-tbar-btn.e-btn .e-tbar-btn-text {
        padding-right: 8px;
    }

    #rteSpecial_char .char_block {
        width: 30px;
        height: 30px;
        line-height: 30px;
        margin: 0 5px 5px 0;
        text-align: center;
        vertical-align: middle;
        border: 1px solid #DDDDDD;
        font-size: 20px;
        cursor: pointer;
        user-select: none;
    }

    @media (min-width: 320px) and (max-width: 480px) {
        .fabric.e-bigger #rteDialog {
            min-width: 281px;
        }
		#rteSpecial_char {
        padding: 15px 0 15px 20px;
		}

        .fabric #rteDialog {
            min-width: 241px;
        }

        .bootstrap.e-bigger #rteDialog,
        .bootstrap #rteDialog {
            min-width: 223px;
        }

        .highcontrast.e-bigger #rteDialog {
            min-width: 283px;
        }
        .highcontrast #rteDialog {
            min-width: 243px;
        }
        .material #rteDialog {
            min-width: 224px;
        }
        .material.e-bigger #rteDialog {
            min-width: 236px;
        }
    }
</style>
<script>
import { RichTextEditorComponent, Toolbar, Link, Image, NodeSelection, HtmlEditor, QuickToolbar, PasteCleanup, Table, Video, Audio } from "@syncfusion/ej2-vue-richtexteditor";
import { DialogComponent } from '@syncfusion/ej2-vue-popups';

export default {
    components: {
      'ejs-richtexteditor': RichTextEditorComponent,
      'ejs-dialog': DialogComponent
    },
    data: function() {
        return {
            selection: new NodeSelection(),
            rteSpecialCharEle: null,
            range: null,
            customBtn: null,
            dialogCtn: null,
            saveSelection: new NodeSelection(),
            target: document.getElementById('rteSampleContainer'),
            header: 'Special Characters',
            visible: false,
            modal: true,
            showCloseIcon: false,
            dlgButtons: [{ click: this.onInsert.bind(this), buttonModel: { isPrimary:'true', content: 'Insert' } }, { buttonModel: { content: 'Cancel' }, click: this.dialogOverlay.bind(this) }],
            toolbarSettings: {
                items: ['Bold', 'Italic', 'Underline', '|', 'Formats', 'Alignments', 'Blockquote', 'OrderedList',
                'UnorderedList', '|', 'CreateLink', 'Image', '|', 'SourceCode',
                {
                    tooltipText: 'Insert Symbol',
                    template: '<button class="e-tbar-btn e-btn" tabindex="-1" id="custom_tbar"  style="width:100%"><div class="e-tbar-btn-text" style="font-weight: 400;"> &#937;</div></button>'
                }, '|', 'Undo', 'Redo']
            },
        };
    },
    methods: {
        onCreate: function() {
        this.customBtn = document.getElementById('custom_tbar');
         this.$refs.dialogObj.ej2Instances.target = document.getElementById('rteSection');
         var proxy = this;
        this.customBtn.onclick = function () {
            proxy.$refs.rteObj.ej2Instances.contentModule.getEditPanel().focus();
            proxy.range = proxy.selection.getRange(document);
            proxy.saveSelection = proxy.selection.save(proxy.range, document);
            proxy.$refs.dialogObj.ej2Instances.content = proxy.$refs.rteSpecialCharEle;
            proxy.$refs.dialogObj.ej2Instances.dataBind();
            proxy.$refs.dialogObj.show();
        };
        },
        actionComplete: function(args) {
           if (args.requestType === 'SourceCode') {
            this.$refs.rteObj.ej2Instances.getToolbar().querySelector('#custom_tbar').parentElement.classList.add('e-overlay');
        } else if (args.requestType === 'Preview') {
            this.$refs.rteObj.ej2Instances.getToolbar().querySelector('#custom_tbar').parentElement.classList.remove('e-overlay');
        }
        },
        dialogCreate: function() {
            var dialogCtn = this.$refs.rteSpecialCharEle;
            var proxy = this;
            dialogCtn.onclick = function (e) {
            var target = e.target;
            var activeEle = proxy.$refs.dialogObj.$el.querySelector('.char_block.e-active');
            if (target.classList.contains('char_block')) {
                target.classList.add('e-active');
                if (activeEle) {
                    activeEle.classList.remove('e-active');
                }
            }
        };
        }, 
        onInsert: function() {
            var activeEle = this.$refs.dialogObj.$el.querySelector('.char_block.e-active');
            if (activeEle) {
                if (this.$refs.rteObj.ej2Instances.formatter.getUndoRedoStack().length === 0) {
                 this.$refs.rteObj.ej2Instances.formatter.saveData();
                }
                this.saveSelection.restore();
                this.$refs.rteObj.ej2Instances.executeCommand('insertText', activeEle.textContent);
                this.$refs.rteObj.ej2Instances.formatter.saveData();
                this.$refs.rteObj.ej2Instances.formatter.enableUndo(this.$refs.rteObj.ej2Instances);
            }
            this.dialogOverlay();
        },
        dialogOverlay: function() {
             var activeEle = this.$refs.dialogObj.$el.querySelector('.char_block.e-active');
            if (activeEle) {
                activeEle.classList.remove('e-active');
            }
            this.$refs.dialogObj.hide();
        }
    },
    provide:{
        richtexteditor:[Toolbar, Link, Image, HtmlEditor, QuickToolbar, PasteCleanup, Table, Video, Audio]
    }
}
</script>