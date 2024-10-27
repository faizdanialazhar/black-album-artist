<script setup>
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue'

const isShown = ref(false)
const isShown1 = ref(false)
const isShown2 = ref(false)
const isShown3 = ref(false)

const artists = [
 {
   name: "KSI",
   albums: 4,
   topTrack: "Not Over Yet",
   monthlyListeners: "12.5M",
   latestAlbum: "THICK OF IT (2024)",
   awards: "2x Platinum Singles",
   genres: ["Hip-Hop", "Pop", "R&B"],
   ref: isShown,
   image: "https://cdns-images.dzcdn.net/images/artist/73b03326a24e59f01b3c91a7d9537773/1900x1900-000000-80-0-0.jpg",
   youtubeLink:'https://youtu.be/At8v_Yc044Y?si=gm_HMA-vSOx-rQQm&t=50'

},
 {
   name: "KAI CENAT",
   followers: "8.7M", 
   platform: "Twitch",
   achievements: "Streamer of the Year 2023",
   activeYears: "2018-Present",
   topCategories: ["Just Chatting", "Reactions", "Gaming"],
   ref: isShown1,
   image: "https://imageio.forbes.com/specials-images/imageserve/65120b9054b995830f7721b2/0x0.jpg?format=jpg&crop=3114,3120,x54,y122,safe&height=416&width=416&fit=bounds",
   youtubeLink:'https://youtu.be/xF6NQABwlck?si=fdrAb2jUenSp4xzd'

},
 {
   name: "DRAKE",
   albums: 8,
   topTrack: "God's Plan",
   monthlyListeners: "78.5M",
   latestAlbum: "For All The Dogs (2023)",
   awards: "5 Grammy Awards",
   recordLabel: "OVO Sound",
   genres: ["Hip-Hop", "R&B", "Pop Rap"],
   ref: isShown2,
   image: "https://cdn.i-scmp.com/sites/default/files/styles/768x768/public/d8/images/canvas/2023/10/17/737f015c-a9ef-4020-9df5-83a9bc70ff96_5ed13648.jpg?itok=akNoFjFy&v=1697537122",
   youtubeLink:'https://www.youtube.com/watch?v=xpVfcZ0ZcFM'
 
},
 {
   name: "ISHOWSPEED",
   followers: "21M",
   platform: "YouTube",
   avgViewers: "200K+",
   topCategories: ["Gaming", "Reactions", "Music"],
   achievements: "Breakout Creator 2022",
   activeYears: "2020-Present",
   ref: isShown3,
   image: "https://i.scdn.co/image/ab67616d00001e02a59bbf995c83b71d3345f281",
   youtubeLink:'https://youtu.be/nILv4VN9IaA?si=NF5TMy_I8MDk4q2R&t=18'
 }
]
</script>

<template>
 <div class="w-full min-h-screen flex flex-col bg-gradient-to-b from-amber-100 to-orange-100">
   <header class="mx-auto my-8 text-5xl font-serif">
     <span class="bg-clip-text text-transparent bg-gradient-to-r from-orange-600 to-pink-600">
       Featured Black Artists
     </span>
   </header>

   <div class="flex flex-wrap justify-center gap-8 mx-auto my-auto px-4">
     <div v-for="artist in artists" 
          :key="artist.name"
          class="group relative"
          @mouseenter="artist.ref = true" 
          @mouseleave="artist.ref = false">
       <div class="album-card transform transition-all duration-300 group-hover:scale-105">
         <img :src="artist.image"
              :alt="`${artist.name} Photo`"
              class="w-64 h-64 object-cover rounded-lg shadow-lg p-2 bg-white/70 backdrop-blur-sm" 
              loading="lazy" />

         <!-- Hover Info Card - Now with transition -->
         <div class="absolute top-0 left-0 w-full h-full rounded-lg overflow-hidden">
           <div class="absolute inset-0 bg-black/60 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
           <div class="absolute inset-0 p-4 text-white transform translate-y-full group-hover:translate-y-0 transition-transform duration-300">
             <h2 class="text-2xl font-bold mb-2">{{ artist.name }}</h2>
             
             <!-- Music Artist Details -->
             <template v-if="artist.monthlyListeners">
               <div class="space-y-1 text-sm">
                 <p class="font-medium">{{ artist.monthlyListeners }} Monthly Listeners</p>
                 <p>{{ artist.latestAlbum }}</p>
                 <p>{{ artist.topTrack }}</p>
                 <p>{{ artist.awards }}</p>
                 <div class="flex flex-wrap gap-1 mt-2">
                   <span v-for="genre in artist.genres" 
                         :key="genre"
                         class="px-2 py-0.5 bg-white/20 rounded-full text-xs">
                     {{ genre }}
                   </span> 
                   <a class="w-full bg-white/30 rounded-full px-3 py-2 text-center" :href="artist.youtubeLink" target="_blank">YouTube</a>
                 </div>
               </div>
             </template>

             <!-- Content Creator Details -->
             <template v-if="artist.followers">
               <div class="space-y-1 text-sm">
                 <p class="font-medium">{{ artist.followers }} Followers</p>
                 <p>{{ artist.platform }}</p>
                 <p>{{ artist.activeYears }}</p>
                 <p>{{ artist.achievements }}</p>
                 <div class="flex flex-wrap gap-1 mt-2">
                   <span v-for="category in artist.topCategories" 
                         :key="category"
                         class="px-2 py-0.5 bg-white/20 rounded-full text-xs">
                     {{ category }}
                   </span>
                   <a class="w-full bg-white/30 rounded-full px-3 py-2 text-center" :href="artist.youtubeLink" target="_blank">YouTube</a>
                 </div>
               </div>
             </template>
           </div>
         </div>
       </div>
     </div>
   </div>
 </div>
</template>

<style>
.album-card img {
 @apply transition-all duration-300;
}

.album-card:hover img {
 @apply shadow-2xl;
}
</style>