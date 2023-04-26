<script>
    import "./Faq.css";
	export let faqs;

	const toggleAnswer = (index) => {
		faqs[index].expanded = !faqs[index].expanded;
	}
</script>

<dl class="faq">
	{#each faqs as faq, index}
		<dt>
			<button
				aria-expanded={faq.expanded}
				aria-controls={`faq-answer-${index}`}
				on:click={() => toggleAnswer(index)}>
				{faq.question}
			</button>
		</dt>
		<dd>
			<div
				id={`faq-answer-${index}`}
				hidden={!faq.expanded}
				class="desc"
			>
				{faq.answer}
			</div>
		</dd>
	{/each}
</dl>