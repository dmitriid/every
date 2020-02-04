<!--
    A custom element for covering a block-level element horizontally,
    with a max-width value representing the typographic measure

    https://absolutely.every-layout.dev/layouts/cover/
-->

<script>
    // TODO: A simple selector such an element or class selector, representing the centered (main) element in the cover
    // export let centered = 'h1';

    // The minimum space between and around all of the child elements
    // For default s1, https://absolutely.every-layout.dev/rudiments/modular-scale/
    export let space = 'var(--s1)';
    // The minimum height for the Cover
    export let minHeight = '100vh';
    // Whether the spacing is also applied as padding to the container element
    export let noPad = false;
</script>

<style>
    .cover {
        --space: var(--s1);
        --min-height: '100vh';
        --padding: var(--s1);
        display: flex;
        flex-direction: column;
        min-height: var(--min-height);
        padding: var(--padding);
    }

    /*
      See discusssion at "Lobotomized owl CSS selector broken"
      https://github.com/sveltejs/svelte/issues/3104
    */
    .cover > :global(*) {
        margin-top: var(--space);
        margin-bottom: var(--space);
    }

    .cover > :first-child:not(h1) {
        margin-top: 0;
    }

    .cover > :last-child:not(h1) {
        margin-bottom: 0;
    }

    .cover > h1 {
        margin-top: auto;
        margin-bottom: auto;
    }
</style>

<div class="cover"
     style="--space: {space === '0' ? '0px' : space}; --min-height: {minHeight}; --padding: {noPad ? '0' : space}">
    <slot/>
</div>