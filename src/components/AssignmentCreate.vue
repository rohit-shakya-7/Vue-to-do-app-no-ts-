<template>

    <form @submit.prevent="add" class="form">
        <div class="name">
            <input type="text" v-model="newAssignment" placeholder="Add new assignment...">
        </div>
        <div class="tag">
            <input type="text" v-model="tag" placeholder="Add new tag..">
        </div>
        <input type="submit" value="Add">
    </form>

</template>

<script>

export default {
    name: 'AssignmentCreate',
    data() {
        return {
            newAssignment: '',
            newTag: '',
        };
    },
    methods: {
        add() {
            this.$emit('add', this.newAssingment, this.tag);
            this.newAssignment = '';
            this.tag = '';
        }
    }
}

</script>