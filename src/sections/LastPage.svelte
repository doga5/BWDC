
<script>
  import { faGithub, faLinkedin } from '@fortawesome/free-brands-svg-icons';
  import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';
</script>

<div class="last">
  <p>
    2025 · Doga Oyku Oruc
    <br /> 
    <a class="links"
      href="https://www.linkedin.com/in/do%C4%9Fa-%C3%B6yk%C3%BC-oru%C3%A7-12762423b/"
      target="_blank"
      rel="noopener"
    >
      <FontAwesomeIcon icon={faLinkedin} />
    </a>
    <a class="links"
      href="https://github.com/doga5"
      target="_blank"
      rel="noopener"
    >
      <FontAwesomeIcon icon={faGithub} />
    </a>
  </p>
</div>





<style>

    .last {
        text-align: center;
        height: 25vh;
        padding: 10px;
        background-color: #f8edf2;
        color: #540023;
        font-family: "Courier New", Courier, monospace;
        font-size: 1.5em;
        font-weight: 600;
        bottom: 0;
        width: 100%;
    }
    .links {
        color: #540023;
        text-decoration: none;
        margin-left: 10px;
        padding-top: 10rem;
    }
</style>