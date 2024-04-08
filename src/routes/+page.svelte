<script>
	import '/src/style.css';
    import Studio from "$lib/components/Studio.svelte"
    import { indexSectionStore, indexStyleStore, isOpenStore } from '$lib/store.js';
	import { onMount } from 'svelte';
	import { estilos } from '$lib/config.js';
    import Subscribe from '$lib/components/Subscribe.svelte';
    import Contact from '$lib/components/Contact.svelte';

	let themes = ['', 'gum', 'dark'];
	let index = 0;
    let header

    onMount(()=> {

        indexStyleStore.subscribe((value) => {
                index = value;
                // metaSymbol.changeTexture(index);
                document.body.classList = themes[index];
        });
    })
</script>


<div class="bg-background lp:h-screen flex flex-col items-center justify-center max-w-screen z-30">

    <div class="dp:max-w-[1440px] dp:mx-auto flex flex-col items-center justify-between lp:rounded-xl lp:h-[95%] p-4 lp:py-4 lp:px-8 shadow-custom">
    <header bind:this={header} class="text-primary font-clash-display w-full">
        <nav class="flex justify-between items-center mx-auto w-full">
            <div class="lp:self-start">
                <a href="https://artdao.xyz/"
                    ><img
                        loading="lazy"
                        src={`/artdao-logo-${estilos[index].primary_media}.svg`}
                        alt="Artdao Logo"
                    /></a
                >
            </div>
            <a href="https://artdao.xyz/"
			><img
				loading="lazy"
				src={`/events/close-${estilos[index].primary_media}.svg`}
				alt="Close"
			/></a
		>
        </nav>
    </header>

    <!-- <div class="text-primary font-clash-display font-normal uppercase lp:mx-10 dp:max-w-[1440px] dp:mx-auto"> -->

    <Studio/>
    <!-- </div> -->

    <div class="hidden w-full lp:flex items-center justify-between">
        <Subscribe />
        <Contact />
    </div>  
</div>
</div>