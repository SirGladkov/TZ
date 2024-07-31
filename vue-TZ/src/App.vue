<script setup lang="ts">
  import {faker } from "@faker-js/faker/locale/ru";

  const items:{isSale: boolean, cost: number, saleCost: number, name: String}[]=[];
  let iterator=0;
  while(iterator<8) {
    items.push({isSale: Math.random()>0.5 ? true : false, cost: Math.round(Math.random()*10000), saleCost: Math.round(Math.random()*10000), name: faker.commerce.productName() })
    iterator++
  }

</script>

<template>
<div>
  <section>
    <div class="bar-info base-wrapper">
        <ul class="bar-info-ul">
          <li>Доставка и оплата</li>
          <li>Гарантия и возврат</li>
          <li>EN</li>
        </ul>
    </div>
    <div class="header base-wrapper">
      <img src="@/assets/images/Logo.svg"/>
      <nav>
        <ul class="header-ul">
          <li>КАТАЛОГ</li>
          <li>О КОМПАНИИ</li>
          <li>КОНТАКТЫ</li>
        </ul>
      </nav>
      <div class="header-form">
        <div class="header-form-input">
          <input placeholder="Искать здесь...">
          <img src="@/assets/images/search-normal.svg"/>
        </div>
        <button class="header-button">
          <div class="header-button-item-badge">
            3
          </div>
          <div class="header-button-corf">
            <img src="@/assets/images/Vector.svg"/>
            <p>Корзина</p>
          </div>  
        </button>
      </div>
    </div>
  </section>
  <section class="base-wrapper">
    <div class="content-wrapper">
      <h1>Результаты поиска</h1>
      <div class="content-block-wrapper">
        <div v-for="(item) in items" v-bind:key="item.name" class="item">
          <img src="@/assets/images/item.png"/>
          <p class="item-name">{{item.name}}</p>
          <div class="typography-wrapper">
            <p class="sale-cost" v-if="item.isSale">{{`${item.saleCost} ₽`}}</p>
            <p class="base-cost" v-if="!item.isSale">{{`${item.cost} ₽`}}</p>
            <p class="base-cost-underline" v-if="item.isSale">{{`${item.cost} ₽`}}</p>
          </div> 
          <div v-if="item.isSale" class="item-sale-block">
            <p>Акция</p>
          </div>
          <div class="item-sale-block-detail-info-ob">
            <button class="item-sale-block-detail-info">
              Подробнее
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
  <section class="base-wrapper footer">
    <div>
      <img class="footer-logo" src="@/assets/images/logoFooter.svg"/>
      <p class="text-politic">Этот сайт защищен от спама службой reCAPTCHA Google. Политика конфиденциальности/Условия предоставления услуг</p>
    </div>
    <div >
      <div class="info-footer-block">
        <p class="footer-text-title">Адрес</p>
        <span>Текст, Текст, Текст</span>
      </div>
      <div class="info-footer-block">
        <p class="footer-text-title">Контакты</p>
        <p>Email: urban.dwelling@yandex.com</p>
        <p>Телефон: 8 (999) 999-99-99</p>
      </div>
    </div>
    <div class="services-footer-block-wrapper">
      <p class="footer-text-title">Услуги</p>
      <p>Каталог</p>
      <p>Контакты</p>
      <p>Доставка и оплата</p>
      <p>Гарантия и возврат</p>
    </div>
    <div class="card-footer-block-wrapper" >
      <p>Публичная оферта</p>
      <p>Политика персональных данных</p>
      <div class="card-footer-card-icon">
        <img src="@/assets/images/mir.svg" />
        <img src="@/assets/images/visa.svg" />
        <img src="@/assets/images/masterCard.svg" />
      </div>
    </div>
 </section>
</div>
</template>

<style scoped>


.base-wrapper{
  padding: 0 260px;
}

.bar-info{
  height: 40px;
  background: #231815;
  display: flex;
  justify-content: end;
  position: sticky;
 
}
.bar-info-ul{
  display: flex;
  align-items: center;
  gap: 70px;
  list-style-type: none;
  margin: 0;
  color: white;
  height: 100%;
}

.header{
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 80px;
  flex-flow: row nowrap;
  width: 100%;
  
}

.header-ul{
  display: flex;
  align-items: center;
  gap:100px;
  list-style-type: none;
}
.header-ul > li{
  font-family: Lato;
  font-size: 16px;
  font-weight: 600;
  line-height: 16px;
  text-align: left;

}
.header-form{
  display: flex;
  gap: 20px;
}

