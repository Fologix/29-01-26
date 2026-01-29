/* app.js — TimeTravel Agency (vanilla JS)
   - Starfield canvas (hero background)
   - Reveal on scroll (IntersectionObserver)
   - Destinations: cards -> modal + prefill booking
   - Chatbot widget: simulated responses + destination context
   - Booking form: fake submit + validation + toast
*/

(() => {
  "use strict";

  // ---------- Helpers ----------
  const $ = (sel, root = document) => root.querySelector(sel);
  const $$ = (sel, root = document) => Array.from(root.querySelectorAll(sel));

  const sleep = (ms) => new Promise((r) => setTimeout(r, ms));

  function clamp(n, min, max) {
    return Math.max(min, Math.min(max, n));
  }

  function toast(msg, ms = 2600) {
    const el = $("#toast");
    if (!el) return;
    el.textContent = msg;
    el.classList.add("show");
    clearTimeout(toast._t);
    toast._t = setTimeout(() => el.classList.remove("show"), ms);
  }

  function smoothScrollTo(selector) {
    const target = $(selector);
    if (!target) return;
    target.scrollIntoView({ behavior: "smooth", block: "start" });
  }

  function formatDateFR(dateStr) {
    try {
      const d = new Date(dateStr);
      if (Number.isNaN(d.getTime())) return dateStr;
      return d.toLocaleDateString("fr-FR", { year: "numeric", month: "long", day: "numeric" });
    } catch {
      return dateStr;
    }
  }

  // ---------- Data ----------
  const DESTS = {
    paris1889: {
      name: "Paris 1889",
      short: "Belle Époque",
      vibe: "Culture & élégance",
      priceBase: 8900,
      duration: "2 à 4 jours (fenêtres courtes et idéales)",
      safety: "Niveau sécurité : élevé (zone urbaine, protocole discret, faible risque biologique).",
      tips: [
        "Exposition Universelle : accès premium, moments clés sélectionnés",
        "Tour Eiffel (construction / inauguration) : vue et itinéraires calibrés",
        "Tenue recommandée : élégante, discrète, accessoires d’époque fournis"
      ],
      opener: "Paris 1889 est une immersion raffinée : Belle Époque, Exposition Universelle et Tour Eiffel. Tu préfères culture, gastronomie ou architecture ?"
    },
    cretace: {
      name: "Crétacé (-65M)",
      short: "Nature sauvage",
      vibe: "Aventure & adrénaline",
      priceBase: 14900,
      duration: "4 à 8 heures (sessions ultra-encadrées)",
      safety: "Niveau sécurité : maximal (équipe renforcée, zones sécurisées, protocole d’extraction prioritaire).",
      tips: [
        "Observation faune : postes protégés, aucune interaction",
        "Écosystème : chaleur / humidité, équipement respiratoire selon zone",
        "Option aventure : parcours balisé + guide en binôme"
      ],
      opener: "Le Crétacé est l’expérience la plus rare : dinosaures, jungle, monde brut… mais 100% encadré. Tu cherches observation ou vraie aventure ?"
    },
    florence1504: {
      name: "Florence 1504",
      short: "Renaissance",
      vibe: "Art & patrimoine",
      priceBase: 9900,
      duration: "2 à 3 jours (itinéraires sur-mesure)",
      safety: "Niveau sécurité : élevé (protocole social + couverture discrète, risque modéré).",
      tips: [
        "Ateliers & art : immersion guidée, itinéraires validés",
        "Architecture : parcours Renaissance + points de vue exclusifs",
        "Tenue : sobre, conforme, accessoires fournis"
      ],
      opener: "Florence 1504, c’est la Renaissance à l’état pur : art, ateliers, architecture. Tu veux plutôt Michel-Ange, patrimoine ou ambiance de ville ?"
    }
  };

  const KEYWORDS = {
    price: ["prix", "budget", "tarif", "coût", "combien", "€", "euro"],
    duration: ["durée", "combien de temps", "jours", "heures", "séjour"],
    safety: ["sécurité", "risque", "danger", "protocole", "assurance"],
    culture: ["culture", "musée", "histoire", "patrimoine", "architecture", "expo"],
    adventure: ["aventure", "adrénaline", "dinos", "dino", "jungle", "survie"],
    art: ["art", "peinture", "sculpture", "renaissance", "michel", "atelier"],
    book: ["réserver", "reservation", "book", "dates", "partir", "retour"]
  };

  // ---------- App State ----------
  let currentDestKey = null;

  function setCurrentDestination(key, { from = "ui" } = {}) {
    if (!DESTS[key]) return;
    currentDestKey = key;

    // Sync select
    const select = $("#destSelect");
    if (select) select.value = key;

    // Update chat context label
    const ctx = $("#chatContext");
    if (ctx) {
      ctx.textContent = `${DESTS[key].name} — ${DESTS[key].vibe}`;
    }

    // Small toast
    if (from !== "init") toast(`Destination sélectionnée : ${DESTS[key].name}`);
  }

  function getDestOrFallback() {
    if (currentDestKey && DESTS[currentDestKey]) return DESTS[currentDestKey];
    return null;
  }

  // ---------- Reveal on scroll ----------
  function initReveal() {
    const els = $$(".reveal");
    if (!els.length) return;

    // Fallback if no IO
    if (!("IntersectionObserver" in window)) {
      els.forEach((el) => el.classList.add("is-visible"));
      return;
    }

    const io = new IntersectionObserver(
      (entries) => {
        for (const e of entries) {
          if (e.isIntersecting) {
            e.target.classList.add("is-visible");
            io.unobserve(e.target);
          }
        }
      },
      { root: null, threshold: 0.12 }
    );

    els.forEach((el) => io.observe(el));
  }

  // ---------- Modal ----------
  function initModal() {
    const modal = $("#destModal");
    if (!modal) return;

    const modalTitle = $("#modalTitle");
    const modalSub = $("#modalSub");
    const modalFacts = $("#modalFacts");
    const modalImg = $("#modalImg");

    const btnClose = $("#modalClose");
    const backdrop = $(".modal-backdrop", modal);

    const btnBook = $("#modalBook");
    const btnChat = $("#modalChat");

    function openModal(destKey, cardEl = null) {
      const d = DESTS[destKey];
      if (!d) return;

      setCurrentDestination(destKey);

      if (modalTitle) modalTitle.textContent = d.name;
      if (modalSub) modalSub.textContent = `${d.short} • ${d.vibe}`;

      if (modalFacts) {
        modalFacts.innerHTML = "";
        const items = [
          { k: "Durée conseillée", v: d.duration },
          { k: "Sécurité", v: d.safety },
          { k: "À ne pas rater", v: d.tips[0] },
          { k: "Conseil style", v: d.tips[2] }
        ];
        for (const it of items) {
          const div = document.createElement("div");
          div.className = "fact";
          div.innerHTML = `<b>${it.k}</b><span>${it.v}</span>`;
          modalFacts.appendChild(div);
        }
      }

      // Copy card thumbnail background if available
      if (modalImg) {
        if (cardEl) {
          const thumb = $(".thumb", cardEl);
          if (thumb) {
            const bg = getComputedStyle(thumb).backgroundImage;
            modalImg.style.backgroundImage = bg;
          }
        } else {
          // fallback: basic gradient
          modalImg.style.backgroundImage =
            "linear-gradient(120deg, rgba(214,178,94,0.12), rgba(126,205,255,0.08))";
        }
      }

      modal.classList.add("open");
      modal.setAttribute("aria-hidden", "false");

      // Lock scroll quickly
      document.documentElement.classList.add("modal-open");

      // Focus close for accessibility
      btnClose?.focus();
    }

    function closeModal() {
      modal.classList.remove("open");
      modal.setAttribute("aria-hidden", "true");
      document.documentElement.classList.remove("modal-open");
    }

    // Bind cards
    $$(".card[data-destination]").forEach((card) => {
      card.addEventListener("click", () => {
        const key = card.getAttribute("data-destination");
        card.classList.add("selected");
        setTimeout(() => card.classList.remove("selected"), 450);
        openModal(key, card);
      });
    });

    btnClose?.addEventListener("click", closeModal);
    backdrop?.addEventListener("click", (e) => {
      if (e.target && e.target.dataset.close === "true") closeModal();
    });

    // ESC closes
    window.addEventListener("keydown", (e) => {
      if (e.key === "Escape" && modal.classList.contains("open")) closeModal();
    });

    btnBook?.addEventListener("click", () => {
      closeModal();
      smoothScrollTo("#reservation");
      // focus select after scroll
      setTimeout(() => $("#destSelect")?.focus(), 350);
    });

    btnChat?.addEventListener("click", () => {
      closeModal();
      openChat();
      // opener message for current destination
      const d = getDestOrFallback();
      if (d) pushBot(d.opener);
    });

    // Expose for other parts
    initModal.openModal = openModal;
    initModal.closeModal = closeModal;
  }

  // ---------- Chatbot ----------
  const chat = {
    panel: null,
    body: null,
    input: null
  };

  function pushMsg(text, who = "bot") {
    if (!chat.body) return;
    const row = document.createElement("div");
    row.className = `msg ${who}`;
    row.innerHTML = `<div class="bubble">${escapeHtml(text).replace(/\n/g, "<br>")}</div>`;
    chat.body.appendChild(row);
    chat.body.scrollTop = chat.body.scrollHeight;
  }

  function pushBot(text) {
    pushMsg(text, "bot");
  }

  function pushUser(text) {
    pushMsg(text, "user");
  }

  function escapeHtml(str) {
    return String(str)
      .replaceAll("&", "&amp;")
      .replaceAll("<", "&lt;")
      .replaceAll(">", "&gt;")
      .replaceAll('"', "&quot;")
      .replaceAll("'", "&#039;");
  }

  function openChat() {
    if (!chat.panel) chat.panel = $("#chatPanel");
    if (!chat.panel) return;

    chat.panel.classList.add("open");
    chat.panel.setAttribute("aria-hidden", "false");
    $("#chatFab")?.classList.add("hidden");

    setTimeout(() => chat.input?.focus(), 120);
  }

  function closeChat() {
    if (!chat.panel) return;
    chat.panel.classList.remove("open");
    chat.panel.setAttribute("aria-hidden", "true");
    $("#chatFab")?.classList.remove("hidden");
  }

  function detectIntent(t) {
    const s = t.toLowerCase();
    for (const [intent, words] of Object.entries(KEYWORDS)) {
      if (words.some((w) => s.includes(w))) return intent;
    }
    return "general";
  }

  function priceFor(destKey, startDate, endDate) {
    const d = DESTS[destKey];
    if (!d) return null;

    // Light heuristic: adjust by days
    let days = 3;
    if (startDate && endDate) {
      const a = new Date(startDate);
      const b = new Date(endDate);
      if (!Number.isNaN(a.getTime()) && !Number.isNaN(b.getTime())) {
        const diff = Math.ceil((b - a) / (1000 * 60 * 60 * 24));
        days = clamp(diff || 3, 1, 7);
      }
    }

    const multiplier = 1 + (days - 2) * 0.12; // +12% per day after 2
    const base = Math.round(d.priceBase * multiplier);
    return base;
  }

  function botReply(userText) {
    const d = getDestOrFallback();

    // If no destination selected, gently guide
    if (!d) {
      const intent = detectIntent(userText);
      if (intent === "price") {
        return "Avant de parler budget, choisis une destination (Paris 1889, Crétacé, Florence 1504). Tu veux laquelle ?";
      }
      return "Je peux te guider 🙂 Choisis une destination (Paris 1889, Crétacé, Florence 1504) ou clique une carte, et je m’adapte.";
    }

    const intent = detectIntent(userText);
    const start = $("#startDate")?.value;
    const end = $("#endDate")?.value;

    switch (intent) {
      case "price": {
        const p = priceFor(currentDestKey, start, end);
        const rangeMin = Math.round(p * 0.92);
        const rangeMax = Math.round(p * 1.08);
        return (
          `Pour ${d.name}, on est sur un budget premium cohérent : ` +
          `**~${rangeMin.toLocaleString("fr-FR")}€ à ${rangeMax.toLocaleString("fr-FR")}€** (simulation).\n` +
          `Ça inclut conciergerie, kit d’époque, et protocole de sécurité.\n` +
          `Tu veux un focus plutôt ${d.vibe.toLowerCase()} ?`
        ).replaceAll("**", ""); // keep simple if CSS doesn't style markdown
      }
      case "duration":
        return `Durée conseillée pour ${d.name} : ${d.duration}.\nOn peut ajuster selon tes contraintes, mais on privilégie des fenêtres courtes et propres.`;
      case "safety":
        return `${d.safety}\nRègle d’or : discrétion + aucun impact sur les événements. Tu veux une version “tranquille” ou “immersive” ?`;
      case "culture":
        return `Parfait. Pour ${d.name}, je te recommande un parcours “culture” : ${d.tips[0]}.\nJe peux aussi te proposer un itinéraire à 3 étapes si tu me dis ton niveau (curieux / passionné).`;
      case "adventure":
        return `Ok, mode aventure. Pour ${d.name} : ${d.tips[1]}.\nJe te pose juste une question : tu veux observation safe ou adrénaline encadrée ?`;
      case "art":
        return `Carrément. Pour ${d.name}, l’axe “art & patrimoine” est top : ${d.tips[0]}.\nTu es plus peinture, sculpture, ou architecture ?`;
      case "book":
        return `Yes. Tu peux remplir le formulaire en bas : destination + dates.\nSi tu me dis tes dates ici, je te conseille aussi le meilleur format de séjour.`;
      default:
        return `Pour ${d.name} : je peux te conseiller sur le programme, la sécurité, le budget et la durée.\nDis-moi juste ce qui t’intéresse le plus (culture / aventure / art / budget).`;
    }
  }

  function initChat() {
    chat.panel = $("#chatPanel");
    chat.body = $("#chatBody");
    chat.input = $("#chatInput");

    const fab = $("#chatFab");
    const close = $("#chatClose");
    const send = $("#chatSend");

    if (!chat.panel || !chat.body || !chat.input) return;

    fab?.addEventListener("click", () => {
      openChat();
      if (!chat.body.childElementCount) {
        pushBot("Bonjour, je suis l’agent virtuel de TimeTravel Agency.\nClique une destination (ou dis-moi celle que tu veux) et je te conseille.");
      }
    });

    $("#btnChatOpen")?.addEventListener("click", () => {
      openChat();
      if (!chat.body.childElementCount) {
        pushBot("Bonjour 🙂 Je suis ton concierge historique.\nTu veux Paris 1889, le Crétacé, ou Florence 1504 ?");
      } else {
        const d = getDestOrFallback();
        if (d) pushBot(d.opener);
      }
    });

    close?.addEventListener("click", closeChat);

    // ESC closes chat too
    window.addEventListener("keydown", (e) => {
      if (e.key === "Escape" && chat.panel.classList.contains("open")) closeChat();
    });

    async function handleSend() {
      const text = chat.input.value.trim();
      if (!text) return;
      chat.input.value = "";
      pushUser(text);

      // simulate "thinking"
      await sleep(250);

      // If user typed a destination name, set it
      const low = text.toLowerCase();
      if (low.includes("paris")) setCurrentDestination("paris1889");
      else if (low.includes("crétacé") || low.includes("cretace") || low.includes("dino")) setCurrentDestination("cretace");
      else if (low.includes("florence") || low.includes("renaissance")) setCurrentDestination("florence1504");

      pushBot(botReply(text));
    }

    send?.addEventListener("click", handleSend);
    chat.input.addEventListener("keydown", (e) => {
      if (e.key === "Enter") handleSend();
    });

    // From booking section button
    $("#btnSuggestChat")?.addEventListener("click", () => {
      openChat();
      const sel = $("#destSelect")?.value;
      if (sel && DESTS[sel]) {
        setCurrentDestination(sel);
        pushBot(`Parfait. ${DESTS[sel].opener}`);
      } else {
        pushBot("Dis-moi la destination qui t’attire le plus, et je te propose un format de voyage.");
      }
    });
  }

  // ---------- Booking Form ----------
  function initBooking() {
    const form = $("#bookingForm");
    if (!form) return;

    const select = $("#destSelect");
    const start = $("#startDate");
    const end = $("#endDate");
    const notes = $("#notes");

    // Keep destination in sync if user selects manually
    select?.addEventListener("change", () => {
      if (select.value) setCurrentDestination(select.value);
    });

    // Simple date constraints
    const today = new Date();
    const pad = (n) => String(n).padStart(2, "0");
    const isoToday = `${today.getFullYear()}-${pad(today.getMonth() + 1)}-${pad(today.getDate())}`;
    if (start) start.min = isoToday;
    if (end) end.min = isoToday;

    start?.addEventListener("change", () => {
      if (end && start.value) end.min = start.value;
    });

    form.addEventListener("submit", (e) => {
      e.preventDefault();

      const destKey = select?.value || "";
      if (!DESTS[destKey]) {
        toast("Choisis une destination 🙂");
        select?.focus();
        return;
      }

      const a = start?.value;
      const b = end?.value;
      if (!a || !b) {
        toast("Choisis des dates de départ / retour.");
        (!a ? start : end)?.focus();
        return;
      }

      const da = new Date(a);
      const db = new Date(b);
      if (db < da) {
        toast("La date de retour doit être après la date de départ.");
        end?.focus();
        return;
      }

      setCurrentDestination(destKey);

      const pref = (notes?.value || "").trim();
      const p = priceFor(destKey, a, b);
      const d = DESTS[destKey];

      toast("Demande enregistrée (simulation) ✅");

      // Optional: also push a chat suggestion
      const summary =
        `Demande reçue (simulation) :\n` +
        `• Destination : ${d.name}\n` +
        `• Départ : ${formatDateFR(a)}\n` +
        `• Retour : ${formatDateFR(b)}\n` +
        (pref ? `• Préférence : ${pref}\n` : "") +
        `• Estimation : ~${p.toLocaleString("fr-FR")}€`;

      // If chat is open, show summary there too
      const panel = $("#chatPanel");
      if (panel && panel.classList.contains("open")) {
        pushBot(summary);
        pushBot("Tu veux que je te propose un itinéraire en 3 étapes selon ta préférence ?");
      }

      // Reset light (keep destination)
      if (notes) notes.value = "";
    });
  }

  // ---------- Smooth anchor / CTA ----------
  function initNavigation() {
    // Smooth scroll for internal anchors
    $$('a[href^="#"]').forEach((a) => {
      a.addEventListener("click", (e) => {
        const href = a.getAttribute("href");
        if (!href || href.length < 2) return;
        const target = $(href);
        if (!target) return;
        e.preventDefault();
        smoothScrollTo(href);
      });
    });

    $("#btnDiscover")?.addEventListener("click", (e) => {
      e.preventDefault();
      smoothScrollTo("#destinations");
    });
  }

  // ---------- Starfield Canvas ----------
  function initStarfield() {
    const canvas = $("#starfield");
    if (!canvas) return;
    const ctx = canvas.getContext("2d", { alpha: true });
    if (!ctx) return;

    let w = 0, h = 0, dpr = 1;
    let stars = [];
    let rafId = null;

    function resize() {
      const rect = canvas.getBoundingClientRect();
      dpr = Math.max(1, Math.min(2, window.devicePixelRatio || 1));
      w = Math.floor(rect.width);
      h = Math.floor(rect.height);
      canvas.width = Math.floor(w * dpr);
      canvas.height = Math.floor(h * dpr);
      ctx.setTransform(dpr, 0, 0, dpr, 0, 0);

      const count = clamp(Math.floor((w * h) / 12000), 60, 220);
      stars = Array.from({ length: count }, () => ({
        x: Math.random() * w,
        y: Math.random() * h,
        r: Math.random() * 1.6 + 0.2,
        v: Math.random() * 0.55 + 0.15
      }));
    }

    function tick() {
      ctx.clearRect(0, 0, w, h);

      // subtle vignette
      const g = ctx.createRadialGradient(w * 0.5, h * 0.35, 20, w * 0.5, h * 0.5, Math.max(w, h) * 0.7);
      g.addColorStop(0, "rgba(214, 178, 94, 0.04)");
      g.addColorStop(1, "rgba(0,0,0,0)");
      ctx.fillStyle = g;
      ctx.fillRect(0, 0, w, h);

      // stars
      ctx.fillStyle = "rgba(255,255,255,0.85)";
      for (const s of stars) {
        s.y += s.v;
        if (s.y > h + 10) {
          s.y = -10;
          s.x = Math.random() * w;
        }
        ctx.globalAlpha = clamp(0.25 + s.r / 2.2, 0.25, 0.9);
        ctx.beginPath();
        ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
        ctx.fill();
      }
      ctx.globalAlpha = 1;

      rafId = requestAnimationFrame(tick);
    }

    // pause on hidden tab
    document.addEventListener("visibilitychange", () => {
      if (document.hidden) {
        if (rafId) cancelAnimationFrame(rafId);
        rafId = null;
      } else if (!rafId) {
        tick();
      }
    });

    window.addEventListener("resize", resize, { passive: true });

    resize();
    tick();
  }

  // ---------- Init ----------
  function init() {
    document.body.classList.add("js");
    initReveal();
    initNavigation();
    initModal();
    initChat();
    initBooking();
    initStarfield();

    // Default destination = Paris (optional)
    setCurrentDestination("paris1889", { from: "init" });

    // welcome toast once
    setTimeout(() => toast("Bienvenue chez TimeTravel Agency ✦"), 400);
  }

  // Run when DOM ready
  if (document.readyState === "loading") {
    document.addEventListener("DOMContentLoaded", init);
  } else {
    init();
  }
})();
