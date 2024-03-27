<template>
    <div>
        <h2>{{ District.district }}</h2>
        <h3>{{ District.ytd_attendance_avg_ }}</h3>
        <h3>{{ District.ytd_enrollemnt_avg_ }}</h3>
    </div>
</template>

<script setup>
    const props = defineProps( {
        District: Object
    })
</script>

<style scoped>

</style>