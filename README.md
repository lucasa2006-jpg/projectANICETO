!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Instituto Aniceto — Cirurgia Facial & Estética de Alta Complexidade</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400&family=Jost:wght@200;300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --crimson: #6B1A2A;
    --crimson-deep: #4A0F1A;
    --crimson-light: #8B2438;
    --gold: #C9A84C;
    --gold-light: #E2C47A;
    --gold-pale: #F5EDD8;
    --cream: #FAF8F5;
    --warm-white: #FFFFFF;
    --charcoal: #1C1C1C;
    --gray-soft: #6B6B6B;
    --gray-line: #E8E0D5;
    --transition: all 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94);
  }

  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Jost', sans-serif;
    background: var(--cream);
    color: var(--charcoal);
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    position: fixed;
    width: 8px;
    height: 8px;
    background: var(--gold);
    border-radius: 50%;
    pointer-events: none;
    z-index: 99999;
    transition: transform 0.15s ease;
    transform: translate(-50%, -50%);
  }
  .cursor-ring {
    position: fixed;
    width: 36px;
    height: 36px;
    border: 1px solid var(--crimson);
    border-radius: 50%;
    pointer-events: none;
    z-index: 99998;
    transition: transform 0.35s ease, width 0.3s, height 0.3s, border-color 0.3s;
    transform: translate(-50%, -50%);
    opacity: 0.6;
  }
  .cursor-ring.hovered {
    width: 56px;
    height: 56px;
    border-color: var(--gold);
    opacity: 1;
  }

  /* Nav */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 1000;
    padding: 24px 64px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    transition: var(--transition);
  }
  nav.scrolled {
    background: rgba(250, 248, 245, 0.96);
    backdrop-filter: blur(16px);
    padding: 16px 64px;
    border-bottom: 1px solid var(--gray-line);
  }

  .nav-logo {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    text-decoration: none;
  }
  .nav-logo-name {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.5rem;
    font-weight: 400;
    letter-spacing: 0.12em;
    color: var(--crimson-deep);
    line-height: 1;
  }
  .nav-logo-sub {
    font-size: 0.6rem;
    font-weight: 300;
    letter-spacing: 0.3em;
    color: var(--gold);
    text-transform: uppercase;
    margin-top: 3px;
  }

  .nav-links {
    display: flex;
    gap: 40px;
    list-style: none;
  }
  .nav-links a {
    text-decoration: none;
    font-size: 0.72rem;
    font-weight: 300;
    letter-spacing: 0.22em;
    text-transform: uppercase;
    color: var(--charcoal);
    position: relative;
    transition: color 0.3s;
  }
  .nav-links a::after {
    content: '';
    position: absolute;
    bottom: -4px;
    left: 0;
    width: 0;
    height: 1px;
    background: var(--gold);
    transition: width 0.4s ease;
  }
  .nav-links a:hover { color: var(--crimson); }
  .nav-links a:hover::after { width: 100%; }

  .nav-cta {
    background: transparent;
    border: 1px solid var(--crimson);
    color: var(--crimson);
    padding: 10px 28px;
    font-family: 'Jost', sans-serif;
    font-size: 0.68rem;
    font-weight: 400;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    cursor: none;
    transition: var(--transition);
    text-decoration: none;
  }
  .nav-cta:hover {
    background: var(--crimson);
    color: var(--warm-white);
  }

  /* Hero */
  .hero {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    position: relative;
    overflow: hidden;
  }

  .hero-content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 160px 80px 80px 120px;
    position: relative;
    z-index: 2;
  }

  .hero-eyebrow {
    font-size: 0.65rem;
    font-weight: 300;
    letter-spacing: 0.4em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 28px;
    opacity: 0;
    animation: fadeUp 0.9s ease 0.3s forwards;
    display: flex;
    align-items: center;
    gap: 16px;
  }
  .hero-eyebrow::before {
    content: '';
    display: block;
    width: 40px;
    height: 1px;
    background: var(--gold);
  }

  .hero-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(3.2rem, 5vw, 5.2rem);
    font-weight: 300;
    line-height: 1.08;
    color: var(--crimson-deep);
    margin-bottom: 32px;
    opacity: 0;
    animation: fadeUp 0.9s ease 0.5s forwards;
  }
  .hero-title em {
    font-style: italic;
    color: var(--crimson-light);
  }

  .hero-text {
    font-size: 0.88rem;
    font-weight: 300;
    line-height: 1.9;
    color: var(--gray-soft);
    max-width: 420px;
    margin-bottom: 52px;
    opacity: 0;
    animation: fadeUp 0.9s ease 0.7s forwards;
    letter-spacing: 0.02em;
  }

  .hero-actions {
    display: flex;
    gap: 24px;
    align-items: center;
    opacity: 0;
    animation: fadeUp 0.9s ease 0.9s forwards;
  }

  .btn-primary {
    background: var(--crimson);
    color: var(--warm-white);
    padding: 16px 44px;
    font-family: 'Jost', sans-serif;
    font-size: 0.72rem;
    font-weight: 400;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    border: none;
    cursor: none;
    transition: var(--transition);
    text-decoration: none;
    display: inline-block;
    position: relative;
    overflow: hidden;
  }
  .btn-primary::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--crimson-deep);
    transform: translateX(-100%);
    transition: transform 0.5s ease;
  }
  .btn-primary:hover::before { transform: translateX(0); }
  .btn-primary span { position: relative; z-index: 1; }

  .btn-ghost {
    color: var(--charcoal);
    font-size: 0.72rem;
    font-weight: 300;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    text-decoration: none;
    display: flex;
    align-items: center;
    gap: 12px;
    transition: color 0.3s;
  }
  .btn-ghost:hover { color: var(--crimson); }
  .btn-ghost-arrow {
    width: 36px;
    height: 36px;
    border: 1px solid currentColor;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: transform 0.3s;
  }
  .btn-ghost:hover .btn-ghost-arrow { transform: rotate(45deg); }

  .hero-stats {
    display: flex;
    gap: 48px;
    margin-top: 72px;
    padding-top: 48px;
    border-top: 1px solid var(--gray-line);
    opacity: 0;
    animation: fadeUp 0.9s ease 1.1s forwards;
  }

  .hero-stat-number {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2.4rem;
    font-weight: 300;
    color: var(--crimson);
    line-height: 1;
  }
  .hero-stat-label {
    font-size: 0.65rem;
    font-weight: 300;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gray-soft);
    margin-top: 6px;
  }
  .hero-stat-gold { color: var(--gold); }

  .hero-visual {
    position: relative;
    overflow: hidden;
  }

  .hero-image-container {
    position: absolute;
    inset: 0;
    opacity: 0;
    animation: fadeIn 1.2s ease 0.2s forwards;
  }

  .hero-image-bg {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transform: scale(1.05);
    animation: zoomOut 8s ease forwards;
  }

  .hero-image-overlay {
    position: absolute;
    inset: 0;
    background: linear-gradient(to right, var(--cream) 0%, transparent 30%),
                linear-gradient(to top, rgba(74,15,26,0.15) 0%, transparent 60%);
  }

  .hero-badge {
    position: absolute;
    bottom: 48px;
    left: -32px;
    background: var(--warm-white);
    padding: 24px 32px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.12);
    opacity: 0;
    animation: fadeIn 0.9s ease 1.3s forwards;
  }
  .hero-badge-text {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.1rem;
    font-weight: 300;
    color: var(--crimson-deep);
    font-style: italic;
  }
  .hero-badge-sub {
    font-size: 0.6rem;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--gold);
    margin-top: 4px;
  }

  /* Gold line decorative */
  .gold-line {
    width: 60px;
    height: 1px;
    background: linear-gradient(to right, var(--gold), transparent);
    margin: 0 auto 24px;
  }

  .gold-line-left {
    margin: 0 0 24px;
  }

  /* Section styles */
  section { padding: 120px 120px; }

  .section-eyebrow {
    font-size: 0.62rem;
    font-weight: 300;
    letter-spacing: 0.4em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 16px;
  }
  .section-eyebrow::before {
    content: '';
    display: block;
    width: 32px;
    height: 1px;
    background: var(--gold);
  }

  .section-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(2.4rem, 3.5vw, 3.8rem);
    font-weight: 300;
    line-height: 1.12;
    color: var(--crimson-deep);
    margin-bottom: 24px;
  }
  .section-title em {
    font-style: italic;
    color: var(--crimson-light);
  }

  /* About */
  .about {
    background: var(--warm-white);
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 80px;
    align-items: center;
  }

  .about-image-wrap {
    position: relative;
  }

  .about-image {
    width: 100%;
    height: 560px;
    object-fit: cover;
    display: block;
  }

  .about-image-frame {
    position: absolute;
    top: -24px;
    left: -24px;
    right: 24px;
    bottom: 24px;
    border: 1px solid var(--gold-light);
    pointer-events: none;
    z-index: 0;
  }

  .about-image-wrap > * { position: relative; z-index: 1; }

  .about-accent {
    position: absolute;
    bottom: -32px;
    right: -32px;
    background: var(--crimson);
    color: var(--warm-white);
    padding: 28px 32px;
    z-index: 2;
  }
  .about-accent-number {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2.6rem;
    font-weight: 300;
    line-height: 1;
  }
  .about-accent-text {
    font-size: 0.6rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    opacity: 0.8;
    margin-top: 4px;
  }

  .about-text {
    font-size: 0.88rem;
    line-height: 1.9;
    color: var(--gray-soft);
    font-weight: 300;
    margin-bottom: 20px;
    letter-spacing: 0.02em;
  }

  .about-philosophy {
    background: var(--gold-pale);
    padding: 32px 36px;
    border-left: 2px solid var(--gold);
    margin: 36px 0;
  }
  .about-philosophy-text {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.35rem;
    font-weight: 400;
    font-style: italic;
    color: var(--crimson-deep);
    line-height: 1.5;
  }

  .about-features {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-top: 36px;
  }
  .about-feature {
    display: flex;
    gap: 14px;
    align-items: flex-start;
  }
  .about-feature-icon {
    width: 28px;
    height: 28px;
    flex-shrink: 0;
    color: var(--gold);
  }
  .about-feature-text {
    font-size: 0.78rem;
    font-weight: 300;
    letter-spacing: 0.05em;
    color: var(--charcoal);
    line-height: 1.5;
  }

  /* Procedures */
  .procedures {
    background: var(--crimson-deep);
    color: var(--warm-white);
    position: relative;
    overflow: hidden;
  }

  .procedures::before {
    content: 'Aniceto';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-family: 'Cormorant Garamond', serif;
    font-size: 22vw;
    font-weight: 300;
    color: rgba(255,255,255,0.02);
    pointer-events: none;
    white-space: nowrap;
    letter-spacing: 0.3em;
  }

  .procedures .section-eyebrow { color: var(--gold-light); }
  .procedures .section-eyebrow::before { background: var(--gold-light); }
  .procedures .section-title { color: var(--warm-white); }
  .procedures .section-title em { color: var(--gold-light); }

  .procedures-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2px;
    margin-top: 72px;
  }

  .procedure-card {
    padding: 36px 28px;
    border: 1px solid rgba(201,168,76,0.15);
    position: relative;
    overflow: hidden;
    transition: var(--transition);
    cursor: none;
    background: rgba(255,255,255,0.02);
  }
  .procedure-card::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(to right, var(--gold), transparent);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.5s ease;
  }
  .procedure-card::after {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(201,168,76,0.06), transparent);
    opacity: 0;
    transition: opacity 0.4s;
  }
  .procedure-card:hover { background: rgba(255,255,255,0.05); }
  .procedure-card:hover::before { transform: scaleX(1); }
  .procedure-card:hover::after { opacity: 1; }

  .procedure-number {
    font-family: 'Cormorant Garamond', serif;
    font-size: 0.8rem;
    color: var(--gold);
    letter-spacing: 0.15em;
    margin-bottom: 20px;
    opacity: 0.7;
  }
  .procedure-name {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.25rem;
    font-weight: 400;
    color: var(--warm-white);
    margin-bottom: 12px;
    line-height: 1.2;
  }
  .procedure-desc {
    font-size: 0.72rem;
    font-weight: 300;
    color: rgba(255,255,255,0.5);
    letter-spacing: 0.05em;
    line-height: 1.6;
  }
  .procedure-arrow {
    position: absolute;
    bottom: 28px;
    right: 28px;
    width: 20px;
    height: 20px;
    opacity: 0;
    transform: translate(-8px, 8px);
    transition: var(--transition);
    color: var(--gold);
  }
  .procedure-card:hover .procedure-arrow {
    opacity: 1;
    transform: translate(0, 0);
  }

  /* Before After */
  .before-after {
    background: var(--cream);
    text-align: center;
  }

  .before-after .section-eyebrow {
    justify-content: center;
  }
  .before-after .section-eyebrow::before { display: none; }

  .ba-disclaimer {
    font-size: 0.68rem;
    font-weight: 300;
    letter-spacing: 0.1em;
    color: var(--gray-soft);
    margin-bottom: 64px;
    max-width: 500px;
    margin-left: auto;
    margin-right: auto;
  }

  .ba-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 32px;
    margin-bottom: 64px;
  }

  .ba-card {
    background: var(--warm-white);
    overflow: hidden;
    box-shadow: 0 4px 32px rgba(0,0,0,0.06);
    transition: var(--transition);
    cursor: none;
  }
  .ba-card:hover { transform: translateY(-8px); box-shadow: 0 20px 60px rgba(107,26,42,0.1); }

  .ba-images {
    position: relative;
    height: 360px;
    overflow: hidden;
  }

  .ba-before, .ba-after {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Cormorant Garamond', serif;
  }
  .ba-before {
    background: linear-gradient(135deg, #f0e8e0, #e8ddd4);
    clip-path: polygon(0 0, 50% 0, 50% 100%, 0 100%);
  }
  .ba-after {
    background: linear-gradient(135deg, #e8d4d8, #d4b8be);
    clip-path: polygon(50% 0, 100% 0, 100% 100%, 50% 100%);
  }
  .ba-before-content, .ba-after-content {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    text-align: center;
  }
  .ba-before-content { left: 25%; transform: translate(-50%, -50%); }
  .ba-after-content { left: 75%; transform: translate(-50%, -50%); }

  .ba-silhouette {
    font-size: 5rem;
    opacity: 0.3;
    line-height: 1;
  }

  .ba-divider-line {
    position: absolute;
    left: 50%;
    top: 0;
    bottom: 0;
    width: 2px;
    background: var(--warm-white);
    transform: translateX(-50%);
    z-index: 2;
  }
  .ba-divider-dot {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 32px;
    height: 32px;
    background: var(--warm-white);
    border-radius: 50%;
    z-index: 3;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 2px 12px rgba(0,0,0,0.15);
  }

  .ba-label-before, .ba-label-after {
    position: absolute;
    top: 16px;
    font-size: 0.6rem;
    font-weight: 300;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    padding: 4px 10px;
    z-index: 4;
  }
  .ba-label-before {
    left: 16px;
    color: var(--gray-soft);
    background: rgba(255,255,255,0.85);
  }
  .ba-label-after {
    right: 16px;
    color: var(--crimson);
    background: rgba(255,255,255,0.85);
  }

  .ba-info {
    padding: 24px 28px;
    text-align: left;
    border-top: 1px solid var(--gray-line);
  }
  .ba-procedure {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.15rem;
    font-weight: 400;
    color: var(--crimson-deep);
    margin-bottom: 6px;
  }
  .ba-detail {
    font-size: 0.7rem;
    font-weight: 300;
    letter-spacing: 0.1em;
    color: var(--gray-soft);
  }

  /* Testimonials */
  .testimonials {
    background: var(--warm-white);
    position: relative;
    overflow: hidden;
  }

  .testimonials::before {
    content: '"';
    position: absolute;
    top: -60px;
    right: 80px;
    font-family: 'Cormorant Garamond', serif;
    font-size: 28rem;
    font-weight: 300;
    color: var(--gold-pale);
    line-height: 1;
    pointer-events: none;
  }

  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 36px;
    margin-top: 72px;
    position: relative;
    z-index: 1;
  }

  .testimonial-card {
    padding: 44px 40px;
    border: 1px solid var(--gray-line);
    position: relative;
    transition: var(--transition);
    background: var(--warm-white);
  }
  .testimonial-card:hover {
    border-color: var(--gold-light);
    box-shadow: 0 16px 48px rgba(107,26,42,0.08);
    transform: translateY(-4px);
  }

  .testimonial-quote {
    color: var(--gold);
    font-size: 2rem;
    font-family: 'Cormorant Garamond', serif;
    line-height: 0.8;
    margin-bottom: 20px;
  }

  .testimonial-text {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.15rem;
    font-weight: 300;
    font-style: italic;
    color: var(--charcoal);
    line-height: 1.7;
    margin-bottom: 28px;
  }

  .testimonial-divider {
    width: 40px;
    height: 1px;
    background: var(--gold);
    margin-bottom: 20px;
  }

  .testimonial-author {
    font-size: 0.75rem;
    font-weight: 500;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--crimson);
    margin-bottom: 4px;
  }
  .testimonial-meta {
    font-size: 0.68rem;
    font-weight: 300;
    letter-spacing: 0.1em;
    color: var(--gray-soft);
  }

  .testimonial-stars {
    position: absolute;
    top: 36px;
    right: 36px;
    color: var(--gold);
    font-size: 0.7rem;
    letter-spacing: 3px;
  }

  /* Contact */
  .contact {
    background: var(--cream);
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0;
    padding: 0;
  }

  .contact-info {
    background: var(--crimson-deep);
    padding: 120px;
    color: var(--warm-white);
    position: relative;
    overflow: hidden;
  }

  .contact-info::before {
    content: '';
    position: absolute;
    width: 400px;
    height: 400px;
    border-radius: 50%;
    border: 1px solid rgba(201,168,76,0.1);
    bottom: -100px;
    right: -100px;
  }
  .contact-info::after {
    content: '';
    position: absolute;
    width: 240px;
    height: 240px;
    border-radius: 50%;
    border: 1px solid rgba(201,168,76,0.08);
    bottom: -60px;
    right: -60px;
  }

  .contact-info .section-title { color: var(--warm-white); }
  .contact-info .section-title em { color: var(--gold-light); }
  .contact-info .section-eyebrow { color: var(--gold-light); }
  .contact-info .section-eyebrow::before { background: var(--gold-light); }

  .contact-text {
    font-size: 0.85rem;
    font-weight: 300;
    line-height: 1.9;
    color: rgba(255,255,255,0.65);
    margin-bottom: 52px;
    letter-spacing: 0.02em;
  }

  .contact-items {
    display: flex;
    flex-direction: column;
    gap: 28px;
    margin-bottom: 48px;
    position: relative;
    z-index: 1;
  }

  .contact-item {
    display: flex;
    gap: 20px;
    align-items: flex-start;
  }
  .contact-item-icon {
    width: 40px;
    height: 40px;
    border: 1px solid rgba(201,168,76,0.3);
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
    color: var(--gold-light);
  }
  .contact-item-label {
    font-size: 0.6rem;
    font-weight: 300;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: var(--gold-light);
    margin-bottom: 6px;
  }
  .contact-item-value {
    font-size: 0.88rem;
    font-weight: 300;
    color: rgba(255,255,255,0.85);
    letter-spacing: 0.03em;
  }

  .whatsapp-btn {
    display: inline-flex;
    align-items: center;
    gap: 14px;
    background: #25D366;
    color: white;
    padding: 18px 40px;
    font-family: 'Jost', sans-serif;
    font-size: 0.75rem;
    font-weight: 400;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    text-decoration: none;
    transition: var(--transition);
    position: relative;
    z-index: 1;
    cursor: none;
  }
  .whatsapp-btn:hover { background: #1da851; transform: translateX(8px); }

  .contact-form-area {
    padding: 120px 80px;
    background: var(--warm-white);
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .contact-form-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 2rem;
    font-weight: 300;
    color: var(--crimson-deep);
    margin-bottom: 40px;
    line-height: 1.2;
  }

  .form-group {
    margin-bottom: 24px;
    position: relative;
  }

  .form-label {
    display: block;
    font-size: 0.62rem;
    font-weight: 300;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 10px;
  }

  .form-input, .form-select, .form-textarea {
    width: 100%;
    background: transparent;
    border: none;
    border-bottom: 1px solid var(--gray-line);
    padding: 12px 0;
    font-family: 'Jost', sans-serif;
    font-size: 0.88rem;
    font-weight: 300;
    color: var(--charcoal);
    outline: none;
    transition: border-color 0.3s;
    cursor: none;
  }
  .form-input:focus, .form-select:focus, .form-textarea:focus {
    border-color: var(--crimson);
  }
  .form-input::placeholder, .form-textarea::placeholder { color: var(--gray-line); }
  .form-select { appearance: none; cursor: none; }

  .form-textarea {
    resize: none;
    height: 80px;
  }

  .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; }

  .form-submit {
    background: var(--crimson);
    color: var(--warm-white);
    border: none;
    padding: 18px 48px;
    font-family: 'Jost', sans-serif;
    font-size: 0.72rem;
    font-weight: 400;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    cursor: none;
    transition: var(--transition);
    display: flex;
    align-items: center;
    gap: 16px;
    width: 100%;
    justify-content: center;
    margin-top: 8px;
    position: relative;
    overflow: hidden;
  }
  .form-submit::before {
    content: '';
    position: absolute;
    inset: 0;
    background: var(--crimson-deep);
    transform: translateX(-100%);
    transition: transform 0.5s ease;
  }
  .form-submit:hover::before { transform: translateX(0); }
  .form-submit span { position: relative; z-index: 1; }

  /* Footer */
  footer {
    background: var(--charcoal);
    color: rgba(255,255,255,0.6);
    padding: 60px 120px;
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 60px;
    align-items: start;
  }

  .footer-logo-name {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.8rem;
    font-weight: 300;
    letter-spacing: 0.1em;
    color: var(--warm-white);
    line-height: 1;
  }
  .footer-logo-sub {
    font-size: 0.55rem;
    letter-spacing: 0.35em;
    text-transform: uppercase;
    color: var(--gold);
    margin-top: 4px;
    margin-bottom: 20px;
  }
  .footer-tagline {
    font-size: 0.78rem;
    font-weight: 300;
    line-height: 1.8;
    letter-spacing: 0.03em;
    max-width: 280px;
  }
  .footer-divider {
    width: 40px;
    height: 1px;
    background: var(--gold);
    margin: 20px 0;
    opacity: 0.5;
  }
  .footer-copy {
    font-size: 0.65rem;
    opacity: 0.4;
    letter-spacing: 0.05em;
  }

  .footer-col-title {
    font-size: 0.6rem;
    font-weight: 400;
    letter-spacing: 0.35em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 24px;
  }
  .footer-links {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 12px;
  }
  .footer-links a {
    text-decoration: none;
    font-size: 0.78rem;
    font-weight: 300;
    color: rgba(255,255,255,0.5);
    transition: color 0.3s;
    letter-spacing: 0.05em;
  }
  .footer-links a:hover { color: var(--gold-light); }

  /* Scroll reveal */
  .reveal {
    opacity: 0;
    transform: translateY(32px);
    transition: opacity 0.9s ease, transform 0.9s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }
  .reveal-delay-1 { transition-delay: 0.1s; }
  .reveal-delay-2 { transition-delay: 0.2s; }
  .reveal-delay-3 { transition-delay: 0.3s; }
  .reveal-delay-4 { transition-delay: 0.4s; }
  .reveal-delay-5 { transition-delay: 0.5s; }

  /* Keyframes */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  @keyframes zoomOut {
    from { transform: scale(1.05); }
    to { transform: scale(1); }
  }

  /* Scrollbar */
  ::-webkit-scrollbar { width: 4px; }
  ::-webkit-scrollbar-track { background: var(--cream); }
  ::-webkit-scrollbar-thumb { background: var(--crimson); }

  /* SVG icons inline */
  .icon { display: inline-block; vertical-align: middle; }
