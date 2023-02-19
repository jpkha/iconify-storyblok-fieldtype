<script>
const Fieldtype = {
  mixins: [window.Storyblok.plugin],
  template: `
  <div>
     <div class="uk-text-center" v-if="model.icon">
     <div> Selected : <span style="font-weight: bold">{{ model.icon }}</span></div>
     <div style="height: 48px; width: auto; padding:8px;display: flex; align-items:center; justify-content:center;">
      <iconify-icon v-bind:icon="model.icon" style="height: 48px; width: auto; font-size: 48px"></iconify-icon>
      <small style="cursor:pointer;" @click="removeIcon">(remove)</small>  
    </div>
    </div>
    <form class="uk-form" @submit.prevent="search">
      <div class="uk-margin">
        <input class="uk-input uk-form-width-medium" v-model="query" placeholder="Search icon" />
        <button class="uk-button uk-button-default" type="submit">Search</button>
      </div>
    </form>
    
    <span v-for="icon in iconify" :key="icon" style="cursor:pointer;" @click="setItem(icon)"
      style="margin: 5px; height: 24px; width: auto; display: inline-block;">
      <iconify-icon v-bind:icon="icon" style="font-size: 24px"></iconify-icon>
    </span>
  </div>`,
    data() {
    return {
      iconify: [],
      query: '',
    }
  },
  methods: {
    search() {
      return fetch(`https://api.iconify.design/search?query=${this.query}`)
      .then((response) => response.json())
      .then((data) => {
        this.iconify = data.icons;
      });
    },
    initWith() {
      return {
        plugin: 'iconify',
        icon: '',
      }
    },
    setItem(name) {
      this.model.icon = name;
    },
    removeIcon() {
      this.model.icon = '';
    },
    pluginCreated() {
        this.$sb.getScript('https://code.iconify.design/iconify-icon/1.0.3/iconify-icon.min.js');
    }
  },
  watch: {
    'model': {
      handler: function (value) {
        this.$emit('changed-model', value);
      },
      deep: true
    }
  }
}
</script>

