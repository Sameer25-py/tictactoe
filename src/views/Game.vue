<template>
<div class = 'wrapper'>
    <div class = 'scoreboard'>
        <div class='score'>
            SCORE
        </div>
        <div class = 'vs'>
            <div class= 'avatar1'>
                <img src="../assets/avatar.png" class = 'avatar'>   
                </div>
             <div class='VS'> 
                VS
            </div>
            <div class="avatar2">
                <img src="../assets/avatar.png" class = 'avatar'>
            </div>
            <div class = 'name1'>
                Player1
            </div>
            <div> 
                <!--empty div -->
                </div>
            <div class='name2'>
                Player2
            </div>
        </div>
        </div>

    <div class = 'turn' v-if ="waiting">
        waiting for Opponent
    </div>

    <div class = 'turn' v-if="turn && !waiting"> 
        Your Turn
        </div>

    <div class = 'turn' v-else-if="!turn && !waiting">
        Opponent Turn
    </div>

    <div id = 'app'>
        <div class = 'gameboard'>
            <table class = 'table'>
                <tr v-bind:key=index v-for='(i,index) in board'>
                    <td v-bind:key=jndex v-for='(j,jndex) in i' @click="clicked(index,jndex)"> {{j}}</td>
                </tr>
            </table>
        </div>
    </div>
    
    <div class = 'chat'>
        <Chat :socket=socket />
    </div>
</div>
    
</template>

<script>
import Chat from './Chat.vue'
import io from 'socket.io-client'
export default {
    name:'Game',
    components:{
        Chat:Chat
    },
    data(){
        return{
            socket : io.connect('http://localhost:9000/player'),
            oval : `<svg id="Capa_1" height="100pt" viewBox="0 0 515.556 515.556" width="100pt" xmlns="http://www.w3.org/2000/svg"><path d="m257.778 515.556c-142.137 0-257.778-115.642-257.778-257.778s115.641-257.778 257.778-257.778 257.778 115.641 257.778 257.778-115.642 257.778-257.778 257.778zm0-451.112c-106.61 0-193.333 86.723-193.333 193.333s86.723 193.333 193.333 193.333 193.333-86.723 193.333-193.333-86.723-193.333-193.333-193.333z"/></svg>`,
            cross: `<svg height="120pt" viewBox="0 0 365.71733 365" width="120pt" xmlns="http://www.w3.org/2000/svg"><g fill="#f44336"><path d="m356.339844 296.347656-286.613282-286.613281c-12.5-12.5-32.765624-12.5-45.246093 0l-15.105469 15.082031c-12.5 12.503906-12.5 32.769532 0 45.25l286.613281 286.613282c12.503907 12.5 32.769531 12.5 45.25 0l15.082031-15.082032c12.523438-12.480468 12.523438-32.75.019532-45.25zm0 0"/><path d="m295.988281 9.734375-286.613281 286.613281c-12.5 12.5-12.5 32.769532 0 45.25l15.082031 15.082032c12.503907 12.5 32.769531 12.5 45.25 0l286.632813-286.59375c12.503906-12.5 12.503906-32.765626 0-45.246094l-15.082032-15.082032c-12.5-12.523437-32.765624-12.523437-45.269531-.023437zm0 0"/></g></svg>`,
            board: [],
            rows : 3,
            columns : 3,
            turn : false,
            winner: null,
            icon:'',
            turn_msg:'',
            waiting:true,
            spectator :false,
            
        }
    },
    methods:{
        clicked(x,y){
            
            if(this.turn == true && !this.waiting){
                if(this.board[x][y] == '')
                {
                    this.board[x][y] = this.icon
                    this.socket.emit('index',this.board)
                    //this.check(x,y)
                    this.turn_changer()
                }
            }
                
        },

        turn_changer(){
            
            this.turn = !this.turn
        },
        board_initialize(){
            this.board= [
                ['','',''],
                ['','',''],
                ['','','']
            ]
    }
},
    mounted(){
        this.board_initialize();

        this.socket.on('hello',msg=>{
            console.log(msg)
        })

        this.socket.on('initialize',icon=>{
            this.icon = icon
        })

        this.socket.on('start',obj=>{
            this.turn  = obj.turn
            this.waiting = false
            this.board = obj.board
        })
        this.socket.on('index',board=>{
                this.board = board
                this.turn  = true    
        })

        this.socket.on('discon', ()=>{
            this.waiting = true
        })
    
    }
}
</script>

<style scoped>

.wrapper{
    display :grid;
    grid-template-columns: 2fr 3fr 2fr;
    grid-gap: 0;
    color:#3239A8;
}

.chat {
    grid-column:3;
    transform:translateY(-170px);
    margin-right:30px;
}
#app{ 
    
    grid-column:2;
    margin-left:auto;
    margin-right: auto;
    color:#3239A8;
    transform: translateY(-40vh);
}
.gameboard{
    position:relative;
}
.gameboard::before {content: ''; position:absolute; top:20px; left: 0; background-color:red; width:100%; height:2px; transform:rotate(45deg);transform-origin: left;}
.turn{
    padding-top:20px;
    font-size: 50px;
}
.score{
    font-size: 10vh;
    margin-top:5vh;
    padding:50px;
    padding-top: 0px;
    color:#3239A8
}
.vs{
    display:grid;
    grid-template-columns: 4fr 1fr 4fr;
    grid-template-rows:1fr;
    align-items:center;
    margin-left:2vw;
}
.VS{
    font-size: 50px;
    color:#3239A8
}

.table{
    margin-top:15vh;
    border-collapse: collapse;
    cursor:pointer;
}
.avatar1,.avatar2{
    border:3px solid #3239A8;
    margin-top:20px;
    width:60%;
    height:70%;
    margin-left:1vw;
    border-radius: 5%;
}
.avatar1{
    margin-left:3vw;

}
.avatar{
width:100%;
height:100%;  
}   
.name1{
    transform: translateX(1vw);
}
.name2{
    transform: translateX(-1vw);
}
.name1,.name2{
    color:#3239A8;
}

td{
    width: 150px;
    height: 150px;
    font-size:50px;
    border:10px solid #747d90;
}

.table > tr:nth-child(1) > td:nth-child(n) {
    border-top: 0px;
}
.table > tr:nth-child(3) > td:nth-child(n) {
    border-bottom:0px;
}
.table > tr:nth-child(3) > td:nth-child(n) {
    border-bottom:0px;
}
.table > tr:nth-child(n) > td:nth-child(1) {
    border-left:0px;
}
.table > tr:nth-child(n) > td:nth-child(3) {
    border-right:0px;
}



</style>