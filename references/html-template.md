# HTML Template — Quick Start Boilerplate

Copy this as a starting point for any Slide Maestro presentation.

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Presentation Title</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link href="https://fonts.googleapis.com/css2?family=YOUR_DISPLAY_FONT:wght@700&family=YOUR_BODY_FONT:wght@400;500&display=swap" rel="stylesheet">
    <style>
        /* ====== VIEWPORT BASE (MANDATORY) ====== */
        html, body { height: 100%; overflow-x: hidden; margin: 0; padding: 0; }
        html { scroll-snap-type: y mandatory; scroll-behavior: smooth; }

        .slide {
            width: 100vw; height: 100vh; height: 100dvh;
            overflow: hidden; scroll-snap-align: start;
            display: flex; flex-direction: column; position: relative;
        }

        .slide-content {
            flex: 1; display: flex; flex-direction: column;
            justify-content: center; max-height: 100%;
            overflow: hidden; padding: var(--slide-padding);
        }

        :root {
            --title-size: clamp(1.5rem, 5vw, 4rem);
            --h2-size: clamp(1.25rem, 3.5vw, 2.5rem);
            --h3-size: clamp(1rem, 2.5vw, 1.75rem);
            --body-size: clamp(0.75rem, 1.5vw, 1.125rem);
            --small-size: clamp(0.65rem, 1vw, 0.875rem);
            --slide-padding: clamp(1rem, 4vw, 4rem);
            --content-gap: clamp(0.5rem, 2vw, 2rem);

            /* ====== THEME (CUSTOMIZE THESE) ====== */
            --bg: #0f172a;
            --surface: #1e293b;
            --ink: #f8fafc;
            --muted: #94a3b8;
            --accent: #3b82f6;
            --font-display: 'YOUR_DISPLAY FONT', sans-serif;
            --font-body: 'YOUR BODY FONT', sans-serif;
        }

        body {
            font-family: var(--font-body);
            color: var(--ink);
            background: var(--bg);
        }

        h1, h2, h3 { font-family: var(--font-display); margin: 0; }
        h1 { font-size: var(--title-size); }
        h2 { font-size: var(--h2-size); }
        h3 { font-size: var(--h3-size); }
        p, li { font-size: var(--body-size); line-height: 1.6; }

        /* Reveal animations */
        [data-reveal] { opacity: 0; transform: translateY(20px); transition: all 0.6s ease-out; }
        [data-reveal].revealed { opacity: 1; transform: translateY(0); }

        /* Progress bar */
        .progress-bar { position: fixed; top: 0; left: 0; height: 3px; background: var(--accent); transition: width 0.3s; z-index: 9999; }

        /* Grid */
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(min(100%, 250px), 1fr)); gap: clamp(0.5rem, 1.5vw, 1rem); }
        .card { background: var(--surface); border-radius: 12px; padding: clamp(1rem, 2vw, 2rem); }

        @media (max-height: 700px) { :root { --slide-padding: clamp(0.75rem, 3vw, 2rem); } }
        @media (max-height: 600px) { :root { --slide-padding: clamp(0.5rem, 2.5vw, 1.5rem); --body-size: clamp(0.7rem, 1.2vw, 0.95rem); } }
        @media (prefers-reduced-motion: reduce) { *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.2s !important; } html { scroll-behavior: auto; } }
    </style>
</head>
<body>

    <!-- SLIDE 1: Title -->
    <section class="slide">
        <div class="slide-content" style="text-align: center;">
            <h1 data-reveal>Your Presentation Title</h1>
            <p data-reveal style="color: var(--muted); margin-top: var(--content-gap);">Subtitle or context line</p>
        </div>
    </section>

    <!-- SLIDE 2: Content -->
    <section class="slide">
        <div class="slide-content">
            <h2 data-reveal>Section Heading</h2>
            <ul style="list-style: none; padding: 0; margin-top: var(--content-gap); display: flex; flex-direction: column; gap: var(--element-gap);">
                <li data-reveal>First point with a verb-led statement</li>
                <li data-reveal>Second point building on the argument</li>
                <li data-reveal>Third point with supporting evidence</li>
                <li data-reveal>Fourth point leading to conclusion</li>
            </ul>
        </div>
    </section>

    <!-- SLIDE 3: Grid -->
    <section class="slide">
        <div class="slide-content">
            <h2 data-reveal style="text-align: center; margin-bottom: var(--content-gap);">Feature Grid</h2>
            <div class="grid">
                <div class="card" data-reveal><h3>Feature 1</h3><p>Description here</p></div>
                <div class="card" data-reveal><h3>Feature 2</h3><p>Description here</p></div>
                <div class="card" data-reveal><h3>Feature 3</h3><p>Description here</p></div>
            </div>
        </div>
    </section>

    <!-- Add more slides as needed -->

    <script>
        // Reveal observer
        const observer = new IntersectionObserver((entries) => {
            entries.forEach((entry, i) => {
                if (entry.isIntersecting) {
                    entry.target.style.transitionDelay = `${i * 80}ms`;
                    entry.target.classList.add('revealed');
                }
            });
        }, { threshold: 0.3 });
        document.querySelectorAll('[data-reveal]').forEach(el => observer.observe(el));

        // Navigation
        class SlideMaestro {
            constructor() { this.slides = document.querySelectorAll('.slide'); this.current = 0; this.init(); }
            init() {
                document.addEventListener('keydown', e => {
                    if (e.key === 'ArrowDown' || e.key === ' ' || e.key === 'PageDown') this.next();
                    if (e.key === 'ArrowUp' || e.key === 'PageUp') this.prev();
                    if (e.key === 'Home') this.goTo(0);
                    if (e.key === 'End') this.goTo(this.slides.length - 1);
                });
                let ty = 0;
                document.addEventListener('touchstart', e => ty = e.touches[0].clientY);
                document.addEventListener('touchend', e => { const d = ty - e.changedTouches[0].clientY; if (Math.abs(d) > 50) d > 0 ? this.next() : this.prev(); });
                const b = document.createElement('div'); b.className = 'progress-bar'; document.body.appendChild(b); this.progressBar = b; this.updateProgress();
            }
            next() { this.goTo(Math.min(this.current + 1, this.slides.length - 1)); }
            prev() { this.goTo(Math.max(this.current - 1, 0)); }
            goTo(i) { this.slides[i].scrollIntoView({ behavior: 'smooth' }); this.current = i; this.updateProgress(); }
            updateProgress() { this.progressBar.style.width = ((this.current + 1) / this.slides.length * 100) + '%'; }
        }
        new SlideMaestro();
    </script>
</body>
</html>
```

Replace: YOUR_DISPLAY_FONT, YOUR_BODY_FONT, theme colors (--bg, --surface, --ink, --muted, --accent).
