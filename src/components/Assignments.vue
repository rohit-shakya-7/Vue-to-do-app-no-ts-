<template>

    <AssignmentTags :tags="assignments.map(a => a.tag)" :currentTag="currentTag" />
    <div class="assignmentLists">
        <assignment-list title="In Progress" :assignments="filters.inProgress" class="assignments"></assignment-list>
        <assignment-list title="Completed" :assignments="filters.completed" class="assignments" can-toggle>
        </assignment-list>
    </div>
    <assignment-create @add="add"></assignment-create>

</template>


<script>

import AssignmentList from "@/components/AssignmentList.vue";
import AssignmentCreate from "@/components/AssignmentCreate.vue";
import AssignmentTag from "@/components/AssignmentTag.vue";


export default {
    name: 'Assignments',
    components: {
        AssignmentList, AssignmentCreate, AssignmentTag
    },
    data() {
        return {
            assignments: [],
            newAssignment: '',
            currentTag: 'all',
        };
    },

    created() {


        fetch('http://localhost:8080/db.json')
            .then(response => response.json())
            .then(data => {
                this.assignments = data;
            });
    },

    computed: {
        filteredAssignments() {
            if (this.currentTag === 'all') {
                return this.assignments;
            }
            return this.assignments.filter(a => (this.currentTag === a.tag));
        },
        filters() {
            return {
                // 'filteredAssignments': this.assignments.filter(a => (a.tag === filterTag)),
                'inProgress': this.filteredAssignments.filter(a => !a.completed),
                'completed': this.filteredAssignments.filter(a => a.completed)
            }
        },
        // inProgress() {
        //     return this.assignments.filter(a=>!a.completed);
        // },
        // completed() {
        //     return this.assignments.filter(a=>a.completed);
        // }
    },

    methods: {
        add(name, tag) {
            this.assignments.push({
                id: this.assignments.length + 1,
                title: name,
                completed: false,
                tag: tag,
            });
        }
    },
}

</script>