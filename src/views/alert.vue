<template>
	<div>
		<container>
			<navbar>
				<a v-link='{"name": "demo"}'><icon type="arrow-left"></icon></a>
				<span class="split"></span>
				<span>Alert</span>
			</navbar>
			<content>
				<group>
					<group-item @click="defaultAlertHandle">
						<span>默认</span>
					</group-item>
					<group-item @click="customAlertHandle">
						<span>自定义</span>
					</group-item>
				</group>
			<alert title="操作成功" message="恭喜您，抢票成功！" :show.sync="showDefault" @click="alertClickHandle"></alert>
			<alert :show.sync="showCustom">
				<div class="alert-header" slot="header"><icon type="check" size="3x" class="text-success"></icon></div>
				<div class="alert-body text-success">丑了点，能说明问题啊！</div>
			</alert>
			</content>
		</container>
	</div>
</template>


<script>
	import { Container, Content, Group, GroupItem, Navbar, Alert, Icon } from '../components/index.js';

	export default {
		components: {
		  	Container,
		  	Content,
		    Group,
		    GroupItem,
		    Navbar,
		    Alert,
		    Icon
		},
		data(){
			return {
				showDefault: false,
				showCustom: false
			}
		},
		methods: {
			//显示默认
			defaultAlertHandle(event){
				this.showDefault = true;
			},
			//显示默认
			customAlertHandle(event){
				this.showCustom = true;
			},
			//确定按钮绑定事件
			alertClickHandle(){
				console.log("确定按钮被点击了！");
			}
		}
	};
</script>