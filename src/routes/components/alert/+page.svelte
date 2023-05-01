<script>
	import Alert from "../../../components/apg/alert/Alert.svelte";

    /* Syntax Highlighting */
	import { HighlightAuto } from "svelte-highlight";
	import github from "svelte-highlight/styles/github";

    // Usage 
    const code = `
<Alert alertMsg={alertMsg} />    
`;
	
	let alertMsg = "";
	
	let msg = `<p>Hello</p>`;
	
	function updateAlert(){
		setTimeout(() => {
			alertMsg = msg;
		},200);
	}
</script>

<svelte:head>
  {@html github}
</svelte:head>

<div class="prose prose-xl max-w-none mb-4">
	<h1>Alert</h1>
    <h2>Description</h2>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Fugit ipsa molestias placeat, dolorum asperiores quibusdam autem, laboriosam veniam totam vel fuga beatae a accusamus, sunt dolor amet tenetur adipisci exercitationem?</p>
</div>

<button on:click={updateAlert}>
	Trigger Alert 
</button>

<Alert alertMsg={alertMsg} />

<div class="prose prose-xl max-w-none mb-4">
    <h2>Usage</h2>
    <HighlightAuto {code} />
</div>

<style>
button {
    border-radius: 5px;
    display: inline-block;
    display: -ms-inline-flexbox;
    display: inline-flex;
    -ms-flex-align: center;
    align-items: center;
    -ms-flex-pack: center;
    justify-content: center;
    padding: 8px 12px;
    border: 2px solid #005a6a;
    font-size: 13px;
    font-size: .8125rem;
    line-height: 1.4;
    background-color: #005a6a;
    text-decoration: none;
    font-weight: 700;
        color: #fff;
}
</style>
