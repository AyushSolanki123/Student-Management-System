<template>
    <div>    
        <div
            class="q-mb-md"
            v-for="(student, index) in students"
            :key="index"
        >
            <StudentCard
                :student="student"
                @deleteStudent="$emit('deleteStudent', student)"
            />
        </div>
    </div>
</template>

<script>
    import StudentCard from 'components/StudentCard.vue'
    export default {
        props: {
            students: {
                type: Array,
                required: true,
                default: []
            }
        },
        components: {
            StudentCard
        }
    }
</script>