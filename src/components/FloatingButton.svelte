<script>
  export let iconUrl = "https://www.svgrepo.com/show/533632/arrow-up.svg";

  function scrollToTop() {
    window.scrollTo({ top: 0, behavior: "smooth" });
  }
</script>

<button class="floating-button" on:click={scrollToTop}>
  <img src={iconUrl} alt="Scroll to top" class="icon" />
</button>

<style>
  .floating-button {
    position: fixed;
    bottom: 2rem;
    right: 2rem;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    border: none;
    background-color: #ff7ce9f7;
    cursor: pointer;
    box-shadow: 0 4px 12px rgba(0,0,0,0.3);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 999;
    transition: transform 0.3s, background-color 0.3s;
    padding: 0;
  }

  .floating-button img.icon {
    width: 60%;
    height: 60%;
    object-fit: contain;
    filter: invert(1) brightness(2); 
  }

  .floating-button:hover {
    background-color: #ff4ac9f7;
    transform: translateY(-3px);
  }
</style>
