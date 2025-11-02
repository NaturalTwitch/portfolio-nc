<script setup>
import { ref } from 'vue'
import { Mail, Send, CheckCircle, AlertCircle } from 'lucide-vue-next'


const FORM_ENDPOINT = 'https://formsubmit.co/dev@mursybot.com'

const name = ref('')
const email = ref('')
const message = ref('')
const loading = ref(false)
const success = ref(false)
const error = ref(null)

const honeypot = ref('')

function resetForm() {
    name.value = ''
    email.value = ''
    message.value = ''
    honeypot.value = ''
}

function validate() {
    if (!name.value.trim()) return 'Please enter your name.'
    if (!email.value.trim()) return 'Please enter your email.'
    // simple email regex
    if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email.value)) return 'Please enter a valid email.'
    if (!message.value.trim()) return 'Please enter a message.'
    return null
}

async function submitForm(e) {
    e.preventDefault()
    error.value = null
    success.value = false

    const v = validate()
    if (v) {
        error.value = v
        return
    }


    if (honeypot.value) {
        error.value = 'Spam detected.'
        return
    }

    if (!FORM_ENDPOINT) {

        const mailto = `mailto:${encodeURIComponent('dev@mursybot.com')}?subject=${encodeURIComponent('Contact from portfolio — ' + name.value)}&body=${encodeURIComponent(message.value + '\n\n— ' + name.value + ' <' + email.value + '>')}`
        window.location.href = mailto
        return
    }

    loading.value = true
    try {
        const payload = new FormData()
        payload.append('name', name.value)
        payload.append('email', email.value)
        payload.append('message', message.value)
        payload.append('_subject', `Portfolio Contact — ${name.value}`)

        const res = await fetch(FORM_ENDPOINT, {
            method: 'POST',
            body: payload,
            headers: {
                Accept: 'application/json'
            }
        })
        if (!res.ok) {
            const body = await res.json().catch(() => null)
            throw new Error(body?.message || `${res.status} ${res.statusText}`)
        }
        success.value = true
        resetForm()
    } catch (err) {
        console.error('Contact submit failed', err)
        error.value = err.message || 'Failed to send message.'
    } finally {
        loading.value = false
    }
}
</script>

<template>
    <div class="stars"></div>
    <section class="contact" aria-labelledby="contact-title">
        <div class="contact-inner">
            <div class="contact-left">
                <h2 id="contact-title" class="contact-title">Get in touch</h2>
                <p class="contact-sub">
                    Want to collaborate, hire me, or just say hi? Drop a message below or email me directly.
                </p>

                <div class="contact-quick">
                    <a :href="'mailto:dev@mursybot.com'" class="contact-quick-item" aria-label="Email">
                        <Mail class="ico" /> dev@mursybot.com
                    </a>
                    <a href="https://github.com/NaturalTwitch" target="_blank" rel="noopener" class="contact-quick-item"
                        aria-label="GitHub">
                        <svg class="ico" width="18" height="18" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                            <path
                                d="M12 .5C5.65.5.75 5.4.75 11.75c0 4.85 3.15 8.95 7.5 10.4.55.1.75-.25.75-.55v-1.95c-3.05.65-3.7-1.45-3.7-1.45-.5-1.3-1.2-1.65-1.2-1.65-.95-.65.05-.65.05-.65 1.05.05 1.6 1.05 1.6 1.05.95 1.6 2.5 1.15 3.1.9.1-.7.35-1.15.65-1.4-2.45-.3-5.05-1.25-5.05-5.55 0-1.25.45-2.3 1.15-3.1-.1-.3-.5-1.5.1-3.15 0 0 .95-.3 3.1 1.15a10.96 10.96 0 0 1 5.65 0c2.15-1.45 3.1-1.15 3.1-1.15.6 1.65.2 2.85.1 3.15.7.8 1.15 1.85 1.15 3.1 0 4.3-2.6 5.25-5.07 5.55.35.3.65.9.65 1.85v2.75c0 .3.2.65.75.55 4.35-1.45 7.5-5.55 7.5-10.4C23.25 5.4 18.35.5 12 .5z"
                                fill="currentColor" />
                        </svg>
                        GitHub
                    </a>
                </div>

                <div v-if="success" class="msg success" role="status">
                    <CheckCircle class="ico" /> Message sent — I’ll get back soon.
                </div>
                <div v-if="error" class="msg error" role="alert">
                    <AlertCircle class="ico" /> {{ error }}
                </div>
            </div>

            <form class="contact-form" @submit="submitForm" novalidate>

                <input v-model="honeypot" name="_honey" type="text" autocomplete="off" class="honeypot" />

                <label class="field">
                    <span class="label">Name</span>
                    <input v-model="name" type="text" placeholder="Your name" required />
                </label>

                <label class="field">
                    <span class="label">Email</span>
                    <input v-model="email" type="email" placeholder="you@example.com" required />
                </label>

                <label class="field">
                    <span class="label">Message</span>
                    <textarea v-model="message" rows="6" placeholder="Tell me about the project or hello…"
                        required></textarea>
                </label>

                <div class="form-row">
                    <button type="submit" class="btn primary" :disabled="loading">
                        <Send class="ico" /> <span v-if="!loading">Send Message</span>
                        <span v-else>Sending…</span>
                    </button>

                    <button type="button" class="btn ghost" @click="resetForm" :disabled="loading">Reset</button>
                </div>

                <div class="note">
                    By sending you agree I can contact you back. If you prefer manual email: <a
                        href="mailto:dev@mursybot.com">dev@mursybot.com</a>
                </div>
            </form>
        </div>
    </section>
