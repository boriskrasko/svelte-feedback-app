<script>
	import FeedbackList from './components/FeedbackList.svelte'
  import FeedbackStats from './components/FeedbackStats.svelte';

	let feedback = [
		{
			id: 1,
			rating: 10,
			text: 'Lorem ipsum'
		},
		{
			id: 2,
			rating: 9,
			text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quo doloremque tenetur eaque voluptates voluptatem quibusdam neque, commodi nam vitae. Est placeat neque, vero facere perspiciatis vitae praesentium voluptates nulla? Veritatis!'
		},
		{
			id: 3,
			rating: 4,
			text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quo doloremque tenetur eaque voluptates voluptatem quibusdam neque, commodi nam vitae. Est placeat neque, vero facere perspiciatis vitae praesentium voluptates nulla? Veritatis!'
		},
		{
			id: 4,
			rating: 7,
			text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quo doloremque tenetur eaque voluptates voluptatem quibusdam neque, commodi nam vitae. Est placeat neque, vero facere perspiciatis vitae praesentium voluptates nulla? Veritatis!'
		},
		{
			id: 5,
			rating: 8,
			text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quo doloremque tenetur eaque voluptates voluptatem quibusdam neque, commodi nam vitae. Est placeat neque, vero facere perspiciatis vitae praesentium voluptates nulla? Veritatis!'
		},
	]

	$: count = feedback.length;
	$: average = feedback.reduce((a, {rating}) => a + rating, 0) / count || 0

	const deleteFeedback = (e) => {
		let itemId = e.detail;
		feedback = feedback.filter(item => item.id !== itemId)
	}
</script>

<main class="container">
	<FeedbackStats {count} {average} />
	<FeedbackList {feedback} on:delete-feedback={deleteFeedback} />
</main>
