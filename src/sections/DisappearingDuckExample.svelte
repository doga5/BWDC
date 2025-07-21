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
                // "active" state
                elem.style.opacity = 1;
            } else if (entry.intersectionRatio < 0.9) {
                // "inactive" state
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
                    <img
                        class="duck-img"
                        src="duck.png"
                        alt="KWK rubber duck!"
                        in:fly={{ y: 200, duration: 2000 }}
                        out:fade
                    />
                {/if}
                <br />
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ObservedArticleText callback={removeDuckCallback} {options}>
                A study conducted by NBER further investigated the occupational segregation by race and education over time.
                They examined whether occupational segregation between Black and White workers is similar in magnitude among
                workers with a Bachelor’s degree as it is among workers who do not have a Bachelor’s degree.
                <br />
                <br />
                 Hypothesis was that observed racial occupational segregation is greater than it would be if workers were randomly
distributed in the labor market.
                <br />
            </ObservedArticleText>

            <ObservedArticleText callback={showDuckCallback} {options}>
                The anylisis revealed that segregation between Black and White workers holding a Bachelor’s degree is
                similar to segregation between Black and White workers without a Bachelor’s degree with magnitude of rougly 0.28 (meaning 28% of workers would need to change
occupations for these two groups to be evenly distributed across all occupations).
            </ObservedArticleText>

            <ObservedArticleText callback={removeDuckCallback} {options}>
                Regardless of educational attainment, considerable occupational
segregation between Black and white workers persists. Even as college attendance has increased
among Black Americans, the observed distribution of occupations to which Black workers have
access significantly deviates from what would be expected in a race-neutral labor market. 
                <br />
                <br />
                This suggests that the labor market remains influenced by systemic factors that limit opportunities for Black workers, even among those with higher education.
            </ObservedArticleText>

        
        {/snippet}
    </Scroller>
</div>


