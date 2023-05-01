<script>
    /* https://www.w3.org/WAI/ARIA/apg/patterns/accordion/examples/accordion/ */ 
    // import "../../../components/apg/accordion/Accordion.css";
    import AccordionGroup from "../../../components/apg/accordion/AccordionGroup.svelte";
    import Accordion from "../../../components/apg/accordion/Accordion.svelte";  
    
    /* Syntax Highlighting */
	import { HighlightAuto } from "svelte-highlight";
	import github from "svelte-highlight/styles/github";

    let code = `import AccordionGroup from "./AccordionGroup.svelte";
import Accordion from "./Accordion.svelte"; 

<AccordionGroup>
    <Accordion 
        headingLevel="2" 
        isExpanded={false} 
        toggleText="Personal Information">
        <p>I am the accordion content</p>
    </Accordion>   
</AccordionGroup> 
`;


</script>

<svelte:head>
  {@html github}
</svelte:head>

<div class="prose prose-xl max-w-none mb-4">
	<h1>Accordion</h1>
    <h2>Description</h2>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Fugit ipsa molestias placeat, dolorum asperiores quibusdam autem, laboriosam veniam totam vel fuga beatae a accusamus, sunt dolor amet tenetur adipisci exercitationem?</p>
</div>

    <!-- usage -->
    <AccordionGroup>

        <Accordion 
            headingLevel="2" 
            isExpanded={false} 
            toggleText="Personal Information">
            <p>I am the accordion content</p>
        </Accordion>

        <Accordion 
            headingLevel="2" 
            isExpanded={false}
            toggleText="Billing Address"
            >
            <p> I am more content</p>
        </Accordion>

        <Accordion 
            headingLevel="2" 
            isExpanded={false}
            toggleText="Shipping Address"
            >
            <p> I am more content</p>
        </Accordion>

    </AccordionGroup>

<div class="prose prose-xl max-w-none mb-4">
    <h2>Usage</h2>
    <HighlightAuto {code} />
</div>