<script>
  import { fade } from "svelte/transition";

  let isOpen = false;

  const toggleMenu = () => {
    isOpen = !isOpen;
  };

  const scrollToSection = (event, id) => {
    event.preventDefault();

    const element = document.querySelector(id);
    if (!element) return;

    const offset = 80;
    const topPos =
      element.getBoundingClientRect().top + window.pageYOffset - offset;

    window.scrollTo({ top: topPos, behavior: "smooth" });

    isOpen = false;
  };

  const handleKeydown = (event) => {
    if (event.key === "Enter" || event.key === " ") {
      toggleMenu();
    }
  };
</script>

<nav class="navbar">
  <div class="nav-container">
    <a href="/" class="logo">
      <img
        src="https://www.svgrepo.com/show/513636/heart.svg"
        alt="Heart"
        class="logo-heart"
      />
      lucía.dev
    </a>

    <button
      class="hamburger"
      class:active={isOpen}
      on:click={toggleMenu}
      aria-label="Menu"
      aria-expanded={isOpen}
      aria-controls="mobile-menu"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="26"
        height="26"
        viewBox="0 0 24 24"
        fill="none"
        stroke="#fff"
        stroke-width="3"
        stroke-linecap="round"
        stroke-linejoin="round"
      >
        {#if isOpen}
          <line x1="18" y1="6" x2="6" y2="18" />
          <line x1="6" y1="6" x2="18" y2="18" />
        {:else}
          <line x1="3" y1="7" x2="21" y2="7" />
          <line x1="3" y1="12" x2="21" y2="12" />
          <line x1="3" y1="17" x2="21" y2="17" />
        {/if}
      </svg>
    </button>

    <ul class="nav-links desktop">
      <li>
        <a href="#home" on:click={(e) => scrollToSection(e, "#home")}>Home</a>
      </li>
      <li>
        <a href="#about" on:click={(e) => scrollToSection(e, "#about")}
          >About me</a
        >
      </li>
      <li>
        <a
          href="#technologies"
          on:click={(e) => scrollToSection(e, "#technologies")}>Technologies</a
        >
      </li>
      <li>
        <a href="#projects" on:click={(e) => scrollToSection(e, "#projects")}
          >Projects</a
        >
      </li>
      <li>
        <a
          href="#contact"
          on:click={(e) => scrollToSection(e, "#contact")}
          class="contact-link">Contact</a
        >
      </li>
    </ul>
  </div>

  {#if isOpen}
    <div
      id="mobile-menu"
      class="mobile-menu-overlay"
      on:click={toggleMenu}
      on:keydown={handleKeydown}
      role="button"
      tabindex="0"
      transition:fade
    >
      <div
        class="mobile-menu-container"
        on:click|stopPropagation
        on:keydown|stopPropagation
      >
        <ul class="nav-links mobile" transition:fade={{ duration: 200 }}>
          <li>
            <a href="#home" on:click={(e) => scrollToSection(e, "#home")}
              >Home</a
            >
          </li>
          <li>
            <a href="#about" on:click={(e) => scrollToSection(e, "#about")}
              >About me</a
            >
          </li>
          <li>
            <a
              href="#technologies"
              on:click={(e) => scrollToSection(e, "#technologies")}
              >Technologies</a
            >
          </li>
          <li>
            <a
              href="#projects"
              on:click={(e) => scrollToSection(e, "#projects")}>Projects</a
            >
          </li>
          <li>
            <a
              href="#contact"
              on:click={(e) => scrollToSection(e, "#contact")}
              class="contact-link">Contact</a
            >
          </li>
        </ul>
      </div>
    </div>
  {/if}
</nav>

<style>
  .navbar {
    background-color: #060211;
    padding: 1rem 2rem;
    position: sticky;
    top: 0;
    z-index: 1000;
    border-bottom: 1px solid rgba(16, 15, 35, 0.97);
    font-family: "Favorit", sans-serif;
  }

  .nav-container {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    width: 100%;
    justify-content: space-between;
    align-items: center;
  }

  .logo {
    font-size: 1.4rem;
    font-weight: 600;
    letter-spacing: 0.5px;
    color: #ffffff;
    text-decoration: none;
    display: flex;
    align-items: center;
    gap: 0.4rem;
    transition: opacity 0.3s ease;
  }

  .logo:hover {
    opacity: 0.8;
  }

  .logo-heart {
    width: 20px;
    height: 20px;
    filter: invert(1) brightness(2);
  }

  .nav-links {
    list-style: none;
    display: flex;
    gap: 2rem;
    margin: 0;
    padding: 0;
  }

  .nav-links li {
    margin: 0;
  }

  .nav-links a {
    color: #b5bac1;
    text-decoration: none;
    font-size: 15px;
    font-weight: 400;
    padding: 8px 16px;
    border-radius: 12px;
    transition: all 0.3s ease;
    display: block;
  }

  .nav-links a:hover {
    color: #9d4edd;
    background-color: rgba(157, 78, 221, 0.1);
    transform: translateY(-1px);
  }

  .contact-link {
    background-color: #9d4edd;
    color: white !important;
    padding: 8px 18px !important;
    border-radius: 16px !important;
    font-weight: 500 !important;
    transition: all 0.3s ease;
    box-shadow: 0 2px 8px rgba(157, 78, 221, 0.2);
    text-align: center;
  }

  .contact-link:hover {
    background-color: #7b2cbf !important;
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(157, 78, 221, 0.3);
  }

  .hamburger {
    display: none;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    padding: 5px;
    border-radius: 12px;
    transition: all 0.3s ease;
    color: #fff;
    cursor: pointer;
    align-items: center;
    justify-content: center;
    position: relative;
    z-index: 1101;
  }

  .hamburger:hover {
    background-color: rgba(255, 255, 255, 0.1);
  }

  .hamburger.active {
    background-color: rgba(65, 20, 59, 0.85);
    border-color: rgba(255, 255, 255, 0.189);
  }

  .mobile-menu-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    justify-content: center;
    align-items: flex-start;
    padding-top: 70px;
    z-index: 1100;
    background: rgba(22, 22, 35, 0.7);
    backdrop-filter: blur(16px);
  }

  .mobile-menu-container {
    width: 80%;
    max-width: 320px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.1);
    padding: 1rem 1.25rem;
    border-radius: 16px;
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.3);
  }

  .mobile {
    display: flex;
    flex-direction: column;
    gap: 0.8rem;
    margin: 0;
    padding: 0;
  }

  .mobile li {
    margin: 0;
  }

  .mobile a {
    font-size: 15px;
    padding: 10px;
    color: #f0f0f0;
    border-radius: 10px;
    transition: background 0.2s;
    display: block;
  }

  .mobile a:not(.contact-link) {
    text-align: left;
    padding-left: 12px;
    padding-right: 12px;
  }

  .mobile a:hover {
    background: rgba(255, 255, 255, 0.08);
  }

  .mobile .contact-link {
    background-color: #9d4edd;
    color: #fff;
    border-radius: 14px;
    padding: 10px 16px;
    font-weight: 500;
    text-align: center;
  }

  @media (max-width: 768px) {
    .navbar {
      padding: 1rem;
    }

    .desktop {
      display: none;
    }

    .hamburger {
      display: flex;
    }

    .logo {
      margin-left: 1rem;
    }
  }
</style>
