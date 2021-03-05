<script>
//import des différents composants
import moment from 'moment'
import newTodo from './new-todo.vue';
import TodoList from './todo-list.vue';






export default {

  components: { newTodo, TodoList },
    name: 'todoCard',

     created: function () { //calendrier
    this.moment = moment;
  },

 data (){
     return {
         tasks: [], //mon tableau qui contiendra mes tasks
         
         
     }
 },

 methods: {
     sendTask(task){ //La méthode qui me permet d'ajouter une task
         this.tasks.push({
             taskName: task,
             check: false,
         })
         
     },

        
  removeTask (check) {  //la méthode qui me permet de supprimer une task
      const taskInd = this.tasks.indexOf(check);
    this.tasks.splice(taskInd, 1);
  }
}
     
 }
 
    

</script>


<template>
    <div>
        <div id='todoCard'>
            <div class="container">
                <div>{{moment(new Date()).format('DD.MM.YYYY [&nbsp;]')}}</div> <!--calendrier-->
                <div>VueJs Tutorial ToDo List</div>
            <p>{{tasks.length}} tâches</p> <!--nombre de taches en fonction de la longueur du tableau-->
                
            </div>
            <newTodo v-on:newTask="sendTask"></newTodo> <!--import de mon composant newTodo-->
 
        <TodoList :tasks="tasks" v-on:RemoveTask="removeTask"></TodoList><!--import de mon composant todolist-->
        </div>
        

        
    </div> 
</template>

<style scoped>
#todoCard {
    width: 80%;
    height: 60%;
    background-color: white;
}

.container{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}
</style>

