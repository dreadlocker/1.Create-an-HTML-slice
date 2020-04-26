<template>
  <div class="holder">
    <div class="header-content-holder">
      <Header
        :groupDescriptor="groupDescriptor"
        :groupDescriptorClasses="groupDescriptorClasses"
        :sliceTitle="sliceTitle"
        :sliceTitleClasses="sliceTitleClasses"
        :sliceDescriptor="sliceDescriptor"
        :sliceDescriptorClasses="sliceDescriptorClasses"
        :sliceLead="sliceLead"
        :sliceLeadClasses="sliceLeadClasses"
        :screenWidth="screenWidth"
      />
      
      <template v-if="screenWidth < 576">
        <Content
          :featureIconsSrcArray="featureIconsSrcArray"
          :featureIconClasses="featureIconClasses"
          :featureTitlesArray="featureTitlesArray"
          :featureTitleClasses="featureTitleClasses"
          :featureBodyTextArray="featureBodyTextArray"
          :featureBodyTextClasses="featureBodyTextClasses"
        />
      </template>
      
      <template v-else-if="screenWidth >= 576 && screenWidth < 1024">
        <div class="content-holder-tablet-wrapper">
          <Content
            :featureIconsSrcArray="featureIconsSrcArrayForColumn1"
            :featureIconClasses="featureIconClasses"
            :featureTitlesArray="featureTitlesArrayForColumn1"
            :featureTitleClasses="featureTitleClasses"
            :featureBodyTextArray="featureBodyTextArrayForColumn1"
            :featureBodyTextClasses="featureBodyTextClasses"
          />
          <Content
            :featureIconsSrcArray="featureIconsSrcArrayForColumn2"
            :featureIconClasses="featureIconClasses"
            :featureTitlesArray="featureTitlesArrayForColumn2"
            :featureTitleClasses="featureTitleClasses"
            :featureBodyTextArray="featureBodyTextArrayForColumn2"
            :featureBodyTextClasses="featureBodyTextClasses"
          />
        </div>
      </template>
      
      <template v-else>
        <Content
          :featureIconsSrcArray="featureIconsSrcArrayForColumn1"
          :featureIconClasses="featureIconClasses"
          :featureTitlesArray="featureTitlesArrayForColumn1"
          :featureTitleClasses="featureTitleClasses"
          :featureBodyTextArray="featureBodyTextArrayForColumn1"
          :featureBodyTextClasses="featureBodyTextClasses"
        />
        <Content
          :featureIconsSrcArray="featureIconsSrcArrayForColumn2"
          :featureIconClasses="featureIconClasses"
          :featureTitlesArray="featureTitlesArrayForColumn2"
          :featureTitleClasses="featureTitleClasses"
          :featureBodyTextArray="featureBodyTextArrayForColumn2"
          :featureBodyTextClasses="featureBodyTextClasses"
        />
      </template>
    </div>

    <Footer
      v-if="screenWidth < 1024"
      :sliceLink="sliceLink"
      :sliceLinkClasses="sliceLinkClasses"
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
      groupDescriptor: "Sync and Share",
      groupDescriptorClasses: "group-descriptor",
      sliceTitle: "Acronis Cyber Disaster Recovery Cloud",
      sliceTitleClasses: "slice-title",
      sliceDescriptor: "Just Updated",
      sliceDescriptorClasses: "slice-descriptor",
      sliceLead: "A turnkey, self-service solution that lets you protect your customers’ workloads by recovering their IT systems and applications utilizing the Acronis cloud infrastructure.",
      sliceLeadClasses: "sub-title",
      // <Content>
      featureIconsSrcArray: [
        "0001_S_full_image_backup.svg",
        "0003_S_active_ransomware_protection.svg",
        ["0071_S_survival_kit.svg", "exclusive"],
        "0072_S_backup_cleanup_tool.svg",
        "0076_L_application_level_replication Copy.svg",
        "0083_L_acronis_instant_restore Copy.svg",
      ],
      featureIconClasses: "feature-icon",
      featureTitlesArray: [
        "AFP Connection to File Shares",
        "File Access for Mobile Devices",
        "Full Content Spotlight Searching",
        "Time Machine Backup to File Shares",
        "Absolute VM Protection",
        "Acronis Instant Restore"
      ],
      featureTitleClasses: "feature-title",
      featureBodyTextArray: [
        "With Acronis Files Connect, Macs connect to and mount file shares on Windows file servers and NAS as native AFP volumes. This allows Mac users to continue using the same tools.",
        [
          {
            text: "Acronis Files Connect",
            className: "colored"
          },
          {
            text: " isn’t limited to Macs. Seamless file access is also provided for mobile devices (iOS, Android, and Windows Phone) with intuitive browsing, searching, previewing.",
          }
        ],
        [
          {
            text: "Acronis Files Connect links Mac Spotlight to a server-side index that seamlessly integrates with the native Windows Search service or a built-in ",
          },
          {
            text: "Acronis content indexer.",
            className: "colored"
          }
        ],
        "With Acronis Files Connect, Mac users’ documents can be automatically backed up to a Windows file server or NAS, and users can selectively restore previous versions directly.",
        "Defend more hypervisors, including RedHat, KVM, Oracle VM, Citrix Xen, VMware and Hyper-V, with simple licensing per host allowing protection for an unlimited number of VMs ",
        "Reduce outage recovery time with best-in-industry RTO by starting any physical or virtual Windows or Linux system directly from the backup storage"
      ],
      featureBodyTextClasses: "feature-body-text",
      // <Footer>
      sliceLink: "Learn More",
      sliceLinkClasses: "slice-link",
      screenWidth: 0
    };
  },
  computed: {
    featureIconsSrcArrayForColumn1() {
      return this.featureIconsSrcArray.filter((_, index) => !(index % 2));
    },
    featureIconsSrcArrayForColumn2() {
      return this.featureIconsSrcArray.filter((_, index) => (index % 2));
    },
    featureTitlesArrayForColumn1() {
      return this.featureTitlesArray.filter((_, index) => !(index % 2));
    },
    featureTitlesArrayForColumn2() {
      return this.featureTitlesArray.filter((_, index) => (index % 2));
    },
    featureBodyTextArrayForColumn1() {
      return this.featureBodyTextArray.filter((_, index) => !(index % 2));
    },
    featureBodyTextArrayForColumn2() {
      return this.featureBodyTextArray.filter((_, index) => (index % 2));
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
    padding: 88px 0 $content-padding-bottom-2

.content-holder-tablet-wrapper
  display: flex
  justify-content: space-between
</style>
