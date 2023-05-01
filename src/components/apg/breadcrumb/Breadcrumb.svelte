<script>
	export let breadcrumbs;
	export let breadCrumbNavLabel;
	export let breadCrumbClass = "breadcrumb";
</script>

<nav aria-label={breadCrumbNavLabel} class={breadCrumbClass}>
	<ol>
		{#each breadcrumbs as item}
			<li>
				<a href="{item.url}" aria-current={item.currentPage ? "page" : null}>{item.linkText}</a>
			</li>
		{/each}
	</ol>
</nav>

<style>
nav.breadcrumb {
  padding: 0.8em 1em;
  border: 1px solid hsl(0deg 0% 90%);
  border-radius: 4px;
  background: hsl(300deg 14% 97%);
  margin-bottom: 1em;
}

nav.breadcrumb ol {
  margin: 0;
  padding-left: 0;
  list-style: none;
}

nav.breadcrumb li {
  display: inline;
}

nav.breadcrumb li + li::before {
  display: inline-block;
  margin: 0 0.5em;
  transform: rotate(15deg);
  border-right: 0.1em solid currentcolor;
  height: 0.8em;
  content: "";
}

nav.breadcrumb [aria-current="page"] {
  color: #000;
  font-weight: 700;
  text-decoration: none;
}

 a {
    color: #036;
    text-decoration: underline;
}

</style>