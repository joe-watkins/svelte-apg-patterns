<script>

	/* Syntax Highlighting */
	import { HighlightAuto } from "svelte-highlight";
	import github from "svelte-highlight/styles/github";

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

	// Usage 
    const code = 
`const faqs = [
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

<Faq faqs={faqs} />`;

</script>

<svelte:head>
  {@html github}
</svelte:head>

<div class="prose prose-xl max-w-none mb-4">
	<h1>Disclosure</h1>
	<h2>Description</h2>
	<p>A disclosure is a widget that enables content to be either collapsed (hidden) or expanded (visible). It has two elements: a disclosure button and a section of content whose visibility is controlled by the button. When the controlled content is hidden, the button is often styled as a typical push button with a right-pointing arrow or triangle to hint that activating the button will display additional content. When the content is visible, the arrow or triangle typically points down.</p>
	<h2>Example</h2>
</div>
<Faq faqs={faqs} />
<div class="prose prose-xl max-w-none mb-4">
	<h2>Usage</h2>
	<HighlightAuto {code} />
</div>
