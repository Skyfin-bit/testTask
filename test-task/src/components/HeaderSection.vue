<template>
    <header class="header" ref="header">
        <div class="topbar">
            <div class="container">
                <div class="topbar_inner">
                    <div class="order_call_btn">
                        <a class="topbar_btn_item" href="#">
                            <span>Заказать звонок</span>
                        </a>
                    </div>
                    <div class="topbar_btns">
                        <a class="topbar_btn_item" href="#">
                            <icon-base
                                icon="message"
                                width="16px" 
                                height="16px"
                                icon-color="#fcab03"
								:styleList="{marginRight: '5px'}"></icon-base>
                            <span>Написать</span>
                        </a>
                        <a class="topbar_btn_item" href="#">
                            <icon-base 
                                icon="call"
                                width="16px" 
                                height="16px"
                                icon-color="#fcab03"
								:styleList="{marginRight: '5px'}"></icon-base>
                            <span>Позвонить</span>
                        </a>
                        <a class="topbar_btn_item" href="#">
                            <icon-base 
                                icon="whatsapp"
                                width="16px" 
                                height="16px"  
                                icon-color="#fcab03"
								:styleList="{marginRight: '5px'}"></icon-base>
                            <span>Написать WA</span>
                        </a>
                    </div>
                </div>
            </div>
        </div>

        <nav 
			:class="{navbar: true, fixed: fixedNavbar}">
            <div class="container">
                <div class="navbar_inner">
                    <a href="#" class="logo">
                        <img src="@/assets/header/logo.png" alt="Logo">
                    </a>
                    <div class="nav_links">
                        <a href="#" class="nav_link">Главная</a>
                        <a href="#" class="nav_link">Для Физ.Лиц</a>
                        <a href="#" class="nav_link">Для Юра.Лиц</a>
                        <a href="#" class="nav_link">Для Юристов</a>
                        <a href="#" class="nav_link">Контакты</a>
                        <div 
							:class="{menu_btn: true, active: isOpened}"
							@click="onMenuBtn">
                            <span class="menu_first"></span>
                            <span class="menu_second"></span>
                            <span class="menu_third"></span>
                        </div>
                    </div>
                </div>
            </div>
        </nav>
    </header>

	<div 
		class="menu"
		ref="menu">
		<div 
		class="menu_inner"
		:style="{
			transition: '.3s linear',
			height: initialMenuHeight,
			maxHeight: menuHeight,
		}">
			<div class="topbar_btns_menu_wrp">
				<a class="topbar_menu_order_call_btn" href="#">
					<span>Заказать звонок</span>
				</a>
				<div class="topbar_menu_btns">
					<a class="topbar_menu_btn_item" href="#">
						<icon-base 
							icon="message"
							width="16px" 
							height="16px"
							icon-color="#fcab03"></icon-base>
					</a>
					<a class="topbar_menu_btn_item" href="#">
						<icon-base 
							icon="call"
							width="16px" 
							height="16px"
							icon-color="#fcab03"></icon-base>
					</a>
					<a class="topbar_menu_btn_item" href="#">
						<icon-base 
							icon="whatsapp"
							width="16px" 
							height="16px"
							icon-color="#fcab03"></icon-base>
					</a>
				</div>
			</div>
			<div class="menu_nav_links">
				<a href="#" class="menu_nav_link_item">Главная</a>
				<a href="#" class="menu_nav_link_item">Для Физ.Лиц</a>
				<a href="#" class="menu_nav_link_item">Для Юра.Лиц</a>
				<a href="#" class="menu_nav_link_item">Для Юристов</a>
				<a href="#" class="menu_nav_link_item">Контакты</a>
			</div>
		</div>
	</div>

	

    <div class="intro" :style="introImg">
        <div class="container">
            <div class="intro_inner">
                <div class="intro_img">
                    <img src="@/assets/header/logo.png" alt="">
                </div>
                <h1 class="intro_title">Палата Юридических Консультантов города Шымкент</h1>
                <h4 class="intro_subtitle">Первая консультация бесплатна!</h4>
                <div class="intro_btns">
                    <div class="intro_btn_item_wrp">
                        <a href="#" class="intro_btn_item">
                            <span>Скачать Прайс</span>
                        </a>
                    </div>
                    <div class="intro_btn_item_wrp">
                        <a href="#" class="intro_btn_item">
                            <span>Оставить Заявку</span>
                        </a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import IconBase from './IconBase';

