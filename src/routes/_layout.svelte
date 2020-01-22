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
		position: relative;
		max-width: 56em;
		background-color: white;
		padding: 2em;
		margin: 0 auto;
		box-sizing: border-box;
	}
</style>

<Nav />

<main>
	<slot></slot>
</main>