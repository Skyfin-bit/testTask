<template>
    <div class="teammate_item">
        <img class="teammate_item_img" :src="teammate.img" alt="Teammate">
        <div class="teammate_item_content">
            <div class="teammate_item_title">{{ teammate.name }}</div>
            <div class="teammate_item_subtitle">{{ teammate.post }}</div>
        </div>
    </div>
</template>

<script>
/* eslint-disable no-unused-vars */
export default {
    name: "TeamSectionItem",
    props: {
        teammate: {
            type: Object,
            required: true,
            default: () => {}
        },
    },
    emits: ["move"],
    methods: {
        moveItems(x) {
            console.log(x)
        }
    }
}
</script>

<style scoped>
    .teammate_item {
        flex: 0 0 calc(100%/3);
        max-width: calc(100%/3);
        text-align: center;
        user-select: none;
    }

    .teammate_item_img{
        width: 100%;
        margin-bottom: -5px;
        -webkit-user-drag: none;
    }

    .teammate_item_content{
        padding: 20px;
        background: #091528;
        min-height: 175px;
        border-right: 2px solid #0b1d37;
    }

    .teammate_item_title{
         font-family: 'Playfair Display', serif;
        font-size: 26px;
        font-weight: 400;
        color: #fff;

        margin-bottom: 15px;
    }

    .teammate_item_subtitle{
        font-family: 'Lato', sans-serif;
        font-size: 12px;
        font-weight: 400;
        color: #b1986f;
        text-transform: uppercase;
        line-height: 1.5;
    }

    @media(max-width: 1000px) {
        .teammate_item_title{
            font-size: 18px;
        }

        .teammate_item_subtitle{
            font-size: 10px;
        }
    }

    @media(max-width: 840px) {
        .teammate_item{
            flex: 0 0 50%;
            max-width: 50%;
        }

        .teammate_item_content{
            min-height: 140px;
        }
    }

    @media(max-width: 500px) {
        .teammate_item{
            flex: 0 0 100%;
            max-width: 100%;
        }
    }
</style>