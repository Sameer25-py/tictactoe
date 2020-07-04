<template>
  <div class="wrapper">
    <div class="scoreboard">
      <h2 class="score">Score</h2>
      <div class="vs">
        <div class="avatar avatar1">
          <img src="../assets/sam.jpg" class="avatar__image" />
          <div class="name">Sameer</div>
        </div>
        <div class="VS">VS</div>
        <div class="avatar avatar2">
          <img src="../assets/azhan.jpg" class="avatar__image" />
          <div class="name">Muhammad Azhan</div>
        </div>
      </div>
      <!--empty div -->
    </div>

    <div class="app">
      <div class="game-status">
        <div class="turn" v-if="waiting">waiting for Opponent</div>
        <div class="turn" v-if="turn && !waiting">Your Turn</div>
        <div class="turn" v-else-if="!turn && !waiting">Opponent Turn</div>
      </div>
      <div class="gameboard">
        <div class="table">
          <div class="row" v-bind:key="index" v-for="(i,index) in board">
            <div
              class="cell"
              v-bind:key="jndex"
              v-for="(j,jndex) in i"
              @click="clicked(index,jndex)"
            >
              {{j}}
              <div class="cell__border border--top"></div>
              <div class="cell__border border--lft"></div>
              <div class="cell__border border--rht"></div>
              <div class="cell__border border--btm"></div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="chat">
      <Chat :socket="socket" />
    </div>
  </div>
</template>

<script>
import Chat from "./Chat.vue";
import io from "socket.io-client";
export default {
  name: "Game",
  components: {
    Chat: Chat
  },
  data() {
    return {
      socket: io.connect("http://localhost:9000/player"),
      oval: `<svg id="Capa_1" height="100pt" viewBox="0 0 515.556 515.556" width="100pt" xmlns="http://www.w3.org/2000/svg"><path d="m257.778 515.556c-142.137 0-257.778-115.642-257.778-257.778s115.641-257.778 257.778-257.778 257.778 115.641 257.778 257.778-115.642 257.778-257.778 257.778zm0-451.112c-106.61 0-193.333 86.723-193.333 193.333s86.723 193.333 193.333 193.333 193.333-86.723 193.333-193.333-86.723-193.333-193.333-193.333z"/></svg>`,
      cross: `<svg height="120pt" viewBox="0 0 365.71733 365" width="120pt" xmlns="http://www.w3.org/2000/svg"><g fill="#f44336"><path d="m356.339844 296.347656-286.613282-286.613281c-12.5-12.5-32.765624-12.5-45.246093 0l-15.105469 15.082031c-12.5 12.503906-12.5 32.769532 0 45.25l286.613281 286.613282c12.503907 12.5 32.769531 12.5 45.25 0l15.082031-15.082032c12.523438-12.480468 12.523438-32.75.019532-45.25zm0 0"/><path d="m295.988281 9.734375-286.613281 286.613281c-12.5 12.5-12.5 32.769532 0 45.25l15.082031 15.082032c12.503907 12.5 32.769531 12.5 45.25 0l286.632813-286.59375c12.503906-12.5 12.503906-32.765626 0-45.246094l-15.082032-15.082032c-12.5-12.523437-32.765624-12.523437-45.269531-.023437zm0 0"/></g></svg>`,
      board: [],
      rows: 3,
      columns: 3,
      turn: false,
      winner: null,
      icon: "",
      turn_msg: "",
      waiting: true,
      spectator: false
    };
  },
  methods: {
    clicked(x, y) {
      if (this.turn == true && !this.waiting) {
        if (this.board[x][y] == "") {
          this.board[x][y] = this.icon;
          this.socket.emit("index", this.board);
          //this.check(x,y)
          this.turn_changer();
        }
      }
    },

    turn_changer() {
      this.turn = !this.turn;
    },
    board_initialize() {
      this.board = [
        ["", "", ""],
        ["", "", ""],
        ["", "", ""]
      ];
    }
  },
  mounted() {
    this.board_initialize();

    this.socket.on("hello", obj => {
      console.log(obj.msg);
      this.board = obj.board;
    });

    this.socket.on("initialize", icon => {
      this.icon = icon;
    });

    this.socket.on("start", obj => {
      this.turn = obj.turn;
      this.waiting = false;
      this.board = obj.board;
    });
    this.socket.on("index", board => {
      this.board = board;
      this.turn = true;
    });

    this.socket.on("discon", () => {
      this.waiting = true;
    });
  }
};
</script>

<style scoped>
.wrapper {
  display: grid;
  grid-template-columns: 1fr;
  grid-gap: 0;
  color: #3239a8;
  max-width: 310px;
  margin: 0 auto;
}

.chat {
  display: none;
}

.app {
  margin: 0;
  color: #3239a8;
}

.game-status {
  color: #777;
}

.table {
  display: flex;
  align-items: center;
  justify-content: center;
}

.cell {
  position: relative;
  margin: 2px;
  width: 80px;
  height: 80px;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
  border: 1px solid #999;
}

.cell:hover {
  animation: beat 0.7s linear infinite;
  box-shadow: 2px 7px 32px rgba(0, 0, 0, 0.1);
  background-color: white;
}

.cell__border {
  position: absolute;
  transition: transform 0.1s ease-in-out;
  background-color: #344;
}

.border--btm,
.border--top {
  width: 100%;
  height: 2px;
  transform: scaleX(0);
}

.border--btm {
  bottom: 0;
  left: 0;
  transform-origin: right;
}

.border--rht,
.border--lft {
  width: 2px;
  height: 100%;
  transform: scaleY(0);
}

.border--rht {
  top: 0;
  right: 0;
  transition-delay: 0.1s;
  transform-origin: top;
}

.border--top {
  top: 0;
  right: 0;
  transition-delay: 0.2s;
  transform-origin: left;
}

.border--lft {
  bottom: 0;
  left: 0;
  transform-origin: bottom;
  transition-delay: 0.3s;
}

.cell:hover .cell__border {
  transform: scale(1);
}

.cell:hover .border--lft {
  transform-origin: top;
}

.cell:hover .border--top {
  transform-origin: right;
}

.cell:hover .border--rht {
  transform-origin: bottom;
}

.cell:hover .border--btm {
  transform-origin: left;
}

.turn,
.score {
  margin: 1rem 0;
}

.turn {
  font-size: 1.5rem;
}
.score {
  font-size: 1.5rem;
  color: #344;
}
.vs {
  margin: 1rem 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.VS {
  font-size: 2rem;
  color: #344;
}

.name {
  color: #344;
}

.avatar__image {
  max-width: 60px;
  height: auto;
  border-radius: 50%;
  margin-bottom: 0.5rem;
  box-shadow: 3px 3px 12px rgba(0, 0, 0, 0.1);
}

@media screen and (min-width: 576px) {
  .wrapper {
    max-width: 540px;
  }
  .cell {
    width: 120px;
    height: 120px;
  }
  .avatar__image {
    max-width: 120px;
  }
}

@media screen and (min-width: 768px) {
  .wrapper {
    max-width: 760px;
  }
  .vs {
    justify-content: center;
  }
  .VS {
    margin: 0 3rem;
  }
}

@media screen and (min-width: 1024px) {
  .wrapper {
    max-width: 996px;
  }
}

@keyframes beat {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
  to {
    transform: scale(1);
  }
}
</style>