<template>
    <div>
        <v-text-field
                v-model="name"
                :label="label"
                readonly
                @click="$refs.fileInput.click()"
                @click:append="$refs.fileInput.click()"
                append-icon="get_app"
                required
        ></v-text-field>
        <input type="file" ref="fileInput" @change="change" class="d-none">
    </div>
</template>

<script>
    export default {
        name: 'FileInput',
        model: {
            event: 'change',
            prop: 'value',
        },
        data() {
            return {
                name: null,
                file: null,
            }
        },
        $_veeValidate: {
            value() {
                return this.file;
            },
        },
        props: {
            label: String,
        },
        watch: {
            file(file) {
                this.$emit('change', file)
            },
        },
        methods: {
            change() {
                if (typeof this.$refs.fileInput.files[0] === 'undefined') {
                    this.name = null
                    this.file = null
                } else {
                    this.name = this.$refs.fileInput.files[0].name
                    this.file = this.$refs.fileInput.files[0]
                }
            }
        },
    }
</script>
