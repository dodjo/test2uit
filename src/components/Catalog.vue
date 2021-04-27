<template>
  <div>
    <header class="header">
      <div class="container">
        <div class="header__block-links">
          <a href="#">Контрагентам</a>
          <a href="#">Дизайнерам</a>
          <a href="#">Вакансии</a>
        </div>
        <a href="#" class="header__logo">
          <img src="@/assets/img/logo.svg" alt="logo" />
        </a>
        <div class="header__menu">
          <div class="header__search">
            <span
              class="iconify"
              data-inline="false"
              data-icon="gridicons:search"
              style="color: #ffffff; font-size: 24px"
            ></span>
            <input
              type="text"
              class="header__search-input"
              placeholder="Поиск"
            />
          </div>
          <div class="header__account">
            <span>
              <a href="#">Вход</a>
              /
              <a href="#">Регистрация</a>
            </span>
            <a href="#">
              <span
                class="iconify"
                data-inline="false"
                data-icon="mdi:account"
                style="color: #ffffff; font-size: 24px"
              ></span>
            </a>
            <a href="#">
              <span
                class="iconify"
                data-inline="false"
                data-icon="topcoat:like"
                style="color: #ffffff; font-size: 18px"
              ></span>
            </a>
          </div>
        </div>
      </div>
      <div
        class="burger"
        @click="burgerState = !burgerState"
        :class="{ active: burgerState }"
      >
        <span></span>
        <span></span>
        <span></span>
      </div>
      <div class="burger-content" :class="{ active: burgerState }">
        <div class="burger-content__block-links">
          <a href="#">Контрагентам</a>
          <a href="#">Дизайнерам</a>
          <a href="#">Вакансии</a>
        </div>

        <div class="burger-content__account">
          <div>
            <a href="#">Вход</a>
            /
            <a href="#">Регистрация</a>
          </div>
          <div class="burger-content__account-icons">
            <a href="#">
              <span
                class="iconify"
                data-inline="false"
                data-icon="mdi:account"
                style="color: #ffffff; font-size: 45px"
              ></span>
            </a>
            <a href="#">
              <span
                class="iconify"
                data-inline="false"
                data-icon="topcoat:like"
                style="color: #ffffff; font-size: 40px"
              ></span>
            </a>
          </div>
        </div>

        <div class="burger-content__search">
          <span
            class="iconify"
            data-inline="false"
            data-icon="gridicons:search"
            style="color: #ffffff; font-size: 40px"
          ></span>
          <input
            type="text"
            class="burger-content__search-input"
            placeholder="Поиск"
          />
        </div>
      </div>
    </header>

    <section class="filter">
      <div class="container">
        <div class="filter__wrap">
          <select
            v-model="filter.brand"
            @change="onFilter"
            name="brand"
            id
            class="selection-box"
          >
            <option value disabled selected>Бренд</option>
            <option value="1">option 1</option>
            <option value="2">option 2</option>
            <option value="3">option 3</option>
          </select>
          <select
            v-model="filter.price"
            @change="onFilter"
            name="price"
            id
            class="selection-box"
          >
            <option value disabled selected>Цена</option>
            <option value="1">option 1</option>
            <option value="2">option 2</option>
            <option value="3">option 3</option>
          </select>
          <select
            v-model="filter.forHome"
            @change="onFilter"
            name="for_home"
            id
            class="selection-box"
          >
            <option value disabled selected>Для кого</option>
            <option value="1">option 1</option>
            <option value="2">option 2</option>
            <option value="3">option 3</option>
          </select>
          <select
            v-model="filter.collection"
            @change="onFilter"
            name="collection"
            id
            class="selection-box"
          >
            <option value disabled selected>Коллекция</option>
            <option value="1">option 1</option>
            <option value="2">option 2</option>
            <option value="3">option 3</option>
          </select>
          <select
            v-model="filter.season"
            @change="onFilter"
            name="season"
            id
            class="selection-box"
          >
            <option value disabled selected>Сезон</option>
            <option value="1">option 1</option>
            <option value="2">option 2</option>
            <option value="3">option 3</option>
          </select>
          <select
            v-model="filter.event"
            @change="onFilter"
            name="event"
            id
            class="selection-box"
          >
            <option value disabled selected>Событие</option>
            <option value="1">option 1</option>
            <option value="2">option 2</option>
            <option value="3">option 3</option>
          </select>
        </div>
      </div>
    </section>

    <section class="product-cards">
      <div class="container">
        <div class="product-cards__wrap">
          <div
            class="product-cards__item"
            v-for="product in productsList"
            :key="product.id"
          >
            <a href="#">
              <img :src="product.image" alt width="280" height="220" />
            </a>
            <p>{{ product.product_type }}</p>
            <a href="#">
              <h3>{{ product.title }}</h3>
            </a>
            <a href="#" class="product-cards__item-btn"
              >{{ product.price }} ₽</a
            >
          </div>
        </div>
        <a href="#" class="product-cards__btn" @click.prevent="loadData()"
          >покажите еще</a
        >
      </div>
    </section>

    <section class="discription">
      <div class="container">
        <div
          class="discription__text-seo"
          :class="{ 'full-text': showFullText }"
        >
          <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Amet, lorem
            eu commodo porttitor erat. Amet mauris cursus bibendum in egestas.
            Nulla porttitor amet quam elit, mauris. Tortor egestas dignissim
            augue suspendisse rutrum pretium lobortis dolor. Commodo sagittis at
            amet faucibus faucibus id. Bibendum placerat convallis gravida eu
            quisque et augue. Sed dignissim amet ut vitae at ornare sed. Commodo
            sagittis at amet faucibus faucibus id. Bibendum placerat convallis
            gravida eu quisque et augue. Sed dignissim amet ut vitae at ornare
            sed. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Amet,
            lorem eu commodo porttitor erat. Amet mauris cursus bibendum in
            egestas. Nulla porttitor amet quam elit, mauris. Tortor egestas
            dignissim augue suspendisse rutrum pretium lobortis dolor. Commodo
            sagittis at amet faucibus faucibus id. Bibendum placerat convallis
            gravida eu quisque et augue. Sed dignissim amet ut vitae at ornare
            sed. Commodo sagittis at amet faucibus faucibus id. Bibendum
            placerat convallis gravida eu quisque et augue. Sed dignissim amet
            ut vitae at ornare sed.
          </p>
          <a
            href="#"
            class="discription__btn"
            @click.prevent="showFullText = !showFullText"
          >
            {{ showFullText ? "показать меньше текста" : "читать полностью" }}
          </a>
        </div>
        <div class="discription__icon-list">
          <div class="discription__icon-item">
            <img src="@/assets/img/delivery.svg" alt />
            <p>Бесплатная доставка</p>
          </div>
          <div class="discription__icon-item">
            <img src="@/assets/img/list.svg" alt />
            <p>Индивидуальный дизайн</p>
          </div>
          <div class="discription__icon-item">
            <img src="@/assets/img/ribbon-design.svg" alt />
            <p>Бесплатная примерка</p>
          </div>
          <div class="discription__icon-item">
            <img src="@/assets/img/jewelry.svg" alt />
            <p>Личный подход</p>
          </div>
        </div>
      </div>
    </section>

    <section class="subscribe">
      <div class="container">
        <div class="subscribe__title">
          <h2>Полезные советы и персональный предложения</h2>
          <h3>Эксклюзивная рассылка</h3>
        </div>
        <div class="subscribe__body">
          <ul class="subscribe__list">
            <li>Личный менеджер</li>
            <li>Доставка и оформление</li>
            <li>Индивидуальный дизайн</li>
          </ul>
          <form
            @submit="onSubmit"
            action="#"
            method="get"
            class="subscribe__form"
          >
            <input
              v-model="form.email"
              type="email"
              class="subscribe__form-email"
              placeholder="Ваш e-mail"
            />
            <button type="submit" class="subscribe__form-btn">отправить</button>
          </form>
        </div>
      </div>
    </section>

    <footer class="footer">
      <div class="container">
        <div class="footer__first-row">
          <div class="footer__column">
            <h3>Полезные ссылки</h3>
            <a href="#">Доставка</a>
            <a href="#">Оплата</a>
            <a href="#">Акции</a>
            <a href="#">Политика конфиденциальности</a>
          </div>
          <div class="footer__column">
            <h3>Оплата</h3>
            <p>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit.
              Ullamcorper justo, nec, pellentesque.
            </p>
            <img src alt />
            <img src alt />
          </div>
          <div class="footer__column">
            <h3>Kонтакты</h3>
            <div class="footer__contacts">
              <a href="tel:88122345655">
                <span
                  class="iconify"
                  data-inline="false"
                  data-icon="entypo:old-phone"
                  style="font-size: 20px"
                ></span
                >8 (812) 234-56-55
              </a>
              <a href="tel:88122345655">
                <span
                  class="iconify"
                  data-inline="false"
                  data-icon="entypo:old-phone"
                  style="font-size: 20px"
                ></span
                >8 (812) 234-56-55
              </a>
              <a href="mailto:ojjo@ojjo.ru">
                <span
                  class="iconify"
                  data-inline="false"
                  data-icon="entypo:mail"
                  style="font-size: 20px"
                ></span
                >ojjo@ojjo.ru
              </a>
            </div>
          </div>
          <div class="footer__column">
            <h3>Социальные сети</h3>
            <p>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit.
              Ullamcorper justo, nec, pellentesque.
            </p>
            <div class="footer__social-links">
              <a href="#">
                <span
                  class="iconify"
                  data-inline="false"
                  data-icon="carbon:logo-youtube"
                  style="font-size: 26px"
                ></span>
              </a>
              <a href="#">
                <span
                  class="iconify"
                  data-inline="false"
                  data-icon="entypo-social:vk"
                  style="font-size: 24px"
                ></span>
              </a>
              <a href="#">
                <span
                  class="iconify"
                  data-inline="false"
                  data-icon="bx:bxl-facebook"
                  style="font-size: 26px"
                ></span>
              </a>
              <a href="#">
                <span
                  class="iconify"
                  data-inline="false"
                  data-icon="bx:bxl-telegram"
                  style="font-size: 24px"
                ></span>
              </a>
              <a href="#">
                <span
                  class="iconify"
                  data-inline="false"
                  data-icon="simple-icons:etsy"
                  style="font-size: 16px"
                ></span>
              </a>
            </div>
          </div>
        </div>
        <div class="footer__last-row">
          <a href="#">(c) 2020 OJJO jewelry</a>
          <a href="#">Договор публичной офферты</a>
          <a href="#">Контрагентам</a>
          <a href="#">Сделано Figma.info</a>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import settings from "../settings.js";
