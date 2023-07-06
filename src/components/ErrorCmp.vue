<script>
export default {
  props: {
    errorData: {
      type: Object,
      required: true
    }
  }
}
</script>

<template>
  <div class="container mx-auto">
    <div class="card">
      <div class="flex flex-col items-center text-center my-5 px-4">
        <h3 class="lg:text-xl text-lg dark:text-slate-300 font-semibold">{{ errorData.title }}</h3>
        <h4 class="lg:text-xl text-lg dark:text-slate-300 font-medium">{{ errorData.message }}</h4>
      </div>
      <img src="../assets/blank.svg" alt="not found image" class="mx-auto" />
    </div>
  </div>
</template>

<style>
.container {
  width: 90%;
  background: transparent;
  position: relative;
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.438);
  overflow: hidden;
  border-radius: 10px;
}

 .card {
  cursor: default;
  width: 100%;
  height: 100%;
  position: relative;
  z-index: 2;
  background-color: rgba(255, 255, 255, 0.074);
  border: 1px solid rgba(255, 255, 255, 0.222);
  -webkit-backdrop-filter: blur(20px);
  backdrop-filter: blur(20px);
  border-radius: 10px;
  transition: all ease 0.3s;
}

.container::after,
.container::before {
  width: 100px;
  height: 100px;
  content: '';
  position: absolute;
  border-radius: 50%;
  transition: 0.5s linear;
}

.container::after {
  top: -20px;
  left: -20px;
  background-color: rgba(125, 214, 66, 0.603);
  animation: animFirst 5s linear infinite;
}

.container::before {
  background-color: rgb(226, 223, 54);
  top: 70%;
  left: 70%;
  animation: animSecond 5s linear infinite;
  animation-delay: 3s;
}

.container:hover {
  box-shadow: 0px 0px 10px rgba(0, 77, 32, 0.432);
}

.container:hover::after {
  left: 80px;
  transform: scale(1.2);
}

.container:hover::before {
  left: -10px;
  transform: scale(1.2);
} 
</style>
