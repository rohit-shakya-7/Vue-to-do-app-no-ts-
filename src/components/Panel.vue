<template>

    <div class="header">
        <h1>
            <slot />
        </h1>
    </div>

</template>

<script>

export default {
    name: 'Panel',
    props: {
        heading: String,
    }
}

</script>