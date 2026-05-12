<script>
    import { page } from "$app/stores";
    let {
        name = "Default",
        href = "#",
        class: className = "",
        disabled = "no",
    } = $props();
</script>

{#if disabled === "yes"}
    <span
        class="px-3 py-1.5 bg-gray-500 text-gray-300 font-medium rounded-md cursor-not-allowed opacity-60 {className}"
    >
        {name}
    </span>
{:else}
    <a
        {href}
        class="px-3 py-1.5 hover:bg-blue-700 text-white font-medium rounded-md
    {className} {$page.url.pathname === href ? 'bg-blue-900' : 'bg-blue-600'}"
    >
        {name}
    </a>
{/if}
