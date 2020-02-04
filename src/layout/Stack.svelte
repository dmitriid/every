<!--
    A custom element for injecting white space (margin) between flow
    (block) elements along a vertical axis.

    https://absolutely.every-layout.dev/layouts/stack/
-->

<script>
    // A CSS margin value
    // For default s1, https://absolutely.every-layout.dev/rudiments/modular-scale/
    export let space = 'var(--s1)';
    // Whether the spaces apply recursively (i.e. regardless of nesting level)
    export let recursive = false;
    // Note: splitAfter is not implemented
</script>

<style>
    .stack {
        --space: 1.5rem;
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
    }

    /*
      See discusssion at "Lobotomized owl CSS selector broken"
      https://github.com/sveltejs/svelte/issues/3104

      Also, `.stack > *` overrides `.stack * + *` so I've commented this
      out for now
    */

    /*.stack > :global(*) {
        margin-top: 0;
        margin-bottom: 0;
    }

    .stack.recursive :global(*) {
        margin-top: 0;
        margin-bottom: 0;
    }*/

    .stack :global(* + *) {
        margin-top: var(--space);
    }
</style>

<div class="stack" class:recursive={recursive} style="--space: {space}">
    <slot/>
</div>