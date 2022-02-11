<template>
	<div class="container">
		<h4>History</h4>
		<div class="flex">
			<p 
				v-for="(number, index) in history"
				:key="index"
				:class="activeIndexes(value).includes(index) ? 'bold' : ''"
				> 
				{{ number }}
			</p>
		</div>
		<input placeholder="Search..." type="number" v-model="value">
	</div>
</template>

<script>
import { ref } from '@vue/reactivity'
import { mapState, mapGetters } from 'vuex'

export default {
	setup() {
		let value = ref(null)

		return { value }
	},
	computed: {
		...mapState([ 'history' ]),
		...mapGetters([ 'activeIndexes' ])
	}
}
</script>

<style scoped>
.container {
	margin-top: 50px;
}

.flex {
	display: flex;
	text-align: center;
	width: 30%;
	margin: 0 auto;
	justify-content: center;
	flex-wrap: wrap;
}

.flex p {
	margin: 5px 10px;
	font-size: 16px;
}

.bold {
	font-weight: 900;
}
</style>