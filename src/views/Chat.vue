<template>
<div class ='chat'>
  <div class="chat-wrapper">
    <div class='chat-box'>
        <div class = 'msg alert'>
          {{alert}}
          </div>
        <div class ='msg' :class = 'binder(msg)' v-for='(msg,index) in msgs' v-bind:key='index'>
            {{msg.message}}
        </div>
    </div>
    <div class = 'interactive-area'>
        <input type='text' placeholder='place here' class = 'type-area' v-model='temp'>
        <button class='send'  @keyup.enter='send' @click='send'>send </button>
    </div>
  </div>
</div>

</template>

<script>

export default {
    name:'Chat',
    props:['socket'],
    data(){
        return {
            msgs :[],
            alert :null,
            temp: ''
        }
    },
    methods:{
        send(e){
          e.preventDefault()
          if (this.temp!=''){
            this.socket.emit('msg',this.temp)
            this.msgs.push({self:true,message:this.temp})
            this.temp = ''
          }
        },
        binder(msg){

          if(msg.self == true){
            return 'msg-left'
          }
          else{
            return 'msg-right'
            
          }

        },
        check(e){
          if(e.keyCode == 13)
          {
            this.send(e)
          }

        }
    },
    mounted(){
      this.socket.on('chat-success',(msg)=>{
        this.alert = msg;
      })
      this.socket.on('msg',(msg)=>{
        this.msgs.push({self:'false',message:msg})
      })
      
    },
    created(){
      window.addEventListener('keyup', this.check)
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
  margin: 8px 0px;
}
.alert{
  align-self:center;
}

.msg-left {
  align-self: flex-start;
}

.msg-right {
  align-self: flex-end;
}


</style>
