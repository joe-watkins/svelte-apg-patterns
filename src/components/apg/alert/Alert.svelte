<script>
	export let alertMsg;
</script>

<div role="alert">
	{@html alertMsg}
</div>

<style>
[role="alert"] {
    padding: 10px;
    border: 2px solid hsl(206deg 74% 54%);
    border-radius: 4px;
    background: hsl(206deg 74% 90%);
    margin-bottom: 1em;
}

[role="alert"]:empty {
    display: none;
}
</style>