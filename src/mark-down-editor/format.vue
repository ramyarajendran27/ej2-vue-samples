<template>
  <div>
    <div class="control-section rte-markdown-custom-format">
      <div class="sample-container">
        <div class="default-section">
          <div id="defaultRTE">
            <ejs-richtexteditor ref="rteInstance" :formatter="formatter" :toolbarSettings="toolbarSettings" :created="created" :editorMode="editorMode">
              The sample is configured with customized markdown syntax using the __formatter__ property. Type the content and click the toolbar item to view customized markdown syntax. For unordered list, you need to add a plus sign before the word (e.g., + list1). Or To make a phrase bold, you need to add two underscores before and after the phrase (e.g., __this text is bold__).
            </ejs-richtexteditor>
          </div>
        </div>
      </div>
    </div>
    <div id="action-description">
      <p>
        This sample demonstrates how to customize tags of markdown formatting.
        Type or edit the text and apply the format to view customized markdown syntax.
        For example, apply “+” to Unordered list.
      </p>
    </div>

    <div id="description">
      The Rich Text Editor allows you to customize the markdown syntax by overriding its default syntax. Configure the customized
      markdown syntax using the <code>formatter</code>property
      <p>
        <b>Injecting Module</b>
      </p>
      <p>
        The above features built as modules have to be included in your application. For example, to use image and link, we need to inject
        <code>Toolbar, Link, Image, HtmlEditor</code> into the <code>provide</code> section.
      </p>
      <p>
        The third-party library <code>Marked</code> is used in this sample to convert markdown into HTML content.
      </p>
    </div>
  </div>
</template>

<style>
  .rte-markdown-custom-format .e-richtexteditor textarea.e-content {
    float: left;
  }
  .rte-markdown-custom-format .e-richtexteditor .e-rte-content {
    overflow: hidden;
  }
  .rte-markdown-custom-format .e-md-preview::before {
    content: "\e7de";
  }
  .rte-markdown-custom-format .e-rte-content .e-content.e-pre-source {
    width: 100%;
  }
  .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview.e-icons::before {
    content: "\e80e";
  }
  .bootstrap4 .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before {
    content: "\e790";
  }  
  .bootstrap4 .rte-markdown-custom-format .e-icon-btn .e-md-preview::before {
    content: "\e787";
  }
  .fluent .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .fluent-dark .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .fluent2 .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .fluent2-dark .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .fluent2-highcontrast .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .tailwind .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .tailwind-dark .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .tailwind3 .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .tailwind3-dark .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .bootstrap5 .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .bootstrap5\.3 .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .bootstrap5\.3-dark .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .bootstrap5-dark .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .material3 .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before,
  .material3-dark .rte-markdown-custom-format .e-icon-btn.e-active .e-md-preview::before {
      content: '\e80e';
  }
  .tailwind .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .tailwind-dark .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .tailwind3 .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .tailwind3-dark .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .bootstrap5 .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .bootstrap5\.3 .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .bootstrap5\.3-dark .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .bootstrap5-dark .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .fluent .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .fluent-dark .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .fluent2 .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .fluent2-dark .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .fluent2-highcontrast .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .material3 .rte-markdown-custom-format .e-icon-btn .e-md-preview::before,
  .material3-dark .rte-markdown-custom-format .e-icon-btn .e-md-preview::before {
      content: '\e7de';
  }
</style>

