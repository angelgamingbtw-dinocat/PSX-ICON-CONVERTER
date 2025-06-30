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

        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@800&display=swap');

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

        .color-option.black { background: #000; }
        .color-option.white { background: #fff; border: 2px solid #ddd; }

        // Slider styles removed - no longer needed
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
            <small>Supports JPG, PNG, GIF formats</small>
            <input type="file" id="fileInput" class="file-input" accept="image/*">
        </div>

        <div class="color-selector">
            <div class="color-option black selected" data-color="black" title="Black Overlay"></div>
            <div class="color-option white" data-color="white" title="White Overlay"></div>
        </div>

        <div class="result-container" id="resultContainer">
            <div class="canvas-container">
                <canvas id="outputCanvas"></canvas>
            </div>
            <div class="processing" id="processingText">Processing your image...</div>
            <button class="download-btn" id="downloadBtn" onclick="downloadImage()" style="display: none;">
                Download Processed Image
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

        // Slider event listener removed - no longer needed

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

        function processImage(img) {
            resultContainer.style.display = 'block';
            processingText.style.display = 'block';
            
            setTimeout(() => {
                const canvas = outputCanvas;
                const ctx = canvas.getContext('2d');
                
                // Calculate canvas size (add space for the maximum possible shift)
                const maxShift = Math.max(50, shiftAmount); // Ensure canvas is wide enough
                canvas.width = img.width + maxShift;
                canvas.height = img.height;
                
                // Clear canvas
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                
                // Helper function to create stroke outline using shadow technique
                function createStrokeOutline(image, strokeWidth, strokeColor) {
                    const outlineCanvas = document.createElement('canvas');
                    const outlineCtx = outlineCanvas.getContext('2d');
                    outlineCanvas.width = image.width + strokeWidth * 2;
                    outlineCanvas.height = image.height + strokeWidth * 2;
                    
                    // Create stroke effect by drawing the image multiple times with offsets
                    outlineCtx.fillStyle = strokeColor;
                    for (let x = -strokeWidth; x <= strokeWidth; x++) {
                        for (let y = -strokeWidth; y <= strokeWidth; y++) {
                            if (x * x + y * y <= strokeWidth * strokeWidth) {
                                outlineCtx.globalCompositeOperation = 'source-over';
                                outlineCtx.drawImage(image, strokeWidth + x, strokeWidth + y);
                                outlineCtx.globalCompositeOperation = 'source-in';
                                outlineCtx.fillRect(0, 0, outlineCanvas.width, outlineCanvas.height);
                            }
                        }
                    }
                    
                    return outlineCanvas;
                }
                
                // LAYER 1 (Bottom layer): Shifted LEFT by slider amount with color overlay and 11px outline
                ctx.save();
                
                // Create color overlay version
                const coloredCanvas = document.createElement('canvas');
                const coloredCtx = coloredCanvas.getContext('2d');
                coloredCanvas.width = img.width;
                coloredCanvas.height = img.height;
                
                // Draw image
                coloredCtx.drawImage(img, 0, 0);
                
                // Apply solid color overlay (pitch black or white)
                coloredCtx.globalCompositeOperation = 'source-atop';
                coloredCtx.fillStyle = selectedColor === 'black' ? '#000000' : '#ffffff';
                coloredCtx.fillRect(0, 0, img.width, img.height);
                
                // Create 11px outline (same color as overlay)
                const layer1Outline = createStrokeOutline(coloredCanvas, 11, selectedColor === 'black' ? '#000000' : '#ffffff');
                
                // Draw Layer 1 shifted LEFT by the slider amount from Layer 2's position
                const basePosition = maxShift; // Base position for Layer 2
                ctx.drawImage(layer1Outline, basePosition - shiftAmount - 11, -11);
                ctx.drawImage(coloredCanvas, basePosition - shiftAmount, 0);
                
                ctx.restore();
                
                // LAYER 2 (Top layer): Original image with 8px outline at normal position
                ctx.save();
                
                // Create 8px outline (same color as Layer 1's outline)
                const layer2Outline = createStrokeOutline(img, 8, selectedColor === 'black' ? '#000000' : '#ffffff');
                
                // Draw Layer 2 at base position
                ctx.drawImage(layer2Outline, basePosition - 8, -8);
                ctx.drawImage(img, basePosition, 0);
                
                ctx.restore();
                
                processingText.style.display = 'none';
                downloadBtn.style.display = 'inline-block';
            }, 100);
        }

        function downloadImage() {
            const canvas = outputCanvas;
            const link = document.createElement('a');
            link.download = 'layered-image.png';
            link.href = canvas.toDataURL();
            link.click();
        }
    </script>
</body>
</html>
