<template>
  <div id="app">
    <div class="app-wrap">
      <header class="header">
        <div class="site-container">
          <h1 class="header__title">Новый гороскоп на 2021 год!</h1>
          <div class="header__text">Узнайте, что Вас ждёт</div>
        </div>
      </header>
      <main class="site-main site-container">
        <template v-if="pageStep == 1">
          <div class="banner">
            <img
              src="@/assets/img/banner.png"
              alt="banner"
              class="img-banner"
            />
            <div class="goroskop-wrap">
              <img
                src="@/assets/img/goroskop.png"
                alt="goroskop"
                class="goroskop-img"
              />
            </div>
          </div>
          <div class="site-info">
            <div class="site-info__title">
              Узнайте, как 2021 год изменит жизнь каждого из нас!
            </div>
            <div class="site-info__content">
              К сожалению, 2020 год принес нам немало неприятностей, даже
              откровенных проблем и несчастий. Не смотря на это, 3 знака зодиака
              очень скоро обретут долгожданное счастье! 2021 год затронет своими
              потрясениями каждого из нас.
            </div>
          </div>
          <div class="change-gender">
            <div class="change-gender__title">Укажите свой пол:</div>
            <div class="change-gender__wrap">
              <label class="site-label">
                <input
                  type="radio"
                  name="gender"
                  v-model="userInfo.gender"
                  value="Женщина"
                />
                <span class="radio"></span>
                <span class="text">Женщина </span>
              </label>
              <label class="site-label">
                <input
                  type="radio"
                  name="gender"
                  v-model="userInfo.gender"
                  value="Мужчина"
                />
                <span class="radio"></span>
                <span class="text">Мужчина</span>
              </label>
            </div>
            <div class="next-btn" v-if="userInfo.gender" @click="startStep()">
              Далее
            </div>
          </div>
        </template>
        <div
          class="progress-wrap"
          v-if="
            pageStep == 2 ||
            pageStep == 3 ||
            pageStep == 4 ||
            pageStep == 5 ||
            pageStep == 6
          "
        >
          <div class="active-lines"></div>
        </div>
        <template v-if="pageStep == 2">
          <div class="polls polls-1">
            <div class="polls__top">
              <div class="active-lines"></div>
            </div>
            <div class="polls__content">
              <div class="content__title">
                В какое время суток Вы чувствуете себя наиболее комфортно?
              </div>
              <div class="content__wrap">
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-1"
                    value="Утро"
                    v-model="userInfo.poll1"
                  />
                  <span class="radio"></span>
                  <span class="text">Утро</span>
                </label>
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-1"
                    value="Ночь"
                    v-model="userInfo.poll1"
                  />
                  <span class="radio"></span>
                  <span class="text">Ночь </span>
                </label>
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-1"
                    value="Вечер"
                    v-model="userInfo.poll1"
                  />
                  <span class="radio"></span>
                  <span class="text">Вечер </span>
                </label>
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-1"
                    value="День"
                    v-model="userInfo.poll1"
                  />
                  <span class="radio"></span>
                  <span class="text">День </span>
                </label>
              </div>
              <div class="next-btn" v-if="userInfo.poll1" @click="pollStep1()">
                Далее
              </div>
            </div>
          </div>
        </template>
        <template v-if="pageStep == 3">
          <div class="polls polls-2">
            <div class="polls__top">
              <div class="active-lines"></div>
            </div>
            <div class="polls__content">
              <div class="content__title">
                Подскажите, мучает ли Вас бессонница последнее время?
              </div>
              <div class="content__wrap">
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-2"
                    value="Да"
                    v-model="userInfo.poll2"
                  />
                  <span class="radio"></span>
                  <span class="text">Да</span>
                </label>
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-2"
                    value="Нет"
                    v-model="userInfo.poll2"
                  />
                  <span class="radio"></span>
                  <span class="text">Нет</span>
                </label>
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-2"
                    value="Иногда"
                    v-model="userInfo.poll2"
                  />
                  <span class="radio"></span>
                  <span class="text">Иногда</span>
                </label>
              </div>
              <div class="next-btn" v-if="userInfo.poll2" @click="pollStep2()">
                Далее
              </div>
            </div>
          </div>
        </template>
        <template v-if="pageStep == 4">
          <div class="polls polls-3">
            <div class="polls__top">
              <div class="active-lines"></div>
            </div>
            <div class="polls__content">
              <div class="content__title">
                Чувствуете ли Вы в последнее время, что вам никак не удается
                осуществить ваши планы?
              </div>
              <div class="content__wrap">
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-3"
                    value="Да"
                    v-model="userInfo.poll3"
                  />
                  <span class="radio"></span>
                  <span class="text">Да</span>
                </label>
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-3"
                    value="Нет"
                    v-model="userInfo.poll3"
                  />
                  <span class="radio"></span>
                  <span class="text">Нет</span>
                </label>
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-3"
                    value="Иногда"
                    v-model="userInfo.poll3"
                  />
                  <span class="radio"></span>
                  <span class="text">Иногда</span>
                </label>
              </div>
              <div class="next-btn" v-if="userInfo.poll3" @click="pollStep3()">
                Далее
              </div>
            </div>
          </div>
        </template>
        <template v-if="pageStep == 5">
          <div class="polls polls-4">
            <div class="polls__top">
              <div class="active-lines"></div>
            </div>
            <div class="polls__content">
              <div class="content__title">
                Какой Вы видите свою жизнь через 5 лет?
              </div>
              <div class="content__wrap">
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-4"
                    value="Брак, семья, дети, дом"
                    v-model="userInfo.poll4"
                  />
                  <span class="radio"></span>
                  <span class="text">Брак, семья, дети, дом</span>
                </label>
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-4"
                    value="Путешествия по Миру"
                    v-model="userInfo.poll4"
                  />
                  <span class="radio"></span>
                  <span class="text">Путешествия по Миру</span>
                </label>
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-4"
                    value="Успешная карьера"
                    v-model="userInfo.poll4"
                  />
                  <span class="radio"></span>
                  <span class="text">Успешная карьера </span>
                </label>
                <label class="site-label">
                  <input
                    type="radio"
                    name="poll-4"
                    value="Всё вместе"
                    v-model="userInfo.poll4"
                  />
                  <span class="radio"></span>
                  <span class="text">Всё вместе</span>
                </label>
              </div>
              <div class="next-btn" v-if="userInfo.poll4" @click="pollStep4()">
                Далее
              </div>
            </div>
          </div>
        </template>
        <template v-if="pageStep == 6">
          <div class="polls polls-5">
            <div class="polls__top">
              <div class="active-lines"></div>
            </div>
            <div class="polls__content">
              <div class="content__title">Введите дату своего рождения:</div>
              <div class="content__wrap">
                <label for="choise-month">Выберите месяц:</label>
                <select
                  name=""
                  id="choise-month"
                  v-model="month"
                  @change="choiseMonth()"
                >
                  <option v-for="mon in 12" :key="mon">
                    {{ mon }}
                  </option>
                </select>
                <label for="choise-day">Выберите день:</label>
                <select
                  name=""
                  id="choise-day"
                  v-model="day"
                  @change="choiseDay()"
                >
                  <option v-for="n in countDay" :key="n">
                    {{ n }}
                  </option>
                </select>
                <label for="choise-year">Выберите год:</label>
                <select
                  name=""
                  id="choise-year"
                  v-model="yearModel"
                  @change="choiseYear()"
                >
                  <option v-for="i in year" :key="i">
                    {{ i }}
                  </option>
                </select>
                <div class="horoscope-info" v-show="horoscopeType">
                  <div class="horoscope-img">
                    <img
                      v-if="view.image != ''"
                      :src="require(`@/assets/img/goroskop-img/${view.image}`)"
                      alt=""
                    />
                  </div>
                  <div class="horoscope-type">{{ view.title }}</div>
                </div>
              </div>
              <div class="next-btn" v-if="poll5Active" @click="pollStep5()">
                Далее
              </div>
            </div>
          </div>
        </template>
        <template v-if="pageStep == 7">
          <div class="polls polls-6">
            <div class="polls__content">
              <div class="content__wrap">
                <div class="content__top">
                  <div class="title">Обработка Ваших данных:</div>
                  <div class="progress">
                    <div class="active"></div>
                  </div>
                </div>
                <div class="content__item">
                  <div class="title">
                    Анализ введенных данных . . . . . . . <span>Выполнено</span>
                  </div>
                  <div class="value"></div>
                </div>
                <div class="content__item">
                  <div class="title">
                    Коррекция астрологического знака . . . . . . .<span
                      >Выполнено</span
                    >
                  </div>
                  <div class="value"></div>
                </div>
                <div class="content__item">
                  <div class="title">
                    Коррекция астрологического знака . . . . . . .<span
                      >Выполнено</span
                    >
                  </div>
                  <div class="value"></div>
                </div>
                <div class="content__item">
                  <div class="title">
                    Расчет вариаций ответов . . . . . . .<span>Выполнено</span>
                  </div>
                  <div class="value"></div>
                </div>
                <div class="content__item">
                  <div class="title">
                    Генерация предсказания . . . . . . .<span>Выполнено</span>
                  </div>
                  <div class="value"></div>
                </div>
                <div class="content__item">
                  <div class="title">
                    Сохранение результата . . . . . . .<span>Выполнено</span>
                  </div>
                  <div class="value"></div>
                </div>
                <div class="content__item">
                  <div class="title">
                    Поиск свободного оператора . . . . . . .<span
                      >Выполнено</span
                    >
                  </div>
                  <div class="value"></div>
                </div>
                <div class="content__item">
                  <div class="title">
                    Начала озвучки и записи аудио-сообщения . . . . . . .<span
                      >Выполнено</span
                    >
                  </div>
                  <div class="value"></div>
                </div>
                <div class="content__entry content__item">Идет запись!</div>
                <div class="content__ready content__item">готово!</div>
              </div>
              <div class="next-btn" v-if="poll6Active" @click="pollStep6()">
                Далее
              </div>
            </div>
          </div>
        </template>
        <template v-if="pageStep == 8">
          <div class="polls polls-7">
            <div class="polls__content">
              <div class="content__wrap">
                <div class="finish-top">Спасибо за Ваши ответы!</div>
                <div class="finish-happy">
                  Поздравляем! Прослушать свой персональный гороскоп возможно
                  уже сейчас!
                </div>
                <div class="finish-text">
                  <h3>2021 год Вас ошарашит!</h3>
                  <p>
                    Вас ждёт то, чего Вы никак не ожидали. Первые известия Вы
                    получите совсем скоро, возможно это 17-18 ноября! Что бы
                    прослушать аудио-сообщение, необходимо нажать на кнопку ниже
                    и позвонить со своего мобильного телефона. Позвоните и
                    Прослушайте очень серьезную информацию!
                  </p>
                </div>
                <div class="next-btn" @click="resultPage()">
                  Звонить и слушать
                </div>
              </div>
            </div>
          </div>
        </template>
        <template v-if="pageStep == 9">
          <div class="finish-page">
            <div class="finish-page__title">Вывод двух видов данных</div>
            <div class="finish-page__wrap">
              <div class="left-column">
                <div class="title">
                  Данные пользователя которые он выбрал при проходе опроса
                </div>
                <div class="wrap" v-if="userInfo">
                  <div class="item">
                    <span>Укажите свой пол:</span
                    ><span>{{ userInfo.gender }}</span>
                  </div>
                  <div class="item">
                    <span
                      >В какое время суток Вы чувствуете себя наиболее
                      комфортно?</span
                    ><span>{{ userInfo.poll1 }}</span>
                  </div>
                  <div class="item">
                    <span
                      >Подскажите, мучает ли Вас бессонница последнее
                      время?</span
                    ><span>{{ userInfo.poll2 }}</span>
                  </div>
                  <div class="item">
                    <span
                      >Чувствуете ли Вы в последнее время, что вам никак не
                      удается осуществить ваши планы? </span
                    ><span>{{ userInfo.poll3 }}</span>
                  </div>
                  <div class="item">
                    <span>Какой Вы видите свою жизнь через 5 лет? </span
                    ><span>{{ userInfo.poll4 }}</span>
                  </div>
                  <div class="item">
                    <span>Введите дату своего рождения: </span
                    ><span>
                      {{ userInfo.poll5 }}
                    </span>
                  </div>
                </div>
              </div>
              <div class="right-column">
                <div class="title">
                  Данные которые приходять с запроса
                  <a href="https://swapi.dev/api/people/1/"
                    >https://swapi.dev/api/people/1/</a
                  >
                </div>
                <div class="subtitle">
                  Для вывода данных нажмите
                  <span @click="getInfo()"
                    ><b style="cursor: pointer">вывести данные</b></span
                  ><br />
                </div>
                <div class="item">
                  {{ infoResponse }}
                </div>
              </div>
            </div>
          </div>
        </template>
      </main>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      userInfo: {
        gender: "",
        poll1: "",
        poll2: "",
        poll3: "",
        poll4: "",
        poll5: "",
      },
      pageStep: 1,
      maxStep: 6,
      month: null,
      day: null,
      year: [],
      poll5Active: false,
      horoscopeType: false,
      poll6Active: false,
      countDay: 31,
      infoResponse: "",
      view: {
        image: "",
        title: "",
      },
      yearModel: "",
    };
  },
  created() {
    for (let i = parseInt(new Date().getFullYear()); i >= 1971; i--) {
      this.year.push(i.toString());
    }
    this.year = this.year.reverse();
  },
  mounted() {},
  methods: {
    dinamic() {
      let linesWidth = (this.pageStep * 100) / this.maxStep;
      setTimeout(() => {
        let lines = document.querySelector(".active-lines");
        lines.style.width = linesWidth + "%";
      }, 200);
    },
    startStep() {
      this.userInfo.gender;
      this.pageStep = 2;
      this.dinamic();
    },
    pollStep1() {
      this.pageStep = 3;
      this.dinamic();
    },
    pollStep2() {
      this.pageStep = 4;
      this.dinamic();
    },
    pollStep3() {
      this.pageStep = 5;
      this.dinamic();
    },
    pollStep4() {
      this.pageStep = 6;
      this.dinamic();
    },
    pollStep5() {
      this.pageStep = 7;
      setTimeout(() => {
        let num = 0;
        let resultText = document.querySelectorAll(".content__item");
        let progressLine = document.querySelector(
          ".content__top .progress .active"
        );
        for (let i = 0; i < resultText.length; i++) {
          setTimeout(() => {
            resultText[i].classList.add("active");
            num += resultText.length;
            progressLine.innerHTML = num;
            progressLine.style.width = num + "%";
            progressLine.style.background = "#419330";
          }, 1000 + i * 1000);
        }
      }, 500);
      setTimeout(() => {
        this.poll6Active = true;
      }, 10000);
    },
    pollStep6() {
      this.pageStep = 8;
    },
    getInfo() {
      this.axios
        .get("https://swapi.dev/api/people/1/")
        .then((response) => (this.infoResponse = response));
    },
    resultPage() {
      this.pageStep = 9;
    },
    choiseYear() {
      this.userInfo.poll5 =
        this.day + " : " + this.month + " : " + this.yearModel;
      this.poll5Active = true;
    },
    choiseMonth() {
      if (
        this.month == 1 ||
        this.month == 3 ||
        this.month == 5 ||
        this.month == 7 ||
        this.month == 8 ||
        this.month == 10 ||
        this.month == 12
      ) {
        this.countDay = 31;
      } else if (
        this.month == 4 ||
        this.month == 6 ||
        this.month == 9 ||
        this.month == 11
      ) {
        this.countDay = 30;
      } else {
        this.countDay = 28;
      }
    },
    choiseDay() {
      let fullDay = +this.day + " " + this.month;
      this.horoscopeType = true;
      if (
        (this.month == 3 && this.day >= 21) ||
        (this.month == 4 && this.day <= 19)
      ) {
        this.view.image = "oven.png";
        this.view.title = "Овен";
      }
      if (
        (this.month == 4 && this.day >= 20) ||
        (this.month == 5 && this.day <= 20)
      ) {
        this.view.image = "teles.png";
        this.view.title = "Телец";
      }
      if (
        (this.month == 5 && this.day >= 21) ||
        (this.month == 6 && this.day <= 20)
      ) {
        this.view.image = "blisnetsi.png";
        this.view.title = "Близнецы";
      }
      if (
        (this.month == 6 && this.day >= 21) ||
        (this.month == 7 && this.day <= 22)
      ) {
        this.view.image = "rak.png";
        this.view.title = "Рак";
      }
      if (
        (this.month == 7 && this.day >= 23) ||
        (this.month == 8 && this.day <= 22)
      ) {
        this.view.image = "lev.png";
        this.view.title = "Лев";
      }
      if (
        (this.month == 8 && this.day >= 23) ||
        (this.month == 9 && this.day <= 22)
      ) {
        this.view.image = "deva.png";
        this.view.title = "Дева";
      }
      if (
        (this.month == 9 && this.day >= 23) ||
        (this.month == 10 && this.day <= 22)
      ) {
        this.view.image = "vesi.png";
        this.view.title = "Весы";
      }
      if (
        (this.month == 10 && this.day >= 23) ||
        (this.month == 11 && this.day <= 21)
      ) {
        this.view.image = "skarpion.png";
        this.view.title = "Скорпион";
      }
      if (
        (this.month == 11 && this.day >= 22) ||
        (this.month == 12 && this.day <= 21)
      ) {
        this.view.image = "streles.png";
        this.view.title = "Стрелец";
      }
      if (
        (this.month == 12 && this.day >= 22) ||
        (this.month == 1 && this.day <= 20)
      ) {
        this.view.image = "kozerog.png";
        this.view.title = "Козерог";
      }
      if (
        (this.month == 1 && this.day >= 21) ||
        (this.month == 2 && this.day <= 18)
      ) {
        this.view.image = "vodoley.png";
        this.view.title = "Водолей";
      }
      if (
        (this.month == 2 && this.day >= 19) ||
        (this.month == 3 && this.day <= 20)
      ) {
        this.view.image = "ribi.png";
        this.view.title = "Рыбы";
      }
    },
  },
};
</script>

