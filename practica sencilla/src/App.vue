<script setup>
import { ref } from 'vue';

 let newTank = ref('@felipep_77')
 let taskList = ref([
 {
  name:'Estudiar Para Calculo',
  done: true
 },{
  name: 'Realizar Diapositivas de Gobierno Tic',
  done: false
 },{
  name:"Programar",
  done: true
 }
 

]) 

function addTask(){
  if(newTank.value.trim()=== '') return{}

  taskList.value.push({
    name: newTank.value,
    done: false
  })

  newTank.value = ''
}

function deleteTask(index){ 
  taskList.value.splice(index,1)

}

function setDone(index){
  taskList.value[index].done = !taskList.value[index].done
  
}

</script>

<template>
<div class="container">
  <h1>to-do list</h1>
  <p class="subtitle">{{newTank}}</p>

  <div>
    <div @dblclick="deleteTask(index)" @click="setDone(index)" class="task " :class="{done: task.done}" v-for="(task,index) in taskList" :key =index >{{ task.name }} <span class="button">x</span></div>
  </div>

  <input @keypress.enter="addTask" v-model="newTank" type="text" placeholder="Escriba su tarea">
  <p v-show="newTank != '' " class="help">Presiona "enter" para agregar la tarea</p>
</div>
</template>

<style scoped> 

.done{
  text-decoration: line-through;
}

.help{
  font-size: 8px;
  margin: 0;
  opacity: .6;
}

.button{
  background-color: #8FC1B5;
  display: inline-block;
  padding: 0 6px;
  border-radius: 3px;
}

.button:hover{
  cursor: pointer;
  color: black;
}

.task{
  background-color: #146551;
  border-radius: 3px;
  margin-bottom: 1px;
  padding: 2px 2px 1px 6px;
  color: white;
  display: flex;
  justify-content: space-between;
}

input{
  border: none;
  background-color: rgb(127, 205, 179);
  padding: 2px 6px;
  border-radius: 3px;
  outline: none;
  width: 100%;
  box-sizing: border-box;
  margin-top: 8px;
}

input::placeholder{
  opacity: .4;
}

.task:hover{
  background-color: #589A8D;
}
.container{
font-family: 'Nanum Pen Script',cursive;
background-color: #008C72;
border-radius: 6px;
max-width: 420px;
margin: 0 auto;
padding: 6px 12px;
}


h1{
  text-transform: uppercase;
  text-align: center;
  font-size: 18px;
  margin: 0;
}


.subtitle{
  font-size: 10px;
  text-align: center;
  margin: 0;
  margin-bottom: 16px;
  opacity: .6;
}

</style>
