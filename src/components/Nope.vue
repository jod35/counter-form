<template>
    <div class="div">
        <small>
            <strong>
                {{greeting.length}} characters /100
            </strong>
        </small>
        <h6 v-if="greeting.length >=100" class="red">Message is long..</h6>
        <p> {{greeting}}</p>
        <textarea v-model="greeting"></textarea>
        <br>
        <button id="click" v-on:click="saveMessage" class="mybtn" >Click</button>

         <ul class="messages">
             <li class="message" v-for="message in messages" v-bind:key="message.id" >
                 <h4>{{message.message}}</h4>
                 <a href="#" v-on:click="deleteMessage(id)">delete</a>
             </li>
         </ul>
    </div>
   
</template>
<script>
export default {
    name:"Nope",
    data(){
        return{
            message:"Hello, Welcome to my app",
            count:0,
            greeting:"Hello",
            messages:[]
        }
    },
    created(){
        console.log(`Message is ${this.message}`)
    }
    ,methods:{
        saveMessage(){
            if(this.greeting.length<100){
                this.messages.unshift({
                    id:this.count,
                    message:this.greeting
                })

                this.count ++
            }

        },
        deleteMessage(messageId){
            let message = this.messages.find(
                (message) => message.id == messageId
            )

            this.messages.pop()
            console.log(message);
        }
    }
}
</script>
<style>
.red{
    color: red;
}
.message{
    padding: 20px;
    background-color: lightgray;
    list-style-type: none;
}
textarea{
    width:80%;
}
.mybtn{
    padding: 20px;
    border: none;
    color: white;
    background-color: dodgerblue;
}
</style>