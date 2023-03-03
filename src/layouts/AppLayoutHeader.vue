<template>
  <header class="header">
    <div class="container">
      <div class="header__body">
        <a class="header__logo logo" href="#">
          <img src="../assets/image/logo.svg" class="logo__img" alt="logo">
          <span class="logo__description">Логотип</span>
        </a>

        <a href="#" class="header__btn">Каталог</a>

        <form action="#" class="header__search search-form">
          <input 
            class="search-form__input"
            :class="{ 'search-form__input--active' : isActiveInput }" 
            type="text" 
            name="search" 
            placeholder="Поиск по 100 000 товаров"
            :value="search" 
            @input="setSearch"
          />
          <button 
            class="search-form__btn search-form__btn--delete"
            :class="{ 'search-form__btn--active' : isActiveInput }"
            @click="deleteSearch"
          >
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path fill-rule="evenodd" clip-rule="evenodd" d="M20.0001 10C20.0001 15.5228 15.5229 20 10.0001 20C4.47721 20 6.10352e-05 15.5228 6.10352e-05 10C6.10352e-05 4.47715 4.47721 0 10.0001 0C15.5229 0 20.0001 4.47715 20.0001 10ZM13.7072 7.70711C14.0977 7.31658 14.0977 6.68342 13.7072 6.29289C13.3166 5.90237 12.6835 5.90237 12.293 6.29289L10.0001 8.58579L7.70717 6.29289C7.31664 5.90237 6.68348 5.90237 6.29295 6.29289C5.90243 6.68342 5.90243 7.31658 6.29295 7.70711L8.58585 10L6.29295 12.2929C5.90243 12.6834 5.90243 13.3166 6.29295 13.7071C6.68348 14.0976 7.31664 14.0976 7.70717 13.7071L10.0001 11.4142L12.293 13.7071C12.6835 14.0976 13.3166 14.0976 13.7072 13.7071C14.0977 13.3166 14.0977 12.6834 13.7072 12.2929L11.4143 10L13.7072 7.70711Z" fill="#333333"/>
            </svg>

          </button>
          <button 
            type="submit" 
            class="search-form__btn search-form__btn--search btn" 
            :class="{ 'search-form__btn--active' : isActiveInput }">Найти</button>
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
import { ref } from 'vue';
  const menuList = [
    {
      id: '1',
      name: 'Информация о компании',
      link: '#',
    },
    {
      id: '2',
      name: 'Контакты',
      link: '#',
    },
    {
      id: '3',
      name: 'Полезные ссылки',
      link: '#',
    }
  ];
  const isActiveInput = ref(false);
  const search = ref('');

  const setSearch =(e)=> {    
    e.target.value? isActiveInput.value = true : isActiveInput.value = false;
    search.value = e.target.value.trim();
  }

  const deleteSearch =()=> {
    search.value = '';
    isActiveInput.value = false;
  }
</script>

<style lang="scss">
@import "@/assets/scss/variables.scss";
.header {
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
      font-family: 'Inter';
      font-weight: 400;
      font-size: 16px;
      line-height: 118.8%;
      color: $color-font-dark;
    }
  }

  .header__btn {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 15.5px 24px;
    border: 1px solid $color-light-blue;
    border-radius: 8px;

    font-family: 'Inter';
    font-weight: 500;
    font-size: 14px;
    line-height: 121%;
    color: $color-font-dark;
  }

  .header__search {
    margin: 0 24px;
  }

  .search-form {
    position: relative;
    flex: 1;
    max-width: 983px;
    
    .search-form__input {
      width: 100%;
      min-height: 48px;
      padding-right: 16px;
      padding-left: 48px;
      border: 1px solid $color-font-second;
      border-radius: 10px;
      background-image: url('@/assets/image/search.svg');
      background-repeat: no-repeat;
      background-position: 16px 12px;

      &--active {
        border-color: #73AFF4;
      }

      &:hover,
      &:focus {
        border-color: #73AFF4;
        outline: none;
        transition: all 0.5s;
      }
    }

    .search-form__btn {
      display: none;
      position: absolute;
      content: ''; 
      cursor: pointer;   

      &--active {
        display: block;
      } 

      &--delete {
        top: 14px;
        right: 83px;
        width: 20px;
        height: 20px;
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
      }
    }
  }

  .header__menu {
    margin-left: auto;
  }

  .menu__list {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;

    .menu__link {
      font-family: 'Inter';
      font-weight: 400;
      font-size: 14px;
      line-height: 121%;
      color: #393939;
    }
  }
}
</style>