<template>
    <section class="team">
        <div class="container">
            <div class="team_inner">
                <div class="team_title">Наша команда</div>
                <div class="team_subtitle">Ключевой состав нашей компании</div>
                <div class="teammates">
                    <div 
                        class="teammates_inner" 
                        :style="{transform: `translateX(${-teamItemMove * teamItemCount}%)`}"
                        v-on:transitionend="onTranstionEnd"
                        ref="teammatesInner">
                        <team-section-item
                            v-for="(teammate, idx) in team"
                            :key="teammate.id"
                            :teammate="teammate"
                            :idx="idx"></team-section-item>
                    </div>
					<div class="teammates_btns">
						<button @click="onPrevBtn" class="prevBtn">
							<icon-base
								icon="arrow"
								width="40px"
								height="40px"
								:styleList="{transform: 'rotate(180deg)'}"></icon-base>
						</button>
						<button @click="onNextBtn" class="nextBtn">
							<icon-base
								icon="arrow"
								width="40px"
								height="40px"></icon-base>
						</button>
					</div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
/* eslint-disable no-unused-vars */
import TeamSectionItem from './TeamSectionItem';
import IconBase from '../IconBase.vue';

export default {
    name: "TeamSection",
    components: {
        TeamSectionItem,
		IconBase
    },
    data() {
        return{
            team: [
                {
                    name: 'Жаманбалинов Ерсаин Сергазыевич',
                    post: 'Председатель аттестационной комиссии палаты',
                    img: require('@/assets/team/4.jpg'),
                    id: "lastClone"
                },
                {
                    name: 'Құдайберген Оралбай Бижанұлы', 
                    post: 'Председатель "Палаты юридических консультантов города Шымкент"', 
                    img: require('@/assets/team/1.jpg'),
                    id: 1
                },
                {
                    name: 'Маханов Бауржан Абдуманопович',
                    post: 'Зам.председателя палаты',
                    img: require('@/assets/team/2.jpg'),
                    id: 2
                },
                {
                    name: 'Жанбаев Аскар Амирович',
                    post: 'Председатель ревизионной комиссии палаты',
                    img: require('@/assets/team/3.jpg'),
                    id: 3
                },
                {
                    name: 'Жаманбалинов Ерсаин Сергазыевич',
                    post: 'Председатель аттестационной комиссии палаты',
                    img: require('@/assets/team/4.jpg'),
                    id: 4
                },
                {
                    name: 'Құдайберген Оралбай Бижанұлы', 
                    post: 'Председатель "Палаты юридических консультантов города Шымкент"', 
                    img: require('@/assets/team/1.jpg'),
                    id: "firstClone"
                },
                {
                    name: 'Маханов Бауржан Абдуманопович',
                    post: 'Зам.председателя палаты',
                    img: require('@/assets/team/2.jpg'),
                    id: "secondClone",
                },
                {
                    name: 'Жанбаев Аскар Амирович',
                    post: 'Председатель ревизионной комиссии палаты',
                    img: require('@/assets/team/3.jpg'),
                    id: "thirdClone"
                },
            ],
            teamItemCount: 1,
            teamItemMove: 100 / 3,
			windowWidth: window.innerWidth,
        }
    },
    methods: {
        onNextBtn() {
			this.basedOnWindowWidth();
            if(this.teamItemCount < this.team.length - 3) {
				this.$refs.teammatesInner.style.transition = '.3s linear';
                this.teamItemCount += 1;
            }
        },
        onPrevBtn() {
			this.basedOnWindowWidth();
            if(this.teamItemCount > 0) {
				this.$refs.teammatesInner.style.transition = '.3s linear';
                this.teamItemCount -= 1;
            }
        },
        onTranstionEnd() {
            if(this.team[this.teamItemCount].id === 'lastClone') {
                this.$refs.teammatesInner.style.transition = 'none';
                this.teamItemCount = this.team.length - 4;
            }else if(this.team[this.teamItemCount].id === 'firstClone') {
                this.$refs.teammatesInner.style.transition = 'none';
                this.teamItemCount = 1;
            }
        },
		basedOnWindowWidth() {
			if(window.innerWidth > 840) {
                this.teamItemMove = 100 / 3
            }
            if(window.innerWidth <= 840) {
                this.teamItemMove = 50
            }
            if(window.innerWidth <= 500) {
                this.teamItemMove = 100
            }
		}
    },
    mounted() {
		this.basedOnWindowWidth();
        setInterval(this.onNextBtn, 5000);
    },
	created() {
		window.addEventListener('resize', () => {
			this.windowWidth = window.innerWidth;
			this.basedOnWindowWidth();
		})
	}
}
</script>

<style scoped>
    .team{
        width: 100%;
        background-color: #0b1d37;
        padding: 100px 0;
    }

    .team_inner{
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .team_title{
        font-family: 'Playfair Display', serif;
        font-size: 36px;
        font-weight: 400;
        color: #fff;
		text-align: center;

        margin-bottom: 15px;
    }

    .team_subtitle{
        font-family: 'Lato', sans-serif;
        font-size: 12px;
        font-weight: 400;
        color: #b1986f;
        text-transform: uppercase;
        letter-spacing: 0.2rem;
        text-align: center;

        padding-bottom: 5px;
        border-bottom: solid 1px rgba(177, 152, 111, 0.5);
        margin-bottom: 60px;
    }

    .teammates{
        width: 100%;
        overflow: hidden;
    }


    .teammates_inner{
        width: 100%;
        display: flex;
        transition: .3s linear;
		margin-bottom: 30px;
    }

	.teammates_btns{
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.teammates_btns button{
		padding: 0 20px;
		background-color: #b1986f;
		border: solid 2px #b1986f;
		border-radius: .25rem;
		transition: .2s linear;
	}

	.teammates_btns button:hover{
		background-color: #000;
	}

	.teammates_btns button:not(:last-of-type) {
		margin-right: 30px;
	}

	.iconPrevBtn{
		width: 30px;
		height: 30px;
	}

	@media(max-width: 300px) {
		.teammates_btns button:not(:last-of-type) {
			margin-right: 10px;
		}

		.teammates_btns button{
			padding: 0 10px;
		}
		
		.teammates_inner{
			margin-bottom: 10px;
		}
	}
</style>