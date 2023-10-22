<script setup>
import { ref } from 'vue'

const email = ref('')
const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/

const isValidEmail = ref(true)
const isError = ref(false)
const emit = defineEmits(['emailRegistered'])

const validateEmail = () => {
  isValidEmail.value = emailRegex.test(email.value)
  if (!isValidEmail.value) {
    isError.value = true
  } else {
    isError.value = false
    emit('emailRegistered', email)
  }
}
</script>

<template>
  <section class="container">
    <article class="info">
      <h1 class="info-title">Stay updated!</h1>
      <p class="info-text">Join 60,000+ product managers receiving monthly updates on:</p>
      <ul class="info-detail">
        <li class="info-detail-item">
          <img class="info-detail-item-icon" src="../assets/images/icon-list.svg" alt="icon list" />
          Product discovery and building what matters
        </li>
        <li class="info-detail-item">
          <img class="info-detail-item-icon" src="../assets/images/icon-list.svg" alt="icon list" />
          Measuring to ensure updates are a success
        </li>
        <li class="info-detail-item">
          <img class="info-detail-item-icon" src="../assets/images/icon-list.svg" alt="icon list" />
          And much more!
        </li>
      </ul>
      <form action="#">
        <label for="email">Email address</label>
        <input type="email" name="email" id="email" :class="{ 'error-input': isError }"
          v-model="email" placeholder="email@company.com" />
        <span v-if="isValidEmail"></span>
        <span class="error-msg" v-else>Valid email required</span>
        <button type="submit" @click.prevent="validateEmail">Subscribe to monthly newsletter</button>
      </form>
    </article>
    <article class="image">
      <picture>
        <source media="(max-width: 860px)" srcset="../assets/images/illustration-sign-up-mobile.svg">
        <img src="../assets/images/illustration-sign-up-desktop.svg" alt="ilustration" />
      </picture>
    </article>
  </section>
</template>

<style scoped>
.container {
  width: 100%;
  max-width: 928px;
  height: 641px;
  display: flex;
  justify-content: space-between;
  position: relative;
  bottom: 1px;
  background-color: var(--white);
  color: var(--dark-slate-grey);
  border-radius: 2.2rem;
}

.info {
  width: 50%;
  padding: 5.75rem 0 6rem 4rem;
  display: flex;
  flex-direction: column;
  color: var(--charcoal-grey);
  transition: .3s;
}

.info-title {
  font-size: 3.5rem;
}

.info-text {
  margin-top: 1.2rem;
  line-height: 1.5rem;
}

.info-detail {
  margin-top: 1.6rem;
}

.info-detail-item {
  display: flex;
  align-items: center;
  list-style: none;
}

.info-detail-item:nth-child(2),
.info-detail-item:nth-child(3) {
  margin-top: 0.8rem;
}

.info-detail-item-icon {
  margin-right: 1rem;
}

form {
  display: flex;
  flex-direction: column;
  position: relative;
}

label {
  margin-top: 2.7rem;
  font-size: 0.75rem;
  font-weight: 700;
}

input {
  width: 376px;
  height: 56px;
  margin-top: 0.6rem;
  padding-left: 1.45rem;
  font-size: 1rem;
  color: var(--charcoal-grey);
  border: 1px solid lightgrey;
  border-radius: 8px;
  outline: none;
}

input:focus {
  border: 1px solid var(--dark-slate-grey);
}

input::placeholder {
  font-family: 'Roboto', sans-serif;
  font-size: 1rem;
  letter-spacing: -0.001rem;
  color: var(--grey);
}

.error-msg {
  position: absolute;
  right: 1.6rem;
  top: 2.7rem;
  font-size: 0.75rem;
  font-weight: 700;
  color: var(--tomato);
}

.error-input {
  color: var(--tomato);
  background-color: hsla(4, 100%, 67%, 0.2);
}

button {
  width: 376px;
  height: 56px;
  margin-top: 1.5rem;
  padding-top: 0.1rem;
  font-size: 0.99rem;
  letter-spacing: -0.003rem;
  color: var(--white);
  border-radius: 8px;
  border: none;
  background-color: hsl(234, 29%, 20%);
  cursor: pointer;
  position: relative;
}

button::before {
  content: 'Subscribe to monthly newsletter';
  position: absolute;
  top: 0;
  right: 0;
  width: 100%;
  height: 100%;
  padding-top: 0.1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 8px;
  background: linear-gradient(90deg, rgba(255, 83, 123, 1) 0%, rgba(255, 105, 58, 1) 100%);
  box-shadow: 0 10px 25px hsla(4, 100%, 67%, 0.4);
  opacity: 0;
  transition: opacity 0.3s;
}

button:hover::before {
  opacity: 1;
}
.image {
  display: flex;
  align-items: center;
  padding: 0.3rem 1.5rem 0 0;
}

@media screen and (max-width: 920px) {
  .info {
    padding-left: 2.2rem;
  }
}

@media screen and (max-width: 860px) {
  .container {
    width: 100vw;
    height: 100%;
    flex-direction: column;
    justify-content: flex-start;
    border-radius: 0;
  }
  .info {
    width: 100%;
    padding: 2rem;
  }
  
  input,
  button {
    width: 100%;
  }

  label {
    margin-left: 0;
  }
  .image {
    width: 100%;
    padding: 0;
    justify-content: center;
    order: -1;
  }
  .image picture {
    width: 100%;
  }
  .image picture img {
    width: 100%;
  }
  .error-msg {
    right: 0;
  }
}

@media screen and (max-width: 480px) {
  .info {
    padding: 1rem;
  }
  .info-title {
    font-size: 2.5rem;
  }
}
</style>