<script>
 
  import { RichTextEditorComponent, Toolbar, Link, Image, Table, MarkdownFormatter, MarkdownEditor } from "@syncfusion/ej2-vue-richtexteditor";
  import { createElement, KeyboardEventArgs } from "@syncfusion/ej2-vue-base";
  import{Tooltip} from "@syncfusion/ej2-vue-popups";
  import { marked } from 'marked';
  
  export default {
    components: {
      'ejs-richtexteditor': RichTextEditorComponent,
      'ejs-tooltip': Tooltip
    },
    data: function() {
      return {
        id: "",
        mdsource: null,
        htmlPreview: null,
        textArea: null,
        previewTextArea: null,
        editorMode: "Markdown",
        placeholder : "Enter your text here...",
        toolbarSettings: {
         items: ['Bold', 'Italic', 'StrikeThrough', '|',
                'Formats', 'Blockquote', 'OrderedList', 'UnorderedList', '|',
                'CreateLink', 'Image', '|',
                {
                  template:
                    '<button id="preview-code" class="e-tbar-btn e-control e-btn e-icon-btn" aria-label="Preview Code">' +
                    '<span class="e-btn-icon e-icons e-md-preview"></span></button>'
                },
                'Undo', 'Redo']
        },
        formatter: new MarkdownFormatter({
          listTags: { OL: "2. ", UL: "+ " },
          formatTags: { Blockquote: "> " },
          selectionTags: { Bold: "__", Italic: "_" }
        })
      };
    },
    methods: {
      created: function() {
        this.rteObj = this.$refs.rteInstance.ej2Instances;
        this.textArea = this.rteObj.contentModule.getEditPanel();
        this.id = this.$refs.rteInstance.ej2Instances.getID() + "html-preview";
        this.mdsource = document.getElementById("preview-code");
        this.htmlPreview = this.rteObj.element.querySelector(this.id);
        this.previewTextArea = this.rteObj.element.querySelector(".e-rte-content");
        this.tooltipObj = new Tooltip({
          content: "Preview",  
          target: "#preview-code"  
        });
        this.tooltipObj.appendTo("#preview-code");
        this.textArea.onkeyup = Event => {
          this.markDownConversion();
        };
        this.mdsource.onclick = e => {
          this.fullPreview();
          if (e.currentTarget.classList.contains("e-active")) {
            this.$refs.rteInstance.disableToolbarItem(["Bold", "Italic", "StrikeThrough", "Formats", "Blockquote", "OrderedList", "UnorderedList", "CreateLink", "Image", "CreateTable"]);
            this.tooltipObj.content = "CodeView";
          } else {
            this.$refs.rteInstance.enableToolbarItem(["Bold", "Italic", "StrikeThrough", "Formats", "Blockquote", "OrderedList", "UnorderedList", "CreateLink", "Image", "CreateTable"]);
            this.tooltipObj.content = "Preview";
          }
        };
      },
      markDownConversion: function() {
        if (this.mdsource.classList.contains("e-active")) {
          this.htmlPreview.innerHTML = marked(this.textArea.value);
        }
      },
      fullPreview: function() {
        if (this.mdsource.classList.contains("e-active")) {
          this.$refs.rteInstance.disableToolbarItem(["Bold", "Italic", "StrikeThrough", "Formats", "Blockquote", "OrderedList", "UnorderedList", "CreateLink", "Image", "CreateTable"]);
          this.mdsource.classList.remove("e-active");
          this.textArea.style.display = "block";
          this.htmlPreview.style.display = "none";
          this.previewTextArea.style.overflow = "hidden";
        } else {
          this.$refs.rteInstance.enableToolbarItem(["Bold", "Italic", "StrikeThrough", "Formats", "Blockquote", "OrderedList", "UnorderedList", "CreateLink", "Image", "CreateTable"]);
          this.mdsource.classList.add("e-active");
          if (!this.htmlPreview) {
            this.htmlPreview = document.createElement("div");
            this.htmlPreview.setAttribute("class", "e-content e-pre-source");
            this.htmlPreview.setAttribute("id", this.id);
            this.textArea.parentNode.appendChild(this.htmlPreview);
            this.previewTextArea.style.overflow = "auto";
          }
          if (this.previewTextArea.style.overflow === "hidden") {
            this.previewTextArea.style.overflow = "auto";
          }
          this.textArea.style.display = "none";
          this.htmlPreview.style.display = "block";
          this.htmlPreview.innerHTML = marked(this.textArea.value);
        }
      }
    },
    provide: {
      richtexteditor: [Toolbar, Link, Image, Table, MarkdownEditor]
    }
  }
</script>