</style>
</head>
<body>

<!-- Custom cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- Navigation -->
<nav id="mainNav">
  <a href="#" class="nav-logo">
    <span class="nav-logo-name">Clínica Aniceto</span>
    <span class="nav-logo-sub">Cirurgia Facial · São Paulo</span>
  </a>

  <ul class="nav-links">
    <li><a href="#sobre">A Clínica</a></li>
    <li><a href="#procedimentos">Procedimentos</a></li>
    <li><a href="#resultados">Resultados</a></li>
    <li><a href="#depoimentos">Depoimentos</a></li>
  </ul>

  <a href="#contato" class="nav-cta">Agendar Consulta</a>
</nav>

<!-- Hero -->
<section class="hero" id="inicio">
  <div class="hero-content">
    <div class="hero-eyebrow">Cirurgia Facial de Alta Complexidade</div>

    <h1 class="hero-title">
      A arte de revelar<br>
      sua <em>beleza</em><br>
      mais autêntica
    </h1>

    <p class="hero-text">
      Procedimentos cirúrgicos e estéticos realizados com maestria técnica e sensibilidade artística, para resultados naturais que respeitam a singularidade de cada paciente.
    </p>

    <div class="hero-actions">
      <a href="#contato" class="btn-primary"><span>Agendar Avaliação</span></a>
      <a href="#procedimentos" class="btn-ghost">
        <span class="btn-ghost-arrow">
          <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
            <path d="M3 7h8M7 3l4 4-4 4" stroke="currentColor" stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </span>
        Ver Procedimentos
      </a>
    </div>

    <div class="hero-stats">
      <div>
        <div class="hero-stat-number">2.400<span class="hero-stat-gold" style="font-size:1.4rem">+</span></div>
        <div class="hero-stat-label">Cirurgias realizadas</div>
      </div>
      <div>
        <div class="hero-stat-number">18<span class="hero-stat-gold" style="font-size:1.4rem">+</span></div>
        <div class="hero-stat-label">Anos de experiência</div>
      </div>
      <div>
        <div class="hero-stat-number">99<span class="hero-stat-gold" style="font-size:1rem">%</span></div>
        <div class="hero-stat-label">Índice de satisfação</div>
      </div>
    </div>
  </div>

  <div class="hero-visual">
    <div class="hero-image-container">
      <!-- Elegant gradient representation of a clinic aesthetic -->
      <div class="hero-image-bg" style="background: linear-gradient(135deg, #f5efe8 0%, #e8d8d0 25%, #d4b8be 50%, #c4a0a8 75%, #b48890 100%); width:100%; height:100%;"></div>
      <div class="hero-image-overlay"></div>

      <!-- Decorative elements representing facial contours -->
      <svg style="position:absolute;inset:0;width:100%;height:100%;opacity:0.15;" viewBox="0 0 600 800" preserveAspectRatio="xMidYMid slice">
        <ellipse cx="300" cy="340" rx="160" ry="210" fill="none" stroke="#6B1A2A" stroke-width="0.8"/>
        <ellipse cx="300" cy="320" rx="120" ry="160" fill="none" stroke="#C9A84C" stroke-width="0.5"/>
        <line x1="300" y1="130" x2="300" y2="530" stroke="#C9A84C" stroke-width="0.5" opacity="0.4"/>
        <circle cx="300" cy="340" r="4" fill="#C9A84C" opacity="0.6"/>
        <path d="M200,280 Q300,220 400,280" fill="none" stroke="#6B1A2A" stroke-width="0.8"/>
        <path d="M220,340 Q270,380 300,385 Q330,380 380,340" fill="none" stroke="#6B1A2A" stroke-width="0.8"/>
        <path d="M240,430 Q300,470 360,430" fill="none" stroke="#C9A84C" stroke-width="0.6"/>
        <!-- golden ratio spirals suggestion -->
        <circle cx="300" cy="340" r="80" fill="none" stroke="#C9A84C" stroke-width="0.3" opacity="0.5"/>
        <circle cx="300" cy="340" r="130" fill="none" stroke="#C9A84C" stroke-width="0.3" opacity="0.3"/>
      </svg>
    </div>

    <div class="hero-badge">
      <div class="hero-badge-text">Membro SBCP</div>
      <div class="hero-badge-sub">Sociedade Brasileira de Cirurgia Plástica</div>
    </div>
  </div>
