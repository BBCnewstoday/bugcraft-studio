<template>
  <div class="container">
    <div class="columns">
     <div class="column">
        <div class="tabs is-boxed">
          <spectateMenu></spectateMenu>
        </div>
        <div data-id="spectateSettings" class="">
           <div class="columns">
              <div class="column">
                 <div class="field">
                    <label class="label is-normal">Pan x</label>
                    <p class="control">
                       <input class="input range ltpurple" type="range">
                    </p>
                 </div>
                 <div class="field">
                    <label class="label is-normal">Pan y</label>
                    <p class="control">
                       <input class="input range ltpurple" type="range">
                    </p>
                 </div>
                 <div class="field">
                    <label class="label is-normal">Pan z</label>
                    <p class="control">
                       <input class="input range ltpurple" type="range">
                    </p>
                 </div>
              </div>
              <div class="column">
                 <label class="label is-normal">Spectate options</label>
                 <div class="field">
                    <input type="checkbox" id="toggle_spectate" name="toggle_spectate" data-id="ENABLE_SPECTATOR" v-on:click="sendMessage" />
                    <label for="toggle_spectate"><span></span>Toggle Spectate Mode (F3)</label>
                 </div>
                 <div class="field">
                    <input type="checkbox" id="toggle_collision" name="toggle_collision" />
                    <label for="toggle_collision"><span></span>Toggle Collision</label>
                 </div>
                 <div class="field">
                    <input type="checkbox" id="toggle_look_at_target" name="toggle_look_at_target" />
                    <label for="toggle_look_at_target"><span></span>Look at selected unit</label>
                 </div>
                 <div class="field">
                    <input type="checkbox" id="toggle_follow_target" name="toggle_follow_target" />
                    <label for="toggle_follow_target"><span></span>Follow target</label>
                 </div>
              </div>
              <div class="column">
                 <div class="field">
                    <label class="label is-normal">Speed</label>
                    <p class="control">
                       <input class="input range ltpurple" name="speed" type="range" min="0.01" max="1.4" step="0.005" value="0.7" v-on:input="setSpeed" >
                    </p>
                 </div>
                 <div class="field">
                    <cameraViewer />
                 </div>
              </div>
           </div>
        </div>
     </div>
    </div>
  </div>
</template>

<script>
  const BugCraft = window.BugCraft;
  export default {
    name: 'spectate',
    components: {
      spectateMenu: require('./spectateMenu'),
      cameraViewer: require('./cameraViewer'),
    },
    methods: {
      sendMessage(element) {
        const domElement = element.currentTarget;
        const messageId = domElement.getAttribute('data-id');
        BugCraft.sendMessage(messageId);
      },
      setSpeed() {},
    },
    data() {
      return {};
    },
  };
</script>
