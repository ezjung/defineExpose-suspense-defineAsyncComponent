<script setup>
import { ref, reactive } from 'vue'


const props = defineProps({
  isBase: Boolean,
})

const emits = defineEmits([ 'close' ])

await new Promise((res) => setTimeout(res, 2000))

const trueOrFalse = ref(false)

const closeModal = () => {
    emits('close')
}


</script>

<template>
  <div class="modal">
    <div class="modal-content">
        <h1>Madal header</h1>
        <p>djjfk djflsdjl jfdlsj fj jflek qw jkfklja 2jd jjd ;klajd dyhwkc</p>
    </div>
    <button @click="closeModal">Close</button>
  </div>
</template>

<style scoped>
.modal {
    position: absolute;
    height: 100%;
    width: 100%;
    top:0;
    left:0;
    background-color: rgba((0,0,0,0.8), green, blue, alpha);
    display: flex;
    align-items: center;
    justify-content: center;
}

</style>