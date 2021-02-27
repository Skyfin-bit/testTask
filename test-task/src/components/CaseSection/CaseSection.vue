<template>
    <section class="case">
        <div class="container">
            <div class="case_inner">
                <header class="case_title">
                    <h3>Наши успехи</h3>
                    <h1>Дела Наших Клиентов</h1>
                    <h4>*Дела Показаны с Разрешения Клиентов</h4>
                </header>
                <div class="cases">
					<div 
						class="icon_wrp next"
						@click="onButtonNextClick">
						<icon-base
							icon="second_arrow"
							width="30px"
							height="30px"
							className="case_section_arrow"
							:styleList="{
								transform: 'translateY(-50%)',
							}"></icon-base>
					</div>
                    <div 
						class="icon_wrp prev"
						@click="onButtonPrevClick">
						<icon-base 
							icon="second_arrow"
							width="30px"
							height="30px"
							className="case_section_arrow"
							:styleList="{
								transform: 'translateY(-50%) rotate(180deg)'
							}"></icon-base>
					</div>
                    <div 
                        class="cases_inner"
                        :style="{transform: `translateX(${-caseItemMove * caseItemCount + initialItemMove}%)`}"
                        v-on:transitionend="onItemTranstionEnd"
                        ref="casesInner">
                        <case-section-item 
                            v-for="(caseItem, idx) in cases" 
                            :key="caseItem.id"
                            :caseItem="caseItem"
                            :idx="idx"
                            @select="onCaseItemClick(idx)"></case-section-item>
                    </div>
					<icon-base icon="second_arrow"></icon-base>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
/* eslint-disable no-unused-vars */
import CaseSectionItem from './CaseSectionItem';
import IconBase from '../IconBase';

export default {
    name: "CaseSection",
    components: {
        CaseSectionItem,
		IconBase
    },  
    data() {
        return{
            cases: [
                {
                    text: `«Компания с сиcтемным подходом к решению поставленной 
                            задачи, что, безусловно, сказывается на конечном результате. 
                            Дается объективная оценка подлежащей разрешению ситуации, 
                            не дают «несбыточных обещаний», досконально изучается предмет обращения»`,
                    name: "Mr. Emma",
                    post: "CEO of Hiday",
                    img: require('@/assets/cases/3.jpg'),
                    rating: 3,
                    class: '',
                    id: "lastClone",
                },
                {
                    text: `«Самые приятные и добрые впечатления 
                            от совместной работы. Очень грамотные 
                            и всегда приветливые, отзывчивые специалисты. 
                            Вы лучшие! Рекомендации с нашей стороны Вашей 
                            фирмы будут самые отличные и высокие. 
                            Желаем удачи и процветания».`,
                    name: "Mr.Oliver",
                    post: "CEO of Hiday",
                    img: require('@/assets/cases/1.jpg'),
                    rating: 3,
                    class: '',
                    id: 1,
                },
                {
                    text: `«Всегда доброжелательное отношение к клиенту, 
                            оперативность в выполнении запросов и оформлении документов. 
                            Спасибо Вам за квалифицированно выполненную работу.»`,
                    name: "Steve Lehman",
                    post: "CEO of Hiday",
                    img: require('@/assets/cases/2.jpg'),
                    rating: 3,
                    class: '',
                    id: 2,
                },
                {
                    text: `«Компания с сиcтемным подходом к решению поставленной 
                            задачи, что, безусловно, сказывается на конечном результате. 
                            Дается объективная оценка подлежащей разрешению ситуации, 
                            не дают «несбыточных обещаний», досконально изучается предмет обращения»`,
                    name: "Mr. Emma",
                    post: "CEO of Hiday",
                    img: require('@/assets/cases/3.jpg'),
                    rating: 3,
                    class: '',
                    id: 3,
                },
                {
                    text: `«Самые приятные и добрые впечатления 
                            от совместной работы. Очень грамотные 
                            и всегда приветливые, отзывчивые специалисты. 
                            Вы лучшие! Рекомендации с нашей стороны Вашей 
                            фирмы будут самые отличные и высокие. 
                            Желаем удачи и процветания».`,
                    name: "Mr.Oliver",
                    post: "CEO of Hiday",
                    img: require('@/assets/cases/1.jpg'),
                    rating: 3,
                    class: '',
                    id: "firstClone",
                },
            ],
			windowWidth: window.innerWidth,
            caseItemCount: 2,
            prevCaseItem: null,
            caseItemMove: 50,
            initialItemMove: 75,
        }
    },
    methods: {
        onCaseItemClick(idx) {
			if(window.innerWidth > 950) {
				if(this.prevCaseItem === this.cases[idx]) {
					return
				}
				this.$refs.casesInner.style.transition = '.3s linear';
				this.caseItemCount = idx + 1;
				if(this.prevCaseItem) {
					this.prevCaseItem.class = '';
				}
				this.changeActiveItem();
			}
        },
		onButtonNextClick() {
			if(this.caseItemCount < this.cases.length - 1) {
				this.$refs.casesInner.style.transition = '0.3s linear';
				this.caseItemCount += 1;
			}
		},
		onButtonPrevClick() {
			if(this.caseItemCount > 0) {
				this.$refs.casesInner.style.transition = '0.3s linear';
				this.caseItemCount -= 1;
			}
		},
        onItemTranstionEnd() {
            if(this.windowWidth > 950){
				if(this.cases[this.caseItemCount - 1].id === 'lastClone') {
                this.$refs.casesInner.style.transition = 'none';
				if(this.prevCaseItem) {
					this.prevCaseItem.class = '';
				}
                this.caseItemCount = this.cases.length - 1;
                this.changeActiveItem();
				}else if(this.cases[this.caseItemCount - 1].id === 'firstClone') {
                this.$refs.casesInner.style.transition = 'none';
                if(this.prevCaseItem) {
					this.prevCaseItem.class = '';
				}
				this.caseItemCount = 2;
                this.changeActiveItem();
				}
			}else{
				if(this.cases[this.caseItemCount].id === 'firstClone') {
					this.$refs.casesInner.style.transition = 'none';
					this.caseItemCount = 1;
				}
				if(this.cases[this.caseItemCount].id === 'lastClone') {
					this.$refs.casesInner.style.transition = 'none';
					this.caseItemCount = this.cases.length - 2;
				}
			}
        },
        changeActiveItem() {
			if(this.prevCaseItem) {
				this.prevCaseItem.class = '';
			}
            this.cases[this.caseItemCount - 1].class = ' active';
            this.prevCaseItem = this.cases[this.caseItemCount - 1];
        },
		setWindowWidth() {
			this.windowWidth = window.innerWidth
        },
		changeParams(x) {
			this.caseItemCount = x > 950 ? 2 : 1;
			this.caseItemMove = x > 950 ? 50 : 100;
			this.initialItemMove = x > 950 ? 75 : 0;
		},
		basedOnWindowWidth() {
			if(this.windowWidth <= 950) {
				this.changeParams(this.windowWidth);
			}
			if(this.windowWidth > 950) {
				this.changeParams(this.windowWidth);
				this.changeActiveItem()
			}
		}
    },
    mounted() {
        this.changeActiveItem();
		this.basedOnWindowWidth();
    },
	created() {
		window.addEventListener('resize', () => {
			this.setWindowWidth();
			this.basedOnWindowWidth();
		})
	}
}
</script>

