<script setup>
import fire from '../assets/fire.svg'
import { url, log } from '../firebase.js'
import { DotsVerticalIcon } from '@heroicons/vue/outline'
import PanelWrapper from '../components/PanelWrapper.vue'
import LinkCard from '../components/LinkCard.vue'

log('web/about')
let guide = $ref({})

async function init () {
  guide = {
    desktop: await url('web/guide_desktop.png'),
    android: await url('web/guide_android.png'),
    ios: await url('web/guide_ios.png')
  }
}
init()
</script>

<template>
  <div class="pb-60 min-h-full relative flex flex-col items-center text-center">
    <div class="w-full relative overflow-hidden" style="max-height: 24rem;">
      <img class="w-full h-full" src="https://my.sa.ucsb.edu/catalog/Current/Images/photo_catalognoborder.jpg">
      <div class="absolute top-0 h-full w-full bg-white opacity-60" />
      <div class="absolute top-0 h-full w-full flex flex-col justify-center" style="color: #0b254e;">
        <h1 class="text-3xl sm:text-5xl font-bold mt-2">We are here for <br> your success.</h1>
      </div>
    </div>
    <div class="p-4 sm:p-10 w-full" style="max-width: 800px;">
      <h2 class="text-xl mt-20 mb-4 font-bold">What's GoGaucho?</h2>
      <p>GoGaucho is the best campus app for UCSB students. <br class="hidden sm:block"> GoGaucho Web is the next generation WebApp, which is designed to serve UCSB students anywhere, anytime, and on any platforms.</p>
      <h2 class="text-xl mt-20 mb-4 font-bold">How to install?</h2>
      <p>Follow the instructions for better experiences.</p>
      <panel-wrapper title="Desktop (Chrome)" class="bg-white mt-4">
        <img class="w-full" :src="guide.desktop">
        <p class="text-left p-2">Open Google Chrome browser and visit <b>ucsb.app</b>, click the install icon on the address bar and install the WebApp to your computer. After installing, you can open GoGaucho as an App from your desktop or Home menu.</p>
      </panel-wrapper>
      <panel-wrapper title="Android (Chrome)" class="bg-white">
        <img class="w-full" :src="guide.android">
        <p class="text-left p-2">Open Google Chrome browser (or any supporting browser) and visit <b>ucsb.app</b>, click the top-right <dots-vertical-icon class="w-5 inline border border-gray-300" /> icon to open the menu, and then click <b>Install app</b>. After installing, you can open GoGaucho as an App from your home screen.</p>
      </panel-wrapper>
      <panel-wrapper title="iOS (Safari)" class="bg-white">
        <img class="w-full" :src="guide.ios">
        <p class="text-left p-2"><b>Only Safari browser can work with WebApp on iOS.</b><br>Open Safari browser and visit <b>ucsb.app</b>, click the sharing button at the bottom(on iPhones) or at the top-right(on iPads), and then click <b>Add to Home Screen</b>. After installing, you can open GoGaucho as an App from your home screen.</p>
      </panel-wrapper>
      <h2 class="text-xl mt-20 mb-4 font-bold">How to navigate?</h2>
      <p>The top-left icon can bring you back to homepage. <br class="hidden sm:block"> You can login to your UCSB Google account on the top-right corner.</p>
      <h2 class="text-xl mt-20 mb-4 font-bold">How does it work?</h2>
      <p>GoGaucho is developed and maintained by UCSB students independently. GoGaucho obtains data from various sources. We are not permitted to store your personal data (schedule etc.) in any form. <b>Your personal data is directly passed from official UCSB server to your devices under proper authorization. </b></p>
      <h2 class="text-xl mt-20 mb-4 font-bold">How to contact us?</h2>
      <p>You are welcomed to contact us for bug reports, feature suggestions, and joining applications. We appreciate your precious ideas and valuable experiences.</p>
      <div class="my-4 flex justify-center flex-wrap">
        <link-card class="m-1 w-full sm:w-64" title="Email" description="gogauchoapp@ucsb.edu" href="mailto:gogauchoapp@ucsb.edu" icon="/icons/logo.png" />
        <link-card class="m-1 w-full sm:w-64" title="Discord" description="Join GoGaucho Server" href="https://discord.gg/64jqp8Z3xH" icon="/icons/links/discord.png" />
        <link-card class="m-1 w-full sm:w-64" title="Twitter" description="Follow @GoGauchoApp" href="https://twitter.com/GoGauchoApp" icon="/icons/links/Twitter.png" />
        <link-card class="m-1 w-full sm:w-64" title="Instagram" description="Follow @GoGauchoApp" href="https://www.instagram.com/GoGauchoApp/" icon="/icons/links/Instagram.png" />
      </div>
    </div>
    <img class="w-40 sm:w-60 absolute bottom-0" :src="fire">
  </div>
</template>
