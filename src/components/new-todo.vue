<template>
    <div id="new-todo">
        <input type="text" v-model="task" placeholder="Ajouter une nouvelle tâche"> <!--avec ce model je vais pouvoir récuper le champ de l'input-->
        <button v-on:click="addtask"><i class="fas fa-plus-circle"></i></button><!--quand je clique sur le bouton je lance la fonction addtask qui agira sur la page todocard-->
        
    </div>
</template>

<style scoped>
#new_todo{

background-color: white;

}

input{
    text-align: center;
    border: none;
    padding: 10px;
    background-color: white;
    border-bottom: 2px solid #0AD3B5;
    font-size: 25px;
}

button{
    background-color: transparent;
    border: none;
    color: green ;
    font-size: 25px;
}
</style>

<script>


export default {
name: 'newTodo',


    data () {
        return {
            task: '' //récupération du champ de l'input
        }
    },


    methods:{
        addtask(){
            this.$emit('newTask', this.task) //ceci me permet de retrouver les éléments de cette page dans la todocard, cela permettra d'ajouter les nouvelles tasks
        }
    }
    
}

</script>