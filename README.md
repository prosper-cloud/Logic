i guess            color: #e0e0e0;
            font-family: 'Space Grotesk', sans-serif;
            overflow-x: hidden;
        }

        /* 3D Canvas Background */
        #canvas-container {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            z-index: -1;
            opacity: 0.6;
        }

        /* --- NEW STUDENT HEADER SECTION --- */
        .student-header {
            width: 100%;
            padding: 40px 10%;
            background: linear-gradient(to bottom, rgba(0, 242, 255, 0.05), transparent);
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .student-info h2 {
            margin: 0;
            font-size: 1.2rem;
            letter-spacing: 3px;
            color: white;
            text-transform: uppercase;
            background: linear-gradient(90deg, #fff, var(--accent), #fff);
            background-size: 200% auto;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: shimmer 4s linear infinite;
        }

        .course-tag {
            font-size: 0.8rem;
            color: var(--logic-gold);
            font-weight: bold;
            border: 1px solid var(--logic-gold);
            padding: 5px 15px;
            border-radius: 4px;
        }

        @keyframes shimmer {
            to { background-position: 200% center; }
        }

        /* Layout */
        .section {
            min-height: 100vh;
            padding: 80px 10%;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .hero { text-align: center; align-items: center; }
        
        h1 {
            font-size: clamp(3rem, 12vw, 7rem);
            margin: 0;
            background: linear-gradient(to bottom, #fff 30%, var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: 700;
        }

        .sub-deck {
            font-family: 'Playfair Display', serif;
            font-style: italic;
            font-size: 1.5rem;
            color: var(--logic-gold);
            margin-top: -10px;
        }

        .glass-panel {
            background: var(--glass);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255,255,255,0.1);
            padding: 50px;
            border-radius: 30px;
            max-width: 800px;
            margin: 20px 0;
        }

        .highlight { color: var(--accent); font-weight: bold; }

        .logic-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-top: 40px;
        }

        .logic-box {
            border-left: 2px solid var(--accent);
            padding: 20px;
            background: rgba(0, 242, 255, 0.05);
            transition: 0.3s;
        }

        .tag {
            font-size: 0.7rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: var(--accent);
            margin-bottom: 10px;
            display: block;
        }
    </style>
</head>
<body>

    <div id="canvas-container"></div>

    <header class="student-header">
        <div class="student-info">
            <h2 class="reveal">Browne Ubawuchi</h2>
            <div style="font-size: 0.9rem; opacity: 0.7; margin-top: 5px;">Imo State University (IMSU)</div>
        </div>
        <div class="course-tag reveal">100LVL LAW COURSE</div>
    </header>

    <section class="section hero">
        <span class="tag">The Blueprint of Justice</span>
        <h1>LOGIC</h1>
        <p class="sub-deck">"Law is reason, free from passion." — Aristotle</p>
    </section>

    <section class="section">
        <div class="glass-panel reveal">
            <span class="tag">01. The Definition</span>
            <h2>Introduction to Logic</h2>
            <p>In the legal sphere, <span class="highlight">Logic</span> is the study of principles of correct reasoning. For a 100lvl student, it is the most critical tool for analyzing statutes and judicial precedents.</p>
        </div>
    </section>

    <section class="section">
        <span class="tag">02. Structure of Argument</span>
        <h2>Logical Pillars</h2>
        
        <div class="logic-grid">
            <div class="logic-box reveal">
                <h3>Deduction</h3>
                <p>Applying the <strong>General Law</strong> to a <strong>Specific Fact</strong>.</p>
            </div>
            <div class="logic-box reveal">
                <h3>Induction</h3>
                <p>Forming a <strong>General Law</strong> from <strong>Specific Observations</strong>.</p>
            </div>
        </div>
    </section>

    <script>
        // --- THREE.JS LOGIC NODES ---
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.getElementById('canvas-container').appendChild(renderer.domElement);

        const group = new THREE.Group();
        const geometry = new THREE.IcosahedronGeometry(0.1, 0);
        const material = new THREE.MeshBasicMaterial({ color: 0x00f2ff, wireframe: true });

        for(let i=0; i<150; i++) {
            const mesh = new THREE.Mesh(geometry, material);
            mesh.position.set((Math.random()-0.5)*20, (Math.random()-0.5)*20, (Math.random()-0.5)*20);
            group.add(mesh);
        }
        scene.add(group);
        camera.position.z = 5;

        function animate() {
            requestAnimationFrame(animate);
            group.rotation.y += 0.0015;
            renderer.render(scene, camera);
        }
        animate();

        // --- SCROLLREVEAL ---
        ScrollReveal().reveal('.reveal', {
            delay: 200,
            distance: '30px',
            origin: 'top',
            opacity: 0,
            duration: 1000,
            interval: 200
        });
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Logic & Reasoning | 3D Experience</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://unpkg.com/scrollreveal"></script>
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #050505;
            --accent: #00f2ff;
            --glass: rgba(255, 255, 255, 0.05);
        }

        body {
            margin: 0;
            background-color: var(--bg);
            color: white;
            font-family: 'Space Grotesk', sans-serif;
            overflow-x: hidden;
        }

        /* 3D Canvas Background */
        #canvas-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            background: radial-gradient(circle at center, transparent 0%, var(--bg) 70%);
        }

        .hero h1 {
            font-size: clamp(3rem, 10vw, 6rem);
            text-transform: uppercase;
            letter-spacing: 10px;
            margin: 0;
            background: linear-gradient(to right, #fff, var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 15px rgba(0, 242, 255, 0.3));
        }

        /* Content Sections */
        .section {
            min-height: 80vh;
            padding: 100px 10%;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .glass-card {
            background: var(--glass);
            backdrop-filter: blur(15px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 40px;
            border-radius: 24px;
            max-width: 500px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.5);
        }

        .glass-card h2 {
            color: var(--accent);
            font-size: 2rem;
            margin-bottom: 20px;
        }

        .tag {
            display: inline-block;
            padding: 5px 15px;
            background: var(--accent);
            color: black;
            border-radius: 50px;
            font-size: 0.8rem;
            font-weight: bold;
            margin-bottom: 15px;
        }

        /* Floating Animation */
        .float {
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
            100% { transform: translateY(0px); }
        }

        .scroll-indicator {
            position: absolute;
            bottom: 30px;
            width: 2px;
            height: 50px;
            background: linear-gradient(to bottom, var(--accent), transparent);
        }
    </style>
</head>
<body>

    <div id="canvas-container"></div>

    <section class="hero">
        <div class="tag">MODULE 01</div>
        <h1 class="reveal">LOGIC</h1>
        <p class="reveal">The Architecture of Thought</p>
        <div class="scroll-indicator"></div>
    </section>

    <section class="section">
        <div class="glass-card reveal">
            <div class="tag">01. DEFINITION</div>
            <h2>What is Logic?</h2>
            <p>Logic is the systematic study of the forms of inference. It is the "toolbox" we use to separate a valid argument from a fallacy. In the world of law, logic is the bridge between evidence and a verdict.</p>
        </div>
    </section>

    <section class="section" style="justify-content: flex-end;">
        <div class="glass-card reveal">
            <div class="tag">02. REASONING</div>
            <h2>Deductive vs. Inductive</h2>
            <p><strong>Deductive:</strong> If the premises are true, the conclusion <em>must</em> be true.<br>
            <strong>Inductive:</strong> If the premises are true, the conclusion is <em>likely</em> to be true.</p>
        </div>
    </section>

    <script>
        // --- 3D BACKGROUND (Three.js) ---
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.getElementById('canvas-container').appendChild(renderer.domElement);

        // Create a floating particle field
        const geometry = new THREE.IcosahedronGeometry(1, 1);
        const material = new THREE.MeshBasicMaterial({ color: 0x00f2ff, wireframe: true });
        const points = [];

        for (let i = 0; i < 50; i++) {
            const mesh = new THREE.Mesh(geometry, material);
            mesh.position.set(
                (Math.random() - 0.5) * 10,
                (Math.random() - 0.5) * 10,
                (Math.random() - 0.5) * 10
            );
            mesh.rotation.set(Math.random() * 2, Math.random() * 2, Math.random() * 2);
            scene.add(mesh);
            points.push(mesh);
        }

        camera.position.z = 5;

        function animate() {
            requestAnimationFrame(animate);
            points.forEach(p => {
                p.rotation.x += 0.002;
                p.rotation.y += 0.002;
            });
            renderer.render(scene, camera);
        }
        animate();

        // Handle Resize
        window.addEventListener('resize', () => {
            camera.aspect = window.innerWidth / window.innerHeight;
            camera.updateProjectionMatrix();
            renderer.setSize(window.innerWidth, window.innerHeight);
        });

        // --- ANIMATIONS (ScrollReveal) ---
        ScrollReveal().reveal('.reveal', {
            delay: 300,
            distance: '50px',
            origin: 'bottom',
            duration: 1000,
            interval: 200,
            reset: true
        });
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Logic & Reasoning | The Foundation of Law</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://unpkg.com/scrollreveal"></script>
    <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;500;700&family=Playfair+Display:ital@1&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg: #02040a;
            --accent: #00f2ff;
            --logic-gold: #fdbb2d;
            --glass: rgba(255, 255, 255, 0.03);
        }

        body {
            margin: 0;
            background-color: var(--bg);
            color: #e0e0e0;
            font-family: 'Space Grotesk', sans-serif;
            overflow-x: hidden;
        }

        /* 3D Canvas Background */
        #canvas-container {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            z-index: -1;
            opacity: 0.6;
        }

        /* Typography & Layout */
        .section {
            min-height: 100vh;
            padding: 80px 10%;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        .hero { text-align: center; align-items: center; }
        
        h1 {
            font-size: clamp(3rem, 12vw, 7rem);
            margin: 0;
            background: linear-gradient(to bottom, #fff 30%, var(--accent));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: 700;
        }

        .sub-deck {
            font-family: 'Playfair Display', serif;
            font-style: italic;
            font-size: 1.5rem;
            color: var(--logic-gold);
            margin-top: -10px;
        }

        .glass-panel {
            background: var(--glass);
            backdrop-filter: blur(20px);
            border: 1px solid rgba(255,255,255,0.1);
            padding: 50px;
            border-radius: 30px;
            max-width: 800px;
            margin: 20px 0;
            line-height: 1.8;
        }

        .highlight { color: var(--accent); font-weight: bold; }

        /* Logic Grid */
        .logic-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin-top: 40px;
        }

        .logic-box {
            border-left: 2px solid var(--accent);
            padding: 20px;
            background: rgba(0, 242, 255, 0.05);
            transition: 0.3s;
        }

        .logic-box:hover { background: rgba(0, 242, 255, 0.1); transform: scale(1.02); }

        .tag {
            font-size: 0.7rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: var(--accent);
            margin-bottom: 10px;
            display: block;
        }

        footer {
            padding: 50px;
            text-align: center;
            font-size: 0.8rem;
            opacity: 0.5;
        }
    </style>
</head>
<body>

    <div id="canvas-container"></div>

    <section class="section hero">
        <span class="tag">The Blueprint of Justice</span>
        <h1>LOGIC</h1>
        <p class="sub-deck">"Law is reason, free from passion." — Aristotle</p>
    </section>

    <section class="section">
        <div class="glass-panel reveal">
            <span class="tag">01. The Definition</span>
            <h2>What is Logic?</h2>
            <p>Logic is not just "common sense." It is the <span class="highlight">formal science of correct reasoning</span>. In the legal world, logic ensures that a conclusion (The Verdict) is the unavoidable result of the facts (The Evidence).</p>
            <p>Without logic, law is merely an exercise of power. With logic, law becomes a pursuit of <strong>Truth</strong>.</p>
        </div>
    </section>

    <section class="section">
        <span class="tag">02. The Two Paths</span>
        <h2>Reasoning Methods</h2>
        <div class="logic-grid">
            <div class="logic-box reveal">
                <h3>Deductive Reasoning</h3>
                <p>Moving from a general rule to a specific case. If the rule is true and the facts fit, the result is <strong>Certain</strong>.</p>
                <p class="highlight">Example: All citizens have rights. You are a citizen. Therefore, you have rights.</p>
            </div>
            <div class="logic-box reveal">
                <h3>Inductive Reasoning</h3>
                <p>Moving from specific observations to a general conclusion. This deals with <strong>Probability</strong>, not certainty.</p>
                <p class="highlight">Example: Every contract signed with this firm has been valid. Therefore, the next one likely will be too.</p>
            </div>
        </div>
    </section>

    <section class="section">
        <div class="glass-panel reveal" style="border-right: 4px solid var(--logic-gold); border-left: none;">
            <span class="tag">03. The Legal Engine</span>
            <h2>The Syllogism</h2>
            <p>This is the 3-step heart of a legal argument:</p>
            <ol>
                <li><strong>Major Premise:</strong> The Law (e.g., "Theft is a crime").</li>
                <li><strong>Minor Premise:</strong> The Fact (e.g., "John took the car").</li>
                <li><strong>Conclusion:</strong> The Verdict (e.g., "John committed a crime").</li>
            </ol>
            <p>If the first two are solid, the third is unshakeable.</p>
        </div>
    </section>

    <footer>
        <p>LAW-BASICS &copy; 2024 | Exploring the Architecture of Thought</p>
    </footer>

    <script>
        // --- THREE.JS BACKGROUND ---
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.getElementById('canvas-container').appendChild(renderer.domElement);

        // Create a "Node" system representing interconnected logic
        const group = new THREE.Group();
        const geometry = new THREE.SphereGeometry(0.05, 16, 16);
        const material = new THREE.MeshBasicMaterial({ color: 0x00f2ff });

        for(let i=0; i<100; i++) {
            const mesh = new THREE.Mesh(geometry, m
