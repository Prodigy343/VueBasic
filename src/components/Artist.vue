<!--template lang="pug">
    li
        h2: a(:href="artist.url" target="_blank")wer
        img(:src="artist.image[2]['#text']")
</template-->
<!--template>
    <li>
    {{artist.name}}
    </li>
</template-->
<template lang="pug">
    li
        h2: a(:href="artist.url" target="_blank")
            |   {{artist.name}}
        img(:src="artist.image[2]['#text']")
</template>

<script>
export default {
    name: 'artist',
    props: ['artist']
}
</script>
