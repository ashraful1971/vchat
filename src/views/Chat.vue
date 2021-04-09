<template>
  <div class="chat">
    <div class="sidebar">
      <ChatItem @itemClick="changeMe" />
      <ChatItem @itemClick="changeMe" />
      <ChatItem @itemClick="changeMe" />
      <ChatItem @itemClick="changeMe" />
    </div>
    <div class="chat-window">
      <div class="msg-history">
        <MessageItem v-for="(item, i) in msg_list" :side="item.me ? 2 : 1" :key="i">{{item.msg}}</MessageItem>
      </div>
      <div class="msg-box">
        <textarea rows="2" cols="2" v-model="new_msg" @keyup.enter="sendMsg" placeholder="Type..."></textarea>
      </div>
    </div>
  </div>
</template>

<script>
  import ChatItem from '@/components/ChatItem.vue'
  import MessageItem from '@/components/MessageItem.vue'
  export default {
    name: 'Chat',
    components: {ChatItem, MessageItem},
    data(){
      return {
        msg_list: [
          {uid: 0, me: true, msg: "How are you?"},
          {uid: 1, me: false, msg: "I'm fine and you?"},
        ],
        new_msg: '',
        me: true
      }
    },
    methods: {
      sendMsg(){
        this.msg_list.push({uid: 1, me: this.me, msg: this.new_msg});
        this.new_msg = "";
      },
      changeMe(){
        this.me = !this.me;
      }
    }
  }
</script>

<style scoped>
  .chat {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    border-top: 1px solid rgba(204, 204, 204, 0.349);
  }
  .chat .sidebar {
    width: 30%;
    min-height: 100vh;
    background-color: #fff;
  }
  .chat .chat-window {
    width: 70%;
    height: 100vh;
    background-color: #ccc;
    overflow: hidden;
  }
  .msg-history {
    overflow-y: scroll;
    height: 100%;
  }
  .msg-box {
    padding: 20px;
    background-color: #fff;
    position: fixed;
    right: 0;
    bottom: 0;
    width: 100%;
    border-top: 1px solid rgba(204, 204, 204, 0.349);
    width: 70%;
    box-sizing: border-box;
    overflow: hidden;
  }
  .msg-box textarea {
    width: 100%;
    border: 2px solid #ccc;
    padding: 20px;
    box-sizing: border-box;
    overflow: hidden;
  }
  .msg-box textarea::placeholder {
    font-family: Arial, Helvetica, sans-serif;
    font-size: 18px;
    color: #777;
  }
</style>
