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
    <div class = 'turn'> 
        TURN PLAYER 1
        </div>
    <div id = 'app'>
        <div class = 'gameboard'>
            <table class = 'table'>
                <tr v-bind:key=i v-for='(i,index) in rows'>
                    <td v-bind:key=j v-for='(j,jndex) in columns' @click="clicked(index,jndex,$event)" v-bind:class="smooth"></td>
                </tr>
            </table>
        </div>
    </div>
    <div class="chat">
        <div>
            Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ut dicta doloremque, animi laborum distinctio quam porro quia aliquid veniam saepe, qui iure laboriosam, aliquam fuga ipsam nihil assumenda eaque impedit consectetur at minima maxime error. Porro officiis quaerat placeat laborum? Libero nesciunt quas minus, illo esse quibusdam iusto placeat et minima possimus iste nobis ullam magni quia aperiam ab dolorum, necessitatibus nam repellendus? Qui iure optio dolores totam tenetur excepturi id eligendi, dignissimos itaque explicabo possimus, amet a autem laborum asperiores illo vel. Quibusdam nulla repellat sint amet dolore porro blanditiis dicta excepturi deleniti unde perspiciatis alias nam voluptas laudantium ipsa ipsum, voluptatem eveniet! Minima necessitatibus atque eius dignissimos culpa voluptas alias id quidem amet repellendus quia non veniam voluptates iure dolore, iusto inventore nostrum unde distinctio! Magnam, aliquid cum est facere provident placeat excepturi aperiam illo fuga quod, deserunt dolorum? Nesciunt iste non, soluta saepe voluptatem necessitatibus, cum sed illum autem nam est nostrum nulla minus commodi deserunt libero quaerat delectus pariatur temporibus distinctio ab! Dolore possimus optio dignissimos, animi omnis a quae deleniti, cupiditate natus, non voluptates voluptas voluptatem? Architecto rem excepturi, iure quod illum libero tempora animi aspernatur in consequuntur eligendi provident enim pariatur minus ad numquam voluptates cum est. Mollitia, officiis fugiat voluptatem natus quos autem minus vitae quia? Nulla nesciunt quibusdam consectetur natus magni facere perspiciatis veniam animi tenetur nobis odit omnis debitis sequi repudiandae molestias, reprehenderit aut beatae commodi. Error minima ex quibusdam inventore et, laboriosam molestiae consectetur provident culpa sunt amet? Nobis repellendus rem doloremque temporibus harum magnam ad, sed minima neque ratione deleniti libero unde recusandae accusantium molestias quae mollitia aliquam nisi fuga eligendi ex. Ullam, itaque illo. Obcaecati aliquid dignissimos consequuntur veniam? Sapiente explicabo dicta obcaecati velit debitis animi blanditiis! Eligendi, quibusdam doloremque temporibus error eum laudantium reiciendis ad, ratione accusantium ut pariatur ipsum eveniet in repellat libero debitis quidem velit cum veniam iure deserunt atque tempora quisquam! Commodi fugiat, doloremque laudantium optio aliquam voluptates, placeat culpa eum tempore dignissimos laboriosam obcaecati amet, ab ratione blanditiis provident. Amet ad dignissimos ipsa? Odit explicabo dolore tempore perferendis, corrupti, incidunt sed voluptatibus repellendus aliquid adipisci laudantium nemo obcaecati maxime laborum odio laboriosam est a voluptatum voluptate neque ea eveniet. Nulla, doloremque soluta nam at nostrum maxime in accusamus repudiandae similique ad. Repudiandae magni adipisci facilis. Voluptatum modi quibusdam saepe aliquid laudantium, fugit enim, iste minus quo necessitatibus temporibus veritatis eligendi animi? Quas eius dolor voluptates perferendis nobis iusto ducimus repudiandae officiis consequuntur vero! Debitis rem a quaerat tenetur reprehenderit earum molestias expedita consectetur assumenda neque, perferendis natus asperiores. Iusto repellendus voluptates error? Quaerat laudantium provident saepe modi dolorem, excepturi tempore facilis, porro quas cupiditate beatae! Et officiis sit nam. Dolores quaerat rerum incidunt, voluptatem obcaecati quidem natus. Ullam, eius neque! Aliquid quia aspernatur excepturi assumenda dignissimos alias repellendus officia facere eius sint, cupiditate ex rem obcaecati aliquam expedita, exercitationem id itaque incidunt vero aut aperiam laborum. Tempora animi maxime quam sapiente quos ut, enim itaque modi ipsa ex voluptatem velit maiores illo voluptas doloremque porro ullam! Quo dolor aliquid, numquam aliquam nisi ducimus error officia atque at cupiditate facilis adipisci praesentium assumenda vitae ex doloribus possimus! Laborum perspiciatis ad quibusdam est fugit unde velit facilis praesentium? Quaerat, porro voluptatum? Harum libero saepe aliquam dolor repellat aliquid quaerat vel corrupti velit laborum culpa placeat quis alias fuga voluptates sequi eos voluptatibus, amet magni. Veritatis repellat nobis ducimus ipsa rem non hic sequi, minus, veniam obcaecati inventore dicta natus dolore soluta esse sapiente qui nesciunt eum sit praesentium fugit maxime minima? Vel eveniet, eligendi saepe nostrum omnis pariatur fuga quam sit sunt nisi reiciendis repellat voluptatibus, praesentium labore expedita porro nesciunt, rerum odit neque consectetur rem commodi ipsam aliquam necessitatibus. Omnis quae odio quisquam facilis cupiditate nam vel quis cumque ea harum? Voluptatum ipsum beatae aspernatur. Cum labore, nulla eaque rem et tenetur sit expedita accusamus officia atque eius porro officiis possimus eveniet, libero ad nemo at dolorem sapiente provident. Illum magni, cumque veritatis exercitationem at ea facilis tempore ut, soluta ratione voluptatibus sint culpa est aliquid earum tenetur deserunt ad laborum rem! Voluptate illo consequuntur laboriosam sapiente commodi cum, omnis perspiciatis nemo ullam harum incidunt. Aut praesentium illum quisquam dicta voluptate. Temporibus nisi saepe ut dicta sed similique ea sapiente eius perspiciatis laborum. Consequatur fugiat sint illum error assumenda molestiae alias culpa doloremque quia reprehenderit doloribus saepe quis tempore maiores placeat praesentium quos commodi, nulla voluptas? Voluptates possimus delectus unde? Necessitatibus iste voluptatem cupiditate eos ex animi repudiandae blanditiis sunt porro nesciunt voluptatum nostrum ut voluptate numquam culpa repellendus, nobis exercitationem accusantium harum cumque. Quibusdam aut ducimus ipsa ut praesentium corrupti, dicta provident ipsum fuga numquam saepe iste. Sapiente illum tempore aut dolorem, eaque delectus cumque, ipsum fuga eius natus ab voluptate repellendus magni neque, sequi quasi possimus impedit cupiditate excepturi? Beatae veniam excepturi reiciendis laboriosam, praesentium vitae tempora, magni veritatis itaque ducimus mollitia voluptas! Laudantium deserunt perferendis voluptas necessitatibus porro dignissimos architecto vitae, ducimus ullam non dolorem tempore doloribus minima earum, odio excepturi assumenda libero ab nisi? Iusto consequatur veritatis omnis minus ut, eius autem amet. Porro dolorem amet temporibus quae harum maxime nulla animi, ratione aliquam tempore, explicabo labore ab facilis aut, illum alias tempora pariatur mollitia quo veniam voluptatum nemo. Atque ab explicabo voluptatem cum laborum animi amet facere culpa reprehenderit quod provident repudiandae repellendus eos nam enim nesciunt quis ex, incidunt temporibus eaque rem tempore nulla numquam earum! Error quas obcaecati voluptatem sapiente. Voluptatibus ipsum soluta corporis ab culpa ipsa perspiciatis adipisci, tenetur optio mollitia vero fugiat ducimus dolores et beatae nobis magnam, voluptate, aliquid unde repudiandae dolorum nesciunt reiciendis velit magni? Sapiente earum reprehenderit repudiandae facilis ipsa hic nisi deserunt deleniti id. Delectus minus vitae dolorum illum quis adipisci dicta aut, iure et quasi rem qui! Quam possimus, consequatur iusto nam architecto distinctio nostrum numquam laudantium expedita amet rerum dolor deleniti officiis, accusantium sapiente porro eveniet, ratione provident at ut! Porro, odit voluptate? Adipisci assumenda qui eveniet excepturi velit non iure tempore eum porro perferendis voluptate necessitatibus, aperiam repellat.
        </div>
        <div>
            hi
        </div>
    </div>
