<script>
  let { title, subtitle } = $props();
</script>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Tomorrow:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap" rel="stylesheet">

<div class="title-card">
  <div class="content">
    <p>{subtitle}</p>
    <h1>{title}</h1>
    <p>By <strong class="name"> <a href="https://www.linkedin.com/in/do%C4%9Fa-%C3%B6yk%C3%BC-oru%C3%A7-12762423b/">Doga Oyku Oruc</a></strong></p>
  </div>
  <img class="Illustration" src="Illustration.png" alt="My own illustration!" />
</div>

<style>
  .title-card {
    background-color: #540023;
    height: 180vh;
    display: flex;
    justify-content: left;
    align-items: left;
    text-align: left;
    padding: 2rem;
    padding-bottom: 20vh;
    box-sizing: border-box;
    font-family: "Tomorrow", sans-serif;
    font-weight: 400;
    font-style: normal;
  }
  .Illustration {
    position: absolute;
    top: 5vh;
    bottom: 0;
    right: 0;
    width: 30rem;
    height: auto;
    opacity: 0.9;
  }
  
  
  .content {
    max-width: 1000px;
    background-color: #540023;
    padding: 2rem;
  }

  h1 {
    font-size: 6rem;
    margin: 0;
    box-sizing: border-box;
    width: 10%;
    color: #F0BF56;;
    padding-bottom: 2rem;
    max-width: 200px;
    font-family: "Tomorrow", sans-serif;
    font-weight: 500;
    font-style: normal;
  }

  p {
    font-size: 2rem;
    color: #f7f5eb;
    margin-top: 0;
  }
  .name {
    border-bottom: #F0BF56 2px solid;
    padding-top: 10rem;
    font-weight: 600;
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
