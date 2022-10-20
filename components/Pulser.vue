<template>
    <div class="pulser-container">
        <div class="pulser first"></div>
        <div class="pulser second"></div>
        <div class="pulser third"></div>
    </div>
</template>

<style scoped>
.pulser-container {
    display: flex;
    gap: 3rem;
    padding: 1rem;
    margin: 1rem;
}
.pulser {
    width: 60px;
    height: 60px;
    background: rebeccapurple;
    border-radius: 50%;
    position: relative;
}

.pulser.first::after {
    animation: pulse 1000ms cubic-bezier(0.9, 0.7, 0.5, 0.9) infinite;
}

.pulser.second::after {
    animation: pulse 1000ms cubic-bezier(0.9, 0.7, 0.5, 0.9) infinite 250ms;
}

.pulser.third::after {
    animation: pulse 1000ms cubic-bezier(0.9, 0.7, 0.5, 0.9) infinite 500ms;
}

@keyframes pulse {
    0% {
        opacity: 0;
    }
    50% {
        transform: scale(1.4);
        opacity: 0.4;
    }
}

.pulser::after {
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    background: blueviolet;
    border-radius: 50%;
    z-index: -1;
}
</style>
