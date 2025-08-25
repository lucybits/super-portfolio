  <script>
    const currentYear = new Date().getFullYear();
  </script>

  <footer class="footer">
    <div class="footer-content">
      <div class="footer-top">
        <div class="status-indicator">
          <span class="status-dot"></span>
          <span class="status-text">Available for work</span>
        </div>
        <div class="social-links">
          <a href="https://github.com/luciapdev" target="_blank" rel="noopener noreferrer" class="social-link">
            <img src="https://www.svgrepo.com/show/501210/github.svg" alt="GitHub" class="social-icon"/>
          </a>
          <a href="https://linkedin.com/in/luciapdev" target="_blank" rel="noopener noreferrer" class="social-link">
            <img src="https://www.svgrepo.com/show/494312/linkedin-rounded.svg" alt="LinkedIn" class="social-icon"/>
          </a>
          <a href="https://twitter.com/luciapdev" target="_blank" rel="noopener noreferrer" class="social-link">
            <img src="https://uxwing.com/wp-content/themes/uxwing/download/brands-and-social-media/x-social-media-black-icon.png" alt="Twitter" class="social-icon"/>
          </a>
        </div>
      </div>
      <div class="footer-bottom">
        <a href="mailto:contact@luciapdev.com" class="email-link">lucia.dev@proton.me</a>
        <div class="copyright">
          © {currentYear} • Made with 💜 by Lucia Pacheco
        </div>
      </div>
    </div>
  </footer>

  <style>
    .footer {
      padding: 2.5rem 2rem;
      background-color: #110530;
      margin-top: auto;
      backdrop-filter: blur(10px);
      border: 1px solid rgba(114, 137, 218, 0.1);
    }

    .footer-content {
      max-width: 1000px;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      gap: 2rem;
    }

    .footer-top {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 0 1rem;
    }

    .status-indicator {
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .status-dot {
      width: 8px;
      height: 8px;
      background-color: #2ecc71;
      border-radius: 50%;
      animation: pulse 2s infinite;
    }

    .status-text {
      color: #2ecc71;
      font-size: 0.9rem;
      font-weight: 500;
    }

    @keyframes pulse {
      0% {
        box-shadow: 0 0 0 0 rgba(46, 204, 113, 0.4);
      }
      70% {
        box-shadow: 0 0 0 6px rgba(46, 204, 113, 0);
      }
      100% {
        box-shadow: 0 0 0 0 rgba(46, 204, 113, 0);
      }
    }

    .social-links {
      display: flex;
      gap: 1.5rem;
    }

    .social-link {
      text-decoration: none;
      transition: all 0.3s ease;
      display: inline-block;
    }

    .social-link:hover {
      opacity: 0.9;
      transform: translateY(-2px);
      filter: drop-shadow(0 0 8px rgba(255, 0, 255, 0.3));
    }
      .social-icon {
        width: 22px;
        height: 22px;
        filter: invert(75%) sepia(20%) saturate(1000%) hue-rotate(260deg);
      }
    .footer-bottom {
      text-align: center;
      display: flex;
      flex-direction: column;
      gap: 1rem;
      padding-top: 1rem;
      border-top: 1px solid rgba(114, 137, 218, 0.1);
    }

    .email-link {
      color: #e4e4e4;
      text-decoration: none;
      transition: color 0.3s ease;
      font-size: 0.95rem;
    }

    .email-link:hover {
      color: #ff69b4;
      text-shadow: 0 0 8px rgba(255, 105, 180, 0.3);
    }

    .copyright {
      font-size: 0.9rem;
      color: #b9bbbe;
      font-weight: 500;
      letter-spacing: 0.3px;
    }

    @media (max-width: 600px) {
      .footer {
        padding: 2rem 1.5rem;
      }

      .footer-top {
        flex-direction: column;
        gap: 2rem;
        padding: 0;
      }
    
      .social-links {
        gap: 2rem;
      }

      .social-icon {
        width: 28px;
        height: 28px;
      }
    
      .status-text {
        font-size: 1rem;
      }

      .footer-bottom {
        padding-top: 1.5rem;
        gap: 1.5rem;
      }

      .email-link {
        font-size: 1.1rem;
      }

      .copyright {
        font-size: 1rem;
      }
    }
  </style>