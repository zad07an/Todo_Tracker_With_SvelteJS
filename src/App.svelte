<script>
	import ReminderFooter from "./components/ReminderFooter.svelte";
import ReminderForm from "./components/ReminderForm.svelte";
  import ReminderList from "./components/ReminderList.svelte";
</script>

<section class="container">
	<div class="reminder_container">
		<div class="app_title">
			<h1>Reminder App</h1>
		</div>
		<ReminderForm/>
		<ReminderList/>
		<ReminderFooter/>
	</div>
</section>

<style scoped>
	.container {
		width: 100%;
		height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
		background: rgb(1, 0, 12);
	}

	.reminder_container {
		width: 600px;
		display: grid;
		grid-template-columns: 1fr;
		grid-gap: 10px;
		background: white;
		border-radius: 10px;
	}

	.app_title {
		padding: 10px 0;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.app_title > h1 {
		font-size: 36px;
	}
</style>