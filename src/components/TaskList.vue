<template>
<div class="container">
    <div class="row">
        <div class="col-md-6">
            <div class="card">
                <div class="card-header">
                    Add A Task
                </div>
                <div class="card-body">
                    <form action="" @submit.prevent="addTask">
                        <div class="form-group">
                            <label for="title">Title</label>
                            <input type="text" name="title" id="title" class="form-control" v-model="todoTitle">
                        </div>
                        <div class="form-group">
                            <label for="description">Description</label>
                            <textarea v-model="todoDescription" name="description" id="description" cols="50" rows="3" class="form-control"></textarea>
                        </div>
                        <div class="form-group">
                            <input v-model="todoDueDate" type="date" class="form-control">
                        </div>
                        <div class="form-group">
                            <input type="submit" value="Add Task" class="btn btn-default btn-lg btn-block">
                        </div>
                    </form>
                </div>
            </div>
        </div>
        <div class="col-md-6">
             <table class="table">
                <thead>
                    <tr>
                    <th scope="col">#</th>
                    <th scope="col">Title</th>
                    <th scope="col">Description</th>
                    <th scope="col">Due date</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="todo in todos" :key="id">
                        <th scope="row">{{ todo.id }}</th>
                        <td>{{ todo.title }}</td>
                        <td>{{ todo.description }}</td>
                        <td>{{ todo.due_at }}</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</div>
</template>

<script>
export default {
  name: 'task-list',
  data () {
    return {
    id: 3,
    todoTitle: '',
    todoDescription: '',
    todoDueDate: '',
    todos: [
        {
        'id': 1,
        'title': 'clean house',
        'description' : 'clean the house',
        'completed' : false,
        'due_date' : Date.now()
        },
         {
        'id': 2,
        'title': 'clean house',
        'description' : 'clean the house',
        'completed' : false,
        'due_date' : Date.now()
        }
    ]
    }
  },
  methods: {
      addTask(){
          this.todos.push({
              id: this.id,
              title: this.todoTitle,
              description: this.todoDescription,
              due_date: this.todoDueDate,
              due_date: moment
          })
          
          this.id++
          this.todoTitle=''
          this.todoDescription=''
          this.todoDueDate=''
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
: