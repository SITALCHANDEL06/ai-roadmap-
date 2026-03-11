<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI Evolution Roadmap</title>
    <style>
        :root {
            --bg-color: #0f172a;
            --card-bg: #1e293b;
            --accent: #3b82f6;
            --accent-glow: #60a5fa;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --timeline-line: #334155;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            overflow-x: hidden;
        }

        /* Header */
        header {
            text-align: center;
            padding: 4rem 1rem;
            background: radial-gradient(circle at top, #1e293b 0%, #0f172a 100%);
        }

        h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            background: linear-gradient(to right, #3b82f6, #8b5cf6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        p.subtitle {
            color: var(--text-muted);
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.6;
        }

        /* Controls */
        .controls {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 3rem;
            flex-wrap: wrap;
        }

        button {
            padding: 0.8rem 1.5rem;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .btn-primary {
            background-color: var(--accent);
            color: white;
            box-shadow: 0 0 15px rgba(59, 130, 246, 0.5);
        }

        .btn-primary:hover {
            background-color: var(--accent-glow);
            transform: translateY(-2px);
        }

        .btn-outline {
            background: transparent;
            border: 1px solid var(--text-muted);
            color: var(--text-muted);
        }

        .btn-outline:hover {
            border-color: var(--accent);
            color: var(--accent);
        }

        /* Roadmap Container */
        .roadmap-container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 0 1rem 4rem 1rem;
            position: relative;
        }

        /* The vertical line */
        .roadmap-container::before {
            content: '';
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 4px;
            height: 100%;
            background: var(--timeline-line);
            border-radius: 2px;
        }

        /* Timeline Item */
        .timeline-item {
            display: flex;
            justify-content: center;
            align-items: center;
            margin-bottom: 3rem;
            position: relative;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeIn 0.6s forwards;
        }

        @keyframes fadeIn {
            to { opacity: 1; transform: translateY(0); }
        }

        .timeline-content {
            width: 45%;
            background: var(--card-bg);
            padding: 1.5rem;
            border-radius: 12px;
            border: 1px solid var(--timeline-line);
            position: relative;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .timeline-content:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            border-color: var(--accent);
        }

        /* Alternating sides */
        .timeline-item:nth-child(odd) {
            justify-content: flex-start;
        }
        
        .timeline-item:nth-child(even) {
            justify-content: flex-end;
        }

        .timeline-item:nth-child(odd) .timeline-content {
            margin-right: auto;
            margin-left: 5%;
        }

        .timeline-item:nth-child(even) .timeline-content {
            margin-left: auto;
            margin-right: 5%;
        }

        /* The dot on the line */
        .timeline-dot {
            width: 20px;
            height: 20px;
            background: var(--accent);
            border-radius: 50%;
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            border: 4px solid var(--bg-color);
            z-index: 2;
            box-shadow: 0 0 10px var(--accent);
        }

        /* Content Styling */
        .year-badge {
            background: rgba(59, 130, 246, 0.1);
            color: var(--accent-glow);
            padding: 0.2rem 0.6rem;
            border-radius: 4px;
            font-size: 0.85rem;
            font-weight: bold;
            display: inline-block;
            margin-bottom: 0.5rem;
        }

        .category-tag {
            font-size: 0.75rem;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 0.5rem;
            display: block;
        }

        h3 {
            margin-bottom: 0.5rem;
            font-size: 1.25rem;
        }

        p {
            color: var(--text-muted);
            font-size: 0.95rem;
            line-height: 1.5;
        }

        /* AI Prediction Section */
        .ai-predictor {
            background: linear-gradient(135deg, #1e293b, #0f172a);
            border: 1px solid var(--accent);
            border-radius: 16px;
            padding: 2rem;
            text-align: center;
            margin-top: 4rem;
            position: relative;
            overflow: hidden;
        }

        .ai-predictor::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; height: 2px;
            background: linear-gradient(90deg, transparent, var(--accent), transparent);
            animation: scan 3s infinite linear;
        }

        @keyframes scan {
            0% { top: 0; opacity: 0; }
            50% { opacity: 1; }
            100% { top: 100%; opacity: 0; }
        }

        .prediction-result {
            margin-top: 1.5rem;
            font-size: 1.2rem;
            min-height: 3rem;
            color: var(--accent-glow);
            font-weight: bold;
        }

        /* Mobile Responsive */
        @media (max-width: 768px) {
            .roadmap-container::before {
                left: 20px;
            }
            
            .timeline-item {
                justify-content: flex-start !important;
                padding-left: 50px;
            }

            .timeline-dot {
                left: 20px;
            }

            .timeline-content {
                width: 100%;
                margin: 0 !important;
            }
        }
    </style>
</head>
<body>

    <header>
        <h1>AI Evolution Roadmap</h1>
        <p class="subtitle">A visual journey through the history, present, and future of Artificial Intelligence.</p>
    </header>

    <div class="controls">
        <button class="btn-primary" onclick="renderRoadmap()">Refresh Roadmap</button>
        <button class="btn-outline" onclick="toggleTheme()">Toggle Theme</button>
    </div>

    <div class="roadmap-container" id="roadmap">
        <!-- Timeline items will be injected here via JS -->
    </div>

    <div class="ai-predictor">
        <h2>🔮 AI Future Prediction Engine</h2>
        <p>Our algorithm analyzes current trends to predict the next major breakthrough.</p>
        <button class="btn-primary" style="margin-top: 1rem;" onclick="predictFuture()">Analyze & Predict</button>
        <div class="prediction-result" id="prediction-text"></div>
    </div>

    <script>
        // Data Source
        const roadmapData = [
            { year: "1950", title: "The Turing Test", category: "Foundations", desc: "Alan Turing publishes 'Computing Machinery and Intelligence', asking 'Can machines think?'." },
            { year: "1956", title: "Dartmouth Conference", category: "Birth of AI", desc: "The term 'Artificial Intelligence' is coined. The field is officially born." },
            { year: "1997", title: "Deep Blue", category: "Chess & Logic", desc: "IBM's Deep Blue defeats world chess champion Garry Kasparov." },
            { year: "2011", title: "Siri & Watson", category: "Consumer AI", desc: "Apple releases Siri. IBM Watson wins Jeopardy!, proving NLP capabilities." },
            { year: "2012", title: "AlexNet", category: "Deep Learning", desc: "Deep convolutional neural networks win ImageNet, sparking the modern Deep Learning revolution." },
            { year: "2017", title: "Transformers", category: "Architecture", desc: "Google publishes 'Attention Is All You Need', introducing the Transformer architecture." },
            { year: "2022", title: "Generative AI Boom", category: "Generative AI", desc: "ChatGPT and DALL-E 2 launch, bringing generative AI to the mainstream public." },
            { year: "2024", title: "Multimodal Models", category: "Current Era", desc: "AI models can now seamlessly process text, audio, video, and images simultaneously." }
        ];

        const futurePredictions = [
            "AGI (Artificial General Intelligence) achieves human-level reasoning.",
            "AI-driven drug discovery cures a major disease within 5 years.",
            "Autonomous vehicles become the standard for public transport.",
            "Brain-Computer Interfaces (BCI) allow direct thought-to-text communication.",
            "AI agents autonomously manage 50% of global financial markets."
        ];

        // Render Function
        function renderRoadmap() {
            const container = document.getElementById('roadmap');
            container.innerHTML = ''; // Clear existing

            roadmapData.forEach((item, index) => {
                const itemDiv = document.createElement('div');
                itemDiv.className = 'timeline-item';
                // Add staggered animation delay
                itemDiv.style.animationDelay = `${index * 0.1}s`;

                itemDiv.innerHTML = `
                    <div class="timeline-dot"></div>
                    <div class="timeline-content">
                        <span class="category-tag">${item.category}</span>
                        <span class="year-badge">${item.year}</span>
                        <h3>${item.title}</h3>
                        <p>${item.desc}</p>
                    </div>
                `;
                container.appendChild(itemDiv);
            });
        }

        // AI Prediction Feature
        function predictFuture() {
            const resultDiv = document.getElementById('prediction-text');
            const btn = document.querySelector('.ai-predictor .btn-primary');
            
            // Simulate processing time
            btn.textContent = "Processing Data...";
            resultDiv.textContent = "Analyzing global trends...";
            resultDiv.style.color = "#94a3b8";

            setTimeout(() => {
                const randomPrediction = futurePredictions[Math.floor(Math.random() * futurePredictions.length)];
                resultDiv.textContent = `Prediction: ${randomPrediction}`;
                resultDiv.style.color = "#60a5fa";
                btn.textContent = "Analyze & Predict";
            }, 1500);
        }

        // Theme Toggle (Simple implementation)
        function toggleTheme() {
            const root = document.documentElement;
            const currentBg = getComputedStyle(root).getPropertyValue('--bg-color');
            
            if (currentBg === '#0f172a') {
                // Switch to Light Mode
                root.style.setProperty('--bg-color', '#f1f5f9');
                root.style.setProperty('--card-bg', '#ffffff');
                root.style.setProperty('--text-main', '#0f172a');
                root.style.setProperty('--text-muted', '#64748b');
                root.style.setProperty('--timeline-line', '#cbd5e1');
            } else {
                // Switch to Dark Mode
                root.style.setProperty('--bg-color', '#0f172a');
                root.style.setProperty('--card-bg', '#1e293b');
                root.style.setProperty('--text-main', '#f8fafc');
                root.style.setProperty('--text-muted', '#94a3b8');
                root.style.setProperty('--timeline-line', '#334155');
            }
        }

        // Initial Render
        renderRoadmap();

    </script>
</body>
</html>
