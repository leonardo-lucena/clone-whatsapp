<template>
   <div class="conversation-area">
    <Header/>

    <div class="card-area">
        <div class="card row items-center justify-between q-px-md"
        v-for="item in currentUsers" 
        :key="item"
        @click="seeConversation(item.id, item.email)"
        >
            <q-avatar size="40px" class="q-mr-sm">
                <q-img src="https://i.pravatar.cc/40"></q-img>
            </q-avatar>

            <div class="message column justify-around full-height q-pt-sm">
                <div class="row justify-between">
                    <div class="column">
                        <span>{{ item.name }}</span>
                        <span v-if="item.newMessage">Nova mensagem recebida</span>
                        <span v-else>Veja a nossa última conversa...</span>
                    </div>
                    <div class="column items-center justify-center">
                        <span>16:34</span>
                    </div>
                    <q-separator></q-separator>
                </div>
            </div>
        </div>
    </div>
   </div>
</template>
  
<script>
import { defineComponent } from 'vue'
import Header from './components/Header.vue'

export default defineComponent({
  name: 'ConversationArea',
  props: ['users'],
  components: {Header},
  data(){
    return {
        currentUsers: []
    }
  },
  methods:{
    seeConversation(id, email){
        this.$emit("selectedItem", {id, email})
    }
  },
  watch:{
    users(){
        this.currentUsers = this.users
    }
  },
  mounted(){
    this.currentUsers = this.users
  }
})
</script>
  
<style lang="scss" scoped>
.conversation-area {
    height: 100vh;
    width: 410px;
    background-color: #fff;
}

.card-area {
    height: calc(100vh - 118px);
    overflow: auto;
}

.card {
    background-color: #fff;
    height: 74px;
    &:hover {
        background-color: $grey-whats;
        cursor: pointer;
    }
}

.q-avatar {
    flex-grow: 0.1;
}

.message {
    flex-grow: 5;
    text-overflow: ellipsis;
    white-space: nowrap;
    overflow: hidden;
    width: 250px;

    span:first-child {
        font-size: 16px;
    };
    span:last-child {
        font-size: 12px;
        color: $sub-title-grey;
    }

}
</style> 