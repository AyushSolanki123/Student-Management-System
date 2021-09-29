<template>
    <q-dialog v-model="showDialog" persistent>
        <q-card class="dialog-card">
            <DialogHeader @closeDialog="closeDialog" />
            <DialogForm :student="student" />
            <DialogFooter @addStudent="addStudent" />
        </q-card>
    </q-dialog>
</template>

<script>
    import DialogHeader from './DialogHeader.vue';
    import DialogForm from './DialogForm.vue';
    import DialogFooter from './DialogFooter.vue';
    export default {
        props: {
            showDialog: {
                type: Boolean,
                required: true,
                default: false                
            }
        },
        components: { 
            DialogHeader,
            DialogFooter,
            DialogForm
        },
        data() {
            return {
                student: {
                    fName: "",
                    lName: ""
                }
            }
        },
        methods: {
            addStudent() {
                this.$emit('addStudent', this.student);
                this.student = {}
            },
            closeDialog() {
                this.$emit('closeDialog');
                this.student = {}
            }
        }
    }
</script>

<style lang="scss">
    .dialog-card {
        border-radius: 19px !important;
        min-width: 280px;
    }
</style>