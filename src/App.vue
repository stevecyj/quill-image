<template>
  <QuillEditor
    theme="snow"
    toolbar="full"
    :modules="modules"
    @editorChange="imageHandler($event)"
  />
  <br />
  <div class="btn btn-primary">Post Preview</div>
</template>

<script>
import { QuillEditor } from '@vueup/vue-quill';
import '@vueup/vue-quill/dist/vue-quill.snow.css';
import BlotFormatter from 'quill-blot-formatter';

export default {
    name: 'App',
    components: {
        QuillEditor,
    },
    data() {
        return {
            modules: {
                toolbar: {
                    container: [['image']],
                    handlers: {
                        image: this.imageHandler,
                    },
                },
                name: 'blotFormatter',
                module: BlotFormatter,
            },
        };
    },
    methods: {
        /**
         * The method for dealing with the image put in the editor
         * to upload the file to firebase storage
         */
        imageHandler(event) {
            let rangy = event.range;
            console.log(rangy);
            console.log(rangy.Range);
        },
    },
};
</script>

<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
