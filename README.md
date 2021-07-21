# Develop 
##Preparation
###Installation Nodejs 
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
VUE_APP_TENANT= eb6146d6-657c-4b0a-a820-2a782fa9bbe6
VUE_APP_CLIENT_ID= 84565fc3-4af0-4a8f-afe3-b2ca03694855
VUE_APP_SECRET= 58-YTMlz-h3ckanthAp.15M0~S--jg3cRq

VUE_APP_XSCOPE='openid profile offline_access User.Read Mail.Send'
VUE_APP_MSLOGIN=https://login.microsoftonline.com/

VUE_APP_DATA_MOC= https://dataapi.moc.go.th/juristic
```

Create .env.local 
```
VUE_APP_TITLE = Partner Portal (Develop)
VUE_APP_REDIRECT = http://localhost:8080
VUE_APP_LOGOUT = http://localhost:8080
VUE_APP_USER_PROFILES = http://localhost:3000/user
VUE_APP_COMPANY_PROFILES = http://localhost:3000/CompanyProfiles
VUE_APP_MENU = http://localhost:3000/Menu
VUE_APP_VST_LOGO = http://localhost:8080/logo.png
VUE_APP_DELER = http://localhost:3000/Deler
VUE_APP_GET_DELER = http://localhost:3000/Deler?AccountIdentifier=057de32f-12cd-4a9e-bdd5-22d95b2744d3
VUE_APP_TITLE = Dynamic Portal (Develop)
VUE_APP_REDIRECT = http://localhost:8080
VUE_APP_LOGOUT = http://localhost:8080

VUE_APP_CONTENT = http://localhost:3000/content
VUE_APP_QUEST = http://localhost:3000/quest
VUE_APP_RESULT = http://localhost:3000/result
VUE_APP_ACHIVE = http://localhost:3000/achieve
```
Create .env.production 
```
VUE_APP_TITLE=Dynamic Portal 
VUE_APP_REDIRECT = https://vpartner.z23.web.core.windows.net/
VUE_APP_LOGOUT = https://vpartner.z23.web.core.windows.net/
VUE_APP_USER_PROFILES = https://vpartnerapi.azurewebsites.net/user
VUE_APP_COMPANY_PROFILES = https://vpartnerapi.azurewebsites.net/CompanyProfiles
VUE_APP_MENU = https://vpartnerapi.azurewebsites.net/Menu
VUE_APP_VST_LOGO = https://vpartner.z23.web.core.windows.net/logo.png
VUE_APP_DELER = https://vpartnerapi.azurewebsites.net/Deler
VUE_APP_GET_DELER = https://vpartnerapi.azurewebsites.net/Deler?AccountIdentifier=057de32f-12cd-4a9e-bdd5-22d95b2744d3
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