<style lang="scss">
*,
*::before,
*::after {
  box-sizing: inherit;
}

html {
  position: relative;
  overflow-x: hidden;
  box-sizing: border-box;
  scroll-behavior: smooth;
}

body {
  -webkit-font-smoothing: antialiased;
  text-decoration-skip: objects;
  text-rendering: optimizeLegibility;
  text-size-adjust: 100%;
  -webkit-tap-highlight-color: transparent;
  font-size: 14px;
  line-height: 20px;
  font-family: "Roboto", sans-serif;
  padding: 0;
  margin: 0;
  color: #343b4d;
}

main {
  flex: 1;
}

p {
  margin: 0;
}

a,
button {
  outline: none;
  transition: 0.4s;
  cursor: pointer;
}

a {
  text-decoration: none;
  color: currentColor;
}

a:hover {
  text-decoration: none !important;
  color: inherit;
}

svg {
  display: block;
  flex: 0 0 auto;
  width: 100%;
  height: 100%;
  fill: currentColor;
}

figure,
picture {
  display: inline-block;
  margin: 0;
  line-height: 0;

  img {
    width: 100%;
  }
}

img {
  vertical-align: top;
  max-width: 100%;
  user-select: none;
}

img[draggable="false"] {
  pointer-events: none;
  // stylelint-disable-next-line
  -webkit-user-drag: none;
}