export default {
    name: 'Header',
    components: {
        IconBase
    },
    data() {
        return{
            introImg: {
                background: `url(${require('@/assets/header/intro.jpg')}) center no-repeat`
            },
			isOpened: false,
			initialMenuHeight: '0px',
			menuHeight: null,
			fixedNavbar: false,
        }
    },
	methods: {
		onMenuBtn() {
			// if(!this.isOpened && !this.isClosed) {
            //     this.isOpened = true;
            // }else if(this.isOpened || this.isClosed) {
            //     this.isOpened = !this.isOpened;
            //     this.isClosed = !this.isClosed;
            // }
			this.isOpened = !this.isOpened;
			if(this.menuHeight === '0px') {
				this.menuHeight = '100vh';
			}else if(this.menuHeight === '100vh'){
				this.menuHeight = '0px';
			}
			if(this.isOpened) {
				this.initialMenuHeight = '100vh';
				document.body.style.overflowY = 'hidden';
			}else{
				this.initialMenuHeight = '0px'
				document.body.style.overflowY = 'scroll';
			}
		},
	},
	mounted() {
		window.addEventListener('scroll', () => {
			if(document.documentElement.scrollTop >= 50) {
				this.fixedNavbar = true;
			}else{
				this.fixedNavbar = false;
			}
		})
	}
}
</script>

