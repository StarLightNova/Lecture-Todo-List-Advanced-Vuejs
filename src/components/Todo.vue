<template>
    <input :id=propId type='checkbox' @click='updateCheck' />
    <label :for=propId>{{propName}}</label>
    <button @click='deleteTodo'>DELETE</button>
</template>

<script>
export default {
    name: 'Todo',
    props: ['propId', 'propName', 'propIsChecked'],
    emits: ['update-check', 'delete-todo'],
    methods: {
        updateCheck(){
            this.$emit('update-check', this.propId);
        },
        deleteTodo(){
            this.$emit('delete-todo', this.propId);
        },
    }
}
</script>