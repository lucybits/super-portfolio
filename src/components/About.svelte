<script>
  import { onMount } from "svelte";
  import gsap from "gsap";
  import { ScrollTrigger } from "gsap/ScrollTrigger";

  gsap.registerPlugin(ScrollTrigger);

  let profileSection;
  let techSection;
  let button;

  onMount(() => {
    ScrollTrigger.create({
      trigger: profileSection,
      start: "top 80%",
      onEnter: () => {
        const tl = gsap.timeline({ defaults: { ease: "power2.out" } });
        tl.from(profileSection, { opacity: 0, y: 20, duration: 1 }).from(
          profileSection.querySelectorAll("h1, p"),
          { opacity: 0, y: 10, stagger: 0.15, duration: 0.8 },
          "-=0.8",
        );
      },
      toggleActions: "play reverse play reverse",
    });

    ScrollTrigger.create({
      trigger: techSection,
      start: "top 80%",
      onEnter: () => {
        const tl = gsap.timeline({ defaults: { ease: "power2.out" } });
        tl.from(techSection, { opacity: 0, y: 20, duration: 1 }).from(
          techSection.querySelectorAll("h1, p"),
          { opacity: 0, y: 10, stagger: 0.15, duration: 0.8 },
          "-=0.8",
        );
      },
      toggleActions: "play reverse play reverse",
    });

    gsap.to(button, {
      y: -2,
      duration: 1.5,
      yoyo: true,
      repeat: -1,
      ease: "sine.inOut",
    });
  });

  function scrollToContact() {
  const contactSection = document.getElementById("contact-section");
  if (contactSection) {
    contactSection.scrollIntoView({ behavior: "smooth" });
  }
}

</script>

<div class="about-container">
  <div class="profile-section" bind:this={profileSection}>
    <div class="title-container">
      <h1>About me<span class="accent">.</span></h1>
    </div>
    <div class="divider"></div>
    <div class="content">
      <p class="intro">
        I'm 20 and study at Instituto Tecnológico de Hermosillo, from
        <span class="highlight">Hermosillo, Sonora, Mexico.</span> I follow web dev
        trends to keep my ideas fresh.
      </p>
    </div>
  </div>

  <div class="tech-section" bind:this={techSection}>
    <div class="title-container">
      <h1>
        My experience<span class="accent">.</span>
        <span class="small-text">(and how I got here)</span>
      </h1>
    </div>
    <div class="divider"></div>
    <div class="content">
      <p class="intro">
        I started with HTML and CSS, then focused on
        <span class="highlight">JavaScript and modern frameworks.</span> I build
        with React, Node.js, and now explore TypeScript and Next.js.
      </p>
    </div>
  </div>

  <div class="button-container">
    <div class="contact-text">
      <p>Interested in working together?</p>
      <p class="subtitle">Let's create something amazing!</p>
    </div>
    <button
      class="contact-button"
      bind:this={button}
      on:click={scrollToContact}
    >
      <span class="button-text">Contact me</span>
    </button>
  </div>
</div>

<style>
  @font-face {
    font-family: "Favorit";
    src: url("/fonts/Favorit.ttf") format("truetype");
  }

  .about-container {
    max-width: 1200px;
    margin: 3rem auto;
    padding: 2rem;
    font-family: "Favorit", sans-serif;
    display: flex;
    flex-wrap: wrap;
    background-color: #060211;
  }

  .profile-section,
  .tech-section {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    min-width: 300px;
    max-width: 550px;
    margin: 0 1rem;
    border-radius: 20px;
    padding: 2rem;
    position: relative;
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 124, 233, 0.15);
  }

  .profile-section {
    background: linear-gradient(
      to bottom,
      rgba(255, 124, 233, 0.08),
      rgba(6, 2, 17, 0.7)
    );
  }

  .tech-section {
    background: linear-gradient(
      to bottom,
      rgba(76, 12, 140, 0.08),
      rgba(6, 2, 17, 0.7)
    );
  }

  .title-container {
    position: relative;
    display: inline-block;
  }

  .divider {
    width: 100%;
    height: 1px;
    background: linear-gradient(to right, transparent, #ff7ce940, transparent);
    margin: -1rem 0;
  }

  h1 {
    font-size: 2.9rem;
    color: #f0f0f0;
    margin: 0;
    font-weight: 600;
    letter-spacing: 0.5px;
  }

  .accent {
    color: #ff7ce9f7;
  }

  .small-text {
    font-size: 1rem;
    color: #e0e0e0;
    font-weight: normal;
    font-style: italic;
  }

  .content {
    display: grid;
    gap: 2rem;
  }

  .intro {
    font-size: 1.2rem;
    line-height: 1.8;
    color: #d8d8d8;
    letter-spacing: 0.2px;
  }

  .highlight {
    padding: 0 6px;
    border-radius: 4px;
    color: #ff7ce9;
  }

  .button-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    margin-top: 3rem;
    gap: 1rem;
  }

  .contact-text {
    text-align: center;
    color: #d8d8d8;
  }

  .contact-button {
    padding: 1rem 3.5rem;
    font-size: 1.2rem;
    color: #ff7ce9f7;
    border: 2px solid #ff7ce9f7;
    border-radius: 30px;
    cursor: pointer;
    transition: all 0.3s ease;
    background: transparent;
    position: relative;
    overflow: hidden;
    letter-spacing: 1.2px;
    font-weight: 500;
    display: flex;
    align-items: center;
    gap: 1rem;
    z-index: 0;
  }

  .contact-button::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 100%;
    background: linear-gradient(90deg, #ff7ce9f7, #cb7cff);
    transition: all 0.3s ease;
    z-index: -1;
  }

  .contact-button:hover {
    color: #060211;
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(255, 124, 233, 0.25);
  }

  .contact-button:hover::before {
    width: 100%;
  }

  @media (max-width: 768px) {
    .about-container {
      flex-direction: column;
      padding: 1.5rem;
      gap: 3rem;
    }

    .profile-section,
    .tech-section {
      align-self: center;
      text-align: center;
      margin: 0;
    }

    h1 {
      font-size: 2rem;
    }
  }
</style>
