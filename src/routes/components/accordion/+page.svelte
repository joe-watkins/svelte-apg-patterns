<script>
    /* https://www.w3.org/WAI/ARIA/apg/patterns/accordion/examples/accordion/ */ 
    // import "../../../components/apg/accordion/Accordion.css";
    import AccordionGroup from "../../../components/apg/accordion/AccordionGroup.svelte";
    import Accordion from "../../../components/apg/accordion/Accordion.svelte";    

</script>

<h1 class="mb-4 text-4xl">Accordion</h1>

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