<style scoped>
    .header{
        position: absolute;
        top: 0;
        left: 0;
        z-index: 999;
        width: 100%;
    }


    /* Topbar */

    .topbar{
        background-color: rgba(75, 85, 95, 0.2);
        border-bottom: solid 1px rgba(255, 255, 255, 0.1);
        padding: 20px 0;
    }

    .topbar_inner{
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
    }

    .order_call_btn{
        padding-right: 50px;
        border-right: solid 1px rgba(255, 255, 255, 0.1);
    }

    .topbar_btns{
        display: flex;
        flex-wrap: wrap;
    }

    .topbar_btn_item{
        display: inline-block;
        padding: 13px 30px;
        border: solid 2px #6e6352;
        background-color: rgba(110, 99, 82, 0.5);
        border-radius: 2rem;
    }

    .topbar_btn_item:not(:last-child) {
        margin-right: 20px;
    }

    .topbar_btn_item span{
        display: inline-block;
        vertical-align: middle;

        font-family: 'Lato', sans-serif;
        font-size: 14px;
        font-weight: 400;
        color: #fff;
    }

    .topbar_btn_item:hover span{
        text-decoration: underline;
    }



    /* Navbar */

    .navbar{
        padding: 20px 0;
		background-color: rgba(75, 85, 95, 0.2);
		border-bottom: solid 1px rgba(255, 255, 255, 0.1);
    }

	.navbar.fixed{
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		z-index: 99;
		background-color: #0b1d37;
	}

    .navbar_inner{
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;

        padding-right: 50px;
        border-right: solid 1px rgba(255, 255, 255, 0.1);
    }

    .logo img{
        width: 50px;
    }

    .nav_links{
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
    }

    .nav_link{
        font-family: 'Lato', sans-serif;
        font-size: 14px;
        font-weight: 700;
        color: #fff;
        text-decoration: none;
        text-transform: uppercase;

        padding: 20px 0;
        transition: .1s linear;
    }

    .nav_link:hover{
        color: #b1986f;
    }

    .nav_link:not(:last-child){
        margin-right: 40px;
    }

    .menu_btn{
        display: none;
        flex-direction: column;
        padding: 5px 10px;
        border: solid 1px rgba(255, 255, 255, 0.2);
        border-radius: 0.25rem;
    }

    .menu_btn span{
        display: inline-block;
        width: 30px;
        height: 2px;
        background-color: rgba(255, 255, 255, 0.5);
        border-radius: 2rem;
		transition: .2s linear;
    }

    .menu_btn span{
        margin: 5px;
    }

	.menu_btn.active .menu_first{
		transform: translateY(12px) rotate(135deg)
	}

	.menu_btn.active .menu_third{
		transform: translateY(-12px) rotate(-135deg);
	}

	.menu_btn.active .menu_second{
		transform: scale(0);
	}

	.menu{
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		z-index: 98;
		overflow: hidden;
		background: #0b1d37;
	}

	.menu_inner{
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.topbar_btns_menu_wrp{
		margin-bottom: 40px;
	}

	.topbar_menu_order_call_btn{
		display: block;
        padding: 13px 30px;
        border: solid 2px #6e6352;
        background-color: rgba(110, 99, 82, 0.5);
        border-radius: 2rem;
		text-decoration: none;
		text-align: center;
		transition: .2s linear;

		margin-bottom: 10px;
	}

	.topbar_menu_order_call_btn:hover{
		background: #6e6352;
		text-decoration: underline #fff;
	}

	.topbar_menu_order_call_btn span{
		font-family: 'Lato', sans-serif;
        font-size: 14px;
        font-weight: 700;
        color: #fff;
	}

	.topbar_menu_btns{
		display: flex;
		flex-wrap: wrap;
	}

	.topbar_menu_btn_item{
		display: inline-block;
		padding: 13px 30px;
        border: solid 2px #6e6352;
        background-color: rgba(110, 99, 82, 0.5);
        border-radius: 2rem;
		text-decoration: none;
		transition: .2s linear;
	}

	.topbar_menu_btn_item:hover{
		background: #6e6352;
	}

	.topbar_menu_btn_item:not(:last-child) {
		margin-right: 10px;
	}

	.menu_nav_links{
		display: flex;
		flex-direction: column;
		text-align: center;
		width: 30%;
	}

	.menu_nav_link_item{
		font-family: 'Lato', sans-serif;
        font-size: 14px;
        font-weight: 700;
        color: #fff;

		padding: 15px 0;
		transition: .2s linear;
	}

	.menu_nav_link_item:hover{
		background: rgba(255, 255, 255, 0.9);
		color: #0b1d37;
	}

	.menu_nav_link_item:not(:last-child) {
		border-bottom: solid 1px rgba(255, 255, 255, 0.1);
	}




    /* Intro */

    .intro{
        width: 100%;
        height: 100vh;
    }

    .intro_inner{
        display: flex;
        flex-direction: column;
        justify-content: center;
        text-align: center;
        height: 100vh;
		padding-top: 18%;
    }

    .intro_title{
        font-family: 'Playfair Display', serif;
        font-size: 48px;
        font-weight: 700;
        color: #fff;

        margin-bottom: 15px;
    }

    .intro_subtitle{
        font-family: 'Lato', sans-serif;
        font-size: 15px;
        font-weight: 400;
        color: #9c9c9c;   
    }

    .intro_btns{
        display: flex;
        align-items: center;
        justify-content: center;
        flex-wrap: wrap;
    }

    .intro_btn_item_wrp{
        padding: 40px 20px;
    }

    .intro_btn_item{
        display: inline-block;
        font-family: 'Lato', sans-serif;
        font-size: 14px;
        font-weight: 700;
        color: #fff;
        transition: .2s linear;

        padding: 20px 30px;
        background-color: #b1986f;
        border: solid 2px #b1986f;
        border-radius: .25rem;
    }

	.intro_btn_item span{
		text-decoration: underline;
	}

    .intro_btn_item:hover{
        background-color: #000;
    }

    @media(max-width: 1000px) {
        .intro_title{
            font-size: 36px;
        }
    }

    @media(max-width: 870px) {
        .navbar_inner{
            padding: 0;
            border: none;
        }

        .menu_btn{
            display: flex;
        }

        .nav_links a{
            display: none;
        }

        .topbar{
            display: none;
        }

        .intro_inner{
            padding: 0;
        }

        .intro_btns{
            display: none;
        }
    }

    @media(max-width: 450px) {
        .intro_title{
            font-size: 24px;
        }

        .intro img{
            width: 100px;
        }
    }


	@media(max-width: 330px) {
		.topbar_btns_menu_wrp{
			margin: 20px 0;
		}
	}
</style>