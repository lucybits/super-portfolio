<script>
  import Header from './components/Header.svelte';
  import Navbar from './components/Navbar.svelte'; 
  import About from './components/About.svelte';
  import Technologies from './components/Technologies.svelte';
  import Projects from './components/Projects.svelte';
  import Contact from './components/Contact.svelte';
  import Footer from './components/Footer.svelte';
  import FloatingButton from './components/FloatingButton.svelte';
</script>

<main style="background-color: #060211; margin: 0; padding: 0; min-height: 100vh;">
  <Navbar />
  <section id="home">
    <Header />
  </section>
  <section id="about">
    <About />
  </section>
  <section id="technologies">
    <Technologies />
  </section>
  <section id="projects">
    <Projects />
  </section>
  <section id="contact">
    <Contact />
  </section>
  <Footer />

   <FloatingButton icon="⬆️" scrollTarget="main" />
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    overscroll-behavior: none;
     width: 100%;
  overflow-x: hidden;
  }
</style>