</div>
    
</template>

<script>
export default {
    name:'Game',
    data(){
        return{
            show : false,
            oval : `<svg id="Capa_1" height="100pt" viewBox="0 0 515.556 515.556" width="100pt" xmlns="http://www.w3.org/2000/svg"><path d="m257.778 515.556c-142.137 0-257.778-115.642-257.778-257.778s115.641-257.778 257.778-257.778 257.778 115.641 257.778 257.778-115.642 257.778-257.778 257.778zm0-451.112c-106.61 0-193.333 86.723-193.333 193.333s86.723 193.333 193.333 193.333 193.333-86.723 193.333-193.333-86.723-193.333-193.333-193.333z"/></svg>`,
            cross: `<svg height="120pt" viewBox="0 0 365.71733 365" width="120pt" xmlns="http://www.w3.org/2000/svg"><g fill="#f44336"><path d="m356.339844 296.347656-286.613282-286.613281c-12.5-12.5-32.765624-12.5-45.246093 0l-15.105469 15.082031c-12.5 12.503906-12.5 32.769532 0 45.25l286.613281 286.613282c12.503907 12.5 32.769531 12.5 45.25 0l15.082031-15.082032c12.523438-12.480468 12.523438-32.75.019532-45.25zm0 0"/><path d="m295.988281 9.734375-286.613281 286.613281c-12.5 12.5-12.5 32.769532 0 45.25l15.082031 15.082032c12.503907 12.5 32.769531 12.5 45.25 0l286.632813-286.59375c12.503906-12.5 12.503906-32.765626 0-45.246094l-15.082032-15.082032c-12.5-12.523437-32.765624-12.523437-45.269531-.023437zm0 0"/></g></svg>`,
            board: [],
            rows : 3,
            columns : 3,
            turn : false,
            winner: null,
            smooth:'smooth'
        }
    },
    methods:{
        clicked(x,y,e){
            console.log(this.board[x][y])
            if(this.board[x][y] === ''){
                if(this.turn){
                    this.board[x][y] = 'o'
                    e.target.innerHTML = this.board[x][y]
                   
                    //this.check(x,y)
                }
                else{
                    this.board[x][y] = 'x'
                    e.target.innerHTML = this.board[x][y]
                    
                    //this.check(x,y)
                }
                this.turn_changer()
            }
            else {
                return 
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
        
    }
    
}
</script>

<style scoped>

.wrapper{
    display :grid;
    grid-template-columns: 2fr 3fr 2fr;
    grid-gap: 1vw;
    color:#3239A8;
}

.chat {
    grid-column:3;
    padding:0px;
    border:5px solid black;
    border-radius:3%;
    overflow: scroll;
    margin-top:-60%;
    width: 500px;
    height:500px;
}
.chat > div{
text-align:left;
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