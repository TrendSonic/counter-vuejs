<template>
  <div>
		<h1>Vuex Counter</h1>
		<h1 class="counter">{{ counter }}</h1>
		<button @click="decreaseToCounter(value)">-</button>
		<input 
			type="number"
			v-model="value"
			>
		<button @click="increaseToCounter(value)">+</button>
		<div>
			<button 
				class="btn"
				@click="addRandomNumber"
				>
				Add random number
			</button>
		</div>
	</div>
</template>

<script>
import { ref } from '@vue/reactivity'
import { mapState, mapMutations, mapActions } from 'vuex'

export default {
	setup() {
		let value = ref(1)

		return { value }
	},
	computed: {
		...mapState([ 'counter' ])
	},
	methods: {
		...mapMutations([ 'increaseToCounter', 'decreaseToCounter' ]),
		...mapActions([ 'addRandomNumber' ])
	}
}
</script>

<style>
.counter {
	font-size: 5rem;
}

button {
	border-radius: 100%;
	border: none;
	width: 2rem;
	height: 2rem;
	font-weight: 700;
	cursor: pointer;
}

input {
	padding: 0.4rem;
	margin: 0 .5rem;
}

.btn {
	border-radius: 0.5rem;
	width: auto;
	background-color: #41B986;
	color: #fff;
	margin-top: 10px;
	cursor: pointer;
}
</style>