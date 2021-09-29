<template>
    <div>      
        <q-btn 
            :label="label"        
            color="primary"
            no-caps
            @click="$emit('atClick')"
        />
    </div>
</template>

<script>
    export default {
        props: {
            label: {
                type: String,
                default: ''
            }
        }
    }
</script>