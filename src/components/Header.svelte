<script>
  import { onMount } from "svelte";
  import gsap from "gsap";

  let header;
  let greeting;
  let name;
  let subtitle;
  let paragraph;
  let tag;
  let socialLinks;

  onMount(() => {
    const tl = gsap.timeline({ defaults: { ease: "power3.out" } });

    tl.from(header, { opacity: 0, y: -60, duration: 1.5 })
      .from(greeting, { opacity: 0, y: 20, duration: 1.2 }, "-=1.2")
      .from(name, { opacity: 0, x: -50, duration: 2 }, "-=1.2")
      .from(subtitle, { opacity: 0, y: 20, duration: 1.5 }, "-=1.5")
      .from(paragraph, { opacity: 0, y: 30, duration: 2 }, "-=1.5")
      .from(tag, { opacity: 0, scale: 0.8, duration: 1.8 }, "-=1.6");

    if (socialLinks) {
      const links = socialLinks.querySelectorAll("span");
      gsap.from(links, { opacity: 0, y: 20, stagger: 0.3, duration: 1.5, ease: "power2.out" });
    }

    gsap.to(tag, { y: -5, duration: 1.8, yoyo: true, repeat: -1, ease: "sine.inOut" });
    gsap.to(name, { x: 5, duration: 2.5, yoyo: true, repeat: -1, ease: "sine.inOut" });
  });
</script>

<header bind:this={header}>
  <h1>
    <span class="greeting" bind:this={greeting}>Hi, I'm</span>
    <span class="name" bind:this={name}>Lucía Pacheco</span>
  </h1>

  <div class="subtitle" bind:this={subtitle}>
    Frontend Developer JR • Computer Systems Engineer
  </div>

  <p bind:this={paragraph}>
    Computer Systems Engineer looking for new opportunities. I'm passionate
    about web development and programming, with experience in various modern
    technologies.
  </p>

  <div class="tag" bind:this={tag}>
    &lt;the.future.is.code/&gt;
  </div>

  <div class="social-links" bind:this={socialLinks}>
    <span>📍 Mexico</span>
    <span>•</span>
    <span>Open to work 💻</span>
  </div>
</header>

<style>
  @font-face {
    font-family: "Radlush";
    src: url("/fonts/Radlush.ttf") format("truetype");
  }
  @font-face {
    font-family: "Favorit";
    src: url("/fonts/Favorit.ttf") format("truetype");
  }
  @font-face {
    font-family: "Monolisa";
    src: url("/fonts/Monolisa.ttf") format("truetype");
  }

  header {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    min-height: 60vh;
    width: 100%;
    max-width: 1200px;
    text-align: center;
    border-radius: 20px;
    margin: 1vh auto 0;
    position: relative;
    padding: 3rem 2rem;
    box-sizing: border-box;
  }

  h1 {
    font-family: "Radlush", sans-serif;
    font-size: clamp(3rem, 7vw, 4rem);
    color: rgb(185, 80, 176);
    margin: 0;
    word-wrap: break-word;
  }

  h1 .greeting {
    color: white;
    display: block;
  }

  h1 .name {
    background: linear-gradient(90deg, #ff00cc, #b338ff, #ff00cc);
    background-size: 200% auto;
    color: transparent;
    -webkit-background-clip: text;
    background-clip: text;
    animation: shine 3s linear infinite;
  }

  .subtitle {
    font-family: "Favorit", sans-serif;
    font-size: clamp(1rem, 2.5vw, 1.2rem);
    color: rgba(255, 255, 255, 0.6);
    margin: 15px 0 25px;
    letter-spacing: 2px;
    text-transform: uppercase;
  }

  p {
    font-family: "Favorit", sans-serif;
    font-size: clamp(1.1rem, 3vw, 1.3rem);
    color: rgba(255, 255, 255, 0.82);
    max-width: 700px;
    line-height: 1.6;
    margin: 1.5rem auto;
    padding: 0 1rem;
  }

  .tag {
    font-family: "Monolisa", monospace;
    font-size: clamp(1rem, 2.5vw, 1.2rem);
    color: #f0f0f0;
    background: linear-gradient(135deg, #6b2b89, #9b4dca);
    padding: 0.9rem 2rem;
    margin-top: 25px;
    border-radius: 15px;
    display: inline-block;
    border: 1px solid rgba(255, 255, 255, 0.1);
    letter-spacing: 1px;
    word-break: break-word;
  }

  .tag:hover {
    background: linear-gradient(135deg, #7c3399, #ae5ee0);
  }

  .social-links {
    margin-top: 25px;
    font-family: "Favorit", sans-serif;
    color: rgba(255, 255, 255, 0.7);
    font-size: clamp(1rem, 2.5vw, 1.1rem);
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
  }

  .social-links span {
    margin: 0 5px;
  }

  @keyframes shine {
    to {
      background-position: 200% center;
    }
  }

  @media (max-width: 768px) {
    header {
      padding: 3rem 2rem;
      min-height: 70vh;
      margin-top: 2vh;
    }

    h1 {
      font-size: 3rem;
    }

    .subtitle {
      font-size: 1.1rem;
    }

    p {
      font-size: 1.2rem;
      padding: 0 1rem;
    }

    .tag {
      font-size: 1.1rem;
    }
  }

  @media (max-width: 480px) {
    header {
      padding: 2rem 1.5rem;
      min-height: 80vh;
    }

    h1 {
      font-size: 2.5rem;
    }

    .subtitle {
      font-size: 1rem;
    }

    p {
      font-size: 1.1rem;
    }

    .tag {
      font-size: 1rem;
      padding: 0.8rem 1.5rem;
    }

    .social-links {
      flex-direction: column;
      gap: 8px;
      font-size: 1rem;
    }

    .social-links span:nth-child(2) {
      display: none;
    }
  }
</style>
