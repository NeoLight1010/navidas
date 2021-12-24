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

    const giftMap: Map<number, string> = new Map();
    for (let i = 0; i < allGifts.length; i++) {
        giftMap.set(i, allGifts[i]);
    }

    export let revealedGifts: Map<number, string> = new Map();

    const revealRandomGift = () => {
        const randomKey = [...giftMap.keys()][Math.floor(Math.random() * giftMap.size)];

        const gift = giftMap.get(randomKey);
        giftMap.delete(randomKey);

        revealedGifts.set(randomKey, gift);
        revealedGifts = revealedGifts;

        console.log(giftMap);
        console.log(revealedGifts);
    };
</script>

<main>
    <h1>navitas</h1>

    <button on:click={revealRandomGift}>Sorpresa :0</button>

    {#each [...revealedGifts.entries()] as [id, path] (id)}
      <img src={path} alt="sorpresa!" width="200px" />
    {/each}
</main>

<style>
    :global(body) {
        height: 100vh;
        background-color: #f3f4f6;
    }

    h1 {
        color: #cb0b0a;
    }
</style>
