<template>
    <div>
        <h2>{{ district }}</h2>
        <h3>{{ ytd_attendance_avg_ }}</h3>
        <h3>{{ ytd_enrollemnt_avg_ }}</h3>
    </div>
</template>

<script setup>
    const props = defineProps( {
        District: Object
    })

// export default {
//     name: 'DistrictCard',
//     props: {
//         district: String,
//         ytd_attendance_avg_: Number,
//         ytd_enrollemnt_avg_: Number,
//     }
// }

</script>

<style scoped>

</style>