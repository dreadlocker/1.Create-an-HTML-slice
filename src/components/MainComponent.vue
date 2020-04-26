<template>
  <div class="holder">
    <div class="header-content-holder">
      <Header
        :text="text"
        :textClasses="textClasses"
        :title="title"
        :titleClasses="titleClasses"
        :lastUpdated="lastUpdated"
        :lastUpdatedClasses="lastUpdatedClasses"
        :subTitle="subTitle"
        :subTitleClasses="subTitleClasses"
        :screenWidth="screenWidth"
      />
      
      <template v-if="screenWidth < 1024">
        <Content
          :renderIcons="true"
          :iconsSrcArray="iconsSrcArray"
          :svgClasses="'svg'"
          :renderTitles="true"
          :titlesArray="titlesArray"
          :contentTitleClasses="contentTitleClasses"
          :infosArray="infosArray"
          :infosClasses="infosClasses"
          :screenWidth="screenWidth"
        />
      </template>
      
      <template v-else>
        <Content
          :renderIcons="true"
          :iconsSrcArray="iconsSrcArrayForColumn1"
          :svgClasses="'svg'"
          :renderTitles="true"
          :titlesArray="titlesArrayForColumn1"
          :contentTitleClasses="contentTitleClasses"
          :infosArray="infosArrayForColumn1"
          :infosClasses="infosClasses"
          :screenWidth="screenWidth"
        />
        <Content
          :renderIcons="true"
          :iconsSrcArray="iconsSrcArrayForColumn2"
          :svgClasses="'svg'"
          :renderTitles="true"
          :titlesArray="titlesArrayForColumn2"
          :contentTitleClasses="contentTitleClasses"
          :infosArray="infosArrayForColumn2"
          :infosClasses="infosClasses"
          :screenWidth="screenWidth"
        />
      </template>
    </div>

    <Footer
      v-if="screenWidth < 1024"
      :footerText="footerText"
      :footerClasses="footerClasses"
    />
  </div>
</template>

<script>
import Header from "./Header.vue";
import Content from "./Content.vue";
import Footer from "./Footer.vue";

export default {
  name: "MainComponent",
  components: {
    Header,
    Content,
    Footer,
  },
  data() {
    return {
      // <Header>
      text: "Sync and Share",
      textClasses: "top-text",
      title: "Acronis Cyber Disaster Recovery Cloud",
      titleClasses: "title",
      lastUpdated: "Just Updated",
      lastUpdatedClasses: "bottom-text",
      subTitle: "A turnkey, self-service solution that lets you protect your customers’ workloads by recovering their IT systems and applications utilizing the Acronis cloud infrastructure.",
      subTitleClasses: "sub-title",
      // <Content>
      iconsSrcArray: [
        "0001_S_full_image_backup.svg",
        "0003_S_active_ransomware_protection.svg",
        ["0071_S_survival_kit.svg", "exclusive"],
        "0072_S_backup_cleanup_tool.svg",
        "0076_L_application_level_replication Copy.svg",
        "0083_L_acronis_instant_restore Copy.svg",
      ],
      titlesArray: [
        "AFP Connection to File Shares",
        "File Access for Mobile Devices",
        "Full Content Spotlight Searching",
        "Time Machine Backup to File Shares",
        "Absolute VM Protection",
        "Acronis Instant Restore"
      ],
      contentTitleClasses: "title",
      infosArray: [
        "With Acronis Files Connect, Macs connect to and mount file shares on Windows file servers and NAS as native AFP volumes. This allows Mac users to continue using the same tools.",
        [
          {
            text1: "Acronis Files Connect",
            className: "colored"
          },
          {
            text2: " isn’t limited to Macs. Seamless file access is also provided for mobile devices (iOS, Android, and Windows Phone) with intuitive browsing, searching, previewing.",
          }
        ],
        [
          {
            text1: "Acronis Files Connect links Mac Spotlight to a server-side index that seamlessly integrates with the native Windows Search service or a built-in ",
          },
          {
            text2: "Acronis content indexer.",
            className: "colored"
          }
        ],
        "With Acronis Files Connect, Mac users’ documents can be automatically backed up to a Windows file server or NAS, and users can selectively restore previous versions directly.",
        "Defend more hypervisors, including RedHat, KVM, Oracle VM, Citrix Xen, VMware and Hyper-V, with simple licensing per host allowing protection for an unlimited number of VMs ",
        "Reduce outage recovery time with best-in-industry RTO by starting any physical or virtual Windows or Linux system directly from the backup storage"
      ],
      infosClasses: "info",
      // <Footer>
      footerText: "Learn More",
      footerClasses: "footer-holder",
      screenWidth: 0
    };
  },
  computed: {
    iconsSrcArrayForColumn1() {
      return this.iconsSrcArray.filter((_, index) => !(index % 2));
    },
    iconsSrcArrayForColumn2() {
      return this.iconsSrcArray.filter((_, index) => (index % 2));
    },
    titlesArrayForColumn1() {
      return this.titlesArray.filter((_, index) => !(index % 2));
    },
    titlesArrayForColumn2() {
      return this.titlesArray.filter((_, index) => (index % 2));
    },
    infosArrayForColumn1() {
      return this.infosArray.filter((_, index) => !(index % 2));
    },
    infosArrayForColumn2() {
      return this.infosArray.filter((_, index) => (index % 2));
    },
  },
  methods: {
    onResize() {
      return this.screenWidth = window.screen.width;
    }
  },
  beforeMount() {
    return this.onResize();
  },
  mounted() {
    return window.addEventListener("resize", this.onResize);
  },
  beforeDestroy() {
    return window.removeEventListener("resize", this.onResize);
  }
};
</script>

<style scoped lang="sass">
@import "@/assets/vars.sass"

.holder
  text-align: left
@media (min-width: $mobile-width-start) and (max-width: $mobile-width-end)
  .holder
    margin: 0 16px
@media (min-width: $tablet-width-start) and (max-width: $pc-width-1024-end)
  .holder
    margin: 0 $pc-margin-right-2
@media (min-width: $pc-width-1280-start)
  .holder
    display: flex
    justify-content: center
    margin: 0 64px
@media (min-width: $pc-width-1440-start)
  .holder
    max-width: 1440px
    margin: auto
@media (min-width: $mobile-width-start) and (max-width: $tablet-width-end)
  .header-content-holder
    padding-top: $padding-top-3
@media (min-width: $pc-width-1024-start)
  .header-content-holder
    width: 100%
    display: flex
    justify-content: space-between
    margin-top: 88px
</style>