import axios from "axios";

export default {
  data() {
    return {
      json: null,
      burgerState: false,
      showFullText: false,
      productsList: [],
      pageNumber: 0,
      pageSize: 3,
      filter: {
        brand: "",
        price: "",
        forHome: "",
        collection: "",
        season: "",
        event: "",
      },
      form: {
        email: "",
      },
    };
  },

  mounted() {
    axios
      .get("products.json")
      .then((response) => {
        this.json = response.data.products;
        console.log(response.data.products);
        this.loadData();
      })
      .catch((error) => console.log(error));
  },

  computed: {
    totalPage() {
      return Math.ceil(Object.keys(this.json).length / this.pageSize);
    },
  },

  methods: {
    loadData() {
      if (this.json !== null) {
        this.productsList.push(
          ...this.json.slice(
            this.pageNumber * this.pageSize,
            this.pageNumber * this.pageSize + this.pageSize
          )
        );
        if (this.pageNumber < this.totalPage) this.pageNumber++;
      }
    },

    onFilter() {
      axios
        .post(settings.URL, JSON.stringify(this.filter))
        .then((response) => console.log(response.data))
        .catch((error) => console.log(error));
    },

    onSubmit(e) {
      e.preventDefault();
      axios
        .post(settings.URL, JSON.stringify(this.form))
        .then((response) => console.log(response.data))
        .catch((error) => console.log(error));
    },
  },
};
</script>
