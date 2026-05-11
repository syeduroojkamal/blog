<script>
    import "./layout.css";
    import favicon from "$lib/assets/favicon.svg";
    import NavBar from "../components/NavBar.svelte";

    let { children } = $props();
</script>

<NavBar />
<svelte:head><link rel="icon" href={favicon} /></svelte:head>
{@render children()}
