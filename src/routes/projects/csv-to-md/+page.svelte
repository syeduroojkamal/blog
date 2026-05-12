<script>
    function copyToClipboard() {
        const outputEl = document.getElementById("output");
        const copyBtn = event.target; // Get the clicked button

        if (!outputEl.value) return;

        // Use the modern Clipboard API
        navigator.clipboard
            .writeText(outputEl.value)
            .then(() => {
                // Provide visual feedback
                const originalText = copyBtn.innerText;
                copyBtn.innerText = "Copied!";

                setTimeout(() => {
                    copyBtn.innerText = originalText;
                }, 2000);
            })
            .catch((err) => {
                console.error("Failed to copy: ", err);
                // Fallback for older browsers
                outputEl.select();
                document.execCommand("copy");
            });
    }
    function convertToMarkdown() {
        const input = document.getElementById("input").value.trim();
        const outputEl = document.getElementById("output");

        if (!input) {
            outputEl.value = "";
            return;
        }

        // Split into rows, handling different OS line breaks
        const lines = input.split(/\r?\n/);

        // Auto-detect if data is Tab-Separated (pasted from Excel) or Comma-Separated
        const separator = lines[0].includes("\t") ? "\t" : ",";

        let markdown = "";

        lines.forEach((line, index) => {
            // Split row into cells and trim whitespace from edges
            const cells = line.split(separator).map((cell) => cell.trim());

            // Build the Markdown row
            markdown += "| " + cells.join(" | ") + " |\n";

            // If it's the first row (header), add the alignment separator row
            if (index === 0) {
                // Left-aligned format
                const separators = cells.map(() => ":---");
                markdown += "| " + separators.join(" | ") + " |\n";
            }
        });

        outputEl.value = markdown;

        // Optional: Auto-select the output for easy copying
        outputEl.select();
    }
</script>

<div class="flex flex-col items-center p-8 space-y-4 max-w-xl mx-auto">
    <!-- Slim Input -->
    <textarea
        id="input"
        placeholder="Paste CSV..."
        class="w-full h-32 p-3 border rounded-md focus:outline-none focus:border-blue-500 font-mono text-sm"
    ></textarea>

    <!-- Clean Button -->
    <button
        onclick={convertToMarkdown}
        class="w-full py-2 border border-black hover:bg-black hover:text-white transition-colors duration-200 uppercase tracking-widest text-xs font-bold"
    >
        Convert
    </button>

    <!-- Read-only Output -->
    <textarea
        readonly
        id="output"
        placeholder="Markdown output..."
        class="w-full h-32 p-3 border rounded-md bg-gray-50 font-mono text-sm resize-none"
    ></textarea>
    <button
        onclick={copyToClipboard}
        class="self-end text-xs text-gray-500 hover:text-black transition underline"
    >
        Copy to clipboard
    </button>
</div>
