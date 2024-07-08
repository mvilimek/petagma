<script setup>
import { ref, computed } from 'vue';
import BaseBreadcrumb from '@/components/shared/BaseBreadcrumb.vue';
import UiParentCard from '@/components/shared/UiParentCard.vue';
import { vMaska } from 'maska';
import UiChildCard from '@/components/shared/UiChildCard.vue';

const page = ref({ title: 'Mask Page' });
const breadcrumbs = ref([
  {
    title: 'Plugins',
    disabled: false,
    href: '#'
  },
  {
    title: 'Mask',
    disabled: true,
    href: '#'
  }
]);

const phoneoptions = { mask: ['+1 (###) ##-##-##', '+1 (###) ###-##-##'] };
const phoneValue = ref('');

const contactoptions = { mask: '+91 #### ###-###' };
const contactValue = ref('');

const hexoptions = { mask: '!#HHHHHH', tokens: { H: { pattern: /[0-9a-fA-F]/, uppercase: true } } };
const hexValue = ref('');

const dateoptions = { mask: '##/##/####' };
const dateValue = ref('');

const ipaddress = { mask: '###.###.###.###' };
const ipValue = ref('');

const ipv4address = { mask: '####.####.####.####' };
const ipv4Value = ref('');

const ipv6address = { mask: '####.####.####.####.####.####' };
const ipv6Value = ref('');

const maskedValue = ref('');
const inputValue = ref('');
const maskPattern = computed(() => ({ mask: maskedValue.value }));
</script>
<template>
  <BaseBreadcrumb :title="page.title" :breadcrumbs="breadcrumbs" />
  <v-row>
    <v-col cols="12" md="12">
      <UiParentCard title="Mask Input">
        <v-row>
          <!-- Base Buttons -->
          <v-col cols="12" lg="6">
            <UiChildCard title="Phone">
              <v-text-field v-model="phoneValue" v-maska:[phoneoptions] color="primary" label="Phone with Code" variant="outlined" />
              <v-text-field v-model="contactValue" v-maska:[contactoptions] color="primary" label="Contact Number" variant="outlined" />
              <v-text-field v-model="hexValue" v-maska:[hexoptions] color="primary" label="Hex color: #121113" variant="outlined" />
              <v-text-field v-model="dateValue" v-maska:[dateoptions] color="primary" label="Date Mask" variant="outlined" />
            </UiChildCard>
          </v-col>
          <v-col cols="12" lg="6">
            <UiChildCard title="Network">
              <v-text-field v-model="ipValue" v-maska:[ipaddress] color="primary" label="Ip Address" variant="outlined" />
              <v-text-field v-model="ipv4Value" v-maska:[ipv4address] color="primary" label="Ipv4 Address" variant="outlined" />
              <v-text-field v-model="ipv6Value" v-maska:[ipv6address] color="primary" label="Ipv6 Address" variant="outlined" />
            </UiChildCard>
          </v-col>
          <v-col cols="12" lg="12">
            <UiChildCard title="Custom">
              <v-text-field v-model="maskedValue" color="primary" variant="outlined" label="Make Mask to apply bottom input" />
              <v-text-field v-model="inputValue" v-maska:[maskPattern] color="primary" label="Masked Input" variant="outlined" />
            </UiChildCard>
          </v-col>
        </v-row>
      </UiParentCard>
    </v-col>
  </v-row>
</template>
