<script>
    import { fly } from 'svelte/transition';
    import { page } from '$app/stores';
    import Header from "../lib/components/Header.svelte";

    const {children} = $props();

    const startTransition = () => {
        document.body.classList.add('page-transition');
    };

    const endTransition = () => {
        document.body.classList.remove('page-transition');
    };
</script>

<Header></Header>

{#key $page.url}

<main
in:fly={{ x: -200, duration: 300, delay: 300 }}
        out:fly={{ x: 200, duration: 300 }}
        onintrostart={startTransition}
        onintroend={endTransition}
        onoutrostart={startTransition}
        onoutroend={endTransition}>
    {@render children()}
</main>
{/key}

