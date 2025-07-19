<script>
  let { title, subtitle } = $props();
</script>

<div class="title-card">
  <div class="content">
    <p>{subtitle}</p>
    <h1>{title}</h1>
    <p>By <strong class="name"> <a href="https://www.linkedin.com/in/do%C4%9Fa-%C3%B6yk%C3%BC-oru%C3%A7-12762423b/">Doga Oyku Oruc</a></strong></p>
  </div>
  <img class="duck-img" src="duck.png" alt="KWK rubber duck!" />
</div>

<style>
  .title-card {
    background-color: #540023;
    height: 100vh;
    display: flex;
    justify-content: left;
    align-items: left;
    text-align: left;
    padding: 3rem;
    box-sizing: border-box;
    font-family: monaco, monospace;
  }
  .duck-img {
    position: absolute;
    bottom: 0;
    right: 0;
    width: 20rem;
    height: auto;
    opacity: 0.1;
  }
  .duck-img:hover {
    opacity: 0.5;
    transition: opacity 0.3s ease-in-out;
  }
  .duck-img:active {
    opacity: 0.8;
    transition: opacity 0.1s ease-in-out;
  }
  .duck-img:focus {
    outline: none;
    box-shadow: 0 0 0 2px #F0BF56;
  }
  .content {
    max-width: 900px;
    background-color: #540023;
    padding: 2rem;
  }

  h1 {
    font-size: 5rem;
    margin: 0;
    color: #F0BF56;
    padding-bottom: 5rem;
    max-width: 700px;
    font-family: monospace, fantasy;
  }

  p {
    font-size: 1.5rem;
    color: #f7f5eb;
    margin-top: 1rem;
  }
  .name {
    border-bottom: #F0BF56 2px solid;
    padding-top: 10rem;
    font-weight: bold;
  }
  .name a {
    color: inherit;
    text-decoration: none;
  }
  .name a:hover {
    color: #F0BF56;
    transition: text-decoration 0.3s ease-in-out;
  }

  @media (max-width: 600px) {
    h1 {
      font-size: 2.2rem;
    }

    p {
      font-size: 1.1rem;
    }
  }
</style>
