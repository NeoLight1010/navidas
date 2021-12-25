<script lang="ts">
    import cool from "./assets/album/cool.jpg";
    import jiji from "./assets/album/jiji.jpg";
    import jsjs from "./assets/album/jsjs.jpg";
    import uuuh from "./assets/album/uuuh.jpg";
    import trono from "./assets/album/trono.jpg";
    import laguito from "./assets/album/laguito.jpg";
    import muyCool from "./assets/album/muy-cool.jpg";
    import perroton from "./assets/album/perroton.jpg";
    import princesa from "./assets/album/princesa.jpg";

    const allGifts = [
        cool,
        jiji,
        jsjs,
        uuuh,
        trono,
        laguito,
        muyCool,
        perroton,
        princesa,
    ];

    const giftPathMap: Map<number, string> = new Map();
    for (let i = 0; i < allGifts.length; i++) {
        giftPathMap.set(i, allGifts[i]);
    }

    export let revealedGifts: Map<
        number,
        { path: string; left: number; top: number }
    > = new Map();

    const revealRandomGift = () => {
        if (giftPathMap.size == 0) return;

        const randomKey = [...giftPathMap.keys()][
            Math.floor(Math.random() * giftPathMap.size)
        ];

        const path = giftPathMap.get(randomKey);
        giftPathMap.delete(randomKey);

        // Get random position
        const left = Math.floor(Math.random() * 100);
        const top = Math.floor(Math.random() * (25));

        revealedGifts.set(randomKey, { path, left, top });
        revealedGifts = revealedGifts;
    };
</script>

<main>
    <!-- Positions should be from left: [48%, 70%], and top: [0%, 25%] -->
    <div id="gift-box">
        {#each [...revealedGifts.entries()] as [id, { path, left, top }] (id)}
            <img
                class="gift"
                style="left: {left}%; top: {top}%"
                src={path}
                alt="sorpresa!"
                width="200px"
            />
        {/each}
    </div>

    <div id="front">
        <h1>navitas</h1>

        <button on:click={revealRandomGift}>Sorpresa :0</button>
    </div>
</main>

<style>
    :global(body) {
        height: 100vh;
        background-color: #f3f4f6;
        overflow: hidden;
    }

    h1 {
        color: #cb0b0a;
    }

    #front {
        position: absolute;

        left: 50%;
        bottom: 50%;
        transform: translateX(-50%) translateY(50%);;

        text-align: center;

        background-color: #004733;

        width: 10em;
        padding: 10px;

        border: solid;
        border-radius: 10%;
        border-color: #a5c1ae;
        border-width: thick;
    }

    #gift-box {
        height: 100vh;
        width: 100vw;

        position: absolute;
    }

    .gift {
        position: absolute;
        transform: translateX(-50%) translateY(50%);;
    }
</style>
