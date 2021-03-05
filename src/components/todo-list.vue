<template>
    <div v-for="task in tasks" :key="task"> <!--liste des composants du tableau tasks-->
        <ul>
            
            <li><input type="checkbox">{{task.taskName}} <button :key="task" @click="removeTask(task)" ><i class="fas fa-trash"></i></button> </li> <!--ici nous avons tout les éléments de notre taches. check,supp et le titre-->
        </ul>
    </div>
</template>

<style scoped>
button{
    width: 50px;
    height: 50px;
    background-color: transparent;
    border: none;
}

li{
    display: flex;
    justify-content: space-around;
    align-items: center;
    font-size: 20px;
}

 ul li input[type=checkbox]{
    width: 100px;
    height: 100px;
}
</style>

<script>
export default {
    name:"toDoList",
    props: { //je définis les types de mes éléments
        tasks: {
            type: Array,
            
        },
        task:{
            type: String
        }

        
    },

methods:{
    removeTask(chek){
        this.$emit('RemoveTask', chek) //ceci me permet de retrouver les éléments de cette page (ul li) pour les envoyer sur la todocard, afin de pouvoir les observer et les supprimer la bas
    }
}
    
    }

    

</script>