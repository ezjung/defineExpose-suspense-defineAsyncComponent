<script setup>
import { ref, computed, defineAsyncComponent } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
// import BaseModal from './components/BaseModal.vue'

const helloWorldRef = ref(null)
const version = computed(() => helloWorldRef.value?.version)
// When import property, Make sure to use optional chaining (or a null-check) on helloWorldRef.value, as it's initially null:
// const version = computed(() => helloWorldRef.value.version)

const arg = "This is parent Args"
// Even you can trigger the function of child component from parent
const sayHello = computed(() => helloWorldRef.value.sayHello)




// Examples for defineAsyncComponent

const isModal = ref(null)

// const HelloWorld = defineAsyncComponent(() => import('./components/HelloWorld.vue'))
const BaseModal = defineAsyncComponent(() => import('./components/BaseModal.vue'))

const closeModal = () => isModal.value = false

</script>

<template>

 <button @click="sayHello(arg)">Change to Hello</button>

 <HelloWorld ref="helloWorldRef" />

 <h1>version:{{ version }}</h1>


 <!-- <BaseModal v-if="isModal" /> -->


 <suspense v-if="isModal">

  <template #default>
    <BaseModal :isBase="isModal" @close="closeModal" />
   </template>

   <template #fallback>
    <p>Loading...</p>
   </template>

 </suspense>



 <button @click="isModal=true">Open Modal</button>


</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
