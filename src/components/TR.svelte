<script>
    import A from "./A.svelte";
    let { date, name, href, disabled } = $props();
</script>

<tr class="odd:bg-white even:bg-slate-50 *:px-4 *:py-3">
    <td class="text-nowrap">{date}</td>
    <td>{name}</td>
    <td class="text-center">
        <A name="Open" {href} {disabled} />
    </td>
</tr>
