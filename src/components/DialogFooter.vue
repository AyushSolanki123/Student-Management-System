<template>
    <q-card-actions align="right" class="bg-light-blue-1">
        <q-btn 
            label="Confirm"
            flat
            color="primary"
            @click="$emit('addStudent')"
        />
    </q-card-actions>
</template>