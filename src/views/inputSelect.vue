<template>
	<div>
		<container>
			<navbar>
				<a v-link='{"name":"demo"}'><icon type="arrow-left"></icon></a>
				<span class="split"></span>
				<span>InputSelect</span>
			</navbar>
			<content>
				<group-title></group-title>
				<input-select :default-value="city" @click="showSlideupHandle" placeholder="请选择城市" v-ref:city>
					<label slot>城市:</label>
				</input-select>
				<input-select :default-value="good" @click="showGoodsHandle" v-ref:goods>
					<label slot>默认值:</label>
				</input-select>
			</content>
			<slide direction="up" :show.sync="showCity">
				<span class="text-danger" slot="header">请选择取货地址</span>
				<selector :options="zones" dispatch="slideup:hide" :sync-component="$refs.city"></selector>
			</slide>
			<slide direction="up" :show.sync="showSex">
				<span class="text-danger" slot="header">请选择擅长</span>
				<selector :options="goods" dispatch="slideup:hide" :sync-component="$refs.goods"></selector>
			</slide>
		</container>
	</div>
</template>


<script>
	import { Container, Content, Navbar, Group, GroupItem, GroupTitle, InputSelect, Slide, Selector, Icon } from '../components/index.js';

	export default {
		components: {
		  	Container,
		  	Content,
		  	Navbar,
		    Group,
		    GroupItem,
		    GroupTitle,
		    InputSelect,
		    Slide,
		    Selector,
		    Icon
		},
		data(){
			return {
				city: {},
				good: {name: '篮球', value: '1'},
				showCity: false,
				showSex: false,
				zones: ['福州', '厦门', '泉州', '北京', '上海', '杭州', '海宁', '广州', '深圳'],
				goods: ['篮球', '足球', '羽毛球'],
			}
		},
		methods: {
			showSlideupHandle(){
				this.showCity = true;
			},
			showGoodsHandle(value, index){
				this.showSex = true;
			}
		}
	};
</script>