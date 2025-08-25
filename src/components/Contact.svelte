<script>
  import { fade } from "svelte/transition";
  import emailjs from "emailjs-com";
  import { onMount } from "svelte";
  import gsap from "gsap";
  import ScrollTrigger from "gsap/ScrollTrigger";

  gsap.registerPlugin(ScrollTrigger);

  let email = "",
    message = "",
    name = "",
    subject = "";

  const SERVICE_ID = "service_6pk3gok";
  const TEMPLATE_ID = "template_ttv2606";
  const PUBLIC_KEY = "4ActSliRx2BAt08PE";

  function isEmailValid(email) {
    const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/;
    const commonDomains = [
      "gmail.com",
      "hotmail.com",
      "yahoo.com",
      "outlook.com",
      "icloud.com",
      "aol.com",
      "protonmail.com",
      "zoho.com",
      "mail.com",
      "gmx.com",
    ];

    if (!emailRegex.test(email)) return false;

    const domain = email.split("@")[1];
    if (!commonDomains.includes(domain)) {
      return confirm(
        "This email domain is not common. Are you sure it is correct?",
      );
    }
    return true;
  }

  function isNameValid(name) {
    return name.length >= 2 && /^[a-zA-ZáéíóúÁÉÍÓÚñÑ\s]+$/.test(name);
  }

  function isSubjectValid(subject) {
    return subject.length >= 3 && subject.length <= 100;
  }

  function isMessageValid(message) {
    return message.length >= 10 && message.length <= 400;
  }

  async function handleSubmit(e) {
    e.preventDefault();

    if (!name || !email || !subject || !message) {
      alert("Please fill in all fields.");
      return;
    }

    if (!isNameValid(name)) {
      alert("Please enter a valid name (letters and spaces only).");
      return;
    }

    if (!isEmailValid(email)) {
      alert("Please enter a valid email address.");
      return;
    }

    if (!isSubjectValid(subject)) {
      alert("Subject must be between 3 and 100 characters.");
      return;
    }

    if (!isMessageValid(message)) {
      alert("Message must be between 10 and 400 characters.");
      return;
    }

    const templateParams = {
      from_name: name,
      reply_to: email,
      subject,
      message,
    };

    try {
      await emailjs.send(SERVICE_ID, TEMPLATE_ID, templateParams, PUBLIC_KEY);
      alert("Message sent successfully!");
      name = email = subject = message = "";
    } catch (error) {
      console.error("Error sending email:", error);
      alert("There was an error sending your message.");
    }
  }

  onMount(() => {
    const h1Elements = document.querySelectorAll(".title-container h1");
    h1Elements.forEach((el) => {
      const text = el.textContent;
      el.innerHTML = text
        .split("")
        .map((char) => `<span class="letter">${char}</span>`)
        .join("");

      gsap.fromTo(
        el.querySelectorAll(".letter"),
        { y: 20, opacity: 0 },
        {
          y: 0,
          opacity: 1,
          stagger: 0.09,
          duration: 1.5,
          ease: "power2.out",
          scrollTrigger: {
            trigger: el,
            start: "top 80%",
            toggleActions: "play none none none",
            markers: false,
            immediateRender: false,
          },
        },
      );
    });

    const highlights = document.querySelectorAll(".highlight");
    highlights.forEach((el) => {
      gsap.fromTo(
        el,
        { y: 10, opacity: 0 },
        {
          y: 0,
          opacity: 1,
          duration: 0.8,
          ease: "power2.out",
          scrollTrigger: {
            trigger: el,
            start: "top 90%",
            toggleActions: "play none none none",
            immediateRender: false,
          },
        },
      );
    });


    ScrollTrigger.refresh();
  });
</script>

<div id="contact-section" class="contact-container" in:fade>
  <div class="content-wrapper">
    <div class="left-grid">
      <div class="title-container">
        <h1>Why not create something amazing together?</h1>
      </div>
      <div class="divider"></div>
      <p>
        You can also email me directly at
        <span class="highlight">lucia.dev@proton.me</span>
      </p>
    </div>

    <div class="right-grid">
      <form on:submit={handleSubmit}>
        <div class="form-group">
          <label for="name">Name</label>
          <input
            type="text"
            id="name"
            bind:value={name}
            placeholder="Your full name"
          />
        </div>
        <div class="form-group">
          <label for="email">Email</label>
          <input
            type="email"
            id="email"
            bind:value={email}
            placeholder="example@email.com"
          />
        </div>
        <div class="form-group">
          <label for="subject">Subject</label>
          <input
            type="text"
            id="subject"
            bind:value={subject}
            placeholder="What would you like to discuss?"
          />
        </div>
        <div class="form-group">
          <label for="message">Message</label>
          <textarea
            id="message"
            bind:value={message}
            placeholder="Tell me more about your project..."
            rows="4"
            maxlength="400"
            style="resize: none;"
          ></textarea>
          <span class="character-count">{message.length}/400</span>
        </div>
        <button type="submit" class="contact-button">
          <span class="button-text">Send message</span>
        </button>
      </form>
    </div>
  </div>
