<script>
import * as pbi from "powerbi-client";

export default {
 name: 'HelloWorld',
 mounted () {
   const permissions = pbi.models.Permissions.All
   const config = {
     type: 'dashboard',
     tokenType: pbi.models.TokenType.Embed,
     accessToken: "H4sIAAAAAAAEAB2TR6-DVhSE_8vbEsn0EikLm15MNXUHXHrHtEuU_56X7OeMRt-c-fvHTmE_peDnzx_8EYVQ0mmU6b545tUWotDJ_I1V7UGP1nsVmZQDyr1WMKZdqTB83F4afdPMimDPePrUdXdDibXilQ7UGTYrISWGV8S6DYF5o7XDOuETfYJ4aJTgs-NNzJ0iepUhjSWKqBlPpI8l2-Hyc-yWpwAMBpmbkTQtldAxmfTJTpKmxcfeUit_p7lHi_bj4f539xpB6pgpv0FuHxWIMAq7mHpJE5Uw-TWgyvgyiQiuvtwlDnzpsBCQi1HyaX7wIbQwcRjiJAHpYxGQUDgaS9RGwoxsVJNXze5NxsZrI6tA6cTPqN5bjRSLibGYfV_jMdePiWCoL7b6BZ2Z6V6WQ4YyY4TgfnrH1GEeHZ9QF8IfdFoUmr4P_sw7NdX10HF3TMW9syPWY3KpqK-OvSX6wTNLAoONmi6iTZtC9ctTnfPWvm6ff-bX7VCOhvGEzBA5iTj8zPAL377COF-kedGPTQPEuIcX2veqc7hcPagvdXUGhbr92YJ0FhkYsdRA2Tm5BUdOqK_zpSrRN3lzxuGsqTS6STl4onTfc7U3W6gYp57lTKteNhtPVrSEbNLVvY_hnTLIdSL2BF_cZXI8PuyQujnWnmG75gGfNy2UuLWau1kiHsGvpeHeN59qOoJ8oW9xbyXqlj1aPFfobCKSzyNJzYkb1wFo4zObI3QoNX4uB3XLP3R66PPEc4SeDjMlkOrobwzWSAG4seC-IsH8ysClkBsMxUcoP5Iv_Z7Qx9BKxT4dXleCyqogLJWF64I8Nzv7IDHjhRPFZr9-_vjhVzhvk17A3zmIZCCmyoOn3gn07kpxAmSSNK7plavzv85o4EX9PQdI7fKqp1-EkZccWRP11RrJAj-Yk0ubMGeiYpYBXdzeasJLuWvW6IqWPQ1PmRrFOe35-Xp5oUipqAUkBZ0aL5qAQqjYxISjOGzZ3g7QCx0v97pm-1ATPjFP6fdDuM1xiyAGca3Gj6azKWnhsoalrOf8_CAztfUvDG1KfCy9yOlmJPJR9WhiRTTro5E-7YVXYfJWxOS2MFlxFv6oULoTaNL1ZbR93uhrvtKDfQTd6xUcHeAealjL1H6HLDnOXp5tmavRD_8ruRGvs6OzC6bstSx3dsOYmg0p2i5wLSxJ3jMp7PGF97J2_vXXf5jhXBerGvxSLk4nJxRjv75rKXg5YUkgDZ7_q7ymGtNtX4tfmVliCx8gSDfINxmSS_8bb_AbVK8WDsZhMsHajRNU3YPOJbczSd8sT7OvFBbEQx6BHrUYGz8fWCZuSOaNBOVpb2Ae0EW294IT63KDJ0gFN8BGrVOKmJyDud6sjpPhTbb4WiT1Bzlg2PhsQyI1vtCG-FvVe5F7Di3KCOk1t9nFUnSs6lGuUY4ubOwblQUWwbPZSJR2B2ZqNNKMbEQCGJgQB_uV42GZgcgQILNZSzfanm2_B6rsZgpRU6tUwaizJzCUdsvqWHSIKLr3ohHLh3fqQMbe7IXoi2VwzJuyn9r0IQQju8440fRlyYMgIu4PgK-J5o1BCKlANlN1cFpG3XVcePxXxj__AugO6FoCBgAA.eyJjbHVzdGVyVXJsIjoiaHR0cHM6Ly9XQUJJLVNPVVRILUNFTlRSQUwtVVMtcmVkaXJlY3QuYW5hbHlzaXMud2luZG93cy5uZXQiLCJlbWJlZEZlYXR1cmVzIjp7Im1vZGVybkVtYmVkIjpmYWxzZX19",
     embedUrl: "https://app.powerbi.com/dashboardEmbed?dashboardId=b504766d-2606-49bc-af5d-dd1032790ae1&config=eyJjbHVzdGVyVXJsIjoiaHR0cHM6Ly9XQUJJLVNPVVRILUNFTlRSQUwtVVMtcmVkaXJlY3QuYW5hbHlzaXMud2luZG93cy5uZXQiLCJlbWJlZEZlYXR1cmVzIjp7Im1vZGVybkVtYmVkIjpmYWxzZX19",
     id: "b504766d-2606-49bc-af5d-dd1032790ae1",
     pageView: 'fitToWidth',
     permissions: permissions,
   };

   let powerbi = new pbi.service.Service(pbi.factories.hpmFactory, pbi.factories.wpmpFactory, pbi.factories.routerFactory);
   const dashboardContainer = document.getElementById('container');
   const dashboard = powerbi.embed(dashboardContainer, config);

   dashboard.off("loaded");
   dashboard.off("rendered");
   dashboard.on("error", function () {
     this.dashboard.off("error");
   });
  }
 }
</script>

<template>
  <div>
   <section id="container" style="height: 950px" />
  </div>
</template>

<style scoped>
</style>