</template>

<style scoped>
:root {
    --neon: #00bcd4;
    --neon-2: #4b8bff;
    --bg: rgba(12, 12, 14, 0.9);
    --muted: #bfc7cf;
    --text: #e8f6fb;
}

.stars {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: transparent;
    z-index: 0;
}

.stars::after {
    content: "";
    position: absolute;
    width: 2px;
    height: 2px;
    background: white;
    box-shadow:
        10vw 20vh white, 30vw 40vh white, 50vw 70vh white, 70vw 10vh white,
        20vw 90vh white, 60vw 50vh white, 80vw 30vh white, 40vw 60vh white,
        15vw 40vh white, 35vw 80vh white, 55vw 20vh white, 75vw 60vh white;
    animation: twinkle 3s infinite alternate;
    border-radius: 50%;
}

@keyframes twinkle {
    0% {
        opacity: 0.2;
    }

    50% {
        opacity: 1;
    }

    100% {
        opacity: 0.2;
    }
}


.contact {
    padding: 36px 20px;
    font-family: 'Poppins', 'Orbitron', sans-serif;
    color: var(--text);
}

.contact-inner {
    max-width: 1100px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 320px 1fr;
    gap: 28px;
}


.contact-left {
    display: flex;
    flex-direction: column;
    gap: 14px;
}

.contact-title {
    font-size: 1.6rem;
    margin: 0;
    background: linear-gradient(90deg, var(--neon), var(--neon-2));
    -webkit-background-clip: text;
    background-clip: text;
    /* -webkit-text-fill-color: transparent; */
    font-weight: 700;
}

.contact-sub {
    margin: 0;
    color: var(--muted);
    font-size: 0.98rem;
}


.contact-quick {
    display: flex;
    flex-direction: column;
    gap: 8px;
    margin-top: 6px;
}

.contact-quick-item {
    display: inline-flex;
    gap: 8px;
    align-items: center;
    padding: 8px 12px;
    border-radius: 10px;
    text-decoration: none;
    color: var(--text);
    background: linear-gradient(90deg, rgba(0, 188, 212, 0.04), rgba(75, 139, 255, 0.04));
    border: 1px solid rgba(0, 188, 212, 0.06);
    font-weight: 600;
}

.ico {
    width: 16px;
    height: 16px;
}


.msg {
    display: flex;
    gap: 8px;
    align-items: center;
    padding: 10px 12px;
    border-radius: 8px;
    font-weight: 600;
}

.msg.success {
    background: rgba(0, 200, 150, 0.06);
    border: 1px solid rgba(0, 200, 150, 0.12);
    color: #c6f6e3;
}

.msg.error {
    background: rgba(255, 90, 90, 0.06);
    border: 1px solid rgba(255, 90, 90, 0.12);
    color: #ffdede;
}


.contact-form {
    background: var(--bg);
    border: 1px solid rgba(0, 188, 212, 0.06);
    padding: 18px;
    border-radius: 12px;
    display: grid;
    gap: 12px;
}


.honeypot {
    display: none !important;
}


.field {
    display: block;
}

.field .label {
    display: block;
    font-size: 0.85rem;
    color: var(--muted);
    margin-bottom: 6px;
    font-weight: 600;
}

.field input[type="text"],
.field input[type="email"],
.field textarea {
    width: 100%;
    padding: 10px 12px;
    border-radius: 8px;
    border: 1px solid rgba(255, 255, 255, 0.04);
    background: rgba(255, 255, 255, 0.02);
    color: var(--text);
    font-size: 0.98rem;
    resize: vertical;
    outline: none;
    transition: box-shadow 120ms ease, transform 120ms ease;
}

.field input:focus,
.field textarea:focus {
    box-shadow: 0 6px 22px rgba(0, 188, 212, 0.06);
    transform: translateY(-2px);
    border-color: rgba(75, 139, 255, 0.18);
}


.form-row {
    display: flex;
    gap: 12px;
    align-items: center;
    flex-wrap: wrap;
}

.btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 10px 14px;
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.04);
    cursor: pointer;
    font-weight: 700;
}

.btn.primary {
    background: linear-gradient(90deg, var(--neon), var(--neon-2));
    color: #0477ba;
}

.btn.ghost {
    background: transparent;
    color: var(--text);
    border: 1px solid rgba(255, 255, 255, 0.04);
}

.btn:disabled {
    opacity: 0.6;
    cursor: not-allowed;
}


.note {
    font-size: 0.85rem;
    color: var(--muted);
    margin-top: 6px;
}


@media (max-width: 900px) {
    .contact-inner {
        grid-template-columns: 1fr;
    }

    .contact-left {
        order: -1;
    }


    .contact-title {
        font-size: 1.4rem;
    }

    .contact-form {
        padding: 14px;
    }

    .form-row {
        flex-direction: column;
        align-items: stretch;
    }

    .btn {
        width: 100%;
        justify-content: center;
    }
}


@media (prefers-reduced-motion: reduce) {

    .avatar,
    .btn,
    .contact-inner,
    .contact-form {
        transition: none !important;
        animation: none !important;
    }
}
</style>
