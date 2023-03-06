<template>
  <header class="header">
    <div class="container">
      <div class="header__body">
        <a class="header__logo logo" href="#">
          <img src="../assets/image/logo.svg" class="logo__img" alt="logo" />
          <span class="logo__description">Логотип</span>
        </a>

        <a href="#" class="header__btn">Каталог</a>

        <form action="#" class="header__search search-form">
          <input
            class="search-form__input"
            :class="{ 'search-form__input--active': isActiveInput }"
            type="text"
            name="search"
            placeholder="Поиск по 100 000 товаров"
            :value="search"
            @input="setSearch"
          />
          <button
            class="search-form__btn search-form__btn--delete"
            :class="{ 'search-form__btn--active': isActiveInput }"
            @click="deleteSearch"
          >
            <svg
              width="20"
              height="20"
              viewBox="0 0 20 20"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M20.0001 10C20.0001 15.5228 15.5229 20 10.0001 20C4.47721 20 6.10352e-05 15.5228 6.10352e-05 10C6.10352e-05 4.47715 4.47721 0 10.0001 0C15.5229 0 20.0001 4.47715 20.0001 10ZM13.7072 7.70711C14.0977 7.31658 14.0977 6.68342 13.7072 6.29289C13.3166 5.90237 12.6835 5.90237 12.293 6.29289L10.0001 8.58579L7.70717 6.29289C7.31664 5.90237 6.68348 5.90237 6.29295 6.29289C5.90243 6.68342 5.90243 7.31658 6.29295 7.70711L8.58585 10L6.29295 12.2929C5.90243 12.6834 5.90243 13.3166 6.29295 13.7071C6.68348 14.0976 7.31664 14.0976 7.70717 13.7071L10.0001 11.4142L12.293 13.7071C12.6835 14.0976 13.3166 14.0976 13.7072 13.7071C14.0977 13.3166 14.0977 12.6834 13.7072 12.2929L11.4143 10L13.7072 7.70711Z"
                fill="#333333"
              />
            </svg>
          </button>
          <button
            type="submit"
            class="search-form__btn search-form__btn--search btn"
            :class="{ 'search-form__btn--active': isActiveInput }"
          >
            Найти
          </button>
        </form>

        <nav class="header__menu menu">
          <ul class="menu__list">
            <li class="menu__item" v-for="item in menuList" :key="item.id">
              <a :href="item.link" class="menu__link">{{ item.name }}</a>
            </li>
          </ul>
        </nav>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref } from "vue";
const menuList = [
  {
    id: "1",
    name: "Информация о компании",
    link: "#",
  },
  {
    id: "2",
    name: "Контакты",
    link: "#",
  },
  {
    id: "3",
    name: "Полезные ссылки",
    link: "#",
  },
];
const isActiveInput = ref(false);
const search = ref("");

const setSearch = (e) => {
  e.target.value ? (isActiveInput.value = true) : (isActiveInput.value = false);
  search.value = e.target.value.trim();
};

