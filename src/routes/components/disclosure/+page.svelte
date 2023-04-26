<script>
	import Faq from "../../../components/apg/disclosure/Faq.svelte";
	const faqs = [
		{
			question: "What is the earth made of?",
			answer: "The earth is not made of cheese.",
			expanded: false
		},
		{
			question: "How do you fish?",
			answer: "Take your rod to the river and cast out your line.",
			expanded: true
		}
	];
</script>

<Faq faqs={faqs} />