<style scoped>
    .case{
        padding: 100px 0;
    }

    .case_title{
        margin-bottom: 60px ;
    }

    .case_title h3{
        display: inline-block;
        font-family: 'Lato', sans-serif;
        font-size: 12px;
        font-weight: 400;
        text-transform: uppercase;
        letter-spacing: 2px;
        color: #b1986f;

        padding-bottom: 5px;
        border-bottom: solid 1px #b1986f;
        margin-bottom: 10px;
    }

    .case_title h1{
        font-family: 'Playfair Display', serif;
        font-size: 36px;
        font-weight: 400;
        color: #333;

        margin-bottom: 15px;
    }

    .case_title h4{
        font-family: 'Lato', sans-serif;
        font-size: 15px;
        font-weight: 400;
        color: #b1b1b1;
    }

    .cases{
        width: 100%;
        overflow: hidden;
        position: relative;
    }

    .cases_inner{
        display: flex;
        transition: .3s linear;
    }

	.icon_wrp{
		display: none;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		position: absolute;
		top: 0;
		bottom: 0;
		z-index: 96;
	}

	.icon_wrp.next{
		right: 0;
		left: 80%;
		border-top-left-radius: 100px;
		border-bottom-left-radius: 100px;
		background: rgb(255,255,255);
		background: linear-gradient(90deg, rgba(255,255,255,0) 0%, rgba(11,29,55,0.3984944319524685) 100%);
	}

	.icon_wrp.prev{
		left: 0;
		right: 80%;
		border-top-right-radius: 100px;
		border-bottom-right-radius: 100px;
		background: rgb(255,255,255);
		background: linear-gradient(270deg, rgba(255,255,255,0) 0%, rgba(11,29,55,0.3984944319524685) 100%);
	}

	@media(max-width:950px) {
		.icon_wrp{
			display: flex;
			opacity: 0;
			transition: .2s linear;
		}

		.icon_wrp:hover{
			opacity: 1;
		}
	}

	@media(max-width: 500px) {
		.icon_wrp.next{
			left: 70%;
		}

		.icon_wrp.prev{
			right: 70%;
		}
	}
</style>