<template>
    <section class="help" :style="helpImg">
		<div class="help_overlay"></div>
		<div class="container">
			<div class="help_inner">
				<div class="price">
					<h1 class="price_title"><span>Скачайте</span> Прайс</h1>
					<h3 class="price_subtitle">С ценами и описанием каждой позиции наших услуг</h3>
					<form>
						<input type="text" class="name" placeholder="Введите имя">
						<input type="number" class="phone_number" placeholder="Введите телефон">
					</form>
					<a 
						class="price_btn" 
						href="#"
						@mouseenter="hoverBtn"
						@mouseleave="hoverBtn">
						<div class="icon_wrp">
							<icon-base
								icon="download"
								:styleList="{
									fill: svgFill,
									transform: 'rotate(90deg)',
								}"
								className="help_section_price_btn"></icon-base>
						</div>
						<span>Скачать</span>
					</a>
				</div>
				<div class="consultation">
					<h3 class="cons_overhead">Получите консультацию прямо сейчас.</h3>
					<h1 class="cons_title">
						Просто позвоните по телефону <span>7-(701)-026-5309</span> для получения помощи
					</h1>
					<a class="cons_btn" href="#">
						<span>Free Consultation</span>
					</a>
				</div>
			</div>
		</div>
    </section>
</template>

<script>
import IconBase from './IconBase';

export default {
    name: "HelpSection",
	components: {
		IconBase
	},
	data() {
		return{
			helpImg: {
                background: `fixed url(${require('@/assets/help/help.jpg')}) center no-repeat`
            },
			svgFill: '#151a28',
			isHovered: false,
		}
	},
	methods: {
		hoverBtn() {
			this.isHovered = !this.isHovered;
			if(this.isHovered) {
				this.svgFill = '#ac9265'
			}else{
				this.svgFill = '#151a28'
			}
		}
	}
}
</script>

<style scoped>
	.help{
		position: relative;
		padding: 100px 0;
	}

	.help_overlay{
		position: absolute;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		background-color: rgba(11, 29, 55, 0.7);
	}

	.help_inner{
		position: relative;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}



	/* Price */
	
	.price{
		padding: 50px;
		background-color: #0b1d37fc;
		display: flex;
		flex-direction: column;
		justify-content: center;
		text-align: center;
		border: solid 1px rgba(172, 146, 101, 0.2);
	}

	.price_title{
        font-family: 'Playfair Display', serif;
		font-size: 36px;
		font-weight: 700;
		color: #fff;

		margin-bottom: 10px;
	}

	.price_title span{
		color: #ac9265;
	}

	.price_subtitle{
        font-family: 'Lato', sans-serif;
		font-size: 13px;
		font-style: italic;
		font-weight: 400;
		color: #cacaca;
		letter-spacing: 0.5px;

		margin-bottom: 70px;
	}

	form{
		display: flex;
		flex-direction: column;
	}

	form input{
        font-family: 'Playfair Display', serif;
		font-size: 18px;
		color: #cdc5b7;

		padding: 15px;
		background-color: #0b1d37fc;
		border: none;
		border-bottom: solid 1px #ac9265;
	}

	form input:focus{
		outline: 5px solid #082d5a;
	}

	.name{
		margin-bottom: 20px;
	}

	.phone_number{
		margin-bottom: 70px;
	}

	input::-webkit-outer-spin-button,
	input::-webkit-inner-spin-button {
		-webkit-appearance: none;
		margin: 0;
	}

	input[type=number] {
		-moz-appearance: textfield;
	}

	.price_btn{
		display: flex;
		align-items: center;
		justify-content: center;
		padding: 10px 40px;
		background-color: #151a28;
		border: none;
		border-radius: 2rem;
		transition: .2s linear;
	}

	.price_btn:hover{
		background-color: #ac9265;
	}

	.price_btn:hover > span{
		color: #fff;
		text-decoration: underline;
	}

	.price_btn:hover > .icon_wrp{
		background-color: #fff;
	}

	.icon_wrp{
		padding: 4px;
		background-color: #ac9265;
		border-radius: 2rem;
		margin-right: 10px;
		transition: .2s linear;
	}

	.price_btn span{
        font-family: 'Playfair Display', serif;
		font-size: 34px;
		font-weight: 700;
		color: #ac9265;
		transition: .2s linear;
	}



	/* Consultation */

	.consultation{
		width: 100%;
		max-width: 600px;
		padding-left: 50px;
	}

	.cons_overhead{
		font-family: 'Lato', sans-serif;
		font-size: 14px;
		color: #b1986f;
		text-transform: uppercase;

		margin-bottom: 30px;
	}

	.cons_title{
		font-family: 'Playfair Display', serif;
		font-size: 36px;
		font-weight: 400;
		color: #fff;

		margin-bottom: 30px;
	}

	.cons_title span{
		color: #ac9265;
		white-space: nowrap;
	}

	.cons_btn{
		display: inline-block;
		background-color: #b1986f47;
		padding: 13px 30px;
		border: solid 2px #ac9265;
		border-radius: 2rem;

		transition: .2s linear;
	}

	.cons_btn span{
		font-family: 'Lato', sans-serif;
		font-size: 14px;
		color: #fff;
	}

	.cons_btn:hover{
		background-color: #ac9265;
	}

	.cons_btn:hover > span{
		text-decoration: underline;
	}

	@media(max-width: 1000px) {
		.help_inner{
			flex-direction: column;
		}

		.price{
			width: 100%;
			margin-bottom: 100px;
		}

		.consultation{
			max-width: 100%;
			text-align: center;
			padding: 0;
		}

		.price_btn{
			min-width: 70%;
			margin: 0 auto;
		}
	}

	@media(max-width: 550px) {
		.price_title{
			font-size: 25px;
		}

		.price_btn span{
			font-size: 20px;
		}

		.icon_wrp{
			padding: 2px 5px;
		}

		.cons_title{
			font-size: 24px;
		}

		.cons_overhead{
			font-size: 12px;
		}
	}

	@media(max-width: 380px) {
		.price{
			padding: 30px;
		}

		form input{
			font-size: 14px;
		}
	}

	@media(max-width: 300px) {
		.price_btn{
			padding: 10px 20px;
		}

		.price_btn span{
			font-size: 14px;
		}

		.icon_wrp{
			padding: 1px 5px;
		}

		.cons_title{
			font-size: 20px;
		}

		.cons_overhead{
			font-size: 10px;
		}

		.cons_btn{
			padding: 13px 20px;
		}

		.cons_btn span{
			font-size: 12px;
		}
	}
</style>