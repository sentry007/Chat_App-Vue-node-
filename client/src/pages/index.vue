<template>
  <VContainer>
    <VForm @submit.prevent="onSubmit">
      <VCard max-width="600" class="mx-auto pa-5">
        <VCardTitle>
          <div class="d-flex align-center justify-center">
            <VIcon icon="mdi-chat" />
            <h3 class="ml-2">Chatapp</h3>
          </div>
        </VCardTitle>
        <VCardText class="py-4">
          <VTextField label="Username" v-model="state.username"></VTextField>
          <VSelect :items="rooms" label="Room" v-model="state.room"></VSelect>
        </VCardText>
        <VCardActions>
          <VBtn
            block
            color="primary"
            :disabled="!state.username || !state.room"
            variant="outlined"
            type="submit"
          >
            Join Chatapp
          </VBtn>
        </VCardActions>
      </VCard>
    </VForm>
  </VContainer>
</template>

<script lang="ts" setup>

import { reactive } from 'vue';
import { useRouter } from 'vue-router';
const router = useRouter();
const rooms = ['Room1', 'Room2', 'Room3', 'Room4'];
const state = reactive({
  username: '',
  room: rooms[0],
});
const onSubmit = () => {
  console.log(state.username);
  console.log('[SUBMIT]');
  router.push(`/chat?username=${state.username}&room=${state.room}`);
};



  //
  // import { ref,onMounted,onBeforeUnmount } from "vue";
  // import {io, type Socket} from "socket.io-client";

  // const socket= ref<Socket>();

  // onMounted(()=>{
  //   socket.value=io('http://localhost:3001/')
  // })

  // onBeforeUnmount(()=>{
  //   console.log("Disconnected");
  //   socket.value?.disconnected();
    
  // })
</script>
