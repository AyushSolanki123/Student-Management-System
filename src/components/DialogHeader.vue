<template>
    <q-card-section class="row justify-between bg-light-blue-1 text-subtitle1">
        Add Student
        <div>
            <q-btn 
                icon="close"
                rounded 
                size="sm"
                flat
                dense
                @click="$emit('closeDialog')"
            />
        </div>
    </q-card-section>
</template>