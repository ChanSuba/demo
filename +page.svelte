<h1>Welcome to Todo List</h1>
<script>
    let todos = [];
    let task = "";
    let filter='all';
    function addTask(){
       todos = [{
           task:task,
           status:"pending"
       }, ...todos];
       task = "";
    }
    function markCompletd(i){
        todos[i].status="completed";
        todos = [...todos];
    }
    function removeTask(i){
        todos.splice(i,i);
        todos=[...todos];
    }
   
   </script>
   
   <style>
       *{
        margin:0px;
        padding: 0px;
       }
       .continer{
        width:100%;
        height: 100vh;
        background: #1e85eb;
        display: flex;
        justify-content: center;
        align-items: center;
       }
       .todo{
        padding: 20px;
        background: #f5f5f5;
        width:250px;
        border-radius: 20px;
       }
       .todo > div{
        margin: 20px 0px;
       }
       .todo .form{
        display: flex;
       }
       .todo .form input
       .todo .form button{
        border: 1px solid #1e85eb;
        height: 40px;
        outline: none;
       }
       .todo .form input{
        flex: 1;
        text-indent: 20px;
       }
       .todo .form button{
        width: 60px;
        margin-left: 5px;
        color: #1e85eb;
        cursor: pointer;
       }
       .todo .tasks{
        min-height: 100px;
       }
       .todo .tasks > .task{
        margin: 10px 0px;
        display: flex;
       }
       .todo .tasks > .task> div{
        flex: 1;
       }
       .todo .tasks > .task> button{
        width: 25px;
        height: 25px;
        border: 1px solid #1e85eb;
        color: #1e85eb;
        border-radius: 50%;
        margin: 0px 5px;
        cursor: pointer;
       }
       .todo .tasks > .task >button.active {
        background: #1e85eb;
        color: #f5f5f5;
       }
       .todo .filters{
        display: flex;
        justify-content: space-between;
       }
       .todo .filters > button{
        padding: 10px 0px;
        border: 1px solid #1e85eb;
        color: #1e85eb;
        border-radius: 20px;
        cursor: pointer;
       }
       .todo .filters >button.active{
        background: #1e85eb;
        color: #f5f5f5;
       }
   
   </style>
   
   <div class="container">
       <div class="todo">
           <div class="form">
               <input type="text" bind:value={task}/>
               <button on:click={addTask}>
                   Add
               </button>
           </div>
           <div class="tasks">
            {#each todos as todo,i}
            {#if filter=='all'}
            <div class="task">
                <div>
                    {todo.task}
                </div>
                <button on:click={()=>{markCompletd(i)}}>
                    &#10004;
                </button>
                <button on:click={()=>{removeTask(i)}}>
                    &#10006;
                </button>
            </div>
       
            {:else if filter=='completed'}
              {#if todo.status=='completed'}

              {/if}
            {:else}

            {/if}
            {/each}
        </div>

           <div class="filter">
              <button class="{filter=='all'?'active':''}" on:click={()=>{filter='all'}}>
               All
              </button>
              <button class= "{filter=='completed'?'active':''}" on:click={()=>{filter='complted'}}>
               Completed
              </button>
              <button class= "{filter=='incomplete'?'active':''}" on:click={()=>{filter='incomplete'}}>
               Incomplete
              </button>
           </div>
       </div>
   </div>