</div>

<style>
  @font-face {
    font-family: "Favorit";
    src: url("/fonts/Favorit.ttf") format("truetype");
  }
  .contact-container {
    padding: 5rem;
    font-family: "Favorit", sans-serif;
    background-color: #060211;
    position: relative;
    overflow: hidden;
  }
  .content-wrapper {
    max-width: 1000px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
  }
  .contact-container::after {
    content: "";
    position: absolute;
    bottom: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(to top, rgba(65, 42, 181, 0.338), transparent);
    pointer-events: none;
  }
  .left-grid {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 1.5rem;
    border-radius: 20px;
  }
  h1 {
    font-size: 2.4rem;
    color: #f0f0f0;
    margin: 0;
    font-weight: 600;
    letter-spacing: 0.5px;
    line-height: 1.2;
  }
  .highlight {
    color: #ff7ce9f7;
  }
  .divider {
    width: 80%;
    height: 1px;
    background: linear-gradient(to right, transparent, #ff7ce940, transparent);
    margin: 0.8rem auto;
  }
  p {
    font-size: 1.1rem;
    line-height: 1.6;
    color: #d8d8d8;
    letter-spacing: 0.3px;
  }
  .right-grid {
    padding: 1.5rem;
    border-radius: 20px;
  }
  .form-group {
    margin-bottom: 1.2rem;
    position: relative;
  }
  label {
    display: block;
    margin-bottom: 0.4rem;
    color: #d8d8d8;
    font-weight: 500;
    text-align: left;
    font-size: 1rem;
    background: transparent !important;
  }
  input,
  textarea {
    width: 100%;
    padding: 0.6rem;
    background: rgba(6, 2, 17, 0.7);
    border: 1px solid rgba(255, 124, 233, 0.15);
    border-radius: 8px;
    font-size: 1rem;
    color: #d8d8d8;
    transition:
      border-color 0.3s ease,
      background-color 0.3s ease;
  }
  input:-webkit-autofill,
  input:-webkit-autofill:hover,
  input:-webkit-autofill:focus,
  input:-webkit-autofill:active {
    -webkit-text-fill-color: #d8d8d8 !important;
    background: rgba(6, 2, 17, 0.7) !important;
    border: 1px solid rgba(255, 124, 233, 0.15) !important;
    transition: background-color 5000s ease-in-out 0s;
    caret-color: #d8d8d8 !important;
  }
  textarea:-webkit-autofill,
  textarea:-webkit-autofill:hover,
  textarea:-webkit-autofill:focus,
  textarea:-webkit-autofill:active {
    -webkit-text-fill-color: #d8d8d8 !important;
    background: rgba(6, 2, 17, 0.7) !important;
    border: 1px solid rgba(255, 124, 233, 0.15) !important;
    transition: background-color 5000s ease-in-out 0s;
    caret-color: #d8d8d8 !important;
  }
  textarea::-webkit-scrollbar {
    width: 8px;
  }
  textarea::-webkit-scrollbar-track {
    background: rgba(6, 2, 17, 0.7);
    border-radius: 4px;
  }
  textarea::-webkit-scrollbar-thumb {
    background: rgba(255, 124, 233, 0.3);
    border-radius: 4px;
    transition: background 0.3s ease;
  }
  textarea::-webkit-scrollbar-thumb:hover {
    background: rgba(255, 124, 233, 0.5);
  }
  input:focus,
  textarea:focus {
    outline: none;
    border-color: #ff7ce9f7;
  }
  .character-count {
    position: absolute;
    bottom: -20px;
    left: 0;
    font-size: 0.8rem;
    color: rgba(216, 216, 216, 0.319);
  }
  .contact-button {
    width: 100%;
    margin: 2rem auto 0;
    display: block;
    padding: 0.6rem;
    font-size: 1rem;
    color: #ff7ce9f7;
    border: 1px solid #ff7ce9f7;
    border-radius: 25px;
    cursor: pointer;
    transition: all 0.3s ease;
    font-family: "Favorit", sans-serif;
    background: transparent;
    letter-spacing: 1.2px;
    font-weight: 500;
  }
  .button-text {
    position: relative;
    z-index: 1;
  }
  .contact-button:hover {
    background: rgba(255, 124, 233, 0.1);
    transform: translateY(-2px);
  }
  @media (max-width: 768px) {
    .content-wrapper {
      grid-template-columns: 1fr;
      gap: 0.5rem;
    }
    .contact-container {
      padding: 1rem;
    }
    .left-grid {
      text-align: left;
    }
    h1 {
      font-size: 1.8rem;
    }
  }
</style>