</section>

<!-- About -->
<section class="about" id="sobre">
  <div class="about-image-wrap reveal">
    <div class="about-image-frame"></div>
    <div class="about-image" style="background: linear-gradient(160deg, #e8ddd4, #d4c4b8, #c4a8a0); position:relative; overflow:hidden;">
      <!-- Abstract medical/clinic elegant illustration -->
      <svg style="position:absolute;inset:0;width:100%;height:100%;opacity:0.6;" viewBox="0 0 460 560" preserveAspectRatio="xMidYMid slice">
        <rect x="0" y="0" width="460" height="560" fill="url(#aboutGrad)"/>
        <defs>
          <linearGradient id="aboutGrad" x1="0%" y1="0%" x2="100%" y2="100%">
            <stop offset="0%" style="stop-color:#f0e8e0"/>
            <stop offset="100%" style="stop-color:#c8a8a0"/>
          </linearGradient>
        </defs>
        <!-- Silhouette profile elegant lines -->
        <path d="M180,80 Q230,60 280,80 Q320,100 330,150 Q345,200 335,260 Q325,320 310,360 Q295,400 290,440 Q285,480 280,520" fill="none" stroke="#6B1A2A" stroke-width="1.5" opacity="0.3"/>
        <path d="M180,80 Q150,120 145,180 Q140,240 155,300 Q170,360 185,400 Q200,440 210,480 Q218,510 220,520" fill="none" stroke="#6B1A2A" stroke-width="1.5" opacity="0.3"/>
        <!-- golden horizontal lines -->
        <line x1="100" y1="200" x2="360" y2="200" stroke="#C9A84C" stroke-width="0.5" opacity="0.5"/>
        <line x1="100" y1="300" x2="360" y2="300" stroke="#C9A84C" stroke-width="0.5" opacity="0.5"/>
        <line x1="100" y1="400" x2="360" y2="400" stroke="#C9A84C" stroke-width="0.5" opacity="0.5"/>
        <circle cx="230" cy="130" r="60" fill="none" stroke="#C9A84C" stroke-width="0.8" opacity="0.4"/>
      </svg>
    </div>
    <div class="about-accent">
      <div class="about-accent-number">18</div>
      <div class="about-accent-text">Anos de excelência</div>
    </div>
  </div>

  <div class="reveal reveal-delay-2">
    <div class="section-eyebrow">Nossa Filosofia</div>
    <h2 class="section-title">Ciência, arte e <em>respeito</em><br>à sua identidade</h2>

    <p class="about-text">
      A Clínica Aniceto foi fundada sobre um princípio inabalável: cada rosto conta uma história única, e nossa missão é realçar essa narrativa com precisão técnica e sensibilidade estética sem precedentes.
    </p>

    <div class="about-philosophy">
      <p class="about-philosophy-text">
        "Beleza não é uniformidade — é a expressão mais refinada da sua singularidade. Nossa cirurgia existe para revelar, não para transformar."
      </p>
    </div>

    <p class="about-text">
      Com especialização avançada em cirurgia facial, nossa equipe combina domínio técnico cirúrgico com um olhar estético apurado, garantindo resultados harmoniosos, naturais e duradouros que preservam a essência de cada paciente.
    </p>

    <div class="about-features">
      <div class="about-feature">
        <svg class="about-feature-icon" viewBox="0 0 28 28" fill="none">
          <path d="M14 3l2.5 8h8.5l-7 5 2.5 8L14 19l-6.5 5 2.5-8-7-5h8.5z" stroke="#C9A84C" stroke-width="1.2" fill="none"/>
        </svg>
        <span class="about-feature-text">Membro titular da Sociedade Brasileira de Cirurgia Plástica</span>
      </div>
      <div class="about-feature">
        <svg class="about-feature-icon" viewBox="0 0 28 28" fill="none">
          <circle cx="14" cy="14" r="10" stroke="#C9A84C" stroke-width="1.2"/>
          <path d="M10 14l3 3 5-5" stroke="#C9A84C" stroke-width="1.2" stroke-linecap="round"/>
        </svg>
        <span class="about-feature-text">Protocolos cirúrgicos de padrão internacional</span>
      </div>
      <div class="about-feature">
        <svg class="about-feature-icon" viewBox="0 0 28 28" fill="none">
          <rect x="4" y="8" width="20" height="14" rx="2" stroke="#C9A84C" stroke-width="1.2"/>
          <path d="M9 8V6a5 5 0 0110 0v2" stroke="#C9A84C" stroke-width="1.2"/>
        </svg>
        <span class="about-feature-text">Infraestrutura hospitalar própria de alta complexidade</span>
      </div>
      <div class="about-feature">
        <svg class="about-feature-icon" viewBox="0 0 28 28" fill="none">
          <path d="M14 5C9 5 5 9 5 14s4 9 9 9 9-4 9-9-4-9-9-9z" stroke="#C9A84C" stroke-width="1.2"/>
          <path d="M14 10v4l3 2" stroke="#C9A84C" stroke-width="1.2" stroke-linecap="round"/>
        </svg>
        <span class="about-feature-text">Acompanhamento pós-operatório dedicado e contínuo</span>
      </div>
    </div>
  </div>
