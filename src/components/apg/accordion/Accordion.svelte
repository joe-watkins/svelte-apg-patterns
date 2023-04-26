<script>

import "./Accordion.css";

export let 
    isExpanded, 
    headingLevel = 2,
    toggleText;

    // create unique ID
    const generateID = () => Date.now().toString(36) + Math.random().toString(36).substring(2, 7);

    let toggleID = generateID();
    let panelID = generateID();

</script>

<style>

</style>

{#if headingLevel == 2}
<h2>
    <button type="button" 
        aria-expanded={isExpanded} 
        aria-controls={panelID} 
        id={toggleID}
        on:click={() => { isExpanded = !isExpanded; }}
        class="accordion-trigger">
        <span class="accordion-title">
            {toggleText}
            <span class="accordion-icon"></span>
        </span>
    </button>
</h2>
{/if}

{#if headingLevel == 3}
<h3>
    <button type="button" 
        aria-expanded={isExpanded} 
        aria-controls={panelID} 
        id={toggleID}
        on:click={() => { isExpanded = !isExpanded; }}
        class="accordion-trigger">
        <span class="accordion-title">
            {toggleText}
        <span class="accordion-icon"></span>
    </span>
</button>
</h3>
{/if}

{#if headingLevel == 4}
<h4>
    <button type="button" 
        aria-expanded={isExpanded} 
        aria-controls={panelID} 
        id={toggleID}
        on:click={() => { isExpanded = !isExpanded; }}
        class="accordion-trigger">
        <span class="accordion-title">
            {toggleText}
        <span class="accordion-icon"></span>
    </span>
</button>
</h4>
{/if}

{#if headingLevel == 5}
<h5>
    <button type="button" 
        aria-expanded={isExpanded} 
        aria-controls={panelID} 
        id={toggleID}
        on:click={() => { isExpanded = !isExpanded; }}
        class="accordion-trigger">
        <span class="accordion-title">
            {toggleText}
        <span class="accordion-icon"></span>
    </span>
</button>
</h5>
{/if}

{#if headingLevel == 6}
<h6>
    <button type="button" 
        aria-expanded={isExpanded} 
        aria-controls={panelID} 
        id={toggleID}
        on:click={() => { isExpanded = !isExpanded; }}
        class="accordion-trigger">
        <span class="accordion-title">
            {toggleText}
        <span class="accordion-icon"></span>
    </span>
</button>
</h6>
{/if}

<div id={panelID}
    role="region"
    aria-labelledby={toggleID}
    hidden={!isExpanded}
    class="accordion-panel"
    >
    <div>
        <slot />
    </div>
</div>
