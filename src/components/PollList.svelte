<script>
    import { fade, slide, scale } from 'svelte/transition';
    import { flip } from 'svelte/animate';
    import PollStore from '../store/PollStore';
    import PollDetails from "./PollDetails.svelte";
</script>

<div class="poll-list">
    {#each $PollStore as poll (poll.id)}
        <div in:fade out:slide|local animate:flip={{duration: 500}}>
            <PollDetails {poll} />
        </div>
    {/each}
</div>

<style>
    .poll-list {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 20px;
    }
</style>