<template>
<div class ='chat'>
  <div class="chat-wrapper">
    <div class='chat-box'>
        <div class ='msg msg-left' v-for='(msg,index) in msgs' v-bind:key='index'>
            {{msg}}
        </div>
    </div>
    <div class = 'interactive-area'>
        <input type='text' placeholder='place here' class = 'type-area' v-model='a' >
        <button class='send' @click='push' >send </button>
    </div>
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

.chat {
  display: flex;
  flex-direction:column;
  align-items: center;
  justify-content: center;
}

.chat-wrapper {
  width:500px;
  height:650px;
}

.chat-box{
    width: 100%;
    height: 100%;
    border:2px solid black;
    padding: 1rem;
    overflow-y: auto;
    display:flex;
    flex-direction: column-reverse;
}

.interactive-area {
  position: sticky;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.type-area{
    border:2px solid black;
    outline:none;
    width: 100%;
    padding: 12px 24px;
}

.send{
  background: none;
    padding: 12px 24px;
    color: white;
    background-color: black;
    cursor: pointer;
    transition: all 0.4s ease-in-out;
}

.send:hover {
  background-color: white;
  color: black;
}

.msg {
  margin: 8px 0;
  border-bottom: 1px solid black;
}

.msg-left {
  align-self: flex-start;
}

.msg-right {
  align-self: flex-end;
}


</style>
