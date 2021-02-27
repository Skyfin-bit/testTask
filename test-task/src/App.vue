<template>
    <div class="app">
        <header-section></header-section>
        <service-section></service-section>
        <team-section></team-section>
        <cases-section></cases-section>
        <help-section></help-section>
        <footer-section></footer-section>
		<div 
		@click="scrollToTop" 
		:class="{scroll_to_top_btn: true, visible: scrollToTopVisible}">
			<icon-base
				icon='second_arrow'
				:styleList="{
					transform: 'rotate(-90deg)',
				}"></icon-base>
		</div>
    </div>
</template>

<script>
/* eslint-disable no-unused-vars */
import HeaderSection from './components/HeaderSection';
import ServiceSection from './components/ServiceSection';
import TeamSection from '@/components/TeamSection/TeamSection';
import CasesSection from '@/components/CaseSection/CaseSection';
import HelpSection from './components/HelpSection';
import FooterSection from './components/FooterSection';
import IconBase from './components/IconBase';

export default {
    name: 'App',
    components: {
        HeaderSection,
        ServiceSection,
        TeamSection,
        CasesSection,
        HelpSection,
        FooterSection,
        IconBase
    },
	data() {
		return{
			requiredScrollHeight: window.innerHeight * 2,
			scrollToTopVisible: false,
		}
	},
	methods: {
		scrollToTop() {
			window.scrollTo({top: 0, behavior: 'smooth'});
		}
	},
	mounted() {
		window.addEventListener('scroll', () => {
			if(document.documentElement.scrollTop >= this.requiredScrollHeight) {
				this.scrollToTopVisible = true;
			}else{
				this.scrollToTopVisible = false;
			}
		})
	}
}
</script>

<style scoped>
	.scroll_to_top_btn{
		display: none;
		position: fixed;
		z-index: 97;
		bottom: 40px;
		right: 40px;
		width: 50px;
		height: 50px;
		border-radius: 50px;
		background: #b1986f;
		cursor: pointer;
	}

	.scroll_to_top_btn.visible{
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	@media(max-width: 600px) {
		.scroll_to_top_btn{
			bottom: 20px;
			right: 20px;
		}
	}
</style>
