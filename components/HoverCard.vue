<script setup lang="ts">
interface HoverCardInterface {
    title: String;
    subtitle: String;
}

const hoverCardData = defineProps<HoverCardInterface>();
const subtitleArray = hoverCardData.subtitle.split(" ");
</script>

<template>
    <div class="card">
        <div class="card-content">
            <h3 class="card-title">
                {{ hoverCardData.title }}
            </h3>
            <h4 class="card-subtitle">
                <span
                    v-for="(item, index) in subtitleArray"
                    :key="index"
                    class="card-subtitle-word"
                    :style="'transition-delay: ' + index * 40 + 'ms'"
                    >{{ item + " " }}</span
                >
            </h4>
        </div>
    </div>
</template>

<style>
:root {
    --card-border: rgb(3, 169, 244);

    --g1: rgb(98, 0, 234);
    --g2: rgb(236, 64, 122);
    --g3: rgb(253, 216, 53);
}

.card {
    aspect-ratio: 1/1.6;
    border: 0.5vmin solid var(--card-border);
    cursor: pointer;
    position: relative;
    width: 56vmin;
}
.card::before {
    background: linear-gradient(
        130deg,
        transparent 0% 33%,
        var(--g1) 66%,
        var(--g2) 83.5%,
        var(--g3) 100%
    );
    background-position: 0% 0%;
    background-size: 300% 300%;
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0px;
    top: 0px;
    pointer-events: none;
    transition: background-position 350ms ease, transform 350ms ease;
    z-index: 1;
}

.card:hover::before {
    background-position: 100% 100%;
    transform: scale(1.08, 1.03);
}

.card-content {
    background-image: radial-gradient(
        rgba(255, 255, 255, 0.2) 8%,
        transparent 8%
    );
    background-position: 0% 0%;
    background-size: 5vmin 5vmin;
    height: calc(100% - 10vmin);
    padding: 5vmin;
    position: relative;
    transition: background-position 350ms ease;
    width: calc(100% - 10vmin);
    z-index: 2;
}

.card:hover > .card-content {
    background-position: -10%, 0;
}

.card-title,
.card-subtitle {
    color: white;
    font-family: "Anek Latin", sans-serif;
    font-weight: 400;
    margin: 0px;
}

.card-title {
    font-size: 6vmin;
}

.card-subtitle {
    font-size: 3vmin;
    margin-top: 2vmin;
}

.card-subtitle-word {
    display: inline-block;
    margin: 0vmin 0.3vmin;
    opacity: 0;
    position: relative;
    transform: translateY(40%);
    transition: none;
}

.card:hover > .card-content > .card-subtitle > .card-subtitle-word {
    opacity: 1;
    transform: translateY(0%);
    transition: opacity 0ms, transform 200ms cubic-bezier(0.9, 0.06, 0.15, 0.9);
}
</style>
