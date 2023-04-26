<script>
	import Alert from "../../../components/apg/alert/Alert.svelte";
	
	let alertMsg = "";
	
	let msg = `<p>Hello</p>`;
	
	function updateAlert(){
		setTimeout(() => {
			alertMsg = msg;
		},200);
	}
</script>

<button on:click={updateAlert}>
	Trigger Alert 
</button>

<Alert alertMsg={alertMsg} />

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