</section>

<!-- Procedures -->
<section class="procedures" id="procedimentos">
  <div class="reveal" style="max-width:560px">
    <div class="section-eyebrow">Especialidades Cirúrgicas</div>
    <h2 class="section-title">Procedimentos que<br><em>transformam</em> vidas</h2>
  </div>

  <div class="procedures-grid">
    <!-- Row 1 -->
    <div class="procedure-card reveal reveal-delay-1">
      <div class="procedure-number">01</div>
      <div class="procedure-name">Blefaroplastia Superior</div>
      <div class="procedure-desc">Rejuvenescimento e definição da pálpebra superior com resultado natural e harmonioso</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="procedure-card reveal reveal-delay-2">
      <div class="procedure-number">02</div>
      <div class="procedure-name">Blefaroplastia Inferior</div>
      <div class="procedure-desc">Remoção de bolsas e rugas subpalpebrais para um olhar descansado e revitalizado</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="procedure-card reveal reveal-delay-3">
      <div class="procedure-number">03</div>
      <div class="procedure-name">Lipo de Papada</div>
      <div class="procedure-desc">Definição precisa do contorno mandibular e cervical com mínima invasão</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="procedure-card reveal reveal-delay-4">
      <div class="procedure-number">04</div>
      <div class="procedure-name">Lifting Facial</div>
      <div class="procedure-desc">Reposicionamento estrutural dos tecidos faciais para rejuvenescimento global</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>

    <!-- Row 2 -->
    <div class="procedure-card reveal reveal-delay-1">
      <div class="procedure-number">05</div>
      <div class="procedure-name">Lifting Temporal</div>
      <div class="procedure-desc">Elevação da região têmporo-frontal para olhar mais jovem e expressivo</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="procedure-card reveal reveal-delay-2">
      <div class="procedure-number">06</div>
      <div class="procedure-name">Mini Lifting</div>
      <div class="procedure-desc">Técnica minimamente invasiva ideal para rejuvenescimento precoce e recuperação rápida</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="procedure-card reveal reveal-delay-3">
      <div class="procedure-number">07</div>
      <div class="procedure-name">Cervicoplastia</div>
      <div class="procedure-desc">Remodelação cirúrgica da região cervical com resultados elegantes e duradouros</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="procedure-card reveal reveal-delay-4">
      <div class="procedure-number">08</div>
      <div class="procedure-name">Lip Lift</div>
      <div class="procedure-desc">Elevação e harmonização do lábio superior para um sorriso mais jovem e definido</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>

    <!-- Row 3 -->
    <div class="procedure-card reveal reveal-delay-1">
      <div class="procedure-number">09</div>
      <div class="procedure-name">Platismoplastia</div>
      <div class="procedure-desc">Correção das bandas platismais para um pescoço mais liso e harmonioso</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="procedure-card reveal reveal-delay-2">
      <div class="procedure-number">10</div>
      <div class="procedure-name">Neck Lift</div>
      <div class="procedure-desc">Rejuvenescimento completo da região cervical integrando múltiplas técnicas avançadas</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="procedure-card reveal reveal-delay-3">
      <div class="procedure-number">11</div>
      <div class="procedure-name">Bichectomia</div>
      <div class="procedure-desc">Remoção precisa das bolas de Bichat para maior definição e elegância facial</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="procedure-card reveal reveal-delay-4">
      <div class="procedure-number">12</div>
      <div class="procedure-name">Rinoplastia</div>
      <div class="procedure-desc">Refinamento cirúrgico do nariz com harmonia proporcional e resultado definitivo</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>

    <!-- Row 4 (last 2 centered) -->
    <div class="procedure-card reveal reveal-delay-1">
      <div class="procedure-number">13</div>
      <div class="procedure-name">Otoplastia</div>
      <div class="procedure-desc">Reposicionamento estético das orelhas para proporção e harmonia facial perfeitas</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="procedure-card reveal reveal-delay-2">
      <div class="procedure-number">14</div>
      <div class="procedure-name">Castanhares</div>
      <div class="procedure-desc">Correção cirúrgica refinada das comissuras labiais para expressão facial mais harmônica</div>
      <svg class="procedure-arrow" viewBox="0 0 20 20" fill="none">
        <path d="M4 10h12M10 4l6 6-6 6" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
    </div>
    <div class="procedure-card reveal reveal-delay-3" style="grid-column: 3/5;">
      <div style="display:flex; align-items:center; justify-content:space-between; gap:24px;">
        <div>
          <div class="procedure-number" style="margin-bottom:8px;">Consulta Personalizada</div>
          <div class="procedure-name" style="margin-bottom:8px;">Avaliação Completa & Plano Cirúrgico</div>
          <div class="procedure-desc">Cada paciente recebe uma avaliação individualizada com planejamento cirúrgico detalhado, tecnologia de simulação digital e acompanhamento médico de excelência.</div>
        </div>
        <a href="#contato" class="btn-primary" style="white-space:nowrap; flex-shrink:0;"><span>Agendar Agora</span></a>
      </div>
    </div>
  </div>
