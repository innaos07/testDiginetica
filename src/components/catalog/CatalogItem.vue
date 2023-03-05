<template>
  <li class="catalog__column">
    <div
      class="catalog__item item-catalog"
      :class="{ 'item-catalog--empty': item.quantity == 0 }"
    >
      <a
        href="#"
        class="item-catalog__image"
        :class="{ 'item-catalog__image--empty': item.quantity == 0 }"
      >
        <span 
          v-if="item.isHit" 
          class="item-catalog__hit"
        >
          Хит продаж
        </span>
        <span 
          v-if="item.discount" 
          class="item-catalog__discount"
        > 
        {{  item.discount }}
        </span>
        <img :src="getImage(item.image)" />
      </a>
      <div class="item-catalog__info">
        <p class="item-catalog__brand">{{ item.brand }}</p>
        <a href="#" class="item-catalog__name">{{ item.name }}</a>
        <div 
          v-if="item.quantity" 
          class="item-catalog__prices"
        >
          <span class="item-catalog__price item-catalog__price--discount">{{ item.priceWithDiscount }}</span>
          <span class="item-catalog__price item-catalog__price--basic">{{ item.price }}</span>
        </div>

        <a 
          href="#" 
          v-if="item.quantity" 
          class="item-catalog__btn btn"
        >
          Купить
        </a>
        <button v-else class="item-catalog__btn item-catalog__btn--empty btn">Сообщить о поступлении</button>
      </div>
    </div>
  </li>
</template>

<script setup>
const props = defineProps({
  item: {
    type: Object,
    default: () => {},
  },
});

const getImage = (image) => {
  return new URL(`../../assets/image/${image}`, import.meta.url).href;
};
</script>


<style lang="scss">
@import "@/assets/scss/variables.scss";

.catalog__column {
  display: flex;
  justify-content: center;
  flex: 0 0 25%;
  padding: 0 12px;

  .item-catalog {
    display: flex;
    flex-direction: column;
    min-height: 356px;
    max-width: 333px;

    &:hover:not(.item-catalog--empty) {
      transition: all 0.5s;

      .item-catalog__image img {
        transform: scale(1.36);
        transition: all 0.5s;
      }

      .item-catalog__name {
        color: $color-font-hover;
        transition: all 0.8s;
      }
    }
  }

  .item-catalog__image {
    position: relative;
    padding-bottom: 200px;
    margin-bottom: 16px;
    overflow: hidden;

    &--empty img {
      opacity: 0.5;
    }

    img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .item-catalog__hit {
      position: absolute;

      top: 12px;
      left: 12px;
      display: block;
      padding: 8px;
      padding-right: 32px;
      border: 1px solid $color-light-grey;
      border-radius: 4px;
      line-height: 114%;
      color: $color-font-main;
      background-color: $color-white;
      background-image: url("../../assets/image/hit.svg");
      background-repeat: no-repeat;
      background-position: 87.3px 8.5px;
      z-index: 100;
    }

    .item-catalog__discount {
      position: absolute;
      bottom: 12px;
      left: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 6px 10px;
      border-radius: 4px;
      font-weight: 700;
      line-height: 14px;
      color: $color-white;
      background-color: $color-brand;
      z-index: 100;
    }
  }

  .item-catalog__info {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: flex-start;

    .item-catalog__brand {
      margin-bottom: 8px;
      color: $color-font-second;
    }

    .item-catalog__name {
      width: 100%;
      color: inherit;
      margin-bottom: 16px;
      display: -webkit-box;
      -webkit-line-clamp: 2;
      -webkit-box-orient: vertical;
      overflow: hidden;
    }
    .item-catalog__prices {
      display: flex;
      margin-bottom: 16px;
    }

    .item-catalog__price {
      display: block;

      &--discount {
        margin-right: 8px;
        font-weight: 700;
        font-size: 16px;
        line-height: 14px;
      }

      &--basic {
        font-size: 12px;
        line-height: 14px;
        color: $color-font-second;
        text-decoration: line-through;
      }
    }

    .item-catalog__btn {
      padding: 12px 16px;
      border: 1px solid $color-brand;
      border-radius: 4px;
      background-color: $color-white;
      color: $color-brand;
      cursor: pointer;

      &--empty {
        width: 100%;
        margin-top: 46px;
        border: 1px solid $color-font-second;
        color: $color-font-second;
      }
    }
  }

  @media (max-width: $xxl-width) {
    .item-catalog {
      max-width: 213px;
    }

    .item-catalog__info {
      .item-catalog__btn {
        margin-top: auto;

        &--empty {
          margin-top: 30px;
        }
      }
    }
  }

  @media (max-width: $xl-width) {
    flex: 0 0 33.33%;
    padding: 0 12px;

    .item-catalog {
      max-width: 100%;
      width: 100%;
      min-width: 165px;
    }
  }

  @media (max-width: $lg-width) {
    flex: 0 0 50%;
  }

  @media (max-width: $md-width) {
    flex: 0 0 33.33%;
    padding: 0 6px;
  }

  @media (max-width: $sm-width) {
    flex: 0 0 50%;
  }
}
</style>