
<template>
  <section class="banner">
    <div class="container">
      <div class="banner-item">
        <h2 class="banner-item--title">
          Онлайн-сервис <br />
          доставки еды на дом
        </h2>
        <p class="banner-item--subtitle">
          Блюда из любимого ресторана привезет курьер в перчатках, маске и с
          антисептиком
        </p>
      </div>
    </div>
  </section>

  <section class="products">
    <div class="container">
      <div class="products-header">
        <h3 class="products-header--title">Рестораны</h3>
        <input
          type="text"
          class="products-header--search"
          placeholder="Поиск блюд и ресторанов"
        />
      </div>

      <div class="products-wrapper" id="rests-container">

        <router-link
          class="products-card"
          v-for="rest in restArray"
          :key="rest.id"
					:to="`/rest?id=${rest.id}`"
        >
          <div class="products-card__image">
            <img :src="getUrl(rest.image)" alt="rests-1" />
          </div>
          <div class="products-card__descript">
            <div class="products-card__descript--row">
              <h4 class="products-card__descript--title">{{ rest.title }}</h4>
              <div class="products-card__descript--badge">{{ rest.time }}</div>
            </div>
            <div class="products-card__descript--row">
              <div class="products-card__descript-info">
                <div class="products-card__descript-info-raiting">
                  <img src="../assets/images/icons/star.svg" alt="star" />
                  {{ rest.rating }}
                </div>
                <div class="products-card__descript-info--price">{{ rest.price }}</div>
                <div class="products-card__descript-info--group">{{ rest.type }}</div>
              </div>
            </div>
          </div>
        </router-link>
        
      </div>
    </div>
  </section>
</template>

<script setup>
import { restArray } from '../constants/rests'; 

const getUrl = (name) => {
	return new URL(`../assets/images/rests/${name}`, import.meta.url)
	// return `../assets/images/rests/image1.jpg`
}

</script>