</section>

<!-- Before / After -->
<section class="before-after" id="resultados">
  <div class="section-eyebrow reveal">Galeria de Resultados</div>
  <h2 class="section-title reveal">Transformações <em>reais,</em><br>resultados extraordinários</h2>
  <p class="ba-disclaimer reveal">
    Todos os resultados são reais e obtidos com consentimento expresso dos pacientes. Resultados individuais podem variar.
  </p>

  <div class="ba-grid">

    <!-- Card 1 -->
    <div class="ba-card reveal reveal-delay-1">
      <div class="ba-images">
        <div class="ba-before">
          <div class="ba-before-content">
            <div class="ba-silhouette">◎</div>
          </div>
        </div>
        <div class="ba-after">
          <div class="ba-after-content">
            <div class="ba-silhouette" style="opacity:0.45;">✦</div>
          </div>
        </div>
        <div class="ba-divider-line"></div>
        <div class="ba-divider-dot">
          <svg width="12" height="12" viewBox="0 0 12 12" fill="none">
            <path d="M2 6h3M7 6h3M5 2v3M5 7v3" stroke="#C9A84C" stroke-width="1.2" stroke-linecap="round"/>
          </svg>
        </div>
        <div class="ba-label-before">Antes</div>
        <div class="ba-label-after">Depois</div>
      </div>
      <div class="ba-info">
        <div class="ba-procedure">Blefaroplastia Superior & Inferior</div>
        <div class="ba-detail">Paciente F, 54 anos · 6 meses pós-operatório</div>
      </div>
    </div>

    <!-- Card 2 -->
    <div class="ba-card reveal reveal-delay-2">
      <div class="ba-images">
        <div class="ba-before" style="background: linear-gradient(135deg, #ede4da, #ddd0c4);">
          <div class="ba-before-content">
            <div class="ba-silhouette">◉</div>
          </div>
        </div>
        <div class="ba-after" style="background: linear-gradient(135deg, #ddd0c8, #c8b4b0);">
          <div class="ba-after-content">
            <div class="ba-silhouette" style="opacity:0.45;">✦</div>
          </div>
        </div>
        <div class="ba-divider-line"></div>
        <div class="ba-divider-dot">
          <svg width="12" height="12" viewBox="0 0 12 12" fill="none">
            <path d="M2 6h3M7 6h3M5 2v3M5 7v3" stroke="#C9A84C" stroke-width="1.2" stroke-linecap="round"/>
          </svg>
        </div>
        <div class="ba-label-before">Antes</div>
        <div class="ba-label-after">Depois</div>
      </div>
      <div class="ba-info">
        <div class="ba-procedure">Lifting Facial Completo</div>
        <div class="ba-detail">Paciente F, 61 anos · 12 meses pós-operatório</div>
      </div>
    </div>

    <!-- Card 3 -->
    <div class="ba-card reveal reveal-delay-3">
      <div class="ba-images">
        <div class="ba-before" style="background: linear-gradient(135deg, #e8dcd4, #d8c8c0);">
          <div class="ba-before-content">
            <div class="ba-silhouette">○</div>
          </div>
        </div>
        <div class="ba-after" style="background: linear-gradient(135deg, #d8c4c8, #c4abb0);">
          <div class="ba-after-content">
            <div class="ba-silhouette" style="opacity:0.5;">◆</div>
          </div>
        </div>
        <div class="ba-divider-line"></div>
        <div class="ba-divider-dot">
          <svg width="12" height="12" viewBox="0 0 12 12" fill="none">
            <path d="M2 6h3M7 6h3M5 2v3M5 7v3" stroke="#C9A84C" stroke-width="1.2" stroke-linecap="round"/>
          </svg>
        </div>
        <div class="ba-label-before">Antes</div>
        <div class="ba-label-after">Depois</div>
      </div>
      <div class="ba-info">
        <div class="ba-procedure">Rinoplastia & Lipo de Papada</div>
        <div class="ba-detail">Paciente F, 38 anos · 8 meses pós-operatório</div>
      </div>
    </div>
  </div>

  <p class="ba-disclaimer reveal" style="margin-top:0;">
    Agende sua avaliação e receba um plano de tratamento personalizado com simulação digital dos resultados esperados.
  </p>
  <div class="reveal">
    <a href="#contato" class="btn-primary"><span>Solicitar Avaliação</span></a>
  </div>
