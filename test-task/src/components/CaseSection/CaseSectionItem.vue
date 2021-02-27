<template>
    <div 
        :class="'case_item' + caseItem.class" 
        @click="onCaseItemClick"
        ref="caseItem">
        <div class="case_text">
            <p>{{ caseItem.text }}</p>
        </div>
        <div class="author">
            <img :src="caseItem.img" alt="" class="author_img">
            <div class="author_content">
                <h1 class="author_name">{{ caseItem.name }}</h1>
                <h3 class="author_post">{{ caseItem.post }}</h3>
                <div class="author_rating"></div>
            </div>
        </div>
    </div>
</template>

<script>
/* eslint-disable no-unused-vars */

export default {
    name: "CaseSectionItem",
    props: {
        caseItem: {
            type: Object,
            required: true,
            default: () => {}
        },
        idx: {
            type: Number,
            require: true,
            default: 1
        }
    },
    emits: ['select'],
    methods: {
        onCaseItemClick() {
            this.$emit('select')
        }
    },
}
</script>

<style scoped>
    .case_item{
        flex: 0 0 50%;
        max-width: 50%;
        text-align: center;
        user-select: none;
        opacity: 0.1;
        margin: 0 10px;
    }

    .case_item.active{
        opacity: 1;
    }

    .case_text{
        position: relative;
        padding: 30px;
        background-color: #0b1d37;
        border: solid 2px #b1986f;

        margin-bottom: 50px;
        line-height: 1.6;
    }

    .case_text::after{
        position: absolute;
        content: "";
        left: 20%;
        bottom: -15px;
        width: 30px;
        height: 30px;
        background-color: #0b1d37;
        border: solid 2px #b1986f;

        transform: rotate(45deg);
    }

    .case_text p{
        font-family: 'Lato', sans-serif;
        font-size: 13px;
        font-weight: 400;
        font-style: italic;
        color: #d0d0d0;

        text-align: center;
        letter-spacing: 0.6px;
    }

    .author{
        display: flex;
        justify-content: flex-start;
        align-items: center;
        padding-left: 15%;
    }

    .author img{
        border-radius: 50px;
        margin-right: 20px;
    }

    @media(max-width: 950px) {
        .case_item{
            flex: 0 0 100%;
            max-width: 100%;
            opacity: 1;
            margin: 0;
        }
    }

	@media(max-width: 350px) {
		.author{
			padding: 5%;
		}
	}

	@media(max-width: 290px) {
		.author{
			flex-direction: column;
			justify-content: center;
		}

		.author img{
			margin-bottom: 10px;
		}
	}
</style>