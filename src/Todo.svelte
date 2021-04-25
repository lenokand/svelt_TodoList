<script>
import { each } from "svelte/internal";


let todos= JSON.parse(localStorage.getItem('todos'))||[]


    let newTodoTitle=""

function addTodo(e){
    e.preventDefault()
    todos = [
        ...todos,
        {
            id: Math.random().toString(36).substr(2,9),
            title:newTodoTitle,
            complete: false
        }
    ]
    newTodoTitle=""
    localStorage.setItem('todos', JSON.stringify(todos))
}
function deleteTodo(id){
   
    let tmp = todos

    let index =tmp.findIndex(todo =>todo.id === id)

    tmp.splice(index,1)

    todos = tmp

}
function compliteTodo(id){
   
    let tmp = todos

    let index =tmp.findIndex(todo =>todo.id === id)

    tmp[index].complete = true

    todos = tmp
    localStorage.setItem('todos', JSON.stringify(todos))
}



</script>

<section>
    <form class="app_form" on:submit={addTodo}>
        
            <input type="text" placeholder='add new todo...' bind:value={newTodoTitle}>
    
        <button type="submit" disabled={!newTodoTitle} >
            <i class="fas fa-plus"></i>
        </button>
    </form>
    <ul>
        {#each todos as todo}

        <li class={todo.complete? "app_complete" :""} on:click={()=>{compliteTodo(todo.id)}}> 
            <span>
                {todo.title}
            </span>
            <button class="app_remove" on:click={()=>{deleteTodo(todo.id)}}>
                <i class="fas fa-trash"></i>
            </button>
        </li>
        {/each}
        
    </ul>
</section>

<style lang="scss">
form {
    display: flex;
    input{
        flex-grow: 1;
        border-radius:  .5rem 0 0 .5rem ;
        padding-left: 1rem;
        color: #3d2369;
        font-weight: 500;
        &:focus{
            outline: 0;
        }
        &::placeholder{
            font-weight: 300;
            color: #3d2369;
            opacity: .6;
        }
    }
    button{
        color: #fff;
       
        background: #800080;  /* fallback for old browsers */
        background: -webkit-linear-gradient(-45deg, #ffc0cb, #800080);  /* Chrome 10-25, Safari 5.1-6 */
        background: linear-gradient(-45deg, #ffc0cb, #800080); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
        border-radius:0 .5rem    .5rem 0;
        padding: 1rem 1.5rem;
        cursor: pointer;
        transition: .4s ease;
        &:hover{
            opacity: .9;
            background: -webkit-linear-gradient(45deg, #ffc0cb, #800080);
        }
        &:disabled{
            opacity: .4;
            pointer-events: none;
        }
    }

}


ul{
    list-style: none;
    padding: 0; 

    li{
        display: flex;
        align-items: center;
        margin-bottom: .5rem;
        padding: 1rem;
        border-radius: 1rem;
        color: #3d2369;
        font-weight: 500;
        box-shadow:  0 4px 10px rgba(0,0,0,.2);
        background-color: rgba(255,255,255,.3);

        cursor: pointer;
        transition: .3s ease;
         &:hover{
            box-shadow:  0 1px 3px rgba(0,0,0,.15);
        background-color: rgba(255,255,255,.5); 
         }
        &.app_complete{
            font-style: italic;
            font-weight: 400;
            color: #534a63de;
            box-shadow: inset 0 4px 7px rgba(0,0,0,.2);
            background-color: transparent;
            cursor: default;
        }
        
        span{
            flex-grow: 1;
            font-size: 1.25rem;
        }
        button{
            cursor: pointer;

            background: #42275a;  /* fallback for old browsers */
background: -webkit-linear-gradient(45deg, #734b6d, #42275a);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(45deg, #734b6d, #42275a); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */


            color: #fff;
            padding: .75rem 1rem;
            border-radius: 15px;
            font-size: .75rem;
            border: none;
            transition: .3s ease;
            &:hover{
                opacity: .7;
            }
        }
    }
    .app_check{

    }
    .app-remove{

    }
}
</style>