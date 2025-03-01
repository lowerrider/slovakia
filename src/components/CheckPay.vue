<template>
  <div class="checkpay-container">
    <div class="first-container">
      <div class="content-wrapper">
        <div class="first-container-left">
          <h3>Проверка права на выплату</h3>
          <h4 style="margin-top: 14px">
            Для того чтобы определить, относитесь ли вы к категории получателей
            государственной поддержки, пожалуйста, заполните короткую форму.
          </h4>
        </div>
        <div class="first-container-right">
          <img
            style="width: 100%; height: auto"
            src="../assets/images/garanty.png"
            alt="" />
        </div>
      </div>
    </div>

    <div class="second_container">
      <div class="content-wrapper">
        <div class="second_container-left">
          <h3 style="color: #003078">Ваши данные нужны для:</h3>
          <li>Проверки соответствия критериям программы.</li>
          <li>
            Обеспечения прозрачности и справедливости распределения средств.
          </li>
          <li>Быстрого и точного расчета вашей выплаты.</li>
        </div>
        <div class="second_container-right">
          <h3 style="color: #003078">Мы гарантируем:</h3>
          <li>Полную конфиденциальность ваших данных.</li>
          <li>Использование информации исключительно в рамках программы.</li>
          <li>Соответствие всем нормам законодательства Словакии</li>
        </div>
      </div>
    </div>

    <div class="form-container">
      <div class="content-wrapper-form">
        <div class="goForm">
          <h4 style="color: white; font-size: 1.5rem; margin: 0">
            Заполните форму ниже:
          </h4>
        </div>
        <input
          v-model="name"
          :class="{ 'error-input': !name && formSubmitted }"
          class="nameInput"
          placeholder="ФИО"
          type="text" />
        <div class="gender-selector-container">
          <div
            class="gender-selector"
            :class="{
              active: selectedGender === 'male',
              'error-input': !selectedGender && formSubmitted,
            }"
            @click="selectGender('male')">
            Мужской
          </div>
          <div
            class="gender-selector"
            :class="{
              active: selectedGender === 'female',
              'error-input': !selectedGender && formSubmitted,
            }"
            @click="selectGender('female')">
            Женский
          </div>
        </div>
        <div
          v-if="formSubmitted && (!name || !selectedGender)"
          class="error-message">
          Пожалуйста, заполните все поля.
        </div>
        <button @click="handleSubmit" class="buttonDiv-button">
          Продолжить
        </button>
        <div class="icon-button">
          <img style="width: 50px" src="../assets/images/Group.png" alt="" />
          <h4 class="icon-button-text">
            Ваши данные в безопасности. Мы соблюдаем GDPR и гарантируем защиту
            вашей личной информации.
          </h4>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CheckPay",
  data() {
    return {
      name: "",
      selectedGender: null,
      formSubmitted: false,
    };
  },
  methods: {
    selectGender(gender) {
      this.selectedGender = gender;
    },
    handleSubmit() {
      this.formSubmitted = true;

      if (this.name && this.selectedGender) {
        this.$emit("showOpros");
      }
    },
  },
};
</script>

<style scoped>
.content-wrapper {
  display: flex;
  max-width: 1024px;
  margin: 0 auto;
  width: 100%;
}

.content-wrapper-form {
  max-width: 1024px;
  margin: 0 auto;
  width: 100%;
}

.first-container {
  background-color: #f3f2f1;
  padding: 2rem 4rem;
  width: 100%;
  display: flex;
  align-items: center;
}

.second_container {
  background-color: white;
  padding: 4rem;
  display: flex;
  width: 100%;
}

.first-container-left {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 50%;
  margin-right: 20px;
}

.first-container-right {
  width: 50%;
}

.error-input {
  border: 2px solid red;
  box-shadow: 0 0 5px rgba(255, 0, 0, 0.5);
}

.error-message {
  text-align: center;
  color: red;
  font-size: 1.2rem;
  margin-top: 1rem;
}

.gender-selector-container {
  display: flex;
  justify-content: space-between;
  gap: 1rem;
}

.buttonDiv-button {
  margin-top: 2rem;
  background-color: #00703c;
  color: white;
  width: 100%;
  height: 4rem;
  outline: none;
}

.gender-selector.active {
  border: 2px solid black;
}

.gender-selector {
  margin-top: 2rem;
  background-color: rgba(0, 0, 0, 0.03);
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 1.6rem;
  height: 3rem;
  line-height: 3rem;
  text-align: center;
  width: 48%;
  border: none;
  outline: none;
}

.nameInput {
  border: none;
  padding: 0 0 0 20px;
  background-color: rgba(0, 0, 0, 0.03);
  margin-top: 1rem;
  height: 3rem;
  width: 100%;
  outline: none;
}

.goForm {
  width: 100%;
  background-color: rgba(0, 48, 120, 1);
  text-align: center;
  margin-top: 30px;
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.icon-button {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
  color: rgba(140, 140, 140, 1);
}

.icon-button-text {
  font-size: 18px;
  margin-top: 10px;
}

@media screen and (max-width: 720px) {
  .first-container {
    padding: 1rem;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
  }

  .form-container {
    padding: 0 20px;
  }

  .first-container {
    padding: 0 20px;
  }

  .content-wrapper {
    flex-direction: column;
  }

  .first-container-left {
    width: 100%;
  }

  .first-container-right {
    width: 100%;
    margin-top: 20px;
    margin-bottom: 20px;
  }

  .first-container-right img {
    max-width: 100%;
    height: auto;
  }

  h3 {
    font-size: 2rem;
  }

  h4 {
    font-size: 1.2rem;
    margin-top: 1rem;
  }

  .gender-selector-container {
    flex-direction: column;
    align-items: center;
  }

  .gender-selector {
    width: 100%;
    margin-top: 1rem;
    font-size: 1.4rem;
  }

  .nameInput {
    font-size: 1.4rem;
  }

  .buttonDiv-button {
    height: 50px;
  }

  .icon-button {
    margin-top: 10px;
  }

  .icon-button-text {
    font-size: 1rem;
  }

  .second_container {
    padding: 2rem;
    flex-direction: column;
    align-items: center;
  }

  .second_container-left,
  .second_container-right {
    width: 100%;
    margin-bottom: 1.5rem;
  }

  h3 {
    font-size: 1.8rem;
  }

  li {
    font-size: 1rem;
  }
}
</style>
