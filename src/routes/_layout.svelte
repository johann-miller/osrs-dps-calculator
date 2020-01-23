<script>
    import {currentUser} from "../stores/user.js"
	import {onMount} from 'svelte'
	import Nav from "../components/Nav.svelte"

    onMount(() => {
        firebase.auth().onAuthStateChanged(function(user) {
            if (user) {
                currentUser.set(user)
            } else {
                currentUser.set(null)
            }
        })
    })
</script>

<style>
	main {
        display: flex;
        flex-flow: column;
        align-items: center;
        min-height: calc(100vh - 3rem);
    }
</style>

<Nav />

<main>
	<slot></slot>
</main>