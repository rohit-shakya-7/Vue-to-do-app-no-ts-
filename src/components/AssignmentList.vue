<template>
    <ul v-show="show && assignments.length">
        <div class="title">
            <h3> {{ title }} <span>({{ assignments.length }})</span></h3>
            <p v-if="canToggle" @click="show = false" style="cursor: pointer;">&times;</p>
        </div>
        <assignment v-for="assignment in assignments" class="assignment" :key='assignment.id' :assignment=assignment>
        </assignment>
    </ul>
</template>

<script>
import Assignment from "@/components/Assignment.vue";

export default {
    name: 'AssignmentList',
    components: {
        Assignment
    },
    props: {
        title: String,
        canToggle: {
            type: Boolean,
            default: false
        },
        assignments: Array,
    },
    data() {
        return {
            show: true,
        }
    }
}

</script>