<script>
    import {currentUser} from "../stores/user.js"
    import {onMount} from "svelte"
    
    function signIn() {
        let provider = new firebase.auth.GoogleAuthProvider()

        firebase.auth().signInWithRedirect(provider).then(function(result) {
            let user = result.user
        }).catch(function(error) {
            // Handle Errors here.
            var errorCode = error.code;
            var errorMessage = error.message;
            // The email of the user's account used.
            var email = error.email;
            // The firebase.auth.AuthCredential type that was used.
            var credential = error.credential;
        })
    }

    function signOut() {
        firebase.auth().signOut().then(function() {
            // Sign-out successful.
            renderSignIn()
        }).catch(function(error) {
            // An error happened.
        })
    }
</script>

{#if $currentUser}
    <button on:click="{signOut}">Sign out</button>
{:else}
    <button on:click="{signIn}">Sign in with Google</button>
{/if}
