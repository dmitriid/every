<!--
    A custom element for placing two elements side-by-side.

    If space permits, the sidebar element has a set width, and the companion
    takes up the rest of the available horizontal space.

    If not, the elements are collapsed into a single column, each taking up
    100% of the horizontal space.

    https://absolutely.every-layout.dev/layouts/sidebar/
-->

<script>
    // Which element to treat as the sidebar (all values but "left" are considered "right")
    export let side = 'left';
    // Represents the width of the sidebar when adjacent.
    // If not set (null) it defaults to the sidebar's content width
    export let sideWidth = null;
    // A CSS *percentage* value.
    // The minimum width of the content element in the horizontal configuration
    export let contentMin = '50%';
    // A CSS margin value representing the space between the two elements
    // For default s1, https://absolutely.every-layout.dev/rudiments/modular-scale/
    export let space = 'var(--s1)';
    // Make the adjacent elements adopt their natural height
    export let noStretch = false;
</script>

<style>
    .with-sidebar {
        overflow: hidden;
        --side-width: '';
        --content-min: '';
        --space: var(--s1);
    }

    /*
      See discusssion at "Lobotomized owl CSS selector broken"
      https://github.com/sveltejs/svelte/issues/3104
    */
    .with-sidebar > :global(*) {
        display: flex;
        flex-wrap: wrap;
        margin: calc(var(--space) / 2 * -1);
    }

    .with-sidebar > :global(*) > :global(*) {
        margin: calc(var(--space) / 2);
        flex-grow: 1;
        flex-basis: var(--side-width);
    }

    .with-sidebar.noStretch > :global(*) {
        align-items: flex-start;
    }

    .with-sidebar.left > :global(* > :last-child) {
        flex-basis: 0;
        flex-grow: 999;
        min-width: calc(var(--content-min) - var(--s1));
    }

    .with-sidebar.right > :global(* > :first-child) {
        flex-basis: 0;
        flex-grow: 999;
        min-width: calc(var(--content-min) - var(--s1));
    }
</style>

<div class="with-sidebar"
     class:noStretch={noStretch}
     class:left={side==='left'}
     class:right={side!=='left'}
     style="--space: {space === '0' ? '0px' : space}; --side-width: {sideWidth}; --content-min: {contentMin}">
    <div>
        <slot/>
    </div>
</div>