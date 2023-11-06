<script lang="ts">
    import { onMount } from "svelte";

    export let timeString = "(loading...)";
    export let dif = (new Date("2024-01-12")).getTime() - (new Date).getTime();

    onMount(() => {
        onTick();
        const tick = setInterval(() => {
            onTick();
            dif -= 1000;
        }, 1000);

        return () => clearInterval(tick);
    });

    const onTick = () => {
        dif = (new Date("2024-01-12")).getTime() - (new Date).getTime();
        let total = dif / 1000;

        const hours = Math.floor(total / 3600);
        total %= 3600;
        const minutes = Math.floor(total / 60);
        const seconds = Math.floor(total % 60);

        timeString = `(${hours}h ${minutes}min ${seconds}s)`;
    }

</script>

<div class="container">
    <div class="canvas">
        <div class="platform p1">

        </div>
        <div class="platform p2" />
        <div class="platform p3" />
    
        <div class="tree t1" />
        <div class="tree t2" />
    
    </div>
    <div class="moon" />
    <main>
        <article class="header">
            <!-- svelte-ignore a11y-missing-attribute -->
            <ul><a>OTA</a><a>JAMIT </a><a>2024</a></ul>
        </article>
    
        <div class="info">
            <article>
                <h1>Missä</h1>
                <h2>Otaniemen Lukio</h2>
            </article>
            <article>
                <h1>Aihe</h1>
                <h2>???</h2>
                <h3>{timeString}</h3>
            </article>
            <article>
                <h1>Milloin</h1>
                <h2>12.1.2024 - 14.1.2024  </h2>
            </article>
        </div>

        <div class="discord">
            <div class="logo" />
            <div class="qr-code" />
        </div>

        <footer class="sponsors">
            <div class="logo hy" />
            <div class="logo fgj" />
            <div class="logo lukema" />
        </footer>
    </main>
</div>


<style>
    .container {
        position: absolute;
        width: 100%;
        height: 100%;
        z-index: 0;

        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
    }

    main {
        position: absolute;
        width: 100%;
        height: 100%;

        max-width: 2100px;

        align-self: flex-start;

        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
    }

    .header {
        position: absolute;
        top: 10%;

        z-index: 7;
    }

    .header ul a {
        font-size: 100px;
        font-family: 'title';
    }

    .header ul a:nth-child(1) {
        color: var(--cyan);
        text-shadow: var(--cyan-dark) 7px 7px;
    }

    .header ul a:nth-child(2) {
        color: var(--pink);
        text-shadow: var(--pink-dark) 7px 7px;
    }

    .header ul a:nth-child(3) {
        color: var(--yellow);
        text-shadow: var(--orange) 7px 7px;
    }

    .info {
        position: absolute;
        width: 50%;
        height: auto;

        right: 5%;
        top: 30%;

        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: space-evenly;

        z-index: 7;

        flex-wrap: wrap;
    }

    .info article {
        min-width: 250px;
        width: 33%;

        height: 175px;

        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .info article h1 {
        font-size: 30px;
        margin: 10px;

        color: var(--pink);
        text-shadow: var(--pink-dark) 3px 3px;

        text-align: center;
    }

    .info article h2 {
        font-size: 40px;
        letter-spacing: 2px;

        color: var(--cyan);
        text-shadow: var(--cyan-dark) 3px 3px;

        text-align: center;
    }

    .info article h3 {
        color: var(--yellow);
        text-shadow: var(--orange) 3px 3px;

        font-size: 30px;
    }

    .discord {
        position: absolute;
        width: 150px;
        height: 150px;

        right: 10px;
        bottom: 10px;

        padding: 5px;

        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;

        z-index: 7;
    }

    .discord .logo {
        width: 90%;
        height: 40px;

        background-position: center center;
        background-size: contain;
        background-repeat: no-repeat;
        background-image: url(/img/discord-logo-black.png);
    }

    .discord .qr-code {
        width: 120px;
        height: 120px;

        border-radius: 5px;

        background-position: center center;
        background-size: cover;
        background-image: url(/img/qr-code.png);
    }

    .canvas {
        position: absolute;
        width: 100%;
        height: 100%;

        max-width: 2100px;

        align-self: flex-start;
        background-color: var(--cyan-darker);

        overflow: hidden;
    }

    .platform {
        position: absolute;
        border: solid var(--debug);
    }

    .platform.p1 {
        width: 1100px;
        height: 250px;

        left: -10px;
        bottom: -20px;
        z-index: 5;

        background-position: top center;
        background-size: 90% 90%;
        scale: 1.1;
        background-repeat: no-repeat;
        background-image: url(/img/p1.png);
    }

    .platform.p2 {
        width: 1000px;
        height: 200px;

        left: 0;
        bottom: 200px;
        z-index: 4;

        background-position: center center;
        background-size: cover;
        background-repeat: no-repeat;
        background-image: url(/img/p2.png);
    }

    .platform.p3 {
        width: 450px;
        height: 260px;

        left: calc(3% + 6%);
        bottom: calc(200px + 190px);
        z-index: 3;

        background-position: top center;
        background-size: cover;
        background-repeat: no-repeat;
        background-image: url(/img/p3.png);
    }

    .tree {
        position: absolute;
        border: solid var(--debug);
        z-index: 6;
    }

    .tree.t1 {
        width: 250px;
        height: 310px;

        bottom: 220px;
        left: calc(5% + 5%);

        z-index: 4;

        background-position: center center;
        background-size: cover;
        background-repeat: no-repeat;
        background-image: url(/img/t1.png);
    }

    .tree.t2 {
        width: 300px;
        height: 375px;

        bottom: calc(200px + 190px);
        left: calc(5% + 30%);

        z-index: 3;

        background-position: center center;
        background-size: cover;
        background-repeat: no-repeat;
        background-image: url(/img/t2.png);
    }

    .moon {
        position: absolute;
        top: 5%;
        right: 5%;

        width: 200px;
        height: 200px;

        background-position: center center;
        background-size: cover;
        background-repeat: no-repeat;
        background-image: url(/img/moon.png);
    }

    .sponsors {
        position: absolute;
        width: 1000px;
        height: 200px;

        left: 0px;
        bottom: 0px;

        z-index: 8;

        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: flex-start;

        border: solid var(--debug);

        flex-wrap: wrap;
    }

    .sponsors .logo {
        width: 100px;
        height: 100px;
        margin: 20px;

        background-position: center center;
        background-repeat: no-repeat;
        background-size: contain;

    }

    .logo.hy {
        background-image: url(/img/hy-logo.png);
    }

    .logo.fgj {
        width: 75px;
        height: 75px;
        background-image: url(/img/fgj-logo.png);
    }

    .logo.lukema {
        width: 125px;
        height: 125px;
        background-image: url(/img/lukema-logo.png);
    }

    @media screen and (max-width: 1250px) {
        .header a {
            text-align: center;
            font-size: 75px;
        }

        .info {
            width: 100%;
            right: 0;
        }

        .platform.p1 {
            left: 0;
        }

        .platform.p2 {
            left: 5%;
        }

        .platform.p3 {
            left: calc(5% + 6%);
        }
    }

    @media screen and (max-width: 650px) {
        .header a {
            font-size: 50px;
        }
    }
</style>