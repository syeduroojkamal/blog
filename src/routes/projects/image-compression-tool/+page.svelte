<script>
    let originalImage = null;

    document.getElementById("upload").addEventListener("change", function (e) {
        const file = e.target.files[0];
        const reader = new FileReader();
        reader.onload = function (event) {
            const img = new Image();
            img.onload = () => {
                originalImage = img;
                previewThreshold(); // initial render
            };
            img.src = event.target.result;
        };
        reader.readAsDataURL(file);
    });

    // LIVE PREVIEW (no scaling for speed)
    document
        .getElementById("threshold")
        .addEventListener("input", previewThreshold);

    function previewThreshold() {
        if (!originalImage) return;

        const threshold = document.getElementById("threshold").value;

        const canvas = document.getElementById("canvas");
        const ctx = canvas.getContext("2d");

        const width = originalImage.width;
        const height = originalImage.height;

        canvas.width = width;
        canvas.height = height;

        ctx.drawImage(originalImage, 0, 0, width, height);

        const imageData = ctx.getImageData(0, 0, width, height);
        const data = imageData.data;

        for (let i = 0; i < data.length; i += 4) {
            const avg = (data[i] + data[i + 1] + data[i + 2]) / 3;
            const value = avg > threshold ? 255 : 0;
            data[i] = data[i + 1] = data[i + 2] = value;
        }

        ctx.putImageData(imageData, 0, 0);
    }

    // FINAL PROCESS (with scaling)
    function processImage() {
        if (!originalImage) return alert("Upload image first");

        const threshold = document.getElementById("threshold").value;
        const scale = document.getElementById("scale").value / 100;

        const canvas = document.getElementById("canvas");
        const ctx = canvas.getContext("2d");

        const width = originalImage.width * scale;
        const height = originalImage.height * scale;

        canvas.width = width;
        canvas.height = height;

        ctx.drawImage(originalImage, 0, 0, width, height);

        const imageData = ctx.getImageData(0, 0, width, height);
        const data = imageData.data;

        for (let i = 0; i < data.length; i += 4) {
            const avg = (data[i] + data[i + 1] + data[i + 2]) / 3;
            const value = avg > threshold ? 255 : 0;
            data[i] = data[i + 1] = data[i + 2] = value;
        }

        ctx.putImageData(imageData, 0, 0);
    }

    function downloadImage() {
        const canvas = document.getElementById("canvas");
        const link = document.createElement("a");
        link.download = "compressed.png";
        link.href = canvas.toDataURL("image/png");
        link.click();
    }
</script>

<div class="card">
    <h1>Black & White Image Compressor</h1>

    <input type="file" id="upload" accept="image/*" />

    <label>Threshold (live preview)</label>
    <input type="range" id="threshold" min="0" max="255" value="150" />

    <label>Scale (applied on render)</label>
    <input type="range" id="scale" min="10" max="100" value="50" />

    <button on:click={processImage()}>Apply Scale & Finalize</button>

    <canvas id="canvas"></canvas>

    <button on:click={downloadImage()}>Download</button>
</div>

<style>
    .card {
        background: #1e293b;
        padding: 20px;
        border-radius: 16px;
        width: 90%;
        max-width: 600px;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
    }
    h1 {
        font-size: 22px;
        margin-bottom: 10px;
    }
    input,
    button {
        margin-top: 10px;
        width: 100%;
        padding: 10px;
        border-radius: 8px;
        border: none;
    }
    button {
        background: #22c55e;
        color: black;
        font-weight: bold;
        cursor: pointer;
    }
    canvas {
        margin-top: 15px;
        max-width: 100%;
        border-radius: 8px;
        background: white;
    }
    label {
        font-size: 14px;
        margin-top: 10px;
        display: block;
    }
</style>
