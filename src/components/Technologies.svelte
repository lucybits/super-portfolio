<script>
  import { onMount } from "svelte";
  import gsap from "gsap";
  import ScrollTrigger from "gsap/ScrollTrigger";

  gsap.registerPlugin(ScrollTrigger);

  onMount(() => {
    gsap.from(".letter", {
      y: 50,
      opacity: 0,
      stagger: 0.08,
      duration: 2,
      ease: "power3.out",
      scrollTrigger: {
        trigger: ".technologies-container",
        start: "top 80%", 
        toggleActions: "play none none reset", 
        markers: false, 
      }
    });

gsap.from(".note-content", {
  y: 10,         
  opacity: 0,    
  duration: 1,     
  ease: "power1.out",
  scrollTrigger: {
    trigger: ".note-container",
    start: "top 85%", 
    toggleActions: "play none none reset",
    markers: false,
  }
});


  });
</script>

<div class="technologies-container">
  <div class="content">
    <h1>
      <span class="letter">S</span>
      <span class="letter">k</span>
      <span class="letter">i</span>
      <span class="letter">l</span>
      <span class="letter">l</span>
      <span class="letter">s</span>
    </h1>

    <div class="tech-list">
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/368761/html5.svg"
          alt="HTML"
          class="tech-icon"
        />
        HTML
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/368619/css3.svg"
          alt="CSS"
          class="tech-icon"
        />
        CSS
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/508920/js01.svg"
          alt="JavaScript"
          class="tech-icon"
        />
        JavaScript
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/369620/typescript.svg"
          alt="TypeScript"
          class="tech-icon"
        />
        TypeScript
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/330257/dart.svg"
          alt="Dart"
          class="tech-icon"
        />
        Dart
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/521303/react-16.svg"
          alt="React"
          class="tech-icon"
        />
        React
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/368993/svelte.svg"
          alt="Svelte"
          class="tech-icon"
        />
        Svelte
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/373446/astro.svg"
          alt="Astro"
          class="tech-icon"
        />
        Astro
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/342068/node-js.svg"
          alt="Node.js"
          class="tech-icon"
        />
        Node.js
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/306466/next-dot-js.svg"
          alt="Next.js"
          class="tech-icon"
        />
        Next.js
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/305812/bootstrap.svg"
          alt="Bootstrap"
          class="tech-icon"
        />
        Bootstrap
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/306062/flutter.svg"
          alt="Flutter"
          class="tech-icon"
        />
        Flutter
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/435684/git.svg"
          alt="Git"
          class="tech-icon"
        />
        Git
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/535339/database.svg"
          alt="SQL"
          class="tech-icon"
        />
        SQL
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/369292/firebase.svg"
          alt="Firebase"
          class="tech-icon"
        />
        Firebase
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/369594/tailwind.svg"
          alt="Tailwind CSS"
          class="tech-icon"
        />
        Tailwind CSS
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/306944/vue-dot-js.svg"
          alt="Vue.js"
          class="tech-icon"
        />
        Vue.js
      </div>
      <div class="tech-item">
        <img
          src="https://www.svgrepo.com/show/342077/nuxt-js.svg"
          alt="Nuxt"
          class="tech-icon"
        />
        NuxtJS
      </div>
      <div class="tech-item">
        <img
          src= "https://www.svgrepo.com/show/508937/rails.svg"
          alt="Ruby on Rails"
          class="tech-icon"
        />
        Ruby on Rails
      </div>
    </div>

    <div class="note-container">
      <div class="note-content">
        <img
          src="https://www.svgrepo.com/show/273718/invention-idea.svg"
          alt="Idea"
          class="note-icon"
        />
        <p class="how-to">
          I learned these technologies through extensive reading of official
          documentation, online courses, personal project development,
          participation in programming communities, and consistent practice to
          improve my skills day by day
        </p>
      </div>
    </div>
  </div>
</div>

