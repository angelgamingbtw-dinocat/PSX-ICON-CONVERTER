<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pet Simulator X Icon Converter</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

<style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@800&display=swap');

    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    body {
        font-family: 'Poppins', sans-serif;
        font-weight: 800;
        color: white;
        text-shadow: 2px 2px 0px #000000, -2px -2px 0px #000000, 2px -2px 0px #000000, -2px 2px 0px #000000;
        background: linear-gradient(135deg, #ffffff 0%, #ffffff 100%);
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 20px;
        position: relative;
    }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-image: url('https://tr.rbxcdn.com/180DAY-63613e0c81a7804328b0f97d13522c1f/420/420/Image/Webp/noFilter');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            filter: brightness(0) saturate(100%) invert(89%) sepia(3%) saturate(191%) hue-rotate(202deg) brightness(95%) contrast(88%);
            opacity: 0.1;
            z-index: -1;
        }

        .container {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            max-width: 900px;
            width: 100%;
        }

        h1 {
            text-align: center;
            color: white;
            text-shadow: 3px 3px 0px #000000, -3px -3px 0px #000000, 3px -3px 0px #000000, -3px 3px 0px #000000;
            margin-bottom: 30px;
            font-size: 2.5em;
            font-weight: 800;
        }

        .upload-area {
            border: 3px dashed #667eea;
            border-radius: 15px;
            padding: 40px;
            text-align: center;
            margin-bottom: 30px;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .upload-area:hover {
            border-color: #764ba2;
            background: rgba(102, 126, 234, 0.05);
        }

        .upload-area.dragover {
            border-color: #764ba2;
            background: rgba(102, 126, 234, 0.1);
            transform: scale(1.02);
        }

        .upload-text {
            color: white;
            text-shadow: 2px 2px 0px #000000, -2px -2px 0px #000000, 2px -2px 0px #000000, -2px 2px 0px #000000;
            font-size: 1.2em;
            font-weight: 800;
            margin-bottom: 10px;
        }

        .file-input {
            display: none;
        }

        .color-selector {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-bottom: 30px;
        }

        .color-option {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            border: 4px solid transparent;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
        }

        .color-option:hover {
            transform: scale(1.1);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .color-option.selected {
            border-color: #333;
            transform: scale(1.15);
        }
        
        .color-option.hue.selected {
            border-color: transparent;
        }

        .color-option.black { background: #000; }
        .color-option.white { background: #fff; border: 2px solid #ddd; }
        .color-option.hue { 
            background: radial-gradient(circle, #000000 0%, #bf68b9 57%, #ed81e6 100%);
        }

        .shift-control {
            display: none;
        }

        .result-container {
            position: relative;
            text-align: center;
            margin-top: 30px;
            display: none;
        }

        .canvas-container {
            position: relative;
            display: inline-block;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
        }

        canvas {
            display: block;
            max-width: 100%;
            height: auto;
        }

        .processing {
            color: white;
            text-shadow: 2px 2px 0px #000000, -2px -2px 0px #000000, 2px -2px 0px #000000, -2px 2px 0px #000000;
            font-size: 1.1em;
            font-weight: 800;
            margin-top: 20px;
        }

        .download-btn {
            background: linear-gradient(135deg, #ffffff 0%, #ffffff 100%);
            color: white;
            text-shadow: 2px 2px 0px #000000, -2px -2px 0px #000000, 2px -2px 0px #000000, -2px 2px 0px #000000;
            border: none;
            padding: 12px 30px;
            border-radius: 25px;
            font-size: 1.1em;
            font-weight: 800;
            cursor: pointer;
            margin-top: 20px;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0, 0.3);
        }

        .download-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0,0,0, 0.4);
        }

        .download-btn:active {
            transform: translateY(0);
        }

        .download-btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
            transform: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>PET SIMULATOR X ICON CONVERTER</h1>
        
        <div class="upload-area" id="uploadArea">
            <div class="upload-text">Drop an image here or click to select</div>
            <input type="file" id="fileInput" class="file-input" accept="image/*">
        </div>

        <div class="color-selector">
            <div class="color-option black selected" data-color="black" title="Black Overlay"></div>
            <div class="color-option white" data-color="white" title="White Overlay"></div>
            <div class="color-option hue" data-color="hue" title="Hue Overlay"></div>
        </div>

        <div class="result-container" id="resultContainer">
            <div class="canvas-container">
                <canvas id="outputCanvas"></canvas>
            </div>
            <div class="processing" id="processingText">Processing your image...</div>
            <button class="download-btn" id="downloadBtn" onclick="downloadImage()" style="display: none;">
                Download Image
            </button>
        </div>
    </div>

    <script>
        const uploadArea = document.getElementById('uploadArea');
        const fileInput = document.getElementById('fileInput');
        const resultContainer = document.getElementById('resultContainer');
        const outputCanvas = document.getElementById('outputCanvas');
        const processingText = document.getElementById('processingText');
        const colorOptions = document.querySelectorAll('.color-option');
        const downloadBtn = document.getElementById('downloadBtn');
        
        let selectedColor = 'black';
        let currentImage = null;
        let shiftAmount = 5; // Fixed at 5px

        // Color selection
        colorOptions.forEach(option => {
            option.addEventListener('click', () => {
                colorOptions.forEach(opt => opt.classList.remove('selected'));
                option.classList.add('selected');
                selectedColor = option.dataset.color;
                
                if (currentImage) {
                    processImage(currentImage);
                }
            });
        });

        // Upload area interactions
        uploadArea.addEventListener('click', () => fileInput.click());
        
        uploadArea.addEventListener('dragover', (e) => {
            e.preventDefault();
            uploadArea.classList.add('dragover');
        });
        
        uploadArea.addEventListener('dragleave', () => {
            uploadArea.classList.remove('dragover');
        });
        
        uploadArea.addEventListener('drop', (e) => {
            e.preventDefault();
            uploadArea.classList.remove('dragover');
            const files = e.dataTransfer.files;
            if (files.length > 0) {
                handleFile(files[0]);
            }
        });

        fileInput.addEventListener('change', (e) => {
            if (e.target.files.length > 0) {
                handleFile(e.target.files[0]);
            }
        });

        function handleFile(file) {
            if (!file.type.startsWith('image/')) {
                alert('Please select a valid image file.');
                return;
            }

            const reader = new FileReader();
            reader.onload = (e) => {
                const img = new Image();
                img.onload = () => {
                    currentImage = img;
                    processImage(img);
                };
                img.src = e.target.result;
            };
            reader.readAsDataURL(file);
        }

        function createGradientFill(ctx, width, height) {
            const centerX = width / 2;
            const centerY = height / 2;
            const radius = Math.max(width, height);
            
            const gradient = ctx.createRadialGradient(centerX, centerY, 0, centerX, centerY, radius);
            gradient.addColorStop(0, '#000000');
            gradient.addColorStop(0.57, '#bf68b9');
            gradient.addColorStop(1, '#ed81e6');
            
            return gradient;
        }

        function applyHueBlend(ctx, width, height, hueColor) {
            const imageData = ctx.getImageData(0, 0, width, height);
            const data = imageData.data;
            const hueRgb = hexToRgb(hueColor);
            const hueHsl = rgbToHsl(hueRgb.r, hueRgb.g, hueRgb.b);
            
            for (let i = 0; i < data.length; i += 4) {
                const r = data[i];
                const g = data[i + 1];
                const b = data[i + 2];
                const a = data[i + 3];
                
                if (a > 0) {
                    const hsl = rgbToHsl(r, g, b);
                    const newHsl = { h: hueHsl.h, s: hsl.s, l: hsl.l };
                    const newRgb = hslToRgb(newHsl.h, newHsl.s, newHsl.l);
                    
                    data[i] = newRgb.r;
                    data[i + 1] = newRgb.g;
                    data[i + 2] = newRgb.b;
                }
            }
            
            ctx.putImageData(imageData, 0, 0);
        }

        function hexToRgb(hex) {
            const result = /^#?([a-f\d]{2})([a-f\d]{2})([a-f\d]{2})$/i.exec(hex);
            return result ? {
                r: parseInt(result[1], 16),
                g: parseInt(result[2], 16),
                b: parseInt(result[3], 16)
            } : null;
        }

        function rgbToHsl(r, g, b) {
            r /= 255; g /= 255; b /= 255;
            const max = Math.max(r, g, b), min = Math.min(r, g, b);
            let h, s, l = (max + min) / 2;
            
            if (max === min) {
                h = s = 0;
            } else {
                const d = max - min;
                s = l > 0.5 ? d / (2 - max - min) : d / (max + min);
                switch (max) {
                    case r: h = (g - b) / d + (g < b ? 6 : 0); break;
                    case g: h = (b - r) / d + 2; break;
                    case b: h = (r - g) / d + 4; break;
                }
                h /= 6;
            }
            return { h, s, l };
        }

        function hslToRgb(h, s, l) {
            let r, g, b;
            
            if (s === 0) {
                r = g = b = l;
            } else {
                const hue2rgb = (p, q, t) => {
                    if (t < 0) t += 1;
                    if (t > 1) t -= 1;
                    if (t < 1/6) return p + (q - p) * 6 * t;
                    if (t < 1/2) return q;
                    if (t < 2/3) return p + (q - p) * (2/3 - t) * 6;
                    return p;
                };
                
                const q = l < 0.5 ? l * (1 + s) : l + s - l * s;
                const p = 2 * l - q;
                r = hue2rgb(p, q, h + 1/3);
                g = hue2rgb(p, q, h);
                b = hue2rgb(p, q, h - 1/3);
            }
            
            return {
                r: Math.round(r * 255),
                g: Math.round(g * 255),
                b: Math.round(b * 255)
            };
        }

        function processImage(img) {
            resultContainer.style.display = 'block';
            processingText.style.display = 'block';
            
            setTimeout(() => {
                const canvas = outputCanvas;
                const ctx = canvas.getContext('2d');
                
                const outlineWidth = 11;
                canvas.width = img.width + shiftAmount + outlineWidth * 2;
                canvas.height = img.height + outlineWidth * 2;
                
                const basePositionX = outlineWidth + shiftAmount;
                const basePositionY = outlineWidth;
                
                ctx.clearRect(0, 0, canvas.width, canvas.height);

                let fillStyle;
                // --- THIS IS THE MODIFIED LOGIC ---
                if (selectedColor === 'gradient' || selectedColor === 'hue') {
                    fillStyle = createGradientFill(ctx, canvas.width, canvas.height);
                } else {
                    fillStyle = selectedColor === 'black' ? '#000000' : '#ffffff';
                }

                ctx.save();
                for (let x = -outlineWidth; x <= outlineWidth; x++) {
                    for (let y = -outlineWidth; y <= outlineWidth; y++) {
                        if (x * x + y * y <= outlineWidth * outlineWidth) {
                            ctx.drawImage(img, basePositionX - shiftAmount + x, basePositionY + y);
                        }
                    }
                }
                ctx.globalCompositeOperation = 'source-in';
                ctx.fillStyle = fillStyle;
                ctx.fillRect(0, 0, canvas.width, canvas.height);
                ctx.restore();

                let topLayerImage = img;
                if (selectedColor === 'hue') {
                    const hueCanvas = document.createElement('canvas');
                    const hueCtx = hueCanvas.getContext('2d');
                    hueCanvas.width = img.width;
                    hueCanvas.height = img.height;
                    hueCtx.drawImage(img, 0, 0);
                    applyHueBlend(hueCtx, img.width, img.height, '#fc00ff');
                    topLayerImage = hueCanvas;
                }
                
                ctx.drawImage(topLayerImage, basePositionX, basePositionY);
                
                processingText.style.display = 'none';
                downloadBtn.style.display = 'inline-block';
            }, 100);
        }

        function downloadImage() {
            const canvas = outputCanvas;
            const link = document.createElement('a');
            link.download = 'processed-icon.png';
            link.href = canvas.toDataURL();
            link.click();
        }
    </script>
</body>
</html>
