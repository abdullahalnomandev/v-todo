<template>
    <div>
        Filter Todos:
        <select @change="filterTodos($event)">
            <option value="200"> 200</option>
            <option value="100"> 100</option>
            <option value="20"> 50</option>
            <option value="20"> 20</option>
            <option value="5"> 5</option>
        </select>
    </div>
</template>

<script>
import {mapActions} from 'vuex';
    export default {
        name:'filterTodos',
        methods: mapActions(['filterTodos'])
    }
</script>

<style lang="scss" scoped>

</style>