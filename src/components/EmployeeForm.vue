<template>
	<div id="employee-form">
		<b-form>
			<b-row>
				<b-col>
					<label
						>Employee Id-number
						<i class="material-icons">border_color</i></label
					>
				</b-col>
				<b-col>
					<input type="Number" v-model="newEmp.id" />
				</b-col>
			</b-row>
			<b-row>
				<b-col>
					<label>Employee Name</label>
				</b-col>
				<b-col>
					<input
						type="text"
						placeholder="snoopy"
						v-model="newEmp.name"
						:class="{ 'has-error': submitting && invalidName }"
						@focus="clearStatus"
						@keypress="clearStatus"
					/>
				</b-col>
			</b-row>
			<p v-if="error && submitting" class="error-message">
				Fill in required fields right now!!
			</p>
			<p v-if="success" class="success-message">Successfully added employee</p>
			<b-btn variant="primary" @click="handleSubmit">
				Save Employee
			</b-btn>
		</b-form>
	</div>
</template>

<script>
export default {
	name: "employee-form",
	data() {
		return {
			submitting: false,
			error: false,
			success: false,
			newEmp: {
				id: "",
				name: "",
			},
		};
	},
	computed: {
		invalidName() {
			console.log(this.newEmp.name === "");
			return this.newEmp.name === "";
		},
	},

	methods: {
		handleSubmit() {
			console.log("testing handleSubmit");
			this.submitting = true;
			this.clearStatus();

			if (this.invalidName) {
				this.error = true;
				return;
			}

			this.$emit("save:employee", this.newEmp);

			this.newEmp = {
				id: "",
				name: "",
			};
			this.error = false;
			this.success = true;
			this.submitting = false;
		},

		clearStatus() {
			this.success = false;
			this.error = false;
		},
	},
};
</script>

<style scoped>
form {
	margin-bottom: 2rem;
}

.error-message {
	color: #d33c40;
}

.success-message {
	color: #32a95d;
}
</style>
