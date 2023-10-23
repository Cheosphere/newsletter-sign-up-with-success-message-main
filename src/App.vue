<script setup>
import { ref } from 'vue'
import SignUp from './components/SignUp.vue'
import SuccessSubscribing from './components/successSubscribing.vue'

const email = ref('')

function emailReceived(data) {
  email.value = data
}
</script>

<template>
  <main class="wrapper" v-cloak>
    <Transition>
      <SuccessSubscribing v-if="email" :message="email" />
    </Transition>
    <SignUp v-if="!email" @emailRegistered="emailReceived" />
  </main>
</template>

<style scoped>
[v-cloak] {
  display: none;
}
.wrapper {
  width: 100%;
  height: 100%;
  background-color: var(--charcoal-grey);
  animation: fadein 1s ease-in-out; 
  box-shadow: 0 10px 50px rgba(0, 0, 0, 0.25);
}

@keyframes fadein {
    0% {
        opacity:0;
        transform: translateY(7rem);
    }
    100% {
        opacity:1;
    }
}

/* we will explain what these classes do next! */
.v-enter-active,
.v-leave-active {
  transition: 1s ease-in-out;
}

.v-enter-from,
.v-leave-to {
  transform: translateY(-100px);
  opacity: 0;
}
@media screen and (max-width: 860px) {
  .wrapper {
    height: 100vh;
    background-color: var(--white);
  }
}
</style>