<style>
  /* TODO TU CSS EXISTENTE, sin cambios */
  @font-face {
    font-family: "Radlush";
    src: url("/fonts/Radlush.ttf") format("truetype");
  }

  @font-face {
    font-family: "Favorit";
    src: url("/fonts/Favorit.ttf") format("truetype");
  }

  .technologies-container {
    border-radius: 50px;
    background-color: #0d0727;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0;
    padding: 2rem 1rem;
    width: 100%;
    max-width: 100%;
    box-sizing: border-box;
  }

  .content {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;
    width: 100%;
    padding-bottom: 2rem;
  }

  h1 {
    margin-top: clamp(10vh, 12vh, 30vh);
    font-family: "Radlush", sans-serif;
    font-size: clamp(2.5rem, 8vw, 6rem);
    color: rgba(45, 38, 79, 0.842);
    text-transform: uppercase;
    letter-spacing: 2px;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    text-align: center;
  }

  .letter {
    position: relative;
    display: inline-block;
    transition: color 0.3s ease;
  }

  .letter:hover {
    color: #e564ff;
  }

  .letter:hover::after {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    color: #e564ff;
    opacity: 0.3;
    border-radius: 4px;
    z-index: -1;
    animation: light-effect 0.3s forwards;
  }

  .tech-list {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(min(100px, 100%), 1fr));
    gap: clamp(0.5rem, 2vw, 1rem);
    max-width: 900px;
    width: 95%;
    margin-top: -2rem;
    padding: clamp(1rem, 3vw, 1.5rem);
  }

  .tech-item {
    font-family: "Favorit", sans-serif;
    background: linear-gradient(
      145deg,
      rgba(147, 51, 234, 0.1),
      rgba(88, 28, 135, 0.2)
    );
    color: #e932e0;
    padding: clamp(0.8rem, 2vw, 1.5rem);
    border-radius: 10px;
    text-align: center;
    font-size: clamp(0.8rem, 2vw, 1rem);
    transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    border: 1px solid rgba(85, 70, 98, 0.2);
    cursor: pointer;
    backdrop-filter: blur(5px);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    min-height: clamp(60px, 10vw, 80px);
    box-shadow: 0 2px 4px rgba(147, 51, 234, 0.1);
    gap: 0.5rem;
  }

  .tech-icon {
    width: clamp(20px, 4vw, 24px);
    height: clamp(20px, 4vw, 24px);
    filter: invert(40%) sepia(90%) saturate(1000%) hue-rotate(270deg)
      brightness(85%) contrast(120%);
    transition: filter 0.3s ease;
  }

  .tech-item:hover .tech-icon {
    filter: brightness(0) invert(1);
  }

  .tech-item:hover {
    transform: translateY(-5px) scale(1.03);
    background: linear-gradient(
      145deg,
      rgba(147, 51, 234, 0.2),
      rgba(88, 28, 135, 0.3)
    );
    border-color: rgba(147, 51, 234, 0.6);
    box-shadow: 0 4px 12px rgba(147, 51, 234, 0.2);
    color: #fff;
  }

  .note-container {
    margin-top: 5px;
    max-width: 900px;
    width: 95%;
    padding: 0 clamp(0.5rem, 2vw, 1rem);
  }

  .note-content {
    background: linear-gradient(
      145deg,
      rgba(233, 50, 224, 0),
      rgba(107, 25, 179, 0.078)
    );
    backdrop-filter: blur(10px);
    border: 1px solid rgba(233, 50, 224, 0.303);
    border-radius: 16px;
    padding: clamp(1rem, 3vw, 1.5rem);
    position: relative;
    transition: all 0.3s ease;
  }

  .note-content:hover {
    transform: translateY(-2px);
    border-color: rgba(233, 50, 224, 0.726);
  }

  .note-icon {
    background-color: rgb(170, 13, 175);
    position: absolute;
    top: -15px;
    left: 20px;
    padding: clamp(6px, 1.5vw, 8px);
    border-radius: 50%;
    width: clamp(20px, 4vw, 24px);
    height: clamp(20px, 4vw, 24px);
  }

  .how-to {
    font-family: "Favorit", sans-serif;
    color: rgba(186, 175, 228, 0.752);
    font-size: clamp(0.85rem, 2vw, 1rem);
    text-align: left;
    line-height: 1.6;
    letter-spacing: 0.5px;
    margin: 0;
    padding-left: clamp(0.5rem, 2vw, 1rem);
  }

  @keyframes light-effect {
    from {
      transform: scale(0);
      opacity: 0;
    }
    to {
      transform: scale(1);
      opacity: 0.3;
    }
  }

  @media (max-width: 480px) {
    h1 {
      font-size: clamp(3rem, 15vw, 5rem); /* Más grande en móvil */
      margin-top: 6vh;
    }

    .tech-list {
      grid-template-columns: repeat(auto-fit, minmax(80px, 1fr));
      gap: 0.8rem;
      padding: 0.8rem;
    }

    .tech-item {
      padding: 0.8rem;
      font-size: 0.8rem;
      min-height: 60px;
    }

    .note-content {
      padding: 1rem;
    }

    .how-to {
      font-size: 1rem;
    }

    .note-icon {
      width: 18px;
      height: 18px;
      padding: 6px;
    }
  }
</style>