const deleteSearch = () => {
  search.value = "";
  isActiveInput.value = false;
};
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";
.header {
  margin-bottom: 24px;
  font-family: "Inter";
  font-weight: 400;
  font-size: 14px;

  .header__body {
    display: flex;
    align-items: center;
    min-height: 72px;
    padding: 12px 0;
  }

  .header__logo {
    margin-right: 8px;
  }

  .logo {
    display: flex;
    align-items: center;
    padding: 14.5px 24px;

    .logo__img {
      width: 18px;
      height: 18px;
      margin-right: 11px;
    }

    .logo__description {
      font-family: inherit;
      font-size: 16px;
      line-height: 118.8%;
      color: $color-font-dark;

      &:hover,
      &:focus {
        color: $color-font-hover;
        transition: all 0.5s;
      }
    }
  }

  .header__btn {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 15.5px 24px;
    border: 1px solid $color-light-blue;
    border-radius: 8px;

    font-weight: 500;
    line-height: 121%;
    color: $color-font-dark;

    &:hover,
    &:focus {
      background: $color-light-blue;
      color: $color-white;
      transition: all 0.5s;
    }
  }

  .header__search {
    margin: 0 24px;
  }

  .search-form {
    position: relative;
    flex: 1;
    max-width: 983px;

    &::before {
      content: "";
      position: absolute;
      top: 12px;
      left: 17px;
      width: 24px;
      height: 24px;
      background-image: url("@/assets/image/search.svg");
      background-repeat: no-repeat;
      background-position: center;
    }

    .search-form__input {
      width: 100%;
      min-height: 48px;
      padding: 12px 16px;
      padding-left: 48px;
      border: 1px solid $color-font-second;
      border-radius: 10px;

      font-family: inherit;
      font-size: 16px;
      line-height: 150%;

      color: inherit;

      &::placeholder {
        font-family: inherit;
        font-size: 16px;
        line-height: 150%;
        color: $color-font-second;
      }

      &--active {
        padding-right: 114px;
        border-color: $color-light-blue;
      }

      &:hover,
      &:focus {
        border-color: $color-light-blue;
        outline: none;
        transition: all 0.5s;
      }
    }

    .search-form__btn {
      display: none;
      position: absolute;
      content: "";
      cursor: pointer;

      &--active {
        display: flex;
        justify-content: center;
        align-items: center;
      }

      &--delete {
        top: 14px;
        right: 83px;
        width: 24px;
        height: 24px;
        background-color: transparent;
        svg path {
          fill: #c2c2c2;
        }

        &:hover,
        &:focus {
          svg path {
            fill: $color-font-main;
            transition: all 0.5s;
          }
        }
      }

      &--search {
        top: 5px;
        right: 5px;
        padding: 12px 16px;
        background-color: $color-light-blue;
        border-radius: 8px;
        color: $color-white;

        &:hover,
        &:focus {
          outline: none;
          opacity: 0.7;
        }
      }
    }
  }

  .header__menu {
    margin-left: auto;
  }

  .menu__list {
    display: flex;
    column-gap: 20px;
    row-gap: 5px;
    flex-wrap: wrap;
    padding: 15.5px 0;

    .menu__link {
      display: block;
      font-family: inherit;
      line-height: 121%;
      color: #393939;

      &:hover,
      &:focus {
        color: $color-font-hover;
        transition: all 0.5s;
      }
    }
  }

  @media (max-width: $xxl-width) {
    .header__logo {
      margin-left: 28px;
    }

    .search-form {
      max-width: 479px;
      min-width: 300px;
    }
  }

  @media (max-width: $md-width) {
    margin-bottom: 0;

    .header__body {
      padding-top: 8px;
      padding-bottom: 12px;
    }

    .header__search {
      margin: 0;
    }

    .search-form {
      max-width: 100%;
      width: 100%;
      padding-left: 36px;
      background-image: url("@/assets/image/arrow-back.svg");
      background-repeat: no-repeat;
      background-position: 0px 9px;
      background-size: 20px 20px;

      &::before {
        display: none;
      }

      .search-form__input {
        min-height: 45px;
        padding-right: 91px;
        padding-left: 0;
        padding-top: 0;
        padding-bottom: 6px;
        border: none;
        border-bottom: 1px solid $color-border;
        border-radius: 0;

        font-family: "Inter";
        font-weight: 400;
        font-size: 16px;
        line-height: 88%;

        &--active {
          padding-right: 127px;
          border-color: $color-border;
        }

        &:hover,
        &:focus {
          border-color: $color-brand;
        }
      }

      .search-form__btn {
        &--delete {
          top: 9px;
          right: 91px;
          width: 20px;
          height: 20px;
          svg {
            width: 16.7px;
            height: 16.7px;
          }
        }

        &--search {
          top: 0;
          right: 0;
          display: block;
          border-radius: 5px;
          font-weight: 400;
          font-size: 16px;
          line-height: 88%;
        }
      }
    }

    .header__logo,
    .header__btn,
    .header__menu {
      display: none;
    }
  }
}
</style>