<template>
  <div class="checkdata-container">
    <div v-if="!isFinished">
      <div class="content-wrapper">
        <img class="loader" src="../assets/images/louder.png" alt="Loading" />
      </div>
      <div class="info-box">
        <div class="content-wrapper">
          <h4>Подождите, проверяем данные.</h4>
          <h4>Это может занять от 1 до 30 минут</h4>
        </div>
      </div>
    </div>

    <div v-else>
      <Congratulations />
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import Congratulations from "./Congratulations.vue";

export default {
  name: "CheckData",
  components: {
    Congratulations,
  },
  setup() {
    const isFinished = ref(false);

    onMounted(() => {
      setTimeout(() => {
        isFinished.value = true;
      }, 20000);
    });

    return {
      isFinished,
    };
  },
};
</script>

<style scoped>
.info-box {
  margin-top: 20px;
  color: white;
  padding: 2rem;
  background-color: rgba(0, 48, 120, 1);
}

.content-wrapper {
  max-width: 1024px;
  margin: 0 auto;
  width: 100%;
  text-align: center;
}

.checkdata-container {
  background-color: rgba(243, 242, 241, 1);
  padding: 50px 0;
}

.loader {
  animation: spin 5s linear infinite;
  margin: 0 auto;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.checkdata-container h3 {
  font-size: 2rem;
  font-weight: bold;
  margin-bottom: 20px;
}

.checkdata-container p {
  font-size: 1.6rem;
  color: #333;
  margin-top: 10px;
}
</style>
