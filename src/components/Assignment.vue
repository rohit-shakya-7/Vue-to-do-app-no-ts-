<template>

<li>
    {{ assignment.title }}
    <input type="checkbox" v-model="assignment.completed">
</li>

</template>

<script>

export default {
    name: 'Assignment',
    props: {
        assignment: Object,
    }
}

</script>