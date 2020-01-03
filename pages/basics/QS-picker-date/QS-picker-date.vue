<template>
	<view>
		<QSPickerDate ref="a" :name="formName" variableName="date"  title="日期"  placherhold="请选择" @showQSPicker="showQSPicker" @hideQSPicker="hideQSPicker"/>
		<button type="primary" style="margin-top: 50rpx;" @tap="getData">获取输入</button>
	</view>
</template>

<script>
	import QSApp from '@/components/QS-inputs-split/js/app.js';
	export default {
		data() {
			return {
				title: 'Hello',
				formName: 'picker',
				itemDisabled: false,
				dateValue: '2019-9-29',
				dataSet: {
					defaultValue: '2019/9/29',
				}
			}
		},
		onReady() {
			this.$refs.a.confirm();
		},
		methods: {
			getData() {
				QSApp.getForm(this.formName).then(res => {
					console.log('获取FORM数据成功: ' + JSON.stringify(res));
					uni.showToast({ title: '获取数据成功' });
					this.reSet();
				}).catch(err => {
					console.log('获取FORM数据失败: ' + JSON.stringify(err));
					uni.showToast({ title: '获取数据异常' });
				});
			},
			showQSPicker() {
				console.log('显示了')
			},
			hideQSPicker() {
				console.log('隐藏了')
			}
		}
	}
</script>

<style>
	
</style>