</section>

<!-- Testimonials -->
<section class="testimonials" id="depoimentos">
  <div class="section-eyebrow reveal">Depoimentos</div>
  <h2 class="section-title reveal">Experiências que<br><em>falam por si</em></h2>

  <div class="testimonials-grid">
    <div class="testimonial-card reveal reveal-delay-1">
      <div class="testimonial-stars">★★★★★</div>
      <div class="testimonial-quote">"</div>
      <p class="testimonial-text">A blefaroplastia transformou completamente minha autoestima. Meu olhar ficou mais jovem sem perder o que é meu. O resultado foi tão natural que as pessoas perguntam se descansei bem nas férias.</p>
      <div class="testimonial-divider"></div>
      <div class="testimonial-author">Mariana C.</div>
      <div class="testimonial-meta">Blefaroplastia Superior · São Paulo</div>
    </div>

    <div class="testimonial-card reveal reveal-delay-2">
      <div class="testimonial-stars">★★★★★</div>
      <div class="testimonial-quote">"</div>
      <p class="testimonial-text">Fiz o lifting facial há dois anos e o resultado ainda me surpreende quando me olho no espelho. A atenção ao detalhe e o cuidado no pós-operatório foram excepcionais. Recomendo sem hesitar.</p>
      <div class="testimonial-divider"></div>
      <div class="testimonial-author">Elisa M.</div>
      <div class="testimonial-meta">Lifting Facial Completo · Campinas</div>
    </div>

    <div class="testimonial-card reveal reveal-delay-3">
      <div class="testimonial-stars">★★★★★</div>
      <div class="testimonial-quote">"</div>
      <p class="testimonial-text">Sempre me incomodei com meu nariz, mas tinha medo de parecer operada. A rinoplastia foi exatamente o que eu queria: harmonia, sem exageros. Me sinto mais eu mesma do que antes.</p>
      <div class="testimonial-divider"></div>
      <div class="testimonial-author">Beatriz F.</div>
      <div class="testimonial-meta">Rinoplastia · Santos</div>
    </div>

    <div class="testimonial-card reveal reveal-delay-1">
      <div class="testimonial-stars">★★★★★</div>
      <div class="testimonial-quote">"</div>
      <p class="testimonial-text">A equipe da Aniceto cuida de cada detalhe com uma elegância que vai muito além da cirurgia. Desde a primeira consulta até o último retorno, me senti em boas mãos em cada etapa.</p>
      <div class="testimonial-divider"></div>
      <div class="testimonial-author">Fernanda O.</div>
      <div class="testimonial-meta">Neck Lift & Cervicoplastia · São Paulo</div>
    </div>

    <div class="testimonial-card reveal reveal-delay-2">
      <div class="testimonial-stars">★★★★★</div>
      <div class="testimonial-quote">"</div>
      <p class="testimonial-text">A otoplastia mudou minha relação comigo mesma. Simples assim. Hoje tenho coragem de usar penteados que nunca imaginei. O resultado estético é impecável e a cicatriz imperceptível.</p>
      <div class="testimonial-divider"></div>
      <div class="testimonial-author">Camila N.</div>
      <div class="testimonial-meta">Otoplastia · São Paulo</div>
    </div>

    <div class="testimonial-card reveal reveal-delay-3">
      <div class="testimonial-stars">★★★★★</div>
      <div class="testimonial-quote">"</div>
      <p class="testimonial-text">A bichectomia deu uma definição ao meu rosto que eu não sabia que era possível. O procedimento foi rápido, seguro e o resultado superou todas as minhas expectativas. Estrutura facial impecável.</p>
      <div class="testimonial-divider"></div>
      <div class="testimonial-author">Juliana P.</div>
      <div class="testimonial-meta">Bichectomia · Rio de Janeiro</div>
    </div>
  </div>
