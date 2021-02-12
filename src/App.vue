
<template>
  <div class="home">
    <ckeditor :editor="editor" v-model="editorData" :config="editorConfig">
    </ckeditor>
    <p>
      <span id="word-count">{{ words }}</span> words -
      <span id="characters-count">{{ characters }}</span> characters
    </p>
  </div>
</template>

<script>
// https://ckeditor.com/docs/ckeditor5/latest/features/word-count.html
import ClassicEditor from "./components/editor/ckeditor";

export default {
  name: "App",
  data() {
    return {
      editor: ClassicEditor,
      words: "",
      editorData: "",
      characters: "",
      editorConfig: {
        placeholder: "Type the content here!",
        wordCount: {
          onUpdate: (stats) => {
            document.getElementById("word-count").innerHTML = stats.words;
            document.getElementById("characters-count").innerHTML =
              stats.characters;
          },
        },
        fontFamily: {
          options: [
            "default",
            "Ubuntu, Arial, sans-serif",
            "Ubuntu Mono, Courier New, Courier, monospace",
          ],
        },
        heading: {
          options: [
            {
              model: "paragraph",
              title: "Paragraph",
              class: "ck-heading_paragraph",
            },
            {
              model: "heading1",
              view: "h1",
              title: "Heading 1",
              class: "ck-heading_heading1",
            },
            {
              model: "heading2",
              view: "h2",
              title: "Heading 2",
              class: "ck-heading_heading2",
            },
            {
              model: "heading3",
              view: "h3",
              title: "Heading 3",
              class: "ck-heading_heading3",
            },
            {
              model: "heading4",
              view: "h4",
              title: "Heading 4",
              class: "ck-heading_heading4",
            },
            {
              model: "heading5",
              view: "h5",
              title: "Heading 5",
              class: "ck-heading_heading5",
            },
            {
              model: "heading6",
              view: "h6",
              title: "Heading 6",
              class: "ck-heading_heading6",
            },
          ],
        },
        supportAllValues: true,
        toolbar: {
          shouldNotGroupWhenFull: true,
          items: [
            "heading",
            "FontFamily",
            "FontSize",
            "FontColor",
            "FontBackgroundColor",
            "Highlight",
            "indent",
            "outdent",
            "|",
            "bold",
            "italic",
            "Underline",
            "strikethrough",
            "HorizontalLine",
            "|",
            "alignment:left",
            "alignment:right",
            "alignment:center",
            "alignment:justify",
            "bulletedList",
            "numberedList",

            "|",
            "blockQuote",
            "insertTable",
            "mediaEmbed",
            "ImageInsert",
            "link",
            // "imageTextAlternative",
            "Superscript",
            "Subscript",

            "|",
            "Code",
            "htmlEmbed",
            "CodeBlock",
            "|",
            "SpecialCharacters",
            "SelectAll",
            "removeFormat",
            "undo",
            "redo",
          ],
        },
        image: {
          styles: ["alignLeft", "alignCenter", "alignRight"],
          resizeOptions: [
            {
              name: "imageResize:original",
              label: "Original",
              value: null,
            },
            {
              name: "imageResize:75",
              label: "75%",
              value: "75",
            },
            {
              name: "imageResize:50",
              label: "50%",
              value: "50",
            },
            {
              name: "imageResize:50",
              label: "20%",
              value: "20",
            },
            {
              name: "imageResize:20",
              label: "10%",
              value: "10",
            },
          ],

          // You need to configure the image toolbar, too, so it shows the new style
          // buttons as well as the resize buttons.
          toolbar: [
            "imageStyle:alignLeft",
            "imageStyle:alignCenter",
            "imageStyle:alignRight",
            "|",
            "imageResize",
            "|",
            "imageTextAlternative",
          ],
        },
        table: {
          contentToolbar: [
            "tableColumn",
            "tableRow",
            "mergeTableCells",
            "tableProperties",
            "tableCellProperties",
          ],
        },
        language: "en",
      },
    };
  },
  //   props: {
  //     value: {
  //       default: "",
  //     },
  //   },
  //   watch: {
  //     value(val) {
  //       this.$emit("data", val);
  //     },
  //   },
};
</script>
