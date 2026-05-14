<script>
    import { onMount } from "svelte";

    // In Svelte 5, we use the $state rune to declare reactive variables.
    // When these change, the UI automatically updates.
    let showingAnswer = $state(false);
    let currentNum1 = $state(0);
    let currentNum2 = $state(0);

    function generateProblem() {
        // Generate num1 between 12 and 30
        currentNum1 = Math.floor(Math.random() * (30 - 12 + 1)) + 12;
        // Generate num2 between 2 and 9
        currentNum2 = Math.floor(Math.random() * (9 - 2 + 1)) + 2;
        showingAnswer = false;
    }

    function handleInteraction() {
        if (!showingAnswer) {
            showingAnswer = true;
        } else {
            generateProblem();
        }
    }

    function handleKeydown(event) {
        if (event.code === "Space") {
            event.preventDefault(); // Prevents page from scrolling down
            handleInteraction();
        }
    }

    function handlePointerdown(event) {
        event.preventDefault();
        handleInteraction();
    }

    // Initialize the first problem when the component mounts to the DOM
    onMount(() => {
        generateProblem();
    });
</script>

<!-- Global event listener for the spacebar -->
<svelte:window onkeydown={handleKeydown} />

<!--
  Main Wrapper
  Uses Tailwind for full screen height, centering, background, and typography
-->
<div
    role="button"
    tabindex="0"
    class="flex min-h-screen flex-col items-center justify-center bg-gray-800 text-white font-sans select-none cursor-pointer overflow-hidden m-0"
    onpointerdown={handlePointerdown}
>
    <div class="text-center">
        <!-- Equation Display -->
        <div class="text-6xl md:text-8xl font-bold m-0 drop-shadow-lg">
            {currentNum1} &times; {currentNum2} = {showingAnswer
                ? currentNum1 * currentNum2
                : "?"}
        </div>

        <!-- Instructional Text -->
        <div
            class="mt-8 text-xl md:text-2xl text-gray-400 bg-black/20 px-5 py-2.5 rounded-lg opacity-80 inline-block"
        >
            {#if showingAnswer}
                Press SPACE (or click) for next
            {:else}
                Press SPACE (or click) for answer
            {/if}
        </div>
    </div>
</div>
