<template>
    <div class="container">
        <!-- Fields -->
        <div class="col-6">
            <div class="row">
                <div class="form-group col-md-12" v-for="(field,key) in fields">
                    <vue-editor class="form-control" v-model="field.label"></vue-editor>
                    <button class="btn btn-success" @click="addRow">+</button>
                    <button class="btn btn-danger" @click="delRow(key)">-</button>
                </div>
            </div>
        </div>

        <div class="col-6 preview-container">
            <vue-json-pretty  :data="$data | customFilter"></vue-json-pretty>
        </div>
    </div>
</template>

<script>
    import {VueEditor} from 'vue2-editor'
    import VueJsonPretty from 'vue-json-pretty'

    export default {
        name: "LivePreview",
        data() {
            return {
                fields: [{
                    label: 'Hello world...<br>This is <strong>editable </strong>some content<br>It works <em>great</em>',
                }]
            };
        },
        methods: {
            addRow: function () {
                this.fields.push({
                    label: '',
                });
            },


            delRow: function (key) {
                this.fields.splice(key, 1);
            },

        },
        filters: {
            customFilter: function (value) {
                const data = value.fields.map(item => {
                    return item.label;
                });
                return {data: data};
            }
        },
        components: {
            VueEditor,
            VueJsonPretty
        }
    }
</script>

<style scoped>
    .container {
        display: flex;
    }

    .container > div {
        flex: 1;
    }

    .preview-container {
        background: #000;
        text-align: left;
        color: #fff;
        width: 100%;
        padding: 10px;
    }

    textarea {
        background: #F5F5F5;
        width: calc(100% - 80px);
        float: left;
        -webkit-border-radius: 0;
        -moz-border-radius: 0;
        border-radius: 0;
        min-height: 120px;
    }

    .btn {
        float: left;
        width: 40px;
        height: 120px;
        padding: 10px;
        -webkit-border-radius: 0;
        -moz-border-radius: 0;
        border-radius: 0;
    }
    .btn-success{
        background: #98CA4C;
        border-color: #98CA4C;
    }
    .btn-danger{
        background: #D55C5D;
        border-color: #D55C5D;
    }
</style>