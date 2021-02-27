<template>
    <footer class="footer">
        <div class="container">
            <div class="footer_inner">
                <div class="footer_column footer_item first">
                    <div class="footer_img">
                        <img src="@/assets/footer/footer.png" alt="FooterImg">
                    </div>
                    <h3 class="footer_title">Палата Юридических Консультантов Города Шымкент</h3>
                </div>
                <div class="footer_column footer_item second">
					<a class="footer_btn" href="#">
						<span>Заказать звонок</span>
					</a>
					<ul class="footer_list">
						<li class="footer_list_item">
							<a href="#">Главная</a>
						</li>
						<li class="footer_list_item">
							<a href="#">Физ.Лица</a>
						</li>
						<li class="footer_list_item">
							<a href="#">Юр.Лица</a>
						</li>
						<li class="footer_list_item">
							<a href="#">Команда</a>
						</li>
						<li class="footer_list_item">
							<a href="#">Прайс</a>
						</li>
					</ul>
				</div>
                <div class="footer_column footer_item  third">
					<a class="footer_btn" href="#">
						<span>Оставить заявку</span>
					</a>
					<ul class="footer_list">
						<li class="footer_list_item">
							<a href="#">Наши услуги</a>
						</li>
						<li class="footer_list_item">
							<a href="#">Наши проекты</a>
						</li>
						<li class="footer_list_item">
							<a href="#">Задать вопросы</a>
						</li>
						<li class="footer_list_item">
							<a href="#">Контакты</a>
						</li>
						<li class="footer_list_item">
							<a href="#">Для юристов</a>
						</li>
					</ul>
				</div>
                <div class="contacts footer_item fourth">
					<h1 class="contacts_title">Контакты</h1>
					<div class="contacts_content">
						<div class="contacts_item">
							<h3>
								<span>&#128393;</span>
								г. Шымкент / Улица 12
							</h3>
						</div>
						<div class="contacts_item cross_wrp">	
							<h3>
								<span class="cross">&#x2A2F;</span>
								Пн - Вс / 8.00 - 18.00 <br> 
								Перерыв / 13.00 - 14.00
							</h3>
						</div>
						<div class="contacts_item">
							<h3>
								<span>&#128393;</span>
								г. Шымкент / Улица 12
							</h3>
						</div>
					</div>
				</div>
            </div>
			<div class="footer_bottom">
				<h3>
					© Copyright 2021 | 
					<a href="#">Палата Юридических Консультантов Города Шымкент</a> 
					| Все Права Защищены.
				</h3>
			</div>
        </div>
    </footer>
</template>

<script>
export default {
	name: 'FooterSection',
	data() {
        return{
        }
    }
}
</script>

<style scoped>
    .footer{
        background-color: #0b1d37;
    }

	.footer_inner{
		display: flex;
		justify-content: space-between;
		flex-wrap: wrap;
		padding: 100px 0;

		border-bottom: solid 1px rgba(255, 255, 255, 0.1);
	}

	.footer_column{
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-right: 20px;
	}

	.footer_img{
		display: flex;
		justify-content: center;
		width: 100%;
		margin-bottom: 30px;
	}

	.footer_img img{
		max-width: 100%;
	}

	.footer_title{
		font-family: 'Lato', sans-serif;
        font-size: 14px;
		font-weight: 400;
		color: #fff;

		text-align: center;
	}

	.footer_btn{
		background-color: #b1986f47;
		padding: 13px 30px;
		border: solid 2px #ac9265;
		border-radius: 2rem;
		transition: .2s linear;

		font-family: 'Lato', sans-serif;
        font-size: 14px;
		color: #fff;

		margin-bottom: 30px;
	}

	.footer_btn:hover{
		background-color: #ac9265;
	}

	.footer_btn:hover > span{
		text-decoration: underline;
	}

	.footer_list_item{
		position: relative;
		list-style: none;
	}

	.footer_list_item::before{
		position: absolute;
		content: url('../assets/footer/arrow.svg');
		width: 8px;
		left: -20px;
	}

	.footer_list_item a{
		font-family: 'Lato', sans-serif;
        font-size: 16px;
		font-weight: 400;
		color: #fff;

		transition: .1s linear;
	}

	.footer_list_item a:hover{
		color: #ac9265;
	}

	.footer_list_item:not(:last-child) {
		margin-bottom: 20px;
	}

	.contacts{
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.contacts_title{
		font-family: 'Playfair Display', serif;
		font-size: 24px;
		font-weight: 400;
		color: #fff;

		margin-bottom: 30px;
	}

	.contacts_item{
		margin-bottom: 10px;
	}

	.contacts_item h3{
		font-family: 'Lato', sans-serif;
		font-size: 16px;
		font-weight: 400;
		color: #fff;
	} 
	
	.contacts_item h3 span{
		margin-right: 10px;
	}

	.cross_wrp h3{
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.cross{
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		font-size: 23px;
	}

	.first{
		order: 1;
	}

	.second{
		order: 2;
	}

	.third{
		order: 3;
	}

	.fourth{
		order: 4;
	}

	.footer_bottom{
		display: flex;
		flex-direction: column;
		justify-content: center;
		text-align: center;
		padding: 35px 0;
	}

	.footer_bottom h3{
		font-family: 'Lato', sans-serif;
		font-size: 16px;
		font-weight: 400;
		color: #fff;
	}

	.footer_bottom h3 a{
		color: #b1986f;
	}

	@media(max-width: 1060px) {
		.footer_inner{
			justify-content: center;
		}

		.footer_item{
			width: 40%;
		}

		.first{
			margin-bottom: 50px;
		}

		.second{
			margin-bottom: 50px;
		}

		.fourth{
			order: 1;
			margin-bottom: 50px;
		}
	}

	@media(max-width: 630px) {
		.footer_inner{
			flex-direction: column;
			justify-content: center;
			align-items: center;
		}

		.footer_item{
			width: 100%;
		}

		.cross_wrp h3{
			justify-content: flex-start;
			align-items: flex-start;
		}

		.contacts_title{
			margin-bottom: 20px;
		}

		.footer_bottom h3{
			font-size: 13px;
		}
	}
</style>