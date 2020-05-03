<template>
	<div class="todo-item" :class="{'is-complete':todo.completed}">
		<div>
			<input :id="todo.id" type="checkbox" @change="$emit('check-todo', todo.id)" :checked="todo.completed" />
			<label :for="todo.id">{{todo.title}}</label>
			<button @click="$emit('del-todo', todo.id)" class="del">X</button>
		</div>
	</div>
</template>

<script>
export default {
	name: "TodoItem",
	props: ["todo"],
};
</script>

<style scoped>
.todo-item {
	background: #f4f4f4;
	padding: 10px;
	border-bottom: 1px #cccccc dotted;
}
.is-complete {
	text-decoration: line-through;
}
.del {
	background: #ff0000;
	color: #fff;
	border: none;
	padding: 5px 9px;
	border-radius: 50%;
	cursor: pointer;
	float: right;
}
label {
	margin: 0 1em;
}
</style>