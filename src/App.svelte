<script>
    import Stack from './layout/Stack.svelte';
    import Sidebar from "./layout/Sidebar.svelte";
    import Cover from "./layout/Cover.svelte";
</script>

<Stack>
    <div style="border: 1px solid gray; padding: var(--s1)">
        <Sidebar sideWidth="var(--s0)" space="var(--s1)">
            <Stack>
                <p>
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas sed tincidunt nibh. Phasellus
                    non
                </p>
                <button>Edit</button>
                <button>Delete</button>
                <button>Share</button>
            </Stack>
            <Cover minHeight="20vh">
                <h1>Creating Custom Dialogs</h1>
                <p>
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas sed tincidunt nibh. Phasellus
                    non
                </p>
            </Cover>
        </Sidebar>
    </div>

    <div style="border: 1px solid gray; padding: var(--s1)">
        <Stack space="var(--s1)" recursive>
            <Stack>
                <label>Email</label>
                <input type="email">
            </Stack>
            <Stack>
                <label>Password</label>
                <input type="password">
            </Stack>
            <Stack>
                <label>Confirm password</label>
                <input type="password">
            </Stack>
            <button>Submit</button>
        </Stack>
    </div>
</Stack>

<style>
    /*
        Setting up measure/threshold

        See https://absolutely.every-layout.dev/rudiments/axioms/

        Also see discusssion at "Lobotomized owl CSS selector broken"
        https://github.com/sveltejs/svelte/issues/3104
    */
    :global(:root) {
        --measure: 60ch;
    }

    :global(.max-width\:measure) {
        max-width: var(--measure);
    }

    :global(.max-width\:measure\/2) {
        max-width: calc(var(--measure) / 2);
    }

    /* TODO: Figure out elements to actually apply this to */
    :global(*) {
        max-width: var(--measure);
    }

    /*
        Setting up spaces

        See https://absolutely.every-layout.dev/rudiments/modular-scale/
    */
    :global(:root) {
        --ratio: 1.5;
        --s-5: calc(var(--s-4) / var(--ratio));
        --s-4: calc(var(--s-3) / var(--ratio));
        --s-3: calc(var(--s-2) / var(--ratio));
        --s-2: calc(var(--s-1) / var(--ratio));
        --s-1: calc(var(--s0) / var(--ratio));
        --s0: 1rem;
        --s1: calc(var(--s0) * var(--ratio));
        --s2: calc(var(--s1) * var(--ratio));
        --s3: calc(var(--s2) * var(--ratio));
        --s4: calc(var(--s3) * var(--ratio));
        --s5: calc(var(--s4) * var(--ratio));
    }

    html,
    body,
    div,
    header,
    nav,
    main,
    footer {
        max-width: none;
    }

    /*
        Modern CSS reset https://hankchizljaw.com/wrote/a-modern-css-reset/
     */
    /* Box sizing rules */
    :global(*),
    :global(*)::before,
    :global(*)::after {
        box-sizing: border-box;
    }

    /* Remove default padding */
    ul[class],
    ol[class] {
        padding: 0;
    }

    /* Remove default margin */
    body,
    h1,
    h2,
    h3,
    h4,
    p,
    ul[class],
    ol[class],
    li,
    figure,
    figcaption,
    blockquote,
    dl,
    dd {
        margin: 0;
    }

    /* Set core body defaults */
    body {
        min-height: 100vh;
        scroll-behavior: smooth;
        text-rendering: optimizeSpeed;
        line-height: 1.5;
    }

    /* Remove list styles on ul, ol elements with a class attribute */
    ul[class],
    ol[class] {
        list-style: none;
    }

    /* A elements that don't have a class get default styles */
    a:not([class]) {
        text-decoration-skip-ink: auto;
    }

    /* Make images easier to work with */
    img {
        max-width: 100%;
        display: block;
    }

    /* Natural flow and rhythm in articles by default */
    article > :global(* + *) {
        margin-top: 1em;
    }

    /* Inherit fonts for inputs and buttons */
    input,
    button,
    textarea,
    select {
        font: inherit;
    }

    /* Remove all animations and transitions for people that prefer not to see them */
    @media (prefers-reduced-motion: reduce) {
        * {
            animation-duration: 0.01ms !important;
            animation-iteration-count: 1 !important;
            transition-duration: 0.01ms !important;
            scroll-behavior: auto !important;
        }
    }
</style>