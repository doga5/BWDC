<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Tomorrow:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap" rel="stylesheet">

<script>
    import { fade, fly } from "svelte/transition";
    import Scroller from "../lib/Scroller.svelte";
    import ObservedArticleText from "../lib/ObservedArticleText.svelte";

    let duckIsVisible = $state(false);

    const options = {
        threshold: [0.85, 0.95],
    };

    const simpleCallback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;

            if (entry.intersectionRatio >= 0.9) {
                
                elem.style.opacity = 1;
            } else if (entry.intersectionRatio < 0.9) {
                
                elem.style.opacity = 0.25;
            }
        });
    };

    const showDuckCallback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;

            if (entry.intersectionRatio >= 0.9) {
                elem.style.opacity = 1;
                duckIsVisible = true;
            } else if (entry.intersectionRatio < 0.9) {
                 elem.style.opacity = 0.25;
            }
        });
    };

    const removeDuckCallback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;

            if (entry.intersectionRatio >= 0.9) {
                elem.style.opacity = 1;
                duckIsVisible = false;
            } else if (entry.intersectionRatio < 0.9) {
                 elem.style.opacity = 0.25;
            }
        });
    };
</script>

<div>
    <Scroller layout="left">
        {#snippet sticky()}
            <div>
                {#if duckIsVisible}
                <h2>Segregation Index Through Years</h2>
                    <img
                        class="duck-img"
                        src="Graph1.png"
                        alt="Graph showing segregation index"
                        in:fly={{ y: 200, duration: 1000 }}
                        out:fade
                    />
                    <div>
                        
                        <p>
                            STARs (skilled through alternative routes): workers who have not completed a four-year college degree but have skills and experience that qualify them for skilled jobs.
                        </p>
                    </div>
                {/if}
                <br />
            
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ObservedArticleText callback={removeDuckCallback} {options}>
                A study conducted by <strong> <a href="https://www.nber.org/papers/w31641">NBER</a></strong> further investigated the <strong>occupational segregation by race and education</strong> over time.
                They examined whether occupational segregation between Black and White workers is <strong>similar in magnitude</strong> among
                workers with a Bachelor’s degree as it is among workers who do not have a Bachelor’s degree.
                <br />
                <br />
                 Hypothesis was that observed racial occupational segregation is <strong>greater than it would be</strong> if workers were randomly
distributed in the labor market.
                <br />
            </ObservedArticleText>

            <ObservedArticleText callback={showDuckCallback} {options}>
                The anylisis revealed that <strong>segregation between Black and White workers holding a Bachelor’s degree is
                similar to segregation between Black and White workers without a Bachelor’s degree</strong> with magnitude of rougly 0.28 (meaning 28% of workers would need to change
occupations for these two groups to be evenly distributed across all occupations).
            </ObservedArticleText>

            <ObservedArticleText callback={removeDuckCallback} {options}>
               <strong>Regardless of educational attainment, considerable occupational
segregation between Black and white workers persists.</strong> Even as college attendance has increased
among Black Americans, the observed distribution of occupations to which Black workers have
access significantly deviates from what would be expected in a race-neutral labor market. 
                <br />
                <br />
                This suggests that the <strong>labor market remains influenced by systemic factors that limit opportunities for Black workers</strong>, even among those with higher education.
            </ObservedArticleText>

        
        {/snippet}
    </Scroller>
</div>


<style>
    .duck-img {
        width: 100%;
        max-width: 600px;
        height: auto;
        opacity: 1;
        transition: opacity 0.1s ease-in-out;
    }
     h2 {
        font-size: 1.8rem;
        color: #F0BF56;
        margin-bottom: 1.5rem;
        
        font-family: "Tomorrow", sans-serif;
        font-weight: 600;
        font-style: normal;
    }
    p {
        font-size: 1rem;
        color: #f7f5eb;
        margin-top: 0;
        font-family: "Tomorrow", sans-serif;
        font-weight: 400;
        font-style: normal;
    }
    </style>