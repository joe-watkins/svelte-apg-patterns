<script>
	import { tick } from "svelte";
	export let showAlertDialog;
	export let destroyNotes;
	export let handleNoConfirmation;
	export let wordCount;
	let btnRef;
	async function autofocus(el) {
		await tick();
		el.focus();
	}
</script>

{#if showAlertDialog}
<div class="dialog-backdrop no-scroll" class:active={showAlertDialog}>
	<div id="alertdialog" role="alertdialog" aria-modal="true" aria-labelledby="dialog_label" aria-describedby="dialog_desc">
		<h2 id="dialog_label" class="dialog_label">Confirmation</h2>
		<div id="dialog_desc" class="dialog_desc">
			<p>Are you sure you want to discard all of your notes?</p>
			<p id="word_count">{wordCount} words will be deleted.</p>
		</div>
		<div class="dialog_form_actions">
			<button type="button" id="notes_cancel" on:click={handleNoConfirmation} use:autofocus>No</button>
			<button type="button" id="notes_confirm" on:click={destroyNotes}>Yes</button>
		</div>
	</div>
</div>
{/if}

<style>
	
[role="alertdialog"] {
  box-sizing: border-box;
  padding: 15px;
  border: 1px solid #000;
  background-color: #fff;
  min-height: 100vh;
}

@media screen and (min-width: 640px) {
  [role="alertdialog"] {
    position: absolute;
    top: 2rem;
    left: 50vw; /* move to the middle of the screen (assumes relative parent is the body/viewport) */
    transform: translateX(
      -50%
    ); /* move backwards 50% of this element's width */

    min-width: calc(640px - (15px * 2)); /* == breakpoint - left+right margin */
    min-height: auto;
    box-shadow: 0 19px 38px rgb(0 0 0 / 12%), 0 15px 12px rgb(0 0 0 / 22%);
  }
}

.dialog_label {
  text-align: center;
}

.dialog_form_actions {
  text-align: right;
  padding: 0 20px 20px;
}

.dialog_desc {
  padding: 10px 20px;
}

/* dialog::backdrop, */
.dialog-backdrop {
  display: none;
  position: fixed;
  overflow-y: auto;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}

@media screen and (min-width: 640px) {
  .dialog-backdrop {
    background: rgb(0 0 0 / 30%);
  }
}

.dialog-backdrop.active {
  display: block;
}

.no-scroll {
  overflow-y: auto !important;
}
</style>