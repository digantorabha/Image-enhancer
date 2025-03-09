<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Optimize and compress your images with our easy-to-use tool. Change image backgrounds and compress images to your desired level.">
    <meta name="keywords" content="image compression, image optimization, background change, image tool, SEO">
    <meta name="author" content="Your Name">
    <title>Image Optimization Tool</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap" rel="stylesheet">
    <style>
        /* Global Styles */
        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f8f9fa;
            color: #333;
        }

        header {
            background-color: #4a90e2;
            color: #fff;
            padding: 20px 0;
            text-align: center;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        main {
            padding: 20px;
            max-width: 800px;
            margin: 0 auto;
        }

        section {
            background-color: #fff;
            padding: 20px;
            margin-bottom: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        h2 {
            margin-top: 0;
            color: #4a90e2;
        }

        input[type="file"] {
            display: none;
        }

        .upload-label {
            display: inline-block;
            background-color: #4a90e2;
            color: #fff;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .upload-label:hover {
            background-color: #357abd;
        }

        #compression-controls {
            text-align: center;
        }

        #compressionLevel {
            width: 80%;
            margin: 10px 0;
        }

        #compressionValue {
            font-weight: bold;
            color: #4a90e2;
        }

        #background-change {
            text-align: center;
        }

        #backgroundColor {
            width: 50px;
            height: 50px;
            padding: 5px;
            border: 2px solid #4a90e2;
            border-radius: 5px;
            cursor: pointer;
        }

        #imageCanvas {
            max-width: 100%;
            height: auto;
            border: 2px dashed #4a90e2;
            border-radius: 10px;
            margin-top: 20px;
        }

        #downloadLink {
            display: inline-block;
            background-color: #4a90e2;
            color: #fff;
            padding: 10px 20px;
            border-radius: 5px;
            text-decoration: none;
            margin-top: 20px;
            transition: background-color 0.3s ease;
        }

        #downloadLink:hover {
            background-color: #357abd;
        }

        footer {
            background-color: #4a90e2;
            color: #fff;
            text-align: center;
            padding: 10px 0;
            position: fixed;
            width: 100%;
            bottom: 0;
            box-shadow: 0 -4px 6px rgba(0, 0, 0, 0.1);
        }

        /* Loading Spinner */
        .loader {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #4a90e2;
            border-radius: 50%;
            width: 30px;
            height: 30px;
            animation: spin 1s linear infinite;
            margin: 20px auto;
            display: none;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <header>
        <h1>Image Optimization Tool</h1>
    </header>

    <main>
        <!-- Ad Space Top -->
        <section id="ad-space-top">
            <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-YOUR_AD_UNIT_ID"
                    crossorigin="anonymous"></script>
            <ins class="adsbygoogle"
                 style="display:block"
                 data-ad-client="ca-pub-YOUR_AD_UNIT_ID"
                 data-ad-slot="1234567890"
                 data-ad-format="auto"
                 data-full-width-responsive="true"></ins>
            <script>
                 (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </section>

        <!-- Image Upload Section -->
        <section id="image-upload">
            <h2>Upload Your Image</h2>
            <label for="imageInput" class="upload-label">Choose Image</label>
            <input type="file" id="imageInput" accept="image/*">
        </section>

        <!-- Compression Controls -->
        <section id="compression-controls">
            <h2>Compression Level</h2>
            <input type="range" id="compressionLevel" min="0" max="100" value="50">
            <span id="compressionValue">50%</span>
        </section>

        <!-- Background Change Section -->
        <section id="background-change">
            <h2>Change Background</h2>
            <input type="color" id="backgroundColor" value="#ffffff">
        </section>

        <!-- Output Section -->
        <section id="output">
            <h2>Optimized Image</h2>
            <div class="loader" id="loader"></div>
            <canvas id="imageCanvas"></canvas>
            <a id="downloadLink" download="optimized-image.png">Download Optimized Image</a>
        </section>

        <!-- Ad Space Bottom -->
        <section id="ad-space-bottom">
            <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-YOUR_AD_UNIT_ID"
                    crossorigin="anonymous"></script>
            <ins class="adsbygoogle"
                 style="display:block"
                 data-ad-client="ca-pub-YOUR_AD_UNIT_ID"
                 data-ad-slot="0987654321"
                 data-ad-format="auto"
                 data-full-width-responsive="true"></ins>
            <script>
                 (adsbygoogle = window.adsbygoogle || []).push({});
            </script>
        </section>
    </main>

    <footer>
        <p>&copy; 2023 Image Optimization Tool. All rights reserved.</p>
    </footer>

    <script>
        // JavaScript for Image Upload, Compression, and Background Change
        document.getElementById('imageInput').addEventListener('change', function(event) {
            const file = event.target.files[0];
            if (file) {
                const loader = document.getElementById('loader');
                loader.style.display = 'block';

                const reader = new FileReader();
                reader.onload = function(e) {
                    const img = new Image();
                    img.src = e.target.result;
                    img.onload = function() {
                        const canvas = document.getElementById('imageCanvas');
                        const ctx = canvas.getContext('2d');
                        canvas.width = img.width;
                        canvas.height = img.height;
                        ctx.drawImage(img, 0, 0);

                        // Apply background color
                        const backgroundColor = document.getElementById('backgroundColor').value;
                        ctx.globalCompositeOperation = 'destination-over';
                        ctx.fillStyle = backgroundColor;
                        ctx.fillRect(0, 0, canvas.width, canvas.height);

                        // Apply compression
                        const compressionLevel = document.getElementById('compressionLevel').value;
                        const dataUrl = canvas.toDataURL('image/jpeg', compressionLevel / 100);
                        document.getElementById('downloadLink').href = dataUrl;

                        loader.style.display = 'none';
                    };
                };
                reader.readAsDataURL(file);
            }
        });

        // Update Compression Level Display
        document.getElementById('compressionLevel').addEventListener('input', function() {
            document.getElementById('compressionValue').textContent = this.value + '%';
        });

        // Change Background Color
        document.getElementById('backgroundColor').addEventListener('input', function() {
            const canvas = document.getElementById('imageCanvas');
            const ctx = canvas.getContext('2d');
            const img = new Image();
            img.src = canvas.toDataURL();
            img.onload = function() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                ctx.drawImage(img, 0, 0);
                const backgroundColor = document.getElementById('backgroundColor').value;
                ctx.globalCompositeOperation = 'destination-over';
                ctx.fillStyle = backgroundColor;
                ctx.fillRect(0, 0, canvas.width, canvas.height);
            };
        });
    </script>
</body>
</html>
