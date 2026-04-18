<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
  <title>Project Escape</title>
  <style>

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background-color: #fafaf9;
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
      line-height: 1.5;
      color: #1a1a1a;
    }

    .site-wrapper {
      max-width: 1280px;
      margin: 0 auto;
      padding: 1.8rem 2rem 3rem;
    }

    /* ---------- MINI TAB (UPPER LEFT) - HOT / COLD / ABOUT / CONTACT / BRANCHES ---------- */
    .mini-tab {
      position: fixed;
      top: 24px;
      left: 24px;
      background: #121212;
      border-radius: 56px;
      padding: 0.45rem;
      box-shadow: 0 12px 24px rgba(0, 0, 0, 0.08);
      display: flex;
      flex-wrap: wrap;
      gap: 0.3rem;
      z-index: 100;
      transition: all 0.25s ease;
    }

    .mini-tab:hover {
      background: #1a2128;
      box-shadow: 0 16px 28px rgba(0, 0, 0, 0.12);
    }

    .tab-item {
      padding: 0.55rem 1.25rem;
      border-radius: 48px;
      background: transparent;
      color: #eef2f5;
      font-size: 0.85rem;
      font-weight: 490;
      letter-spacing: 0.01em;
      border: none;
      cursor: pointer;
      transition: all 0.22s cubic-bezier(0.2, 0.9, 0.4, 1.1);
      white-space: nowrap;
    }

    .tab-item:hover {
      background: #2d3a44;
      color: white;
      transform: translateY(-1px);
    }

    .tab-item.active {
      background: #eef2f5;
      color: #0a1922;
      font-weight: 580;
      box-shadow: inset 0 0 0 0.5px rgba(0,0,0,0.04);
    }

    /* mobile responsive */
    @media (max-width: 760px) {
      .mini-tab {
        position: relative;
        top: 0;
        left: 0;
        margin-bottom: 2rem;
        justify-content: center;
        flex-wrap: wrap;
        border-radius: 48px;
      }
      .site-wrapper {
        padding-top: 0.8rem;
      }
      .tab-item {
        padding: 0.45rem 1rem;
        font-size: 0.78rem;
      }
    }

    /* brand header */
    .brand {
      margin-top: 0.6rem;
      margin-bottom: 2rem;
      border-bottom: 1px solid #dadce0;
      padding-bottom: 1.2rem;
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      flex-wrap: wrap;
      gap: 0.8rem;
    }

    .brand h1 {
      font-size: 2.1rem;
      font-weight: 360;
      letter-spacing: -0.02em;
      color: #161616;
      text-transform: uppercase;
    }

    .brand span {
      font-weight: 580;
      background: #1a2c3e;
      color: #f5f7f9;
      padding: 0.2rem 0.9rem;
      font-size: 0.85rem;
      border-radius: 32px;
    }

    .section-label {
      display: flex;
      align-items: baseline;
      margin-bottom: 1.8rem;
    }

    .section-label h2 {
      font-weight: 420;
      font-size: 1.65rem;
      color: #2b2b2b;
      border-left: 5px solid #1a2c3e;
      padding-left: 1rem;
    }

    /* ---------- PRODUCT GRID ---------- */
    .product-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 2rem 1.8rem;
      margin-bottom: 3rem;
    }

    .drink-card {
      background: #ffffff;
      border: 1px solid #e5e8ec;
      border-radius: 28px;
      padding: 1.5rem 1rem 1.4rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      transition: transform 0.25s ease, border-color 0.25s, box-shadow 0.3s, opacity 0.25s ease;
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.02);
      opacity: 1;
    }

    /* filtering transition — seamless hide/show */
    .drink-card.hide-drink {
      display: none;
    }

    .drink-card:hover {
      transform: translateY(-6px);
      border-color: #9aaebf;
      box-shadow: 0 22px 30px -14px rgba(0, 0, 0, 0.1);
    }

    /* ===== PRODUCT PICTURE PLACEHOLDER ===== */
    /* Replace background-image with actual product images */
    .drink-img {
      width: 88px;
      height: 88px;
      border-radius: 50%;
      background: #eef2f5;
      margin-bottom: 1rem;
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.2s;
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
      background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="44" height="44" viewBox="0 0 44 44"><circle cx="22" cy="22" r="9" fill="%23cbd5e1" /></svg>');
    }
    /* INSTRUCTION: to add product images, set background-image on each .drink-img 
       Example: document.querySelectorAll('.drink-img')[0].style.backgroundImage = "url('espresso.jpg')"; */

    .drink-name {
      font-size: 1.3rem;
      font-weight: 530;
      color: #171717;
      margin-bottom: 0.2rem;
    }

    .drink-desc {
      font-size: 0.78rem;
      color: #52606b;
      margin-bottom: 1rem;
      text-transform: uppercase;
      letter-spacing: 0.06em;
      font-weight: 380;
    }

    .price {
      font-weight: 560;
      background: #f1f3f6;
      padding: 0.3rem 1.2rem;
      border-radius: 60px;
      color: #1e2e3a;
      font-size: 0.95rem;
      border: 0.5px solid #d0d8e0;
      transition: all 0.2s;
    }

    .drink-card:hover .price {
      background: #1a2c3e;
      color: white;
      border-color: #1a2c3e;
    }

    /* company section */
    .company-section {
      margin-top: 2.5rem;
      border-top: 1px solid #cdd3d9;
      padding-top: 2rem;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 2rem;
    }

    .about-block, .branches-block {
      background: #ffffff;
      border-radius: 24px;
      padding: 1.7rem 1.9rem;
      border: 1px solid #e2e6ea;
      transition: all 0.2s;
    }

    .about-block:hover, .branches-block:hover {
      background: #fcfdfe;
      border-color: #b9c6d2;
    }

    .block-title {
      font-size: 1.2rem;
      font-weight: 560;
      color: #121212;
      margin-bottom: 0.9rem;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .company-desc {
      color: #2c3e4e;
      margin-bottom: 0.7rem;
      font-size: 0.95rem;
      line-height: 1.45;
    }

    .branch-list {
      list-style: none;
    }

    .branch-list li {
      padding: 0.45rem 0;
      border-bottom: 0.5px dashed #cbd5e1;
      font-size: 0.94rem;
      display: flex;
      gap: 10px;
      color: #1f2d38;
    }

    .branch-list li:last-child {
      border-bottom: none;
    }

    .contact-details {
      margin-top: 2rem;
      background: #ffffff;
      padding: 1.2rem 1.8rem;
      border-radius: 44px;
      border: 1px solid #dee3e9;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      align-items: center;
      gap: 1rem;
      transition: all 0.2s;
    }

    .contact-details:hover {
      border-color: #b1c0cd;
      background: #fefefe;
    }

    .contact-item {
      display: flex;
      align-items: center;
      gap: 8px;
      color: #1d2c38;
      font-weight: 440;
      font-size: 0.9rem;
    }

    .contact-item span {
      background: #eef2f6;
      border-radius: 100%;
      width: 32px;
      height: 32px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      font-size: 1rem;
      color: #1a2c3e;
    }

    .footnote {
      text-align: center;
      color: #6b7a86;
      font-size: 0.75rem;
      margin-top: 3rem;
      letter-spacing: 0.6px;
    }

    html {
      scroll-behavior: smooth;
    }

    @media (max-width: 780px) {
      .company-section {
        grid-template-columns: 1fr;
        gap: 1.5rem;
      }
      .brand h1 {
        font-size: 1.7rem;
      }
    }

    /* background image instruction */
    /* ===== BACKGROUND IMAGE: add to body if needed 
       body { background-image: url('your-bg.jpg'); background-size: cover; } */
  </style>
</head>
<body>
  <div class="site-wrapper">

    <!-- MINI TAB: HOT / COLD + About / Contact / Branches (all functional) -->
    <div class="mini-tab" id="tabContainer">
      <button class="tab-item" data-filter="hot">HOT</button>
      <button class="tab-item" data-filter="cold">COLD</button>
      <button class="tab-item" data-scroll="about">ABOUT</button>
      <button class="tab-item" data-scroll="contact">CONTACT</button>
      <button class="tab-item" data-scroll="branches">BRANCHES</button>
    </div>

    <!-- brand header -->
    <div class="brand">
      <p><h1>Project Escape <span>COFFEE</span></h1></p>
      <div style="color:#5a6e7c;">est. 2025</div>
    </div>

    <!-- DRINKS SECTION -->
    <div class="section-label" id="drinks-section">
      <h2>DRINKS — hot & cold menu</h2>
    </div>

    <div class="product-grid" id="drinksGrid">
      <!-- ========= HOT BEVERAGES ========= -->
      <div class="drink-card" data-category="hot">
        <div class="drink-img"></div>
        <div class="drink-name">ESPRESSO</div>
        <div class="drink-desc">single origin · bold</div>
        <span class="price">$3.20</span>
      </div>
      <div class="drink-card" data-category="hot">
        <div class="drink-img"></div>
        <div class="drink-name">AMERICANO</div>
        <div class="drink-desc">smooth · black</div>
        <span class="price">$3.80</span>
      </div>
      <div class="drink-card" data-category="hot">
        <div class="drink-img"></div>
        <div class="drink-name">FLAT WHITE</div>
        <div class="drink-desc">velvety · double shot</div>
        <span class="price">$4.80</span>
      </div>
      <div class="drink-card" data-category="hot">
        <div class="drink-img"></div>
        <div class="drink-name">LATTE</div>
        <div class="drink-desc">creamy · steamed milk</div>
        <span class="price">$4.90</span>
      </div>
      <div class="drink-card" data-category="hot">
        <div class="drink-img"></div>
        <div class="drink-name">CAPPUCCINO</div>
        <div class="drink-desc">foam · cinnamon dust</div>
        <span class="price">$4.60</span>
      </div>
      <div class="drink-card" data-category="hot">
        <div class="drink-img"></div>
        <div class="drink-name">MOCHA</div>
        <div class="drink-desc">dark chocolate · espresso</div>
        <span class="price">$5.20</span>
      </div>
      <div class="drink-card" data-category="hot">
        <div class="drink-img"></div>
        <div class="drink-name">HOT POUR OVER</div>
        <div class="drink-desc">single origin · filter</div>
        <span class="price">$4.50</span>
      </div>
      
      <!-- ========= COLD BEVERAGES ========= -->
      <div class="drink-card" data-category="cold">
        <div class="drink-img"></div>
        <div class="drink-name">COLD BREW</div>
        <div class="drink-desc">12hr steep · smooth</div>
        <span class="price">$4.40</span>
      </div>
      <div class="drink-card" data-category="cold">
        <div class="drink-img"></div>
        <div class="drink-name">ICED LATTE</div>
        <div class="drink-desc">espresso · chilled milk</div>
        <span class="price">$4.90</span>
      </div>
      <div class="drink-card" data-category="cold">
        <div class="drink-img"></div>
        <div class="drink-name">ICED AMERICANO</div>
        <div class="drink-desc">refreshing · bold</div>
        <span class="price">$3.90</span>
      </div>
      <div class="drink-card" data-category="cold">
        <div class="drink-img"></div>
        <div class="drink-name">NITRO COLD BREW</div>
        <div class="drink-desc">creamy · nitro infusion</div>
        <span class="price">$5.00</span>
      </div>
      <div class="drink-card" data-category="cold">
        <div class="drink-img"></div>
        <div class="drink-name">ICED MATCHA LATTE</div>
        <div class="drink-desc">ceremonial · oat milk</div>
        <span class="price">$5.30</span>
      </div>
      <div class="drink-card" data-category="cold">
        <div class="drink-img"></div>
        <div class="drink-name">FROZEN MOCHA</div>
        <div class="drink-desc">blended · chocolate</div>
        <span class="price">$5.50</span>
      </div>
    </div>

    <!-- ABOUT / COMPANY / BRANCHES sections -->
    <div class="company-section" id="companyInfo">
      <div class="about-block" id="aboutBlock">
        <div class="block-title">
          <i>⚫</i> ABOUT THE CAFE
        </div>
        <div class="company-desc">
          wala pa ko malagay hehe sample palang to.
        </div>
        <div class="company-desc" style="border-left: 3px solid #1a2c3e; padding-left: 1rem; margin-top: 0.8rem;">
          “Founded in blah blah.”
        </div>
      </div>
      <div class="branches-block" id="branchesBlock">
        <div class="block-title">
          <i>◉</i> OTHER BRANCHES
        </div>
        <ul class="branch-list">
          <li><span class="branch-icon">◈</span> blah blah · pelepens</li>
          <li><span class="branch-icon">◈</span> blah blah · hatdog</li>
          <li><span class="branch-icon">◈</span> blep · antipolo</li>
          <li><span class="branch-icon">◈</span> bleep · olfu?</li>
          <li><span class="branch-icon">◈</span> beeeppp · sumulong</li>
        </ul>
        <div style="margin-top: 1rem; font-size: 0.85rem; color: #4f6573; border-top: 0.5px solid #cbdae3; padding-top: 0.8rem;">
          each cafe independent · same roast
        </div>
      </div>
    </div>

    <!-- CONTACT DETAILS block -->
    <div class="contact-details" id="contactBlock">
      <div class="contact-item">
        <span>☎</span> +1 (212) 555 3730
      </div>
      <div class="contact-item">
        <span>✉</span> projectescape.coffee
      </div>
      <div class="contact-item">
        <span>📍</span> 311 W BROADWAY · NYC
      </div>
      <div class="contact-item">
        <span>⏱</span> 7am – 5pm daily
      </div>
    </div>

    <div class="footnote">
      FILTER · POUR OVER · SIPHON — ALL DAY GRAYS
    </div>
  </div>

  <script>
    (function() {
      "use strict";

      // DOM elements
      const allTabs = document.querySelectorAll('.tab-item');
      const filterTabs = document.querySelectorAll('.tab-item[data-filter]');  // HOT / COLD
      const scrollTabs = document.querySelectorAll('.tab-item[data-scroll]'); // ABOUT, CONTACT, BRANCHES
      const drinkCards = document.querySelectorAll('.drink-card');

      // Helper: remove active class from all tabs
      function removeActiveClasses() {
        allTabs.forEach(tab => tab.classList.remove('active'));
      }

      // ----- FILTERING FUNCTION (HOT or COLD) seamless -----
      function filterDrinks(category) {
        drinkCards.forEach(card => {
          const cardCategory = card.getAttribute('data-category');
          if (category === 'all') {
            card.classList.remove('hide-drink');
          } else {
            if (cardCategory === category) {
              card.classList.remove('hide-drink');
            } else {
              card.classList.add('hide-drink');
            }
          }
        });
      }

      // ----- SMOOTH SCROLL with offset (clean, no overlap) -----
      function smoothScrollToElement(elementId, offset = 70) {
        const targetElement = document.getElementById(elementId);
        if (!targetElement) return;
        const elementPosition = targetElement.getBoundingClientRect().top + window.pageYOffset;
        const offsetPosition = elementPosition - offset;
        window.scrollTo({
          top: offsetPosition,
          behavior: 'smooth'
        });
      }

      // ----- HANDLE FILTER BUTTONS (HOT and COLD) -----
      filterTabs.forEach(tab => {
        tab.addEventListener('click', function(e) {
          e.preventDefault();
          const filterValue = this.getAttribute('data-filter'); // 'hot' or 'cold'
          
          // update active class for filter tabs
          removeActiveClasses();
          this.classList.add('active');
          
          // apply filtering — show only drinks matching category
          filterDrinks(filterValue);
        });
      });

      // ----- HANDLE SCROLL BUTTONS (ABOUT, CONTACT, BRANCHES) -----
      scrollTabs.forEach(tab => {
        tab.addEventListener('click', function(e) {
          e.preventDefault();
          const scrollTarget = this.getAttribute('data-scroll'); // 'about', 'contact', 'branches'
          
          // update active class
          removeActiveClasses();
          this.classList.add('active');
          
          let targetId = '';
          if (scrollTarget === 'about') targetId = 'aboutBlock';
          else if (scrollTarget === 'contact') targetId = 'contactBlock';
          else if (scrollTarget === 'branches') targetId = 'branchesBlock';
          
          if (targetId) {
            smoothScrollToElement(targetId, 70);
          }
        });
      });

      // ----- Set default state: show HOT drinks by default (active HOT tab) -----
      function setDefaultState() {
        const defaultHotBtn = document.querySelector('.tab-item[data-filter="hot"]');
        if (defaultHotBtn) {
          removeActiveClasses();
          defaultHotBtn.classList.add('active');
          filterDrinks('hot');   // initially only hot beverages visible
        } else {
          filterDrinks('hot');
        }
      }

      // Ensure that when clicking scroll buttons, filter tabs lose active style, and vice versa
      filterTabs.forEach(btn => {
        btn.addEventListener('click', () => {
          scrollTabs.forEach(scrollTab => scrollTab.classList.remove('active'));
        });
      });
      
      scrollTabs.forEach(btn => {
        btn.addEventListener('click', () => {
          filterTabs.forEach(filterBtn => filterBtn.classList.remove('active'));
        });
      });

      // initialize: show HOT drinks on page load
      setDefaultState();
      
      // console log for check
      console.log('Seamless HOT/COLD filter active — transition smooth');
    })();
  </script>
</body>
</html>