.header-form-input{
  display: flex;
  padding: 10px 16px;
  width: 170px;
  height: 40px;
  border: 1px solid #F5F5F5;
  border-radius: 20px;
}
.header-form-input > input {
  border: none;
  outline:none;
  width: 90%;
}


.header-form-button{
  border: none;
  background: white;

}

.header-form-input{
  width: 172px;
  height: 39px;
  border: none;
}

.header-button{
  border-radius: 100px;
  background: black;
  color: white;
  padding: 4px 19px;
  position: relative;
}

.header-button-corf{
  display: flex;
  align-items: center;
  gap:12px;
}
.header-button-item-badge{
  background: white;
  border-radius: 10px;
  width:18px;
  height: 18px;
  position: absolute;
  right: 74px;
  top: 2px;
  color: black;
}

.content-wrapper{
  padding-top: 40px;
  padding-bottom: 60px;
}
.content-wrapper > h1{
  font-family: Korataki;
  font-size: 44px;
  font-weight: 400;
  line-height: 61.6px;
  text-align: left;
  color: #231815;
}

.content-block-wrapper{
  display: grid;
  grid-template-columns:25% 25% 25% 25%;
  grid-row-gap: 50px;
  grid-column-gap: 30px;
}

.item{
  position: relative;
}
.item img{
  object-fit: contain;
  width: 100%;
  border-radius: 20px;
  max-width: 320px;
  max-height: 477px;
}
.item-name{
  font-family: Lato;
  font-size: 18px;
  font-weight: 700;
  line-height: 25.2px;
  text-align: left;
  color: #231815;
}
.item-sale-block{
  position: absolute;
  width: 126px;
  height: 38px;
  background: black;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 20px;
  top:10px;
  left: 10px;
}
.item-sale-block-detail-info-ob{
  opacity: 0;
  backdrop-filter: blur(0.9px);
  position: absolute;
    top: 380px;
    border: none;
  width: 320px;
  height: 88px;
  top: 389px;
  border-radius: 0px 0px 20px 20px;
  display:flex;
  align-items: center;
  justify-content: center;

}
.item:hover .item-sale-block-detail-info-ob {
  opacity: 1;
}

.item-sale-block-detail-info{
  background: #E45302;
  width: 258px;
  height: 48px;
  border-radius: 20px;
  color: white;
  font-family: Lato;
  font-size: 16px;
  font-weight: 600;
  line-height: 22.4px;
  cursor: pointer;
  border: none;

}
.item:hover .item-sale-block-detail-info {
  opacity: 1;
}

.typography-wrapper{
  display: flex;
  gap: 10px;
}
.sale-cost{
  font-family: Lato;
  font-size: 22px;
  font-weight: 600;
  line-height: 30.8px;
  text-align: left;
  color: #E45302;
}
.base-cost{
  font-family: Lato;
  font-size: 22px;
  font-weight: 700;
  line-height: 30.8px;
  text-align: left;
}
.base-cost-underline{
  font-family: Lato;
  font-size: 22px;
  font-weight: 700;
  line-height: 30.8px;
  text-align: left;
  text-decoration-line: line-through;
}
.footer{
  padding-top: 60px !important;
  padding-bottom: 60px !important;
  background: black;
  display: flex;
  gap: 110px;
  color: #F5F5F5;
}
.footer-logo{
  margin-bottom: 53px;
}
.text-politic{
  width: 322px;
  font-family: Roboto;
  font-size: 16px;
  font-weight: 400;
  line-height: 20.8px;
  text-align: left;
  color: #808080;
}
.info-footer-block{
  margin-bottom: 40px;
}
.info-footer-block p{
 margin-bottom: 20px;
}
.footer-text-title{
  font-family: Lato;
  font-size: 18px;
  font-weight: 700;
  line-height: 18px;
  text-align: left;
  color: #F5F5F5;
  margin-bottom: 20px;
;
}
.services-footer-block-wrapper{
  margin-bottom: 20px;
}
.services-footer-block-wrapper p{
 margin-bottom: 20px;
}
.card-footer-block-wrapper{
  text-align: end;
  color: #808080;
}
.card-footer-card-icon{
  margin-top: 72px;
  display: flex;
  gap: 33px;
  justify-content: end;
}

</style>