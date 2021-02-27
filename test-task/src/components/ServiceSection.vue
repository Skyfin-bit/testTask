<template>
    <section class="service" :style="serviceImg">
        <div class="container">
            <div class="service_inner">
                <h1 class="service_title">Наши услуги</h1>
                <h4 class="service_subtitle">Работаем По Всем Категориям - Выберите Нужное Направление</h4>
                <div class="service_cards">
                    <a href="#"  class="service_card_item">
                        <icon-base
                            icon="home" 
                            width="60px" 
                            height="60px"
                            iconColor="#b1986f" 
                            :styleList="{marginBottom: '20px'}"></icon-base>
                        <h1 class="service_card_item_title">Услуги Для Физических Лиц</h1>
                        <h4 class="service_card_item_subtitle"></h4>
                    </a>
                    <a href="#" class="service_card_item">
                        <icon-base 
                            icon="suitcase" 
                            width="60px" 
                            height="60px"
                            iconColor="#b1986f"
                            :styleList="{marginBottom: '20px'}"></icon-base>
                        <h1 class="service_card_item_title">Услуги Для Юридических Лиц</h1>
                        <h4 class="service_card_item_subtitle"></h4>
                    </a>
                    <a href="#" class="service_card_item">
                        <icon-base
                            icon="weight-scale" 
                            width="60px" 
                            height="60px"
                            iconColor="#b1986f"
                            :styleList="{marginBottom: '20px'}"></icon-base>
                        <h1 class="service_card_item_title">Палат Юридических Консультантов</h1>
                        <h4 class="service_card_item_subtitle">Для Юристов</h4>
                    </a>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
/* eslint-disable no-unused-vars */
import IconBase from './IconBase';

export default {
    name: 'ServiceSection',
    components: {
        IconBase
    },
    data() {
        return{
            serviceImg: {
                background: `fixed url(${require('@/assets/service/service.jpg')}) center no-repeat`
            }
        }
    }
}
</script>

<style scoped>
    .service{
        width: 100%;
        padding: 100px 0;
    }

    .service_inner{
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .service_title{
        font-family: 'Playfair Display', serif;
        font-size: 36px;
        font-weight: 400;
        color: #fff;
        text-align: center;

        margin-bottom: 15px;
    }

    .service_subtitle{
        font-family: 'Lato', sans-serif;
        font-size: 15px;
        font-weight: 400;
        color: #9c9c9c;
        text-align: center;

        margin-bottom: 50px;
    }

    .service_cards{
        display: flex;
        align-items: center;
        justify-content: space-between;
        flex-wrap: wrap;
    }

    .service_card_item{
        position: relative;
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: center;

        width: 30%;
        padding: 40px;

        background-color: rgba(11, 29, 55, 0.8);
        border: solid 2px #c9b89c1f;
        text-decoration: none;

        transition: .2s linear;
    }  

    .service_card_item:hover{
        border: solid 2px #6e6352;
    }

    .service_card_item::before{
        position: absolute;
        content: '';
        top: 0;
        left: 50%;
        width: 2px;
        height: 20px;
        background-color: #c9b89c1f;
        transition: .2s linear;
    }

    .service_card_item:hover::before{
        background-color: #6e6352;
    }

    .service_card_item_title{
        font-family: 'Playfair Display', serif;
        font-size: 24px;
        font-weight: 400;
        color: #fff;

        margin-bottom: 15px;
        transition: .2s linear;
    }

    .service_card_item_title:hover{
        text-decoration: underline;
    }

    .service_card_item:hover > .service_card_item_title{
        color: #6e6352;
    }

    .service_card_item_subtitle{
        font-family: 'Lato', sans-serif;
        font-size: 15px;
        font-weight: 400;
        color: #9c9c9c;
    }

    @media(max-width: 1000px) {
        .service_card_item_title{
            font-size: 20px;
        }
    }

    @media(max-width: 700px) {
        .service_card_item{
            width: 100%;
        }

        .service_card_item:not(:last-child) {
            margin-bottom: 30px;
        }
    }
</style>