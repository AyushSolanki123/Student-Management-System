<template>
    <q-card-section class="q-gutter-md">
        <div>Enter First Name:</div>
        <q-input 
            placeholder="Enter First Name"
            outlined
            clearable
            v-model="student.fName" 
            @input="$emit('update:student', $event)"           
        />
        <div>Enter Last Name:</div>
        <q-input 
            placeholder="Enter Last Name"
            outlined
            clearable
            @input="$emit('update:student', $event)"           
            v-model="student.lName"
        />
    </q-card-section>
</template>

<script>
    export default {
        props: {
            student: {
                type: Object,
                required: true,
                default: {}
            }
        }   
    }
</script>