/* =============================================================================
   H&S Holdings  /  Interactions
   ============================================================================= */

(function(){
  'use strict';

  /* ---------- Sticky nav scroll state ---------- */
  const nav = document.querySelector('.nav');
  if (nav) {
    let lastY = 0;
    const onScroll = () => {
      const y = window.scrollY;
      if (y > 60) nav.classList.add('is-scrolled');
      else nav.classList.remove('is-scrolled');
      lastY = y;
    };
    onScroll();
    window.addEventListener('scroll', onScroll, { passive: true });
  }

  /* ---------- Mobile menu ---------- */
  const toggle = document.querySelector('.nav-toggle');
  const body = document.body;
  if (toggle) {
    toggle.addEventListener('click', () => {
      body.classList.toggle('menu-open');
      const expanded = body.classList.contains('menu-open');
      toggle.setAttribute('aria-expanded', expanded);
    });
    document.querySelectorAll('.mobile-menu a').forEach(a => {
      a.addEventListener('click', () => {
        body.classList.remove('menu-open');
        toggle.setAttribute('aria-expanded', 'false');
      });
    });
  }

  /* ---------- Scroll reveal ---------- */
  if ('IntersectionObserver' in window && !window.matchMedia('(prefers-reduced-motion: reduce)').matches) {
    const reveals = document.querySelectorAll('.reveal');
    const io = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible');
          io.unobserve(entry.target);
        }
      });
    }, { threshold: 0.12, rootMargin: '0px 0px -60px 0px' });
    reveals.forEach(el => io.observe(el));
  } else {
    document.querySelectorAll('.reveal').forEach(el => el.classList.add('is-visible'));
  }

  /* ---------- Counter animation ---------- */
  const counters = document.querySelectorAll('[data-count]');
  if (counters.length && 'IntersectionObserver' in window) {
    const animate = (el) => {
      const target = parseInt(el.dataset.count, 10);
      const duration = 1400;
      const start = performance.now();
      const easeOut = t => 1 - Math.pow(1 - t, 3);
      const tick = (now) => {
        const t = Math.min((now - start) / duration, 1);
        const val = Math.floor(target * easeOut(t));
        el.textContent = val.toString();
        if (t < 1) requestAnimationFrame(tick);
        else el.textContent = target.toString();
      };
      requestAnimationFrame(tick);
    };
    const countIo = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          animate(entry.target);
          countIo.unobserve(entry.target);
        }
      });
    }, { threshold: 0.4 });
    counters.forEach(c => countIo.observe(c));
  }

  /* ---------- Smooth anchor scroll for in-page links ---------- */
  document.querySelectorAll('a[href^="#"]').forEach(a => {
    a.addEventListener('click', (e) => {
      const href = a.getAttribute('href');
      if (href.length > 1) {
        const target = document.querySelector(href);
        if (target) {
          e.preventDefault();
          const top = target.getBoundingClientRect().top + window.scrollY - 80;
          window.scrollTo({ top, behavior: 'smooth' });
        }
      }
    });
  });

  /* ---------- Form: basic client validation and demo submit ---------- */
  const form = document.querySelector('form[data-form="inquiry"]');
  if (form) {
    form.addEventListener('submit', (e) => {
      e.preventDefault();
      const required = form.querySelectorAll('[required]');
      let valid = true;
      required.forEach(field => {
        if (!field.value.trim()) {
          field.style.borderColor = '#c44';
          valid = false;
        } else {
          field.style.borderColor = '';
        }
      });
      if (!valid) return;
      const btn = form.querySelector('button[type="submit"]');
      const originalText = btn.textContent;
      btn.textContent = 'Sending...';
      btn.disabled = true;
      // In production, this should POST to the server-side handler.
      setTimeout(() => {
        form.innerHTML = '<div style="padding:40px 20px;text-align:center"><div style="font-family:var(--font-display);font-size:1.5rem;color:var(--ink);margin-bottom:12px;letter-spacing:-0.012em">Thank you.</div><p style="color:var(--slate);max-width:42ch;margin:0 auto">Your inquiry has been received. A member of our team will respond within one business day.</p></div>';
      }, 700);
    });
  }

  /* ---------- Subtle parallax on hero background ---------- */
  const heroBg = document.querySelector('.hero .hero-bg');
  if (heroBg && !window.matchMedia('(prefers-reduced-motion: reduce)').matches) {
    let ticking = false;
    const onParallax = () => {
      if (!ticking) {
        requestAnimationFrame(() => {
          const y = window.scrollY;
          if (y < window.innerHeight) {
            heroBg.style.transform = `translateY(${y * 0.25}px)`;
          }
          ticking = false;
        });
        ticking = true;
      }
    };
    window.addEventListener('scroll', onParallax, { passive: true });
  }

})();
