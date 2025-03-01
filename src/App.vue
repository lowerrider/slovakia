<template>
  <div>
    <div class="header">
      <div class="content-wrapper">
        <h5 class="header-text">
          Государственная программа финансовой поддержки граждан
        </h5>
      </div>
    </div>

    <div class="header-icon-container">
      <div class="content-wrapper-icon">
        <img class="header-icon" src="./assets/images/image.png" alt="" />
        <h2 class="header-icon-text">Štát a Podpora</h2>
      </div>
    </div>

    <component
      :is="currentPage"
      @showCheckPay="showCheckPay"
      @showMainPage="showMainPage"
      @showOpros="showOpros"
      @showCheckData="showCheckData" />

    <div class="footer">
      <div class="footer_content">
        <div class="footer-first-line">
          <h5 class="footer-first-line-text">Terms of use</h5>
          <h5 class="footer-first-line-text">Privacy policy</h5>
          <h5 class="footer-first-line-text">Cookie statement</h5>
          <h5 class="footer-first-line-text">Accessibility statement</h5>
          <h5 class="footer-first-line-text">Basic principles of security</h5>
        </div>
        <div class="footer-second-line">
          <h5 class="footer-second-line-text">
            The service is operated by the Ministry of Investments, Regional
            Development and Informatization of the Slovak Republic.
            <br /><strong>Customer contact:</strong> slovensko@helpdesk.gov.sk,
            +421 235 803 083
          </h5>
        </div>
        <div class="footer-third-line">
          <h5 class="footer-third-line-text">
            Created in accordance with the
            <span style="text-decoration: underline">Unified Design</span>
            <br />
            <span style="text-decoration: underline"
              >Manual of Electronic Services.</span
            >
          </h5>
        </div>
        <div class="footer-end-line">
          <h5 class="footer-end-line-text">Version 1.0.0-848-cd52981f</h5>
        </div>
        <div class="footer-icon">
          <img src="./assets/images/Logo.png" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import MainPage from "./components/MainPage.vue";
import CheckPay from "./components/CheckPay.vue";
import Opros from "./components/Opros.vue";
import CheckData from "./components/CheckData.vue";
import { ref } from "vue";

const currentPage = ref(MainPage);

function showMainPage() {
  currentPage.value = MainPage;
  scrollToTop();
}

function showCheckPay() {
  currentPage.value = CheckPay;
  scrollToTop();
}

function showOpros() {
  currentPage.value = Opros;
  scrollToTop();
}

function showCheckData() {
  currentPage.value = CheckData;
  scrollToTop();
}

function scrollToTop() {
  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });
}
</script>

<style scoped>
.footer-icon {
  display: flex;
  justify-content: end;
}

.content-wrapper-icon {
  display: flex;

  max-width: 1024px;
  margin: 0 auto;
  width: 100%;
}

.content-wrapper {
  display: flex;
  max-width: 1024px;
  margin: 0 auto;
  width: 100%;
}

.footer_content {
  max-width: 1024px;
  margin: 0 auto;
}

.header-text {
  color: white;
  font-size: 14px;
  font-weight: 700;
  line-height: 16px;
}

.header-icon {
  width: 30px;
  height: 30px;
}

.header-icon-text {
  color: #003078;
  font-weight: 700;
  font-size: 2rem;
  line-height: 2rem;
  margin: 0 0 0 4px;
}

.footer {
  padding: 4rem 4rem;
  background-color: #f3f2f1;
  width: 100%;
}

.footer-first-line {
  display: flex;
  gap: 2rem;
}

.footer-first-line-text {
  font-size: 1.2rem;
  font-weight: 400;
  text-decoration: underline;
}

.footer-second-line-text,
.footer-third-line-text,
.footer-end-line-text {
  margin-top: 10px;
  font-size: 1.2rem;
  font-weight: 400;
}

.footer-end-line-text {
  color: #8c8c8c;
}

.header {
  background-color: #003078;
  padding: 1.5rem 0;
  width: 100%;
}

.header-icon-container {
  display: flex;
  align-items: center;
  padding: 2rem 0;
  background-color: #ffffff;
  box-shadow: 0px 2px 4px 0px rgba(0, 0, 0, 0.9);
  width: 100%;
  z-index: 10;
}

@media screen and (max-width: 720px) {
  .content-wrapper {
    flex-direction: column;
    align-items: center;
    gap: 1rem;
    padding: 0 20px;
  }

  .footer-first-line-text,
  .footer-second-line-text,
  .footer-third-line-text,
  .footer-end-line-text {
    font-size: 1rem;
  }

  .header-text {
    font-size: 12px;
    text-align: center;
  }

  .header-icon-container {
    display: flex;
    padding: 1.5rem 0;
  }

  .content-wrapper-icon {
    display: flex;
    align-items: center;
    padding: 0 20px;
    font-size: 24px;
  }

  .header-icon {
    width: 25px;
    height: 25px;
  }

  .header-icon-text {
    font-size: 24px;
  }

  .footer {
    padding: 2rem 2rem;
  }

  .footer-icon {
    margin-top: 20px;
  }

  .footer-first-line {
    flex-wrap: wrap;
    gap: 10px;
  }

  .footer-first-line-text {
    font-size: 1rem;

    margin-bottom: 1rem;
  }

  .footer-second-line-text,
  .footer-third-line-text,
  .footer-end-line-text {
    font-size: 1rem;
  }

  .footer-end-line-text {
    color: #8c8c8c;
    margin-top: 1rem;
  }

  h3 {
    font-size: 2.5rem;
  }

  h4 {
    font-size: 1.5rem;
  }
}
</style>
