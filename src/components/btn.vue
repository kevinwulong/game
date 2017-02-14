<template>
<div class="btn">
	<button @click="btnOne">{{opOne}}</button>
	<button @click="btnTwo">{{opTwo}}</button>
</div>
</template>
<script>
export default {
	data() {
	  return {
	  	opOne: '能看到，你是谁？',
	  	opTwo:  '内心os: 这是骗子吧',
	  	gameOver: true
	  }
	},
	props: {
		btnValue: {
			type: Array
		}
	},
	methods: {
		btnOne() {
			this.gameOver= false
			this.$emit('go')
		},
		btnTwo() {
			if (this.gameOver) {
				this.$emit('over', '不按套路走！游戏结束')
			}
		}
	}
}
</script>
<style scoped>
.btn{
	width:100%;
	height: 100%;
};
.btn>button{
	display: block;
	float: left;
	width:40%;
	height: 80%;
	margin:2% 5%;
	border-radius: 10px;
	background: rgb(141, 153, 174);
	outline:none;
	color:black;
	border: none;
};

</style>
