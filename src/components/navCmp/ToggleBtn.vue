<script setup>
import { useDark } from '@vueuse/core'

const isDark = useDark()
</script>

<template>
  <div class="toggle-switch">
    <label class="switch-label">
      <input type="checkbox" class="checkbox" v-model="isDark" />
      <span class="slider"></span>
    </label>
  </div>
</template>

<style>
.toggle-switch {
  position: relative;
  width: 100px;
  height: 50px;
  --light: #d8dbe0;
  --dark: #28292c;
  --link: rgb(27, 129, 112);
  --link-hover: rgb(24, 94, 82);
}

.switch-label {
  position: absolute;
  width: 100%;
  height: 50px;
  background-color: var(--dark);
  border-radius: 25px;
  cursor: pointer;
  border: 3px solid var(--dark);
}

.checkbox {
  position: absolute;
  display: none;
}

.slider {
  position: absolute;
  width: 100%;
  height: 100%;
  border-radius: 25px;
  -webkit-transition: 0.3s;
  transition: 0.3s;
}

.checkbox:checked ~ .slider {
  background-color: var(--light);
}

.slider::before {
  content: '';
  position: absolute;
  top: 10px;
  left: 10px;
  width: 25px;
  height: 25px;
  border-radius: 50%;
  -webkit-box-shadow: inset 12px -4px 0px 0px var(--light);
  box-shadow: inset 12px -4px 0px 0px var(--light);
  background-color: var(--dark);
  -webkit-transition: 0.3s;
  transition: 0.3s;
}

.checkbox:checked ~ .slider::before {
  -webkit-transform: translateX(50px);
  -ms-transform: translateX(50px);
  transform: translateX(50px);
  background-color: var(--dark);
  -webkit-box-shadow: none;
  box-shadow: none;
}

@media (max-width: 680px) {
  .toggle-switch {
    width: 85px;
    height: 40px;
  }

  .switch-label {
    height: 40px;
  }

  .slider::before {
    top: 8px;
    left: 5px;
    width: 20px;
    height: 20px;
    border-radius: 50%;
  }

  .checkbox:checked ~ .slider::before {
    -webkit-transform: translateX(48px);
    -ms-transform: translateX(48px);
    transform: translateX(48px);
  }
}
</style>