</section>

<!-- Contact -->
<section class="contact" id="contato">
  <div class="contact-info">
    <div class="section-eyebrow">Fale Conosco</div>
    <h2 class="section-title">Inicie sua<br><em>jornada</em> conosco</h2>

    <p class="contact-text">
      A primeira consulta é o início de uma relação de confiança. Venha conhecer nossa clínica e conversar com nossos especialistas sobre suas expectativas sem qualquer compromisso.
    </p>

    <div class="contact-items">
      <div class="contact-item">
        <div class="contact-item-icon">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
            <path d="M9 2a5 5 0 100 10A5 5 0 009 2zM3.5 15s0-3 5.5-3 5.5 3 5.5 3" stroke="currentColor" stroke-width="1.2" stroke-linecap="round"/>
          </svg>
        </div>
        <div>
          <div class="contact-item-label">Consultas</div>
          <div class="contact-item-value">Segunda a Sexta, 9h às 18h</div>
        </div>
      </div>

      <div class="contact-item">
        <div class="contact-item-icon">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
            <path d="M9 1C5.7 1 3 3.7 3 7c0 4.5 6 10 6 10s6-5.5 6-10c0-3.3-2.7-6-6-6z" stroke="currentColor" stroke-width="1.2"/>
            <circle cx="9" cy="7" r="1.5" stroke="currentColor" stroke-width="1.2"/>
          </svg>
        </div>
        <div>
          <div class="contact-item-label">Endereço</div>
          <div class="contact-item-value">Rua Teodoro Sampaio 2775, São Paulo, São Paulo,<br>Faria Lima · São Paulo, SP</div>
        </div>
      </div>

      <div class="contact-item">
        <div class="contact-item-icon">
          <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
            <path d="M3 3h3l1.5 3.5L6 8s1 2 4 4l1.5-1.5L15 12v3s-3 1-6-2S1 6 3 3z" stroke="currentColor" stroke-width="1.2" stroke-linejoin="round"/>
          </svg>
        </div>
        <div>
          <div class="contact-item-label">Telefone</div>
          <div class="contact-item-value">(11) 3456-7890</div>
        </div>
      </div>
    </div>

    <a href="https://wa.me/5511946276180" id="whatsappBtn" class="whatsapp-btn" target="_blank" rel="noopener">
      <svg width="22" height="22" viewBox="0 0 22 22" fill="none">
        <path d="M11 2C6.03 2 2 6.03 2 11c0 1.7.46 3.3 1.24 4.7L2 20l4.44-1.22C7.77 19.56 9.35 20 11 20c4.97 0 9-4.03 9-9s-4.03-9-9-9z" fill="white" opacity="0.9"/>
        <path d="M8 8.5c0 0 .5-1 1.5-1s1.5.5 2 1.5.5 2 .5 2-.5 1-1 1.5-.5 1 0 1.5 1.5 1.5 2.5.5 1.5-2 1.5-2" stroke="#25D366" stroke-width="1.2" stroke-linecap="round"/>
      </svg>
      <span>Agendar pelo WhatsApp</span>
    </a>
  </div>

  <script>
    // Build WhatsApp message from form fields and open chat
    (function(){
      var btn = document.getElementById('whatsappBtn');
      if(!btn) return;

      btn.addEventListener('click', function(e){
        e.preventDefault();

        function qs(selector){ return document.querySelector(selector); }

        var name = (qs('input[type="text"].form-input')||{value:''}).value.trim();
        var phone = (qs('input[type="tel"].form-input')||{value:''}).value.trim();
        var email = (qs('input[type="email"].form-input')||{value:''}).value.trim();
        var procedure = (qs('select.form-select')||{value:''}).value;

        var parts = [];
        if(name) parts.push('Nome: ' + name);
        if(phone) parts.push('Telefone: ' + phone);
        if(email) parts.push('E-mail: ' + email);
        if(procedure) parts.push('Procedimento: ' + procedure);

        var text = 'Ol%C3%A1%2C%20gostaria%20de%20agendar%20uma%20consulta%20na%20Cl%C3%ADnica%20Aniceto.'; // default
        if(parts.length) {
          text = encodeURIComponent('Olá, gostaria de agendar uma consulta na Clínica Aniceto.\n' + parts.join('\n'));
        }

        var phoneNumber = '5511934567890';
        var url = 'https://wa.me/' + phoneNumber + '?text=' + text;
        window.open(url, '_blank', 'noopener');
      });
    })();
  </script>

  <div class="contact-form-area">
    <div class="contact-form-title reveal">Solicitar consulta<br>de avaliação</div>

        <div class="form-group">
          <label class="form-label">Nome Completo</label>
          <input type="text" class="form-input" placeholder="Seu nome">
        </div>
        <div class="form-group">
          <label class="form-label">Telefone / WhatsApp</label>
          <input type="tel" class="form-input" placeholder="(11) 9xxxx-xxxx">
        </div>
      </div>

      <div class="form-group reveal reveal-delay-2">
        <label class="form-label">E-mail</label>
        <input type="email" class="form-input" placeholder="seu@email.com">
      </div>

      <div class="form-group reveal reveal-delay-3">
        <label class="form-label">Procedimento de Interesse</label>
        <select class="form-select form-input">
          <option value="">Selecione um procedimento</option>
          <option>Blefaroplastia Superior</option>
          <option>Blefaroplastia Inferior</option>
          <option>Lipo de Papada</option>
          <option>Lifting Facial</option>
          <option>Lifting Temporal</option>
          <option>Mini Lifting</option>
          <option>Cervicoplastia</option>
          <option>Lip Lift</option>
          <option>Platismoplastia</option>
          <option>Neck Lift</option>
          <option>Bichectomia</option>
          <option>Castanhares</option>
          <option>Rinoplastia</option>
          <option>Otoplastia</option>
          <option>Outros / Avaliação Geral</option>
        </select>
      </div>

      <div class="form-group reveal reveal-delay-4">
        <label class="form-label">Mensagem (opcional)</label>
        <textarea class="form-textarea form-input" placeholder="Conte-nos sobre suas expectativas ou dúvidas..."></textarea>
      </div>

      <button type="submit" class="form-submit reveal reveal-delay-5" onclick="handleFormSubmit(this)">
        <span>Solicitar Agendamento</span>
        <svg width="18" height="18" viewBox="0 0 18 18" fill="none">
          <path d="M3 9h12M9 3l6 6-6 6" stroke="white" stroke-width="1.2" stroke-linecap="round"/>
        </svg>
      </button>
    </form>
  </div>
