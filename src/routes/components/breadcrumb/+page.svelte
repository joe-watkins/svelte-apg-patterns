<script>

    /* Syntax Highlighting */
    import { HighlightAuto } from "svelte-highlight";
    import github from "svelte-highlight/styles/github";

	import Breadcrumb from "../../../components/apg/breadcrumb/Breadcrumb.svelte";

	let breadcrumbs = [
		{ url: "test", linkText: "WAI-ARIA Authoring Practices Guide (APG)" },
		{ url: "another", linkText: "Patterns" },
		{ url: "another", linkText: "Breadcrumb Pattern" },
		{ url: "test", linkText: "Breadcrumb Example", currentPage: true }
	];

    // Usage 
    const code = `import Breadcrumb from "../Breadcrumb.svelte";    

/* Define data for breadcrumbs */ 
let breadcrumbs = [
    { url: "test", linkText: "WAI-ARIA Authoring Practices Guide (APG)" },
    { url: "another", linkText: "Patterns" },
    { url: "another", linkText: "Breadcrumb Pattern" },
    { url: "test", linkText: "Breadcrumb Example", currentPage: true }
];

<Breadcrumb 
    breadcrumbs={breadcrumbs} 
    breadCrumbNavLabel="Breadcrumbs" 
    breadCrumbClass="breadcrumb" 
/>`;

</script>

<svelte:head>
  {@html github}
</svelte:head>
<div class="prose prose-xl max-w-none">
    <h1>Breadcrumb</h1>
    <h2>Description</h2>
    <p>A breadcrumb trail consists of a list of links to the parent pages of the current page in hierarchical order. It helps users find their place within a website or web application. Breadcrumbs are often placed horizontally before a page's main conten</p>
    <h2>Example</h2>
    <Breadcrumb 
        breadcrumbs={breadcrumbs} 
        breadCrumbNavLabel="Breadcrumbs" 
        breadCrumbClass="breadcrumb" 
    />

    <h2>Usage</h2>
    <HighlightAuto {code} />
</div>