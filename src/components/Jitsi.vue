<template>
  <vue-jitsi-meet
    ref="jitsiRef"
    domain="meet.jit.si"
    :options="jitsiOptions"
  ></vue-jitsi-meet>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import { JitsiMeet } from '@mycure/vue-jitsi-meet';

@Component({
  components: {
    "vue-jitsi-meet": JitsiMeet,
  }
})
export default class Jitsi extends Vue {
  get jitsiOptions () {
      return {
        roomName: 'some-room-name',
        noSSL: false,
        userInfo: {
          email: 'user@email.com',
          displayName: '',
        },
        configOverwrite: {
          enableNoisyMicDetection: false
        },
        interfaceConfigOverwrite: {
          SHOW_JITSI_WATERMARK: false,
          SHOW_WATERMARK_FOR_GUESTS: false,
          SHOW_CHROME_EXTENSION_BANNER: false
        },
        onload: this.onIFrameLoad
      };
  }

  onIFrameLoad (): void {
    (this.$refs.jitsiRef as any).addEventListener('participantJoined', this.onParticipantJoined);
  }

  onParticipantJoined (e): void {
    console.log("participant joined " + e)
  }
}
</script>

<style scoped lang="scss">

</style>
