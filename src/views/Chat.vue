<template>
    <div id="tarkjs-container" class="chat">
        <i>Loading Chat...</i>
    </div>
</template>

<style lang="scss">
.chat {
    width: 90%;
    height: 500px;
    margin: 30px;
}
</style>

<script>
import Talk from 'talkjs'
export default {
    name: 'InBox',
    props: {
        currentUser: {
            type: Object,
            required: true,
        }
    },
    mounted: function() {
        Talk.ready.then(function() {
            var me = new Talk.User({
                id: currentUser.id,
                name: currentUser.name,
                email: currentUser.email,
                photoUrl: currentUser.photo,
                welcomeMessage: "Hey there! How are you? :-)",
            })
        })
    }
}

window.talkSession = new TalkSession({
    appId: process.env.VUE_APP_CHAT_API_ID,
    me: me,
})
</script>