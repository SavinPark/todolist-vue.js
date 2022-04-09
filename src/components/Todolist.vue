<template>
  <div>
	 <!-- main.todo -->
    <main class="todo">
        <div class="container">
            <h1>To - Do List</h1>

            <!-- ul.list_add -->
            <TodoInput @addTodo="addTodo"/>
            <!--// ul.list_add -->

            <!-- ul.todo_list -->
            <ul class="todo_list">
                <li class="todo_list_tit"><p>할 일</p></li>
				<!--li><p>{{ todolist.filter(todo => todo.done === true).length }} / {{ todolist.length }} 건 처리</p></li-->
				<li><p>{{ remaining }} / {{ todolist.length }} 건 처리</p></li>
                <li class="del_btn" v-for="(item, index) in todolist" :key="index">
					<!--:class="{doneStyle:todo.done}" -->
                    <p :class="{doneStyle:item.done}"><input type="checkbox" name="check1" v-model="item.done">{{ item.todo }}</p>
                    <ul class="todo_list_btn">
                        <li><button>수 정</button></li>
                        <li><button @click="delTodo(index)">삭 제</button></li>
                    </ul>
                </li>
            </ul>
            <!--// ul.todo_list -->

        </div>
    </main>
    <!--// main.todo -->
  </div>
</template>

<script>
import TodoInput from './TodoInput.vue'
	
export default {
  name: 'todolist',
  components: {
	  TodoInput
  },
  data: function() {
    return { 
		todolist: [
			{done: false, todo: 'Vue.js 복습하기'},
			{done: false, todo: 'Vue.js 과제하기'},
			{done: false, todo: 'velog 기록'},
			{done: false, todo: 'Spring 프로젝트 - 페이징 처리'},
			{done: false, todo: 'Spring 프로젝트 - 첨부파일 개별 삭제 기능 구현'},
			{done: false, todo: '방청소하기'},
		]
	}
  },
  computed: {
	  remaining() {
		  return this.todolist.filter(function(val) {
			  return val.done;
		  }).length;
	  }
  },
  methods: {
	  addTodo(val) {
		  console.log(val);
		  this.todolist.push({done: false, todo: val});
	  },
	  delTodo(index) {
		  if(confirm("할 일을 정말 삭제하시겠습니까?")) {
		    this.todolist.splice(index, 1);
		  }
	  },
	  editTodo() {
		 console.log("할 일 수정 기능 구현하기!");
	  },
  }
}
</script>

<style>
	.doneStyle {
	    text-decoration : line-through;
		color: lightgray;
	}
</style>