<template>
    <div>
        <h2>{{ District.district }}</h2>
        <h3>Attendance Average: {{ District.ytd_attendance_avg_ }}</h3>
        <h3>Enrollemnt Average: {{ District.ytd_enrollment_avg_ }}</h3>
    </div>
</template>

<script setup>
    const props = defineProps( {
        District: Object
    })
</script>

<style scoped>

</style>