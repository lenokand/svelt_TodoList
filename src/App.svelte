<script>
	import Todo from "./Todo.svelte"
	export let name;
	export let version
</script>

<main>
	<div class="app">
		<h1>{name} <span>{version} </span></h1>
		<Todo/> 
	</div>


</main>

<style lang="scss">
	main {
		display: flex;
		width: 100%;
		height: 100vh;
		justify-content: center;
		align-items: center;

		background: #FEAC5E;  /* fallback for old browsers */
		background: -webkit-linear-gradient(-45deg, #4BC0C8, #C779D0, #FEAC5E);  /* Chrome 10-25, Safari 5.1-6 */
		background: linear-gradient(-45deg, #4BC0C8, #C779D0, #FEAC5E); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
		.app{
			background-color: rgba(255, 255, 255, 0.336);
			width: 100%;
			max-width: 420px;
			padding: 1.5rem;
			border-radius: 1.5rem;
			box-shadow: 0 2px rgba(0, 0, 0, 0.2);
			flex-direction: column;
			transform: translateY(-2rem);
			h1{
				color: #6b37a3;
				text-align: center;
				margin-bottom: 0.5rem;
				font-weight: 900;
				span{
					color: #ac7ab5;

					font-size: 1rem;
					display: inline-block;
					transform: translateY(-1rem);
				}

			}
		}

	}

	

	@media (min-width: 450px) {
		.app{
			background-color: rgba(255, 255, 255, 0.336);
			width: 100%;
			max-width: 330px;
			padding: 1.5rem;
		}
	}
</style>