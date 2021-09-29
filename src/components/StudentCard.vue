<template>
    <q-card class="my-card" >
        <q-card-section class="bg-primary text-white">
            <div class="text-h6">Student</div>
        </q-card-section>

        <q-separator />

        <q-card-section horizontal>
            <div class="text-subtitle2 col q-pa-md">
                {{ student.fName }} {{ student.lName }} 
            </div>

            <q-card-actions vertical class="justify-around">
                <q-btn 
                    @click="$emit('deleteStudent')"
                    icon="delete"
                    color="negative"
                    flat
                    dense
                    round
                />
            </q-card-actions>
        </q-card-section>

    </q-card>
</template>

<script>
    export default {
        props: {
            student: {
                type: Object,
                default: null
            }
        }
    }
</script>