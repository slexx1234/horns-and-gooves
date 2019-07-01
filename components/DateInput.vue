<template>
    <v-dialog
            ref="dialog"
            v-model="dialog"
            :return-value.sync="date"
            persistent
            lazy
            full-width
            width="290px"
    >
        <template v-slot:activator="{ on }">
            <v-text-field
                    v-model="date"
                    :label="label"
                    :error-messages="errorMessages"
                    readonly
                    v-on="on"
            ></v-text-field>
        </template>
        <v-date-picker v-model="date" scrollable locale="ru">
            <v-spacer></v-spacer>
            <v-btn flat color="primary" @click="dialog = false">Закрыть</v-btn>
            <v-btn flat color="primary" @click="$refs.dialog.save(date)">Выбрать</v-btn>
        </v-date-picker>
    </v-dialog>
</template>

<script>
    export default {
        name: 'DateInput',
        model: {
            event: 'change',
            prop: 'value',
        },
        $_veeValidate: {
            value() {
                return this.date;
            },
        },
        props: {
            label: String,
            errorMessages: Array,
            value: String,
        },
        watch: {
            date(date) {
                this.$emit('change', date)
            },
        },
        data() {
            return {
                dialog: false,
                date: this.value,
            }
        },
    }
</script>
