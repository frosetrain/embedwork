<script lang="ts">
    let value = $state("");
    let real = $state("");

    function handleSubmit(event: SubmitEvent & { currentTarget: EventTarget & HTMLFormElement }) {
        event.preventDefault();
        let begin = value.indexOf("?v=");
        if (begin >= 0) {
            real = value.slice(begin + 3);
        } else {
            real = value;
        }
        value = "";
    }
</script>

<form onsubmit={handleSubmit}>
    <label for="url">Video URL</label>
    <input bind:value type="text" id="url" name="url" />
    <input type="submit" value="Submit" />
</form>

{#if real}
    <p>{real}</p>
    <iframe
        width="560"
        height="315"
        src="https://www.youtube.com/embed/{real}"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
        referrerpolicy="strict-origin-when-cross-origin"
        allowfullscreen
    ></iframe>
{/if}
