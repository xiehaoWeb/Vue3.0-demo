<template>
	<div class="container">
		<header>
			<ul>
				<li v-for="item in Data" :key="item.url">{{item.label}}</li>
			</ul>
		</header>
		<main>
			<nav>
				<ul>
					<li>1</li>
					<li>2</li>
					<li>3</li>
				</ul>
			</nav>
			<section>
				内容
			</section>
		</main>
		<footer>
			底部
		</footer>
	</div>
	<!-- <img src="./logo.png">
  <h1>Hello Vue 3!</h1>
  <button @click="inc">Clicked {{ count }} times.</button> -->
</template>

<script>
	import {
		ref
	} from 'vue'
	function fetch(){
		return new Promise((res,rej)=>{
			setTimeout(()=>{
				res([
					{label:"工作台",url:"1"},
					{label:"商机管理",url:"2"},
					{label:"立项管理",url:"3"},
					{label:"投标管理",url:"4"},
				])
			},200)
		})
	}
	async function loadStarship() {
	  const res = await fetch();
	  console.log(res)
	  return res;
	}
	export default {
		setup() {
			let { Data } = loadStarship();
			console.log(Data)
			return {
				Data,
			}
		}
	}
</script>

<style scoped>
	
	ul{
		margin: 0;
		padding:0;
		list-style: none;
		display: grid;
		color: white;
		gap:10px;
		place-items: center;
	}
	.container{
		display: grid;
		grid-template-rows:60px auto 40px;
	}
	header{
		background-color: #000000;
	}
	main{
		background-color: #ffd900;
		display: grid;
		grid-template-columns:200px auto;
		column-gap: 10px; 
	}
	footer{
		background-color: #009E94;
	}
	nav{
		background-color: #01AAED;
	}
	section{
		background-color: #5FB878;
	}
</style>
