<script>
  import { onMount } from "svelte";
  import gsap from "gsap";
  import ScrollTrigger from "gsap/ScrollTrigger";

  gsap.registerPlugin(ScrollTrigger);

  const projects = [
    {
      title: "GPT Remodel",
      description:
        "A static redesign of ChatGPT with a beautiful interface using React and Node.js.",
      image:
        "https://i.pinimg.com/736x/ae/ce/d3/aeced35f9178ec72de27c2397290adf8.jpg",
      tags: ["React", "Node.js", "Vite"],
      link: "https://chatgpt-redesign-tau.vercel.app/",
      desktopOnly: true,
    },
    {
      title: "SwatchMe",
      description: "A color palette generation website",
      image:
        "https://registry.npmmirror.com/@lobehub/fluent-emoji-3d/latest/files/assets/1f3a8.webp",
      tags: ["React", "Node.js", "MongoDB"],
      link: "https://github.com/lucybits/swatchme",
    },
    {
      title: "Web Portfolio",
      description: "A modern personal portfolio with a lovely interface.",
      image:
        "https://static.vecteezy.com/system/resources/previews/024/082/860/non_2x/illustration-creative-folder-office-3d-icon-portfolio-symbols-isolated-on-background-vector.jpg",
      tags: ["Svelte", "Pure CSS", "Javascript"],
      link: "facebook.com",
    },
    {
      title: "Congreso PROXY",
      description:
        "Web portal developed with students for Congreso PROXY at Instituto Tecnologico de Hermosillo.",
      image:
        "https://influencermarketinghub.com/wp-content/uploads/2023/07/Technology-conferences-2023.png",
      tags: ["React", "Node.js", "Vite"],
      link: "https://congresoproxy.com",
    },
    {
      title: "Planna",
      description:
        "A to-do list application with a minimalist and functional interface.",
      image:
        "https://s.wsj.net/public/resources/images/BN-VN271_Todo_O_M_20171010165421.jpg",
      tags: ["React", "CSS", "LocalStorage"],
      link: "https://planna.netlify.app",
      desktopOnly: true,
    },
  ];

  onMount(() => {
    // Animación de los artículos
    gsap.utils.toArray(".projects-grid article").forEach((el, i) => {
      gsap.fromTo(
        el,
        { opacity: 0, y: 20 },
        {
          opacity: 1,
          y: 0,
          duration: 0.8,
          delay: i * 0.1,
          ease: "power2.out",
          scrollTrigger: {
            trigger: el,
            start: "top 85%",
            end: "bottom 15%",
            toggleActions: "play reverse play reverse",
          },
        },
      );
    });

    // Animación de los tags
    gsap.utils.toArray(".tags .tag").forEach((tag, i) => {
      gsap.fromTo(
        tag,
        { opacity: 0, y: 10 },
        {
          opacity: 1,
          y: 0,
          duration: 0.5,
          delay: i * 0.05,
          ease: "power1.out",
          scrollTrigger: {
            trigger: tag.closest("article"),
            start: "top 85%",
            end: "bottom 15%",
            toggleActions: "play reverse play reverse",
          },
        },
      );
    });
  });
</script>

<section>
  <h2>✧ Projects ✧</h2>

  <div class="projects-grid">
    {#each projects as project}
      <article>
        <div class="content">
          <a
            href={project.link}
            target="_blank"
            rel="noopener noreferrer"
            class="image-container"
          >
            {#if project.desktopOnly}
              <span class="desktop-label">Desktop only</span>
            {/if}
            <img src={project.image} alt={project.title} />
            <div class="overlay">
              <span class="demo-text">View demo</span>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="arrow-icon"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M14 5l7 7m0 0l-7 7m7-7H3"
                />
              </svg>
            </div>
          </a>

          <h3>{project.title}</h3>
          <p>{project.description}</p>

          <div class="tags">
            {#each project.tags as tag, i}
              <span
                class="tag"
                style="background: {[
                  '#9370DB',
                  '#e13dd7',
                  '#800080',
                  '#FF69B4',
                  '#BA55D3',
                ][i % 5]};">{tag}</span
              >
            {/each}
          </div>
        </div>
      </article>
    {/each}
  </div>
</section>

<style>
  :global(*) {
    font-family: "Favorit", sans-serif;
  }

  @font-face {
    font-family: "Favorit";
    src: url("/fonts/Favorit.ttf") format("truetype");
  }

  section {
    padding: 4rem 2rem;
    max-width: 85rem;
    margin: 0 auto;
  }

  h2 {
    font-size: 2.5rem;
    font-weight: bold;
    text-align: center;
    margin-bottom: 3rem;
    color: #ffffff;
  }

  .projects-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 1.5rem;
    padding: 0 1rem;
  }

  @media (min-width: 768px) {
    .projects-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  @media (min-width: 1024px) {
    .projects-grid {
      grid-template-columns: repeat(3, 1fr);
    }
  }

  article {
    position: relative;
    border-radius: 1rem;
    padding: 1.25rem;
    border: 1px solid #141738;
    transition: all 0.3s;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
    background-color: rgba(15, 12, 35, 0.7);
  }

  article:hover {
    transform: translateY(-5px);
    border: 1px solid #e53fe247;
  }

  .content {
    position: relative;
  }

  .image-container {
    position: relative;
    display: block;
    width: 100%;
    height: 11rem;
    border-radius: 0.75rem;
    overflow: hidden;
    margin-bottom: 0.75rem;
  }

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s;
  }

  .overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.7);
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 0.3s;
  }

  .demo-text {
    color: white;
    font-weight: 500;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .image-container:hover .overlay {
    opacity: 1;
  }
  .image-container:hover img {
    transform: scale(1.05);
  }

  .desktop-label {
    position: absolute;
    top: 0.5rem;
    left: 0.5rem;
    background: rgba(102, 0, 255, 0.85);
    color: white;
    font-size: 0.65rem;
    padding: 0.25rem 0.5rem;
    border-radius: 0.5rem;
    font-weight: 600;
    text-transform: uppercase;
    pointer-events: none;
    z-index: 10;
    box-shadow: 0 0 6px rgba(0, 0, 0, 0.4);
  }

  h3 {
    font-size: 1.25rem;
    font-weight: 600;
    margin-bottom: 0.5rem;
    color: #ffffff;
  }
  p {
    color: #b9bbbe;
    margin-bottom: 0.75rem;
    font-size: 0.9rem;
  }
  .tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    margin-bottom: 0.75rem;
  }
  .tag {
    padding: 0.25rem 0.75rem;
    font-size: 0.875rem;
    border-radius: 9999px;
    color: #ffffff;
    font-weight: 500;
    text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
  }

  .arrow-icon {
    height: 1.5rem;
    width: 1.5rem;
    margin-left: 0.5rem;
    color: white;
  }
</style>
