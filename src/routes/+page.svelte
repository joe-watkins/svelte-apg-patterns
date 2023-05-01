<script>
    import ComponentCard from "../components/global/ComponentCard.svelte";
</script>

<h1 class="mb-4 text-2xl">Home</h1>
<p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Illum, eum, aut totam ex molestiae corrupti minus autem perspiciatis corporis hic excepturi asperiores quaerat. Soluta minus sunt labore tempore maiores at?</p>

<h2 class="mb-4 text-2xl">Recent Components</h2>

<div class="md:grid gap-4 grid-cols-3 auto-rows-auto mx-auto">
    <ComponentCard 
        name="Accordion" 
        imgUrl="./src/assets/faq.png"
        imageAlt=""
        componentPage="/components/accordion">
        I am the description.
    </ComponentCard>
    <ComponentCard 
        name="Disclosure - FAQ" 
        imgUrl="./src/assets/disclosure.png"
        imageAlt=""
        componentPage="/components/disclosure">
        I am the description.
    </ComponentCard>
    <ComponentCard 
        name="Alert" 
        imgUrl="./src/assets/alert.png"
        imageAlt=""
        componentPage="/components/alert">
        I am the description.
    </ComponentCard>
    <ComponentCard 
        name="Alert Dialog" 
        imgUrl="./src/assets/alert-dialog.png"
        imageAlt=""
        componentPage="/components/alert-dialog">
        I am the description.
    </ComponentCard>
    <ComponentCard 
        name="Breadcrumb" 
        imgUrl="./src/assets/breadcrumb.png"
        imageAlt=""
        componentPage="/components/breadcrumb">
        I am the description.
    </ComponentCard>
</div>
