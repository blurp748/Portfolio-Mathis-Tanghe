<template>
  <div class="page">
    <div class="box-3">
      <div @click="show" class="btn btn-three">
        <span>Ouvrir mon CV</span>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  setup() {
    return {
      show() {
        window.open('https://api.tanghe.dev/cv');
      }
    };
  },
});
</script>

<style scoped>
.page {
  overflow: unset;
  width: 100vw;
  height: 100vh;
}

@media screen and (max-width: 720px) {
  .page {
    background-image: url("../assets/background_19.png");
    background-repeat: no-repeat;
    background-size: cover;
  }
}

@media screen and (min-width: 721px) {

}

div[class*=box] {
  height: 100%;
  width: 100%; 
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn {
  color: #FFF;
  transition: all 0.5s;
  position: relative;
  line-height: 50px;
  height: 50px;
  text-align: center;
  width: 250px;
  cursor: pointer;
}
.btn::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  background-color: rgba(255,255,255,0.1);
  transition: all 0.3s;
}
.btn:hover::before {
  opacity: 0 ;
  transform: scale(0.5,0.5);
}
.btn::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
  opacity: 0;
  transition: all 0.3s;
  border: 1px solid rgba(255,255,255,0.5);
  transform: scale(1.2,1.2);
}
.btn:hover::after {
  opacity: 1;
  transform: scale(1,1);
}
</style>
