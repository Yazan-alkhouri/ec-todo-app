<template>
<div class="all">
    
    <svg id="icon" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 0 24 24" width="24"><path d="M0 0h24v24H0z" fill="none"/><path d="M8.1 13.34l2.83-2.83L3.91 3.5c-1.56 1.56-1.56 4.09 0 5.66l4.19 4.18zm6.78-1.81c1.53.71 3.68.21 5.27-1.38 1.91-1.91 2.28-4.65.81-6.12-1.46-1.46-4.2-1.1-6.12.81-1.59 1.59-2.09 3.74-1.38 5.27L3.7 19.87l1.41 1.41L12 14.41l6.88 6.88 1.41-1.41L13.41 13l1.47-1.47z"/></svg>
  
    <h2 v-if="welcomemsg">Välkommen till Todo List</h2>
    <h2 v-if="Titleseen">Du har {{number}} todos kvar att göra</h2>

    <!-- <p v-bind=""></p> -->
    
    <ul id="todoItems">
        
        <li id="onetodo"
       
    
        v-for="(element, index) in Todos"
        v-bind:key="index"
        ><input type="checkbox" id="checkbox" >
        
        <span class="close" 
        v-bind="closed" 
        >&times;</span>

        {{element}}</li>
    </ul>



    <!-- button och text -->
    <div id="info">
    
        <input type="text" v-model="txt" placeholder="Add todo" >
        <strong id="alertmsg" v-if="error">Du kan inte lägga till en tom todo </strong>
        <button
        v-on:click="AddTodo()">Lägg till todo
        </button>

        

    

        
        
        
    </div>

</div>    
</template>

<script>
export default {

    data(){ return{
        Todos:[],
        welcomemsg: true,
        Titleseen:false,
        number:0,
        txt:'',
        error: false,
        
    }},
    methods: {
        AddTodo(){
            if(this.txt == '')
                this.error = true;
                else{
                this.Titleseen = true;
                this.welcomemsg = false;
                this.Todos.push(this.txt);
                this.txt = "";
                this.number++
                }
            }

        
         

        
            
   


    }
    
}
</script>

<style scoped>
.all{
    text-align: center;
    
    
    
}
#icon{
   width: 200px;
    height: 200px;
   
}
input[type=text] {
    width: 300px;
    height: 50px;
    border-radius: 0px;
    font-size: x-large;
    color:rgb(7, 14, 54);


  
}
div button{
    width: 310px;
    height: 60px;
    color: white;
    background-color: black;
    border-radius: 10px;
    font-size: large;
    cursor: pointer;
    
}


#info{

  display: grid;  
  justify-content: center;
    
}

#todoItems{
     
      
}



#onetodo{
    
    
    padding-top: 10px;
    margin-bottom: 5px;
    background-color: rgb(184, 179, 179);
    font-size: large;
    position: relative;
    height: 40px; 
    justify-content: center;
    justify-items: center;
     width: 300px;
     margin-left:570px ; 
    /* change it  */
    
    
    
    
   
}

#alertmsg{
    color: red;
    font-size: large;
}

.close {
    font-size: 30px;
    position: absolute;
    left: 0.1px;
    top: 0.1px;
  
}

.close:hover {
    cursor: pointer;
    color: red;
    
    
    }

</style>

