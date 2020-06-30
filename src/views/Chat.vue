<template>
<div class ='chat'>
    <div class='chat-box'>
        <div class ='text' v-for='i in msgs' v-bind:key=i>
            <div class="msg">{{i}}</div>
            
            
        </div>
    </div>
    <div class = 'interactive-area'>
        <input type='text' placeholder='place here' class = 'type-area' v-model='a' >
        <button class='send' @click='push' >send </button>
    </div>
</div>
    
</template>

<script>
export default {
    name:'Chat',
    data(){
        return {
            a :null,
            msgs :[]
        }
    },
    methods:{
        push(){
            if(this.a !=null){
                this.msgs.push(this.a)
            }
            this.a = null;
            console.log(this.msgs)
            

        }
    }
    
}
</script>

<style scoped>
.chat-box{
    margin-top:5vh;
    margin-left:auto;
    margin-right:auto;
    width:500px;
    height:650px;
    border:5px solid black;
    border-collapse: collapse;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    padding:0rem 2rem;
    text-align:left;
    overflow-y: scroll;
}
.interactive-area{
    width:100%;
    height:50px;
    top:580px;
    border-radius:15px;
    border-collapse:collapse;
    bottom:0;
    position:sticky;
    

    
}
.type-area{
    border-radius:15px;
    border:3px solid black;
    outline:none;
    height:100%;

}
.send{
    position:absolute;
    top:20px;
    padding:5px;
}
.type-area:focus{
    width:500px;
}
.text{
    display:flex;
    flex-direction: column; align-items: flex-start; justify-content: flex-end;
    height:100%;
    min-height:100%;


}
.text:nth-child(even)
{
    justify-self:flex-start;


}


</style>