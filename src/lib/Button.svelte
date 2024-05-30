<script>
    export let shadow = false;
    export let size = "small";
</script>

<button class:size-lg={size=='large'} class:size-sm={size=='small'} class:shadow><slot>Fallback</slot></button>

<style lang="scss">
    button {
        border: none;
        background-color: #ff3e00;
        color: #ffffff;
        padding: 15px 20px;
        font-weight: bold;
        border-radius: 5px;
        cursor: pointer;
        &.size-sm {
            padding: 15px 20px;
        }
        &.size-lg {
            padding: 20px 25px;
            font-size: 20px;
        }
        &.shadow {
            box-shadow: 0 0 10px rgba(6, 42, 245, 0.3);
        }
    }
</style>