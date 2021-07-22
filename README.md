# Develop

## Preparation

### Installation Nodejs 
https://nodejs.org/en/download/ 
run cmd terminal 
```
npm install -g @vue/cli
```
run Power shell terminal
```
npm install --global --production windows-build-tools
```
## Project Started 
###Vue project Create 
All Default selected 
```
vue create partner  
cd partner
vue add vuetify
vue add router
```
Create .eslintignore files 
``` 
/build/**
/coverage/**
/docs/**
/jsdoc/**
/templates/**
/tests/bench/**
/tests/fixtures/**
/tests/performance/**
/tmp/**
/tools/internal-rules/node_modules/**
/lib/rules/utils/unicode/is-combining-character.js
test.js
!.eslintrc.js
/src/**
```
add axios 
```
vue add axios
```

## Create Environment variable
Create .env 

```
 
```

Create .env.local 
```
 
```
Create .env.production 
```
 
```
add Authentication Module 
```
npm install vue-msal
```
edit @dynamic/src/main.js
```
import Vue from 'vue'
import './plugins/axios'
import App from './App.vue'
import vuetify from './plugins/vuetify';
import router from './router'
import msal from 'vue-msal' // For Authentication Module

Vue.config.productionTip = false 

// For Authentication Module
Vue.use(msal, {
  auth: {
    clientId: process.env.VUE_APP_CLIENT_ID,
    tenantId: process.env.VUE_APP_TENANT,
    redirectUri: process.env.VUE_APP_REDIRECT,
    scopes: process.env.VUE_APP_XSCOPE
  }
});
new Vue({
  vuetify,
  router,
  render: h => h(App)
}).$mount('#app')
```
# A grid layout system for Vue.js
Install Components  
```
npm install vue-grid-layout --save
```
# A ckeditor for Vue.js
Install Components  
```
npm install ckeditor4-vue --save
```

# v-runtime-template
A Vue.js components that makes easy compiling and interpreting a Vue.js template at runtime by using a v-html like API.

Install Components  
```
npm install v-runtime-template --save 
```
You must use the with-compiler Vue.js version. This is needed in order to compile on-the-fly Vue.js templates. For that, you can set a webpack alias for vue to the vue/dist/vue.common file.

For example, if you use the Vue CLI, create or modify the vue.config.js file adding the following alias:
```
// vue.config.js
module.exports = {
  runtimeCompiler: true
};
```
