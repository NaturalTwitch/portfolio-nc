<script setup>
import { RouterLink } from 'vue-router'

const profileSrc = '/src/assets/Me.png'
</script>

<template>
    <section class="about" aria-labelledby="about-title">
        <div class="about-inner">
            <div class="about-left" aria-hidden="false">
                <div class="avatar" aria-hidden="true">
                    <img :src="profileSrc" alt="Norm profile photo" />
                </div>

                <div class="quick-ctas">
                    <a class="cta github" :href="'https://github.com/NaturalTwitch'" target="_blank" rel="noopener">
                        GitHub
                    </a>
                    <RouterLink to="/contact" class="cta ghost">Contact</RouterLink>
                    <a class="cta ghost" href="/resume.pdf" target="_blank" rel="noopener">Resume</a>
                </div>
            </div>

            <div class="about-right">
                <h2 id="about-title" class="about-title">About Me</h2>

                <p class="lead">
                    Hey — I’m <strong>Norm (NaturalTwitch)</strong>, a full-stack developer who builds automation, bots,
                    and hosting tools.
                    I created <em>Mursy</em> (Discord bots, dashboards and tooling) and love shipping tools that make
                    life easier.
                </p>

                <ul class="highlights" aria-hidden="true">
                    <li><strong>Primary:</strong> JavaScript · Node.js · Vue · PostgreSQL</li>
                    <li><strong>Infra:</strong> Linux · Windows · Nginx</li>
                    <li><strong>Extras:</strong> Automation · IoT · Game tooling</li>
                </ul>

                <div class="now">
                    <p><strong>Now:</strong> Building Mursy Hosting and an invoice dashboard — focusing on reliability,
                        automation, and developer UX.</p>
                </div>

                <div class="stats" role="list">
                    <div class="stat" role="listitem">
                        <div class="num">11</div>
                        <div class="label">Public repos</div>
                    </div>
                    <div class="stat" role="listitem">
                        <div class="num">10k+</div>
                        <div class="label">Users across projects</div>
                    </div>
                    <div class="stat" role="listitem">
                        <div class="num">5+</div>
                        <div class="label">Years coding</div>
                    </div>
                </div>

                <p class="closing">
                    I love sci-fi, Linux boxes, and solving boring problems with clever automation. Want to collab or
                    see source?
                    Hit my GitHub or drop a message via Contact.
                </p>
            </div>
        </div>
    </section>
</template>

<style scoped>
:root {
    --neon-primary: #00bcd4;
    --neon-secondary: #4b8bff;
    --bg-card: rgba(12, 12, 14, 0.88);
    --muted: #bfc7cf;
    --text: #e6eef6;
    --glow-weak: 0 0 8px rgba(0, 188, 212, 0.08);
    --glow-strong: 0 0 20px rgba(75, 139, 255, 0.12);
}


.about {
    padding: 36px 20px;
    font-family: 'Orbitron', 'Poppins', sans-serif;
    color: var(--text);
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}


.about-inner {
    max-width: 1100px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 240px 1fr;
    gap: 28px;
    align-items: start;
}


.about-left {
    display: flex;
    flex-direction: column;
    gap: 16px;
    align-items: center;
}


.avatar {
    width: 220px;
    height: 220px;
    border-radius: 14px;
    background: linear-gradient(180deg, rgba(255, 255, 255, 0.02), rgba(255, 255, 255, 0.01));
    border: 1px solid rgba(0, 188, 212, 0.12);
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: var(--glow-weak);
    overflow: hidden;
    transition: transform 220ms ease, box-shadow 220ms ease;
}


.avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    display: block;
    border-radius: 12px;
}


.avatar:hover {
    transform: translateY(-6px);
    box-shadow: var(--glow-strong);
}


.quick-ctas {
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
    justify-content: center;
    width: 100%;
}


.cta {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 8px 12px;
    border-radius: 10px;
    text-decoration: none;
    font-weight: 700;
    font-size: 0.95rem;
    border: 1px solid rgba(0, 188, 212, 0.10);
    transition: transform 160ms ease, box-shadow 160ms ease;
}


.cta.github {
    background: linear-gradient(90deg, var(--neon-primary), var(--neon-secondary));
    color: var(--text);
    box-shadow: 0 10px 28px rgba(0, 188, 212, 0.06);
}


.cta.ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid rgba(0, 188, 212, 0.10);
}


.cta:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 36px rgba(0, 188, 212, 0.06);
}


.about-right {
    position: relative;
}


.about-title {
    font-size: 1.8rem;
    margin: 0 0 12px 0;
    background: linear-gradient(90deg, var(--neon-primary), var(--neon-secondary));
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    display: inline-block;
    font-weight: 700;
}


.lead {
    margin: 0 0 12px 0;
    font-size: 1.05rem;
    opacity: 0.95;
    line-height: 1.45;
}


.highlights {
    list-style: none;
    padding: 0;
    margin: 6px 0 18px 0;
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
}

.highlights li {
    background: rgba(0, 188, 212, 0.04);
    border: 1px solid rgba(0, 188, 212, 0.06);
    padding: 8px 12px;
    border-radius: 999px;
    font-size: 0.9rem;
    color: var(--muted);
}


.now {
    margin-bottom: 14px;
    font-size: 0.95rem;
    color: #dbe8f2;
}


.stats {
    display: flex;
    gap: 18px;
    margin: 12px 0 18px 0;
    flex-wrap: wrap;
}

.stat {
    background: var(--bg-card);
    padding: 10px 12px;
    border-radius: 8px;
    border: 1px solid rgba(0, 188, 212, 0.06);
    min-width: 110px;
}

.stat .num {
    font-weight: 800;
    font-size: 1.1rem;
    color: var(--neon-primary);
}

.stat .label {
    font-size: 0.8rem;
    color: var(--muted);
}

.closing {
    margin-top: 6px;
    color: #cde6f6;
    opacity: 0.95;
}


.about-inner>* {
    transform: translateY(0);
    opacity: 1;
}


@media (max-width: 820px) {
    .about-inner {
        grid-template-columns: 1fr;
        gap: 18px;
    }


    .about-left {
        flex-direction: row;
        align-items: center;
        justify-content: space-between;
        gap: 12px;
    }


    .avatar {
        width: 96px;
        height: 96px;
        border-radius: 12px;
        box-shadow: 0 0 10px rgba(0, 188, 212, 0.05);
        overflow: hidden;
    }

    .avatar img {
        border-radius: 10px;
    }

    .quick-ctas {
        display: flex;
        gap: 8px;
        flex-direction: column;
        align-items: flex-end;
        min-width: 120px;
    }

    .cta {
        padding: 10px 12px;
        font-size: 0.92rem;
        border-radius: 8px;
    }

    .about-title {
        font-size: 1.4rem;
    }

    .lead {
        font-size: 0.98rem;
    }

    .highlights li {
        font-size: 0.85rem;
        padding: 6px 10px;
    }

    .stats {
        gap: 10px;
        justify-content: flex-start;
    }
}


@media (max-width: 420px) {
    .avatar {
        width: 80px;
        height: 80px;
    }

    .about-title {
        font-size: 1.2rem;
    }

    .lead {
        font-size: 0.92rem;
    }
}

@media (prefers-reduced-motion: reduce) {

    .avatar,
    .cta,
    .about-inner>* {
        transition: none !important;
        animation: none !important;
    }
}
</style>
