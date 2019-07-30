<template>
  <div>
    <h1>{{animal.name}} ({{this.$route.params.species}})</h1>
    <p>Age: {{animal.age}} years old</p>
    <p>Breed: {{animal.breed}}</p>
  </div>
</template>

<script>
import { mapState } from 'vuex';
export default {
	data() {
		return { animal: {} };
	},
	computed: {
		...mapState(['cats', 'dogs'])
	},
	mounted() {
		const id = this.$route.params.id;
		const animal = this[this.$route.params.species][id];

		this.animal = animal;
	}
};
</script>