fieldset {
  margin: 0;
  border: 0;
  padding: 0;
}

ul,
li {
  list-style: none;
  margin: 0;
  padding: 0;
}

video {
  outline: none;
  width: 100%;
  height: 100%;
}

iframe {
  display: block;
}
hr {
  box-sizing: content-box; /* 1 */
  height: 0; /* 1 */
  overflow: visible; /* 2 */
}
button,
[type="button"],
[type="reset"],
[type="submit"] {
  -webkit-appearance: button;
}
button::-moz-focus-inner,
[type="button"]::-moz-focus-inner,
[type="reset"]::-moz-focus-inner,
[type="submit"]::-moz-focus-inner {
  border-style: none;
  padding: 0;
}
button:-moz-focusring,
[type="button"]:-moz-focusring,
[type="reset"]:-moz-focusring,
[type="submit"]:-moz-focusring {
  outline: 1px dotted ButtonText;
}
textarea {
  overflow: auto;
}
[type="checkbox"],
[type="radio"] {
  box-sizing: border-box; /* 1 */
  padding: 0; /* 2 */
}
[type="number"]::-webkit-inner-spin-button,
[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
[type="search"] {
  -webkit-appearance: textfield; /* 1 */
  outline-offset: -2px; /* 2 */
}

[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}

::-webkit-file-upload-button {
  -webkit-appearance: button; /* 1 */
  font: inherit; /* 2 */
}
[hidden] {
  display: none;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  margin: 0;
}

.site-container {
  max-width: 640px;
  margin: auto;
  padding: 0 16px;
}
.next-btn {
  background-color: #315dfa;
  border: 1px solid #315dfa;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  height: 45px;
  max-width: 190px;
  width: 100%;
  margin: 15px auto;
  cursor: pointer;
}

.header {
  background: #315dfa;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.1);
  color: #afdce6;
  padding: 10px 0;
}
.header__title {
  font-weight: 700;
  font-size: 20px;
  line-height: 22px;
}
.banner {
  position: relative;
  margin-bottom: 30px;
}
.banner .goroskop-wrap {
  position: absolute;
  top: 0;
  left: 0;
  width: 50%;
  height: 100%;
}
.banner .goroskop-img {
  animation: 15s linear 0s normal none infinite running rot;
}
@keyframes rot {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
@-webkit-keyframes rot {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.site-info {
  margin-bottom: 40px;
}
.site-info__title {
  font-weight: 500;
  font-size: 20px;
  line-height: 22px;
  color: #315df9;
  margin-bottom: 20px;
}
.site-info__content {
  font-size: 16px;
  line-height: 23px;
}
.change-gender__title {
  width: 100%;
  height: 50px;
  background-color: #343b4d;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  font-size: 14px;
  line-height: 22px;
  color: #fff;
}
.change-gender__wrap {
  background-color: #f3f4f8;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  padding: 25px 15px;
}
.polls .content__title {
  text-align: center;
  padding: 16px 22px;
  color: #fff;
  background-color: #343b4d;
}
.polls .content__wrap {
  background-color: #f3f4f8;
  display: flex;
  flex-direction: column;
  padding: 37px 17px;
}
.polls .content__wrap .site-label {
  margin-bottom: 30px;
}
.polls .content__wrap .site-label:last-child {
  margin-bottom: 0;
}
.polls .content__wrap select {
  height: 45px;
  padding: 12px 17px;
  appearance: none;
  cursor: pointer;
  // background-image: url();
  background-position: 97% center;
  background-repeat: no-repeat;
  margin-bottom: 15px;
}
.polls .content__item {
  display: none;
  margin-bottom: 20px;
}
.polls .content__item:last-child {
  margin-bottom: 0;
}
.polls .content__item span {
  color: #419330;
}
.polls .content__item.active {
  display: block;
}
.polls .content__entry {
  color: rgba(183, 0, 0, 0.711);
  text-transform: uppercase;
}
.polls .content__ready {
  text-transform: uppercase;
  color: #343b4d;
}
.polls .content__top {
  margin-bottom: 30px;
}
.polls .content__top .title {
  font-weight: 700;
  font-size: 14px;
  line-height: 19px;
  color: #343b4d;
  margin-bottom: 20px;
}
.polls .content__top .progress {
  background-color: #f3f4f8;
  color: #fff;
  font-weight: 500;
  height: 42px;
}
.polls .content__top .active {
  background-color: #f3f4f8;
  height: 42px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.polls .polls-5 .content__wrap {
  padding: 37px 50px;
}
.polls .horoscope-info {
  display: flex;
  align-items: center;
  flex-direction: column;
}
.site-label {
  cursor: pointer;
  display: flex;
  align-items: center;
}
.site-label input {
  opacity: 0;
  z-index: -1;
  position: absolute;
}
.site-label .radio {
  min-width: 15px;
  height: 15px;
  background: #fff;
  border: 1px solid #d6d6d6;
  box-sizing: border-box;
  display: inline-block;
  border-radius: 50px;
  margin: 0 11px 0 0;
  position: relative;
}
.site-label .radio:after {
  content: none;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 5px;
  height: 5px;
  background-color: #291a0e;
  border-radius: 50px;
}
.site-label input:checked ~ .text {
  font-weight: 700;
  color: #315dfa;
}
.site-label input:checked + .radio:after {
  content: "";
}
.finish-top {
  font-size: 20px;
  margin-bottom: 20px;
}
.finish-happy {
  margin-bottom: 10px;
}
.finish-text {
  margin-bottom: 20px;
}
.finish-text h3 {
  margin-bottom: 10px;
}
.finish-page {
  padding: 20px 0;
}
.finish-page__title {
  font-size: 20px;
  margin-bottom: 20px;
}
.finish-page__wrap .title {
  font-size: 16px;
  font-style: italic;
  margin-bottom: 10px;
}
.finish-page__wrap .item {
  display: flex;
  justify-content: space-between;
}
.finish-page__wrap .item span:first-child {
  font-weight: 600;
}
.finish-page__wrap .left-column {
  margin-bottom: 20px;
}
</style>
