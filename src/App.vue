<template>
	<div id="app">
		<img
			alt="Vue logo"
			src="./assets/logo.png"
		>

		<div class="container">
			<form-wizard
				title="Form Wizard demo"
				subtitle="demo1"
				:nextButtonText="numeroPagina"
				backButtonText="INDIETRO"
				finishButtonText="FINE"
				stepSize="sm"
				color="lightblue"
			>
				<tab-content
					title="Inserisci CODICE"
					:before-change="check1"
				>
					prima tab

					<div v-if="!blackOut">

						<h3>Premi 1 per passare</h3>
						<h3>Premuto {{valore}}</h3>

						<div>

							<button @click="valore = 1">1</button>
							<button @click="valore = 2">2</button>
							<button @click="valore = 3">3</button>
						</div>
					</div>
					<div v-else>
						hai sbagliato bello

						<button @click="reload()">Ricarica la pagina</button>

					</div>

				</tab-content>
				<tab-content
					title="Valida CODICE"
					:before-change="check2"
				>
					<h3>Premi 2 per passare</h3>
					<h3>Premuto {{valore}}</h3>

					<div>

						<button @click="valore = 1">1</button>
						<button @click="valore = 2">2</button>
						<button @click="valore = 3">3</button>
					</div>
				</tab-content>
				<tab-content
					title="Conferma VINCITA"
					:before-change="check3"
				>
					<h3>Premi 3 per passare</h3>
					<h3>Premuto {{valore}}</h3>

					<div>

						<button @click="valore = 1">1</button>
						<button @click="valore = 2">2</button>
						<button @click="valore = 3">3</button>
					</div>
				</tab-content>
				<!-- <tab-content
					title="Check FORM"
					:before-change="check3"
				>

					<form action="">

						<input type="text">
						<input type="text">
					</form>

				</tab-content> -->
			</form-wizard>
		</div>
	</div>
</template>

<script>
	import { FormWizard, TabContent } from 'vue-form-wizard';
	import 'vue-form-wizard/dist/vue-form-wizard.min.css';

	export default {
		name: 'App',
		components: {
			FormWizard,
			TabContent,
		},
		data() {
			return {
				valore: 0,
				blackOut: false,
				numPagina: 2,
			};
		},
		methods: {
			reload() {
				window.location.reload();
			},

			check1() {
				console.log(this.valore);

				if (this.valore === 1) {
					this.numPagina = 3;
					return true;
				} else {
					this.blackOut = true;

					return false;
				}
			},
			check2() {
				console.log(this.valore);

				if (this.valore === 2) {
					return true;
				} else {
					return false;
				}
			},
			check3() {
				console.log(this.valore);

				if (this.valore === 3) {
					return true;
				} else {
					return false;
				}
			},
		},

		computed: {
			numeroPagina() {
				return 'pagina' + this.numPagina;
			},
		},
	};
</script>

<style>
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}

	.container {
		max-width: 1200px;
		margin: 0 auto;
	}
</style>
