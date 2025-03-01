<template>
  <div style="background-color: rgba(243, 242, 241, 1)" class="opros-container">
    <div class="stepper">
      <div class="content-wrapper">
        <div style="margin: 20px 0" class="steps">
          <span
            v-for="(question, index) in questions"
            :key="index"
            :class="[
              'step',
              { active: currentQuestionIndex >= index },
              { future: currentQuestionIndex < index },
            ]"></span>
        </div>
      </div>
    </div>

    <div class="question-container">
      <div class="content-wrapper">
        <div
          style="
            display: flex;
            flex-direction: column;
            align-items: start;
            text-align: start;
          "
          class="questions">
          <h3>{{ questions[currentQuestionIndex].title }}</h3>
          <h4 style="text-align: start">
            {{ questions[currentQuestionIndex].subtitle }}
          </h4>
        </div>

        <div class="answers-container">
          <div
            v-for="(answer, index) in questions[currentQuestionIndex].answers"
            :key="index"
            :class="[
              'answer-selector',
              { selected: selectedAnswerIndex === index },
            ]"
            @click="selectAnswer(index)">
            {{ answer }}
          </div>
        </div>
      </div>
    </div>

    <div class="buttons-container">
      <button class="buttonDiv-button-back" @click="goBack">Назад</button>
      <button
        class="buttonDiv-button"
        @click="nextQuestion"
        :disabled="selectedAnswerIndex === null">
        Далее
      </button>
    </div>

    <h4 class="buttons-container-text">
      Все данные строго конфиденциальны и используются только для расчета
      выплат.
    </h4>
  </div>
</template>

<script>
export default {
  name: "Opros",
  data() {
    return {
      currentQuestionIndex: 0,
      selectedAnswerIndex: null,
      questions: [
        {
          title: "1. Из какой вы области?",
          subtitle:
            "Помогите нам определить ваш регион проживания. Это важно для корректного расчета выплат и учета региональных особенностей программы.",
          answers: [
            "Братиславский край",
            "Трнавский край",
            "Тренчинский край",
            "Нитранский край",
            "Жилинский край",
            "Банскобистрицкий край",
            "Прешовский край",
            "Кошицкий край",
          ],
        },
        {
          title: "2. Укажите ваш возраст",
          subtitle:
            "Возрастная категория помогает определить, подходите ли вы под условия программы.",
          answers: ["18–25 лет", "25–40 лет", "40–55 лет", "55+ лет"],
        },
        {
          title: "3. Получали ли вы выплаты от государства в 2025 году?",
          subtitle:
            "Эта информация нужна для исключения дублирования выплат и учета вашего текущего статуса.",
          answers: [
            "Да, получал(а)",
            "Нет, не получал(а)",
            "Стою в очереди на выплату",
          ],
        },
        {
          title: "4. Какой у вас тип занятости?",
          subtitle:
            "Эта информация нужна для исключения дублирования выплат и учета вашего текущего статуса.",
          answers: [
            "Работаю по трудовому договору",
            "Самозанятый/фрилансер",
            "Пенсионер",
            "Студент",
            "Безработный",
          ],
        },
        {
          title: "5. Сколько человек в вашей семье?",
          subtitle:
            "Количество членов семьи учитывается при расчете размера выплаты.",
          answers: [
            "1 человек (живу один/одна)",
            "2 человека",
            "3–4 человека",
            "5 и более человек",
          ],
        },
        {
          title: "6. Какой у вас средний ежемесячный доход?",
          subtitle:
            "Эта информация нужна для определения вашего финансового положения.",
          answers: ["До 500 €", "500–1000 €", "1000–1500 €", "Более 1500 €"],
        },
        {
          title: "7. Есть ли у вас несовершеннолетние дети?",
          subtitle: "Наличие детей может повлиять на размер выплаты.",
          answers: ["Да, есть", "Нет"],
        },
        {
          title: "8. Как вы оцениваете свое текущее финансовое положение?",
          subtitle: "Этот вопрос поможет лучше понять вашу ситуацию.",
          answers: [
            "Отличное, нет проблем",
            "Стабильное, но есть небольшие трудности",
            "Сложное, нужна поддержка",
            "Очень тяжелое",
          ],
        },
      ],
    };
  },
  methods: {
    selectAnswer(index) {
      this.selectedAnswerIndex = index;
      this.moveToNextQuestion();
    },
    moveToNextQuestion() {
      if (this.selectedAnswerIndex !== null) {
        if (this.currentQuestionIndex < this.questions.length - 1) {
          this.currentQuestionIndex++;
          this.selectedAnswerIndex = null;
        }
      }
    },
    goBack() {
      this.$emit("showCheckPay");
    },
    nextQuestion() {
      if (this.currentQuestionIndex === this.questions.length - 1) {
        this.$emit("showCheckData");
      } else {
        this.moveToNextQuestion();
      }
    },
  },
};
</script>

<style scoped>
.buttons-container-text {
  text-align: center;
  font-size: 18px;
  color: rgba(140, 140, 140, 1);
}

.content-wrapper {
  max-width: 1024px;
  margin: 0 auto;
  width: 100%;
}

.stepper {
  display: flex;
  justify-content: center;
  height: 60px;
}

.steps {
  display: flex;
  justify-content: center;
  gap: 10px;
}

.step {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background-image: linear-gradient(
    to right,
    rgba(217, 217, 217, 1),
    rgba(172, 169, 169, 1)
  );
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background-color 0.3s;
}

.step.active {
  background-image: linear-gradient(
    to right,
    rgba(0, 48, 120, 1),
    rgba(63, 117, 199, 1)
  );
}

.step.future {
  background-color: gray;
}

.question-container {
  text-align: center;
}

.answers-container {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 20px;
}

.answer-selector {
  background-color: rgba(0, 0, 0, 0.03);
  padding: 1rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1.6rem;
  text-align: center;
  transition: background-color 0.3s;
}

.answer-selector:hover {
  background-color: rgba(0, 0, 0, 0.1);
}

.answer-selector.selected {
  background-color: #00703c;
  color: white;
}

.buttons-container {
  max-width: 1024px;
  display: flex;
  justify-content: space-between;
  margin: 40px auto;
  gap: 20px;
}

.buttonDiv-button {
  background-color: #00703c;
  color: white;
  width: 48%;
  height: 3rem;
  font-size: 1.4rem;
  cursor: pointer;
  border: none;
}

.buttonDiv-button-back {
  background-color: rgba(0, 48, 120, 1);
  color: white;
  width: 48%;
  height: 3rem;
  font-size: 1.4rem;
  cursor: pointer;
  border: none;
}

.buttonDiv-button:disabled {
  background-color: #cccccc;
  cursor: not-allowed;
}

.buttonDiv-button-back:disabled {
  background-color: #cccccc;
  cursor: not-allowed;
}

@media screen and (max-width: 720px) {
  .content-wrapper {
    padding: 0 20px;
  }

  .steps {
    gap: 8px;
  }

  .step {
    width: 20px;
    height: 20px;
  }

  .question-container h3 {
    font-size: 1.6rem;
  }

  .question-container h4 {
    font-size: 1.2rem;
  }

  .answers-container {
    gap: 8px;
  }

  .answer-selector {
    font-size: 1.4rem;
    padding: 0.8rem;
  }

  .buttonDiv-button,
  .buttonDiv-button-back {
    font-size: 1.2rem;
    height: 3rem;
  }

  .buttons-container {
    gap: 10px;
    padding: 0 20px;
    justify-content: center;
  }

  .buttons-container-text {
    font-size: 16px;
  }
}
</style>