</section>

<!-- Footer -->
<footer>
  <div>
    <div class="footer-logo-name">Clínica Aniceto</div>
    <div class="footer-logo-sub">Cirurgia Facial de Alta Complexidade</div>
    <p class="footer-tagline">Excelência técnica, sensibilidade artística e compromisso com a autenticidade de cada paciente.</p>
    <div class="footer-divider"></div>
    <div class="footer-copy">© 2024 Clínica Aniceto. Todos os direitos reservados.<br>CRM/SP — Conselho Regional de Medicina</div>
  </div>

  <div>
    <div class="footer-col-title">Procedimentos</div>
    <ul class="footer-links">
      <li><a href="#">Blefaroplastia</a></li>
      <li><a href="#">Lifting Facial</a></li>
      <li><a href="#">Rinoplastia</a></li>
      <li><a href="#">Neck Lift</a></li>
      <li><a href="#">Bichectomia</a></li>
      <li><a href="#">Otoplastia</a></li>
    </ul>
  </div>

  <div>
    <div class="footer-col-title">Clínica</div>
    <ul class="footer-links">
      <li><a href="#">Nossa Filosofia</a></li>
      <li><a href="#">Equipe Médica</a></li>
      <li><a href="#">Infraestrutura</a></li>
      <li><a href="#">Galeria</a></li>
      <li><a href="#">Blog Médico</a></li>
    </ul>
  </div>

 

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mouseX = 0, mouseY = 0;

  document.addEventListener('mousemove', (e) => {
    mouseX = e.clientX;
    mouseY = e.clientY;
    cursor.style.left = mouseX + 'px';
    cursor.style.top = mouseY + 'px';
    ring.style.left = mouseX + 'px';
    ring.style.top = mouseY + 'px';
  });

  document.querySelectorAll('a, button, .procedure-card, .ba-card, .testimonial-card').forEach(el => {
    el.addEventListener('mouseenter', () => ring.classList.add('hovered'));
    el.addEventListener('mouseleave', () => ring.classList.remove('hovered'));
  });

  // Nav scroll
  const nav = document.getElementById('mainNav');
  window.addEventListener('scroll', () => {
    nav.classList.toggle('scrolled', window.scrollY > 60);
  });

  // Scroll reveal
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.12 });

  reveals.forEach(el => observer.observe(el));

  // Form submit handler
  function async (params)  
    handleFormSubmit
  (btn) 
    const span = btn.querySelector('span');
    span.textContent = 'Solicitação Enviada ✓';
    btn.style.background = '#2d6a3f';
    setTimeout(() => {
      span.textContent = 'Solicitar Agendamento';
      btn.style.background = '';
    }, 3000);
</script>
</body>
</html>

