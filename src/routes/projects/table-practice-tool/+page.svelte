<script>
    let start = $state(false);
    let n = $state();
    let rand = $state(5);
    let action = $state(true);
    let actionBtn;

    function handleAction() {
        if (!n) return;
        start = true;
        if (action) {
            let temp = rand;
            rand = Math.floor(Math.random() * 8) + 2;
            while (temp === rand) {
                rand = Math.floor(Math.random() * 8) + 2;
            }
        }
        action = !action;
    }
</script>

<div class="text-4xl flex flex-col items-center mt-10 gap-5">
    <div class="rounded flex flex-col items-center">
        {#if !start}
            <input
                type="number"
                placeholder="Table"
                class="text-center"
                bind:value={n}
                onkeydown={(e) => {
                    if (e.key === "Enter") {
                        handleAction();
                        actionBtn && actionBtn.focus();
                    }
                }}
            />
        {:else}
            <p class="">{n} x {rand} = {action ? n * rand : "?"}</p>
        {/if}
    </div>
    <button
        class="px-8 py-4 bg-blue-600 hover:bg-blue-700 text-white font-medium rounded-md shadow-md"
        bind:this={actionBtn}
        onclick={handleAction}>Action</button
    >
</div>
