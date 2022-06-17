<template>
    
    <panel class="panel">TO DO LIST</panel>
    <Assignments />
</template>

<style src="../assets/css/style.css" />

<script>

import Assignments from '../components/Assignments.vue';
import Panel from '../components/Panel.vue';

export default{
    name: 'Todo',
    components: {
        Assignments,
        Panel
    }
}

</script>

<style scoped>

.panel{
    margin-bottom: 30px;
}
</style>
