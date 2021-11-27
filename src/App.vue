<template>
	<TodoList/>
</template>

<script>
import TodoList from './components/TodoList.vue'

export default {
	name: 'App',
	components:{
		TodoList,
	},
	data(){
		return {
			welcome: 'Salem Alem! x2',
		}
	}
}
</script>