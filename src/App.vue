<template>
    <div id="app">
        <LivePreview></LivePreview>
    </div>
</template>

<script>
    import LivePreview from './components/LivePreview'

    export default {
        name: 'app',
        components: {
            LivePreview
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }

    .ql-toolbar {
        display: none !important;
    }

    .quillWrapper {
        min-height: 120px !important;
        width: calc(100% - 80px) !important;
        padding: 0 !important;
        background: #F5F5F5 !important;
        float: left;
        height: auto;
    }

    .ql-editor {
        min-height: auto !important;
    }

    .ql-container.ql-snow {
        border: 0 !important;
    }

    .vjs__tree .vjs__value__string{
        word-break: break-all !important;
    }
</style>
