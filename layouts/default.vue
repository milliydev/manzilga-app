<template>
  <div>
    <LayoutHeader />
    <main>
      <AboutSection/>
      <Testimoialsectin/>
      <slot />
]       <CWhychooseus/>
      <COurservices/>
      <BlogSection/>
      <CommonCOurservices/>
      <CommonCContact/>
      <COurteam/>
      <CCompanyLogo/>


    </main>
    <LayoutFooter />
  </div>
</template>
<script setup lang="ts">
import AboutSection from  "~/components/Common/AboutSection.vue";
import Testimoialsectin from "~/components/Common/Testimoialsectin.vue";
import CWhychooseus from "~/components/Common/CWhychooseus.vue";
import COurteam from "~/components/Common/COurteam.vue";
import CCompanyLogo from "~/components/Common/CCompanyLogo.vue";
</script>