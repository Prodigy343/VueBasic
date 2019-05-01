<template lang="pug">
    li
        a(:href="artist.url" target="_blank")
            h2
                |   {{artist.name}}
            img(:src="artist.image[2]['#text']")
</template>

<script>
export default {
    name: 'artist',
    props: ['artist']
}
</script>
