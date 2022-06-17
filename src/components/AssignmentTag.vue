<template>

    <div class="tags">
        <h5>Tags: </h5>
        <button v-for="tag in allTags" @click="$emit('update:currentTag', tag)" :key="allTags.indexOf(tag)" :class="{
            'active': tag === currentTag
        }">{{ tag }}</button>
    </div>

</template>

<script>

export default {
    name: 'AssignmentTag',
    props: {
        tags: Array,
        currentTag: String,
    },
    computed: {
        allTags() {
            return ['all', ...new Set(this.tags)];
        }
    },
}

</script>