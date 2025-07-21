<script>
    // `layout` can be either "right" or "left"
    // `sticky` and `scrolly` are the snippets passed in (see one of the examples)
    let { layout, sticky, scrolly } = $props(); 
</script>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Tomorrow:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap" rel="stylesheet">


<div class="wrapper {layout}">
    <div class="sticky">
        {@render sticky()}
    </div>

    <div class="scrolly">
        {@render scrolly()}
    </div>
</div>

<style>
   
    .wrapper {
        background-color: #540023;
        padding: min(100vh, 10rem) 1rem;
        border-style: solid;
        border-color: #540023;
       background-image: image-set(url('Backg.png') 1.5x);  
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        align-items: flex-start;
    }

    .left .scrolly {
        order: 0;
    }
    .left .sticky {
        order: 1;
    }

    .right .scrolly {
        order: 1;
    }
    .right .sticky {
        order: 0;
    }

    .sticky,
    .scrolly {
        display: flex;
        flex-direction: column;
        flex: 1 1; /* Allows growing, shrinking */
    }

    .sticky {
        position: sticky;
        top: 50vh;
        transform: translateY(-50%);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 0;
    }

    .scrolly {
        z-index: 1;
    }

    @media (max-width: 768px) {
        .wrapper {
            flex-direction: column;
            padding: 2rem 1rem;
            width: 100vw;
        }

        .sticky,
        .scrolly {
            flex: 1 1 auto;
            min-width: 100%;
            position: static; /* remove sticky on mobile */
            transform: none;
        }

        .sticky {
            margin-bottom: 2rem;
        }
    }
</style>
