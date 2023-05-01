<script>
	import Dialog from "./Dialog.svelte";

	import { onMount } from "svelte";

	let btnLoadingState = false;
	let btnSavedState = false;
	let disableDiscardBtn = false;
	let disableSaveBtn = false;
	let showAlertDialog = false;
	let textAreaRef;
	let discardRef;
	let statusMsgContainer;
	let statusMsg;
	let wordCount;
	let notes = "This is an example text box, which unsurprisingly contains text. The user is given the option to save this text - which triggers a basic alert - or to discard the text - which triggers an alert dialog that prompts the user for confirmation.";
	let initialNotes = notes;

	onMount(() => {
		let localStorageNotes = localStorage.getItem("notes");
		
		if (localStorageNotes && notes !== localStorageNotes) {
			notes = localStorageNotes;
		}
	});

	function compare() {
		if(initialNotes == notes && initialNotes == localStorage.getItem("notes")){
			disableSaveBtn = true;
		}else if(notes == localStorage.getItem("notes")){
			disableSaveBtn = true;
		} else {
			disableSaveBtn = false;
			btnSavedState = false;
			disableDiscardBtn = false;
		}
	}
	
	function save() {
		btnLoadingState = true;
		localStorage.setItem("notes", notes);
		statusMsg = "Loading";
		setTimeout(() => {
			btnLoadingState = false;
			btnSavedState = true;
			disableSaveBtn = true;
			statusMsg = "Saved Successfully";
		},2000);
	}
	
	function destroyNotes() {
		showAlertDialog = false;
		disableDiscardBtn = true;
		document.body.style = "";
		localStorage.removeItem("notes");
		notes = "";
		textAreaRef.focus();
		if(btnSavedState && disableSaveBtn){
			disableSaveBtn = false;
			btnSavedState = false;
		}
		statusMsg = "";
	}
	
	function spawnAlertDialog() {
		wordCount = notes.split(" ").length;
		if(disableDiscardBtn){
			return false;
		}
		document.body.style = "overflow: hidden";
		showAlertDialog = true;
	}
	
	function handleNoConfirmation() {
		document.body.style = "";
		showAlertDialog = false;
		setTimeout(function(){
			discardRef.focus();
		},200);
	}
	
	function on_key_down(e) {
		var mod = navigator.userAgent.includes('Mac') ? e.metaKey : e.ctrlKey;
		if ((e.key === 's') & mod && !disableSaveBtn) {
			e.preventDefault();
			save();
		}
		if(e.key === "Escape" && showAlertDialog){
			handleNoConfirmation();
		}
	}
	
</script>

<svelte:window on:keydown={on_key_down} />

<div class="alert-dialog-form" inert={showAlertDialog}>
	<label for="notes">Notes</label>
	<textarea class="notes" name="notes" id="notes" rows="7" bind:value={notes} on:keyup={compare} bind:this={textAreaRef}></textarea>
	<div class="visually-hidden" id="notes_save_status" role="alert" bind:this={statusMsgContainer}>
		{#if statusMsg}
			{statusMsg}
		{/if}
	</div>
	<div>
		<button id="notes_save" class:loading={btnLoadingState} class:saved={btnSavedState} on:click={save} aria-disabled={disableSaveBtn}>
			Save
			<svg class="icon spinner"
				 viewBox="0 0 32 32"
				 aria-hidden="true">
				<path d="M16 32c-4.274 0-8.292-1.664-11.314-4.686s-4.686-7.040-4.686-11.314c0-3.026 0.849-5.973 2.456-8.522 1.563-2.478 3.771-4.48 6.386-5.791l1.344 2.682c-2.126 1.065-3.922 2.693-5.192 4.708-1.305 2.069-1.994 4.462-1.994 6.922 0 7.168 5.832 13 13 13s13-5.832 13-13c0-2.459-0.69-4.853-1.994-6.922-1.271-2.015-3.066-3.643-5.192-4.708l1.344-2.682c2.615 1.31 4.824 3.313 6.386 5.791 1.607 2.549 2.456 5.495 2.456 8.522 0 4.274-1.664 8.292-4.686 11.314s-7.040 4.686-11.314 4.686z"></path>
		</svg>
		<svg class="icon check"
				 viewBox="0 0 32 32"
				 aria-hidden="true">
			<path d="M27 4l-15 15-7-7-5 5 12 12 20-20z"></path>
		</svg>
		</button>
		<button id="notes_discard" on:click={spawnAlertDialog} bind:this={discardRef} aria-disabled={disableDiscardBtn}>Discard</button>
	</div>
</div>

<Dialog showAlertDialog={showAlertDialog} handleNoConfirmation={handleNoConfirmation} destroyNotes={destroyNotes} wordCount={wordCount} />

<style>
button {
    border-radius: 5px;
	display: inline-flex;
	align-items: center;
    padding: 8px 12px;
    border: 2px solid #005a6a;
    font-size: 13px;
    line-height: 1.4;
    background-color: #005a6a;
    text-decoration: none;
    font-weight: 700;
	color: #fff;
	margin-bottom: 3em;
}
	
button:focus-visible {
	outline: 2px dashed darkblue;
}

/* styling for alertdialog example */
.notes {
  display: block;
  font-size: 1rem;
  line-height: 1.3;
  min-width: 400px;
  max-width: 100%;
  width: 33%;
  outline: 1px solid #222;
  padding: .5em;
  margin-bottom: 1em;
}

.visually-hidden {
  border: 0;
  clip: rect(0 0 0 0);
  height: auto;
  margin: 0;
  overflow: hidden;
  padding: 0;
  position: absolute;
  width: 1px;
  white-space: nowrap;
}

#notes_save[aria-disabled="true"], #notes_discard[aria-disabled="true"] {
  opacity: 0.4;
}

#notes_save {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
}

#notes_save svg {
  display: block;
  width: 0.75rem;
	fill: currentColor;
}

#notes_save .icon {
  display: none;
}

@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

#notes_save.loading .spinner {
  display: block;
  animation: rotate 2s linear infinite;
}

#notes_save.saved .check {
  display: block;
}
</style>