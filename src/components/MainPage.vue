<template>
  <div class="body">
    <div class="text-container-first">
      <div class="content-wrapper">
        <div class="text-container-first-left">
          <h3 class="text-container-first-title">
            Ваш шанс получить выплату от государства!
          </h3>
          <h4 style="font-weight: 400" class="text-container-first-subTitle">
            Правительство Словакии выделило 989 миллионов евро для поддержки
            граждан в рамках новой государственной программы. Эти средства
            предназначены для тех, кто соответствует определенным критериям.
            Возможно, вы тоже имеете право на выплату!
          </h4>
        </div>
        <div class="text-container-first-right">
          <img
            class="text-container-first-right-image"
            src="../assets/images/image-right.png"
            alt="" />
        </div>
      </div>
    </div>
    <div class="content-wrapper">
      <div class="devider"></div>
    </div>

    <div class="subDiv">
      <div class="content-wrapper">
        <div class="subDiv-left">
          <h3 class="subDiv-left-title">Почему это важно</h3>
          <h4 style="font-weight: 300" class="subDiv-left-subtitle">
            В сложившейся экономической ситуации государство стремится
            поддержать своих граждан. Независимо от того, нуждаетесь ли вы в
            помощи для покрытия текущих расходов или просто хотите улучшить свое
            финансовое положение, эта программа может стать для вас отличной
            возможностью.
          </h4>
        </div>

        <div class="subDiv-right">
          <div>
            <h3 class="subDiv-left-title">Как это работает?</h3>
            <h4
              style="font-weight: 300; margin-bottom: 20px"
              class="subDiv-left-subtitle">
              Пройдите короткий опрос, чтобы проверить, относитесь ли вы к
              категории получателей.
            </h4>
          </div>
          <button @click="$emit('showCheckPay')" class="subDiv-right-button">
            Узнайте, имеете ли вы право на выплату
          </button>
        </div>
      </div>
    </div>

    <div class="buttonDiv-background">
      <div class="content-wrapper">
        <div class="buttonDiv">
          <h3>Не упустите свой шанс!</h3>
          <h4 style="font-weight: 300">
            Государство готово помочь, но важно действовать сейчас. Проверьте,
            подходите ли вы под критерии программы, и узнайте, как получить свою
            выплату.
          </h4>
          <img
            class="buttonDiv-image"
            src="../assets/images/5304bbd0692869304df5e04bbd2d8e1a.jpg" />
          <button @click="$emit('showCheckPay')" class="buttonDiv-button">
            Проверить право на выплату
          </button>
          <h5 class="buttonDiv-text">
            Государство заботится о вас – проверьте свое право на поддержку!
          </h5>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MainPage",
};
</script>

<style scoped>
.devider {
  height: 1px;
  width: 100%;
  background-color: rgba(172, 169, 169, 1);
}

.content-wrapper {
  display: flex;
  max-width: 1024px;
  margin: 0 auto;
  width: 100%;
}

.text-container-first {
  background-color: #f3f2f1;
  padding: 3rem 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.text-container-first-left {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 50%;
}

.text-container-first-right {
  width: 50%;
  display: flex;
  justify-content: center;
}

.text-container-first-title {
  font-size: 42px;
  line-height: 4rem;
  font-weight: 700;
}

.text-container-first-subTitle {
  font-size: 18px;
  line-height: 2rem;
  font-weight: 400;
}

.text-container-first-right-image {
  width: 100%;
  height: auto;
}

.subDiv {
  display: flex;
  justify-content: space-between;
  padding: 2rem 0;
  gap: 20px;
  background-color: #f3f2f1;
}

.subDiv-left-title {
  color: #003078;
  font-size: 36px;
  margin-bottom: 12px;
}

.subDiv-left-subtitle {
  font-size: 18px;
  font-weight: 100;
}

.subDiv-left {
  width: 50%;
}

.subDiv-right {
  width: 50%;

  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-left: 20px;
}

.subDiv-right-button {
  background-color: #003078;
  color: white;
  height: 100px;
  width: 100%;
  font-size: 18px;
}

.buttonDiv-image {
  width: 100%;
  max-height: 300px;
  object-fit: cover;
  margin: 2rem 0;
}

.buttonDiv-button {
  background-color: #00703c;
  color: white;
  width: 100%;
  height: 4rem;
  outline: none;
}

.buttonDiv-text {
  text-align: center;
  color: #8c8c8c;
  font-weight: 400;
  margin-top: 1rem;
  font-size: 1rem;
}

@media screen and (max-width: 720px) {
  .text-container-first {
    flex-direction: column;
    padding: 1rem 0;
  }

  .content-wrapper {
    flex-direction: column;
    gap: 20px;
  }

  .text-container-first-left {
    width: 100%;
    padding: 0 20px;
  }

  .text-container-first-right {
    width: 100%;
    text-align: center;
  }

  .text-container-first-title {
    font-size: 26px;
    line-height: 24px;
    font-weight: 700;
  }

  .text-container-first-subTitle {
    font-size: 1.2rem;
    line-height: 1.8rem;
  }

  .text-container-first-right-image {
    width: 80%;
    margin-top: 1rem;
  }

  h3 {
    font-size: 26px;
  }

  .subDiv {
    flex-direction: column;
    gap: 20px;
    padding: 1rem 0;
  }

  .subDiv-left,
  .subDiv-right {
    width: 100%;
    margin-left: 0;
    padding: 0 20px;
  }

  .subDiv-left-title {
    font-size: 2rem;
  }

  .subDiv-left-subtitle {
    font-size: 1rem;
    font-weight: 400;
  }

  .subDiv-right-button {
    width: 100%;
    font-size: 16px;
    padding: 1rem;
  }

  .buttonDiv-image {
    width: 100%;
    max-height: 200px;
  }

  .buttonDiv-button {
    width: 100%;
    height: 3rem;
    font-size: 16px;
  }

  .buttonDiv {
    padding: 0 20px;
  }

  .buttonDiv-text {
    font-size: 0.9rem;
  }
}